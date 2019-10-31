---
title: Establezca el tiempo de espera al realizar llamadas externas en un complemento | MicrosoftDocs
description: Limite el período de tiempo que las llamadas externas esperarán una respuesta en los complementos
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/19/2019
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-timeout-when-making-external-calls-in-a-plug-in"></a>Establecer tiempo de espera al realizar llamadas externas en un complemento

**Categoría**: rendimiento

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

Si un complemento realiza solicitudes web externas que no responden rápidamente, el complemento esperará el período de tiempo de espera predeterminado completo antes producir error. Esta duración puede producir una transacción larga que pueda afectar a otras operaciones. Si se registra el complemento:

- Los usuarios pueden experimentar de forma sincrónica:

    - Aplicaciones basadas en modelos que dejan de responder
    - Interacciones lentas con el cliente
    - El explorador deja de responder

- De forma asincrónica, las ejecuciones de complementos pueden prolongarse durante más tiempo antes de dar error. 

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

El valor de tiempo de espera predeterminado para clientes .Net Htttp es de 100 segundos, solo 20 segundos menos que el tiempo disponible para que termine el complemento. Lo mejor es establecer un tiempo base esperado al que responderá un servicio de llamada. Cuanta más supere este tiempo de respuesta normal, mayor será la probabilidad de que finalmente produzca un error. Como práctica recomendada para rendimiento, es mejor que el error se produzca rápidamente que permitir que el período de tiempo de espera predeterminado expire. Deberá controlar el periodo que esperará la llamada al servicio externo.

El valor de tiempo de espera que debe establecer dependerá del servicio. Por ejemplo, si puede supervisar el rendimiento del servicio puede determinar una duración en la que 99,999% de las solicitudes tengan éxito y establecer el período de tiempo de espera con esa duración con un búfer de unos segundos. Esto evitará que los valores atípicos ocasionales tengan un impacto excesivo en el rendimiento del complemento.

Si usa la [clase System.Net.Http.HttpClient](/dotnet/api/system.net.http.httpclient), puede establecer el valor de `Timeout` de forma explícita, como se indica en este ejemplo que establece el tiempo de espera en 15 segundos.

```csharp
using (HttpClient client = new HttpClient())
{
  client.Timeout = TimeSpan.FromMilliseconds(15000); //15 seconds
  client.DefaultRequestHeaders.ConnectionClose = true; //Set KeepAlive to false
  

  HttpResponseMessage response =  client.GetAsync(webAddress).Result; //Make sure it is synchonrous
  response.EnsureSuccessStatusCode();

  string responseText = response.Content.ReadAsStringAsync().Result; //Make sure it is synchonrous
  tracingService.Trace(responseText);
  //Log success in the Plugin Trace Log:
  tracingService.Trace("HttpClientPlugin completed successfully.");
}
```

Si usa la [clase System.Net.WebClient](/dotnet/api/system.net.webclient), necesita crear una clase derivada y reemplazar el [método base GetWebRequest](/dotnet/api/system.net.webclient.getwebrequest) para establecer el tiempo de espera:

```csharp
  /// <summary>
  /// A class derived from WebClient with 15 second timeout and KeepAlive disabled
  /// </summary>
  public class CustomWebClient : WebClient
  {
    protected override WebRequest GetWebRequest(Uri address)
    {
      HttpWebRequest request = (HttpWebRequest)base.GetWebRequest(address);
      if (request != null)
      {
        request.Timeout = 15000; //15 Seconds
        request.KeepAlive = false;
      }
      return request;
    }
  }
```

A continuación puede usar esta clase en el código del complemento:

```csharp
using (CustomWebClient client = new CustomWebClient())
{
  byte[] responseBytes = client.DownloadData(webAddress);
  string response = Encoding.UTF8.GetString(responseBytes);
  tracingService.Trace(response);
  //Log success in the Plugin Trace Log:
  tracingService.Trace("WebClientPlugin completed successfully.");
}
```

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Ejemplo: acceso web desde un complemento de espacio aislado](../../org-service/samples/web-access-plugin.md)<br />
[Establecer KeepAlive en false para interactuar con hosts externos en un complemento](set-keepalive-false-interacting-external-hosts-plugin.md)
