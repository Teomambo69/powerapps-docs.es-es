---
title: Uso del servicio de detección con las ensamblados SDK (Common Data Service) | Microsoft Docs
description: Describe cómo usar los servicios de detección con las API disponibles en los ensamblados SDK.
ms.custom: ''
ms.date: 1/16/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1eaf51018a94a226a5fa240a6f18f6107dc833dd
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2975687"
---
# <a name="use-the-discovery-service-with-the-sdk-assemblies"></a>Uso del servicio de detección con las ensamblados SDK

> [!IMPORTANT]
> A partir del 2 de marzo de 2020, el servicio de detección *regional* [quedará obsoleto](/power-platform/important-changes-coming#regional-discovery-service-is-deprecated).
> 
> Para obtener información sobre cómo hacer la transición para usar el servicio de detección *global*, consulte [Modificar su código para usar el servicio de detección global](../webapi/discovery-orgsdk-to-webapi.md).

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Para acceder al servicio de detección con las API de los ensamblados SDK, agregue una referencia al ensamblado `Microsoft.Xrm.Sdk.dll` al proyecto de Visual Studio. A continuación, agregue una instrucción `using` para acceder al espacio de nombres <xref:Microsoft.Xrm.Sdk.Discovery>.

<xref:Microsoft.Xrm.Sdk.WebServiceClient.DiscoveryWebProxyClient> implementa la interfaz <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService>.

La interfaz <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService> proporciona <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)> método que usará para pasar de una instancia de la clase de <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> abstracta.

## <a name="regional-discovery-services"></a>Servicios de detección regionales

Cuando crea un instancia de <xref:Microsoft.Xrm.Sdk.WebServiceClient.DiscoveryWebProxyClient> deberá proporcionar una dirección URL para un centro de datos regional mediante uno de los siguientes valores.

[!INCLUDE [regional-discovery-services](../../../includes/regional-discovery-services.md)]

> [!NOTE]
> Si no conoce la región del usuario, debe recorrer las regiones disponibles hasta obtener resultados. Un único servicio de detección global también está disponible. Más información: [Detectar la URL de su organización](../webapi/discover-url-organization-web-api.md).

## <a name="discovery-service-messages"></a>Mensajes del servicio de detección

Hay tres mensajes que puede usar y que heredan todos de las clase <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> abstracta.

 En la tabla siguiente se muestran los mensajes compatibles con el método <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)>.  
  
|Mensaje|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveUserIdByExternalIdRequest>|Recupera el id. del usuario que inició sesión en Common Data Service|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationRequest>|Recupera información acerca de una organización.|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest>|Recupera información sobre las organizaciones a las que pertenezca el usuario.|  

## <a name="example"></a>Ejemplo

El siguiente código para una aplicación de consola usa el mensaje <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest> para recuperar todas las organizaciones de un usuario.

```csharp
using System;
using System.Linq;
using Microsoft.Xrm.Sdk.Discovery;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Xrm.Sdk.WebServiceClient;

namespace DiscoveryServiceSample
{
    class Program
    {
        //These sample application registration values are available for all online instances.
        // this sample requires ADAL.net 5.2 + 
        public static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d";

        static OrganizationDetailCollection GetOrganizationDetails(DiscoveryWebProxyClient svc)
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
            string authority = @"https://login.microsoftonline.com/common";
            string northAmericaResourceUrl = "https://disco.crm.dynamics.com";
            string discoveryUrl = $"{northAmericaResourceUrl}/XRMServices/2011/Discovery.svc/web";
            Uri discoveryUri = new Uri(discoveryUrl);

            AuthenticationContext authContext = new AuthenticationContext(authority, false);
            string username = "you@yourorg.onmicrosoft.com";
            string password = "yourPassword"; 

            AuthenticationResult authResult = null;
            if (username != string.Empty && password != string.Empty)
            {
                UserPasswordCredential cred = new UserPasswordCredential(username, password);
                authResult = authContext.AcquireTokenAsync(northAmericaResourceUrl, clientId, cred).Result;
            }

           
            using (var svc = new DiscoveryWebProxyClient(discoveryUri))
            {
                svc.HeaderToken = authResult.AccessToken;

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
  URL: https://orgaservice.crm.dynamics.com/
  Name: OrganizationService
  URL: https://orgaservice.api.crm.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgaservice.api.crm.dynamics.com/XRMServices/2011/OrganizationData.svc

Organization Name: Organization B
Unique Name: orgb
Endpoints:
  Name: WebApplication
  URL: https://orgbservice.crm.dynamics.com/
  Name: OrganizationService
  URL: https://orgbservice.api.crm.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgbservice.api.crm.dynamics.com/XRMServices/2011/OrganizationData.svc
```

> [!NOTE]
> `OrganizationDataService` es el servicio de datos de la organización en desuso, no la API web. Este servicio no incluye una dirección URL para la API web.


### <a name="see-also"></a>Vea también

[Servicios de detección](../discovery-service.md)<br />
[Detectar la URL de su organización](../webapi/discover-url-organization-web-api.md)
