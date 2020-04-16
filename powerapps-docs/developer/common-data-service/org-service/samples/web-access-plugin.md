---
title: 'Ejemplo: acceso web desde un complemento (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo escribir un complemento que tiene acceso a recursos en la red.
ms.custom: ''
ms.date: 8/19/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1e6d56cfe5bf51a58bb81dc845df19f3af62a4de
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155500"
---
# <a name="sample-web-access-from-a-plug-in"></a>Ejemplo: Acceso web desde un complemento

En este ejemplo se muestra cómo escribir un complemento que tiene acceso a recursos en la red como un servicio web o fuente. También demuestra cómo limitar la duración de tiempo permitida para esta llamada. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WebAccessPlugin).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

1. Descargar o clonar el informe de [Muestras](https://github.com/Microsoft/PowerApps-Samples) para que tenga una copia local. Este ejemplo se encuentra en PowerApps-Samples-master\cds\orgsvc\C#\WebAccessPlugin.
1. Hay dos diferentes ejemplos de clase de complemento: 
    - WebClientPlugin usa [Clase WebClient](/dotnet/api/system.net.webclient)
    - HttpClientPlugin usa [Clase HttpClient](/dotnet/api/system.net.http.httpclient)
1. Abra la solución de ejemplo en Visual Studio, vaya a las propiedades del proyecto y comprueba que el ensamblado se firmará durante la compilación. Presione la F6 para compilar el ensamblado del ejemplo (WebAccessPlugin.dll).
1. Ejecute la herramienta de registro de complementos y registre el ensamblado en el espacio aislado y la base de datos del servidor de Common Data Service. 
1. Para cualquiera de los tipos de complementos, cuando registre un paso, especifique una cadena URI web (es decir, `https://www.microsoft.com` en el campo no seguro de configuración.
    - Si no se proporciona un valor, se usará el predeterminado `https://www.bing.com`.
1. Use una aplicación o escriba código para realizar la operación adecuada para invocar la solicitud de mensaje y de entidad donde registró al complemento.
1. Cuando el complemento se ejecuta, si la duración de la llamada supera el límite de 15 segundos, lanzará un error. En caso contrario deberá tener éxito.
1. Cuando haya terminado con la prueba, cancele el registro del ensamblado y el paso.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Cuando se ejecuta, el complemento descarga los datos de la página web de la dirección de servicio web especificada (o la dirección predeterminada). Si la solicitud supera el límite de 15 segundos lanzará una [InvalidPluginExecutionException](/dotnet/api/microsoft.xrm.sdk.invalidpluginexecutionexception) y escribirá los detalles en el registro de seguimiento del complemento.

- Si el complemento `WebClientPlugin` produce error, escribirá algo como lo siguiente en el registro de seguimiento del complemento:
    ```
    Downloading the target URI: https://www.bing.com
    Exception: Microsoft.Xrm.Sdk.InvalidPluginExecutionException: The timeout elapsed while attempting to issue the request. ---> System.Net.WebException: The operation has timed out
      at System.Net.WebClient.DownloadDataInternal(Uri address, WebRequest& request)
      at System.Net.WebClient.DownloadData(Uri address)
      at PowerApps.Samples.WebClientPlugin.Execute(IServiceProvider serviceProvider)
      --- End of inner exception stack trace ---
      at PowerApps.Samples.WebClientPlugin.Execute(IServiceProvider serviceProvider)
    ```

- Si el complemento `HttpClientPlugin` produce error, escribirá algo como lo siguiente en el registro de seguimiento del complemento:
    ```
    Downloading the target URI: https://www.bing.com
    Inner Exceptions:
      Exception: System.Threading.Tasks.TaskCanceledException: A task was canceled.
    Exception: Microsoft.Xrm.Sdk.InvalidPluginExecutionException: An exception occurred while attempting to issue the request.
       at PowerApps.Samples.HttpClientPlugin.Execute(IServiceProvider serviceProvider)
    ```
    [TaskCanceledException](/dotnet/api/system.threading.tasks.taskcanceledexception) es un tanto ambiguo sobre la causa de la tarea que es cancelada. Para obtener una solución más completa que muestre cómo detectar explícitamente errores debidos tiempos de temporización, vea esta entrada de blog: [Mejor control de tiempos de espera con HttpClient](https://thomaslevesque.com/2018/02/25/better-timeout-handling-with-httpclient/).

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprueba el parámetro de configuración sin proteger del constructor para un valor de dirección web; de lo contrario, se usa el valor predeterminado.
2. En función de qué complemento esté registrado, el método `Execute` del complemento utiliza [Clase HttpClient](/dotnet/api/system.net.webclient) o [Clase HttpClient](/dotnet/api/system.net.http.httpclient) para descargar datos de la página web.
3. Si la llamada superó la duración de 15 segundos especificada, se lanzará una [InvalidPluginExecutionException](/dotnet/api/microsoft.xrm.sdk.invalidpluginexecutionexception) y detalles sobre el error se escribirán en el registro de seguimiento de complementos.

### <a name="demonstrate"></a>Demostración

#### <a name="webclientplugin-plugin"></a>Complemento WebClientPlugin

1. Utiliza una clase `CustomWebClient` derivada para etablecer la [Propiedad WebRequest.Timeout](/dotnet/api/system.net.webrequest.timeout) que no está disponible en la clase `WebClient`.

   ````
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
    ````

1. Utiliza el [Método WebClient.DownloadData](/dotnet/api/system.net.webclient.downloaddata) para descargar los datos del recurso.
1. Muestra cómo analizar la [Clase WebException](/dotnet/api/system.net.webexception) esperada y usar la [Propiedad Status](/dotnet/api/system.net.webexception.status) para determinar si la causa del error fue un tiempo de espera.

#### <a name="httpclientplugin-plugin"></a>Complemento HttpClientPlugin

1. Utiliza la [Clase HttpClient](/dotnet/api/system.net.http.httpclient) y establece la [Propiedad Timeout](/dotnet/api/system.net.http.httpclient.timeout) para limitar el tiempo permitido para que la operación se complete.
1. Captura la [Clase AggregateException](/dotnet/api/system.aggregateexception) esperada y examina las excepciones internas para la [TaskCanceledException](/dotnet/api/system.threading.tasks.taskcanceledexception) esperada


### <a name="see-also"></a>Vea también

[Acceso a recursos web externos](../../access-web-services.md)<br/>
[Registro de un complemento](../../register-plug-in.md)