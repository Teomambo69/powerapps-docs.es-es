---
title: Uso del servicio de detección con los ensamblados SDK (Common Data Service) | Microsoft Docs
description: Describe cómo usar los servicios de detección con ensamblados SDK de .NET.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-discovery-service-with-the-sdk-assemblies"></a>Uso del servicio de detección con las ensamblados SDK

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]


Para usar el servicio de detección con los ensamblados SDK, agregue una referencia al ensamblado `Microsoft.Xrm.Sdk.dll` al proyecto de Visual Studio. A continuación, agregue una instrucción `using` o <xref:Microsoft.Xrm.Sdk.Discovery> para acceder al espacio de nombres Microsoft.Xrm.Sdk.Discovery. 

<xref:Microsoft.Xrm.Sdk.Client.DiscoveryServiceProxy> implementa la interfaz <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService>.

La interfaz <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService> proporciona <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)> método que usará para pasar de una instancia de la clase de <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> abstracta.

## <a name="regional-discovery-services"></a>Servicios de detección regionales

Cuando crea un instancia de <xref:Microsoft.Xrm.Sdk.Client.DiscoveryServiceProxy> deberá proporcionar una dirección URL para un centro de datos regional mediante uno de los siguientes valores.

[!INCLUDE [regional-discovery-services](../../../includes/regional-discovery-services.md)]

> [!NOTE]
> Si no conoce la región del usuario, debe recorrer las regiones disponibles hasta obtener resultados. La API web ofrece un único servicio de detección global. Más información: [Detectar la dirección URL de su organización con la API web](../webapi/discover-url-organization-web-api.md).

## <a name="discovery-service-messages"></a>Mensajes del servicio de detección

Hay tres mensajes que puede usar y que heredan todos de las clase <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> abstracta.

 En la tabla siguiente se muestran los mensajes compatibles con el método <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)>.  
  
|Mensaje|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveUserIdByExternalIdRequest>|Recupera el id. del usuario que inició sesión en Common Data Service.|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationRequest>|Recupera información acerca de una organización.|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest>|Recupera información sobre las organizaciones a las que pertenezca el usuario.|  

## <a name="example"></a>Ejemplo

El siguiente código para una aplicación de consola usa el mensaje <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest> para recuperar todas las organizaciones de un usuario.

```csharp
using System;
using System.Linq;
using Microsoft.Xrm.Sdk.Discovery;
using Microsoft.Xrm.Sdk.Client;
using System.ServiceModel.Description;

namespace DiscoveryServiceSample
{
  class Program
  {

    static OrganizationDetailCollection GetOrganizationDetails(DiscoveryServiceProxy svc)
    {

      var request = new RetrieveOrganizationsRequest()
      {
        AccessType = EndpointAccessType.Default,
        Release = OrganizationRelease.Current
      };
      try
      {
        var response = (RetrieveOrganizationsResponse)svc.Execute(request);
        return response.Details;
      }
      catch (Exception)
      {
        throw;
      }
    }
    static void Main(string[] args)
    {
      string canadaUrl = "https://disco.crm3.dynamics.com/XRMServices/2011/Discovery.svc";
      Uri discoveryUri = new Uri(canadaUrl);

      ClientCredentials creds = new ClientCredentials();
      creds.UserName.UserName = "you@yourorg.onmicrosoft.com";
      creds.UserName.Password = "yourPassword";

      using (var svc = new DiscoveryServiceProxy(discoveryUri, null, creds, null))
      {

        OrganizationDetailCollection details = GetOrganizationDetails(svc);

        details.ToList().ForEach(x =>
        {
          Console.WriteLine("Organization Name: {0}", x.FriendlyName);
          Console.WriteLine("Unique Name: {0}", x.UniqueName);
          Console.WriteLine("Endpoints:");
          foreach (var endpoint in x.Endpoints)
          {
            Console.WriteLine("  Name: {0}", endpoint.Key);
            Console.WriteLine("  URL: {0}", endpoint.Value);
          }
          Console.WriteLine();
        });
      };
      Console.ReadLine();
    }
  }
}

```

Los resultados pueden asemejarse a estos para un usuario con acceso a dos instancias:

```
Organization Name: Organization A
Unique Name: orga
Endpoints:
  Name: WebApplication
  URL: https://orgaservice.crm3.dynamics.com/
  Name: OrganizationService
  URL: https://orgaservice.api.crm3.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgaservice.api.crm3.dynamics.com/XRMServices/2011/OrganizationData.svc

Organization Name: Organization B
Unique Name: orgb
Endpoints:
  Name: WebApplication
  URL: https://orgbservice.crm3.dynamics.com/
  Name: OrganizationService
  URL: https://orgbservice.api.crm3.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgbservice.api.crm3.dynamics.com/XRMServices/2011/OrganizationData.svc
```

> [!NOTE]
> `OrganizationDataService` es el servicio de datos de la organización en desuso, no la API web. Este servicio no incluye una dirección URL para la API web.


### <a name="see-also"></a>Vea también

[Servicios de detección](../discovery-service.md)<br />
[Detecte la dirección URL de su organización con la API web.](../webapi/discover-url-organization-web-api.md)