---
title: Ejemplo de servicio de detección global (C#) (Common Data Service) | Microsoft Docs
description: En este ejemplo se muestra cómo acceder al servicio de detección global utilizando la API OData v4 RESTful
ms.custom: ''
ms.date: 1/16/2020
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c65092ed5b34bd06645e92f691cfe07ffc3eb233
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155016"
---
# <a name="global-discovery-service-sample-c"></a>Ejemplo de servicio de detección global (C#)

En este ejemplo se muestra cómo acceder al servicio de detección utilizando la API OData v4 RESTful.

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

Este ejemplo está disponible en GitHub en [https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery)

## <a name="what-this-sample-does"></a>Qué hace este ejemplo"
" Este ejemplo devuelve las instancias disponibles de Common Data Service para una credencial de usuario determinada.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Este ejemplo usará la información de sus credenciales en el archivo App.config, pero no usará la dirección URL configurada en la cadena de conexión.
En su lugar, solo usará las credenciales de usuario y el identificador de cliente.
''''''''''''
### <a name="demonstrates"></a>Demostraciones

Este ejemplo usa un HttpClient para autenticar mediante ADAL (v2.29) e invocar al servicio de detección para que devuelva información sobre las instancias disponibles a las que se puede conectar el usuario.

El ejemplo dependen del método `GetInstances` y la clae `Instance` a continuación:

```csharp    
    /// <summary>
    /// Uses the Discovery Service to return organization instances.
    /// </summary>
    /// <param name="clientId">The Azure AD client (app) registration</param>
    /// <param name="username">The user name</param>
    /// <param name="password">The password</param>
    /// <returns>A List of Instances</returns>
    static List<Instance> GetInstances(string clientId, string username, string password)
    {

      string GlobalDiscoUrl = "https://globaldisco.crm.dynamics.com/";
      AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.com", false);

      UserCredential cred = new UserCredential(username, password);
      AuthenticationResult authResult = authContext.AcquireToken(GlobalDiscoUrl, clientId, cred);
'
      HttpClient client = new HttpClient();
      client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);
      client.Timeout = new TimeSpan(0, 2, 0);
      client.BaseAddress = new Uri(GlobalDiscoUrl);

      HttpResponseMessage response = client.GetAsync("api/discovery/v2.0/Instances", HttpCompletionOption.ResponseHeadersRead).Result;


      if (response.IsSuccessStatusCode)
      {
        //Get the response content and parse it.
        string result = response.Content.ReadAsStringAsync().Result;
        JObject body = JObject.Parse(result);
        JArray values = (JArray)body.GetValue("value");''

        if (!values.HasValues)
        {
          return new List<Instance>();
        }'

        return JsonConvert.DeserializeObject<List<Instance>>(values.ToString());
      }'
      else
      {
        throw new Exception(response.ReasonPhrase);
      }'
    }
```


```csharp
/// <summary>
  /// Object returned from the Discovery Service.
  /// </summary>
  class Instance
  {
    public string Id { get; set; }
    public string UniqueName { get; set; }
    public string UrlName { get; set; }
    public string FriendlyName { get; set; }
    public int State { get; set; }
    public string Version { get; set; }
    public string Url { get; set; }
    public string ApiUrl { get; set; }
    public DateTime LastUpdated { get; set; }
  }
```

                                                                                                                    '''