---
title: Detectar la dirección URL de su organización con la API web (Common Data Service)| Microsoft Docs
description: Obtenga información sobre cómo usar la API web para detectar en el tiempo de ejecución las organizaciones o instancias a las que pertenece el usuario que ha iniciado sesión
ms.custom: ''
ms.date: 04/22/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 2db13b4e-0e7c-4f25-b7be-70a612fb96e2
caps.latest.revision: 18
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7b69f19979b154a08aca23dacab58e4882066495
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909294"
---
# <a name="discover-the-url-for-your-organization-using-the-web-api"></a>Detecte la dirección URL de su organización con la API web.

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Con el servicio de detección de la API web, puede usar los parámetros `$filter` y `$select` estándar para una solicitud de servicio de API web para personalizar la lista devuelta de datos de la instancia.
<!-- TODO should only talk about the global discovery service -->

## <a name="global-discovery-service"></a>Servicio de detección global

Además de los servicios de detección específicos del centro de datos, que están disponibles en el extremo 2011 (SOAP) y a través de la API web, también hay un servicio de detección global de la API web que abarca todos los centros de datos operativos. Para obtener más información acerca del servicio de detección en el extremo de 2011, consulte [Servicio de detección](../org-service/discovery-service.md)

> [!NOTE]
> Se recomienda que los usuarios cambien del antiguo servicio de detección regional (`https://disco.crm.dynamics.com`) al servicio de detección global (`https://globaldisco.crm.dynamics.com`).
> 
> Para usuarios de Dynamics 365 US Government, el servicio de detección global está disponible para usuarios de **GCC** y **GCC High** , y la dirección URL es diferente de la dirección URL del servicio de detección global regular. Más información: [Direcciones URL de Dynamics 365 Government](https://docs.microsoft.com/dynamics365/customer-engagement/admin/government/microsoft-dynamics-365-government#dynamics-365-us-government-urls).

  
## <a name="information-provided-by-the-discovery-service"></a>Información proporcionada por el servicio de detección 
 
 La información de la organización se almacenan en la entidad `Instance` del servicio de detección.  Para ver el tipo de información incluida en esa entidad, envíe una solicitud HTTP GET al servicio para una de sus instancia.  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
```  
  
En el ejemplo anterior, el servicio de detección global de Common Data Service se utiliza para obtener la información de la organización de la instancia con un nombre único de "myorg". Se tratará con mayor detenimiento más información acerca de esta solicitud más adelante en este tema.  

 

  
### <a name="scope-of-the-returned-information"></a>Ámbito de la información devuelta

Para el servicio de detección global, el conjunto de entidades `Instances` devuelve el conjunto de instancias al que el usuario tiene acceso en todas las geografías, cuando no se aplica ningún filtro.   Los datos de devolución tiene un ámbito como se describe a continuación.  
  
-   Incluye todas las instancias en la nube comercial donde el usuario se aprovisiona y habilita, salvo que no se devuelven instancias de nubes soberanas
-   No incluye las instancias donde está deshabilitada la cuenta del usuario
-   No incluye las instancias en las que los usuarios se han filtrado basándose en un grupo de seguridad de la instancia
-   No incluye instancias donde el usuario tiene acceso como resultado de ser administrador delegado
-   Si el usuario que llama no tiene acceso a ninguna instancia, la respuesta devuelve simplemente una lista vacía

## <a name="how-to-access-the-discovery-services"></a>Cómo obtener acceso a los servicios de detección

En general, la dirección de la API web del servicio de detección tiene el siguiente formato: `<service base address>/api/discovery/`.  A continuación, se identifican las direcciones para cada tipo de implementación. Encontrará con facilidad las direcciones de la API web y el número de versión para su implementación en la aplicación web de Common Data Service si navega hasta **Configuración > Personalización > Recursos de desarrollador**  
  
### <a name="common-data-service-discovery-services"></a>Common Data Service Servicios de detección  

La dirección base del servicio de detección global es: `https://globaldisco.crm.dynamics.com/`. Esto da como resultado la dirección de servicio de `https://globaldisco.crm.dynamics.com/api/discovery/`.  
  
## <a name="using-the-discovery-service"></a>Uso del servicio de detección  

Se usa un conjunto de entidad denominado `Instances` para recopilar información de la instancia. Puede usar `$select` y `$filter` con el conjunto de entidades Instancias para filtrar los datos devueltos. También puede usar `$metadata` para obtener el documento de metadatos del servicio.  
  
### <a name="authentication"></a>Autenticación

Las instancias de la API web de Common Data Service del servicio de detección requieren autenticación con tokens de acceso de OAuth.

Cuando se configura el servicio de detección para la autenticación de OAuth, una solicitud enviada a la API web de servicio sin un token de acceso desencadena un desafío del portador con la autoridad del extremo "común" y el id. de recurso del servicio.
### <a name="cors-support"></a>Soporte técnico de CORS

La API web del servicio de detección admite la norma CORS para acceso de origen cruzado como hace la Web API.  Para obtener más información sobre el soporte técnico de CORS, consulte [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página](../oauth-cross-origin-resource-sharing-connect-single-page-application.md).  
  
### <a name="examples"></a>Ejemplos  
  
-   Obtenga los detalles de una instancia determinada. Si sale del GUID, se devuelven todas las instancias a las que el usuario autenticado tiene acceso.  
  
    ```http      
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(<guid>)
    GET https://disco.crm.dynamics.com/api/discovery/v9.0/Instances(<guid>)  
    ```  
  
-   Puede usar el atributo UniqueName como clave alternativa.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
    ```  
  
-   Recupere una lista de instancias disponible, filtrada por tipo de producción.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances?$select=DisplayName,Description&$filter=Type+eq+0   
    ```  
  
-   Recupere el valor de la propiedad del id. de la instancia específica.  
  
    ```http  
    GET https://disco.crm.dynamics.com/api/discovery/v9.0/Instances(UniqueName='myorg')/Id/$value  
    ```

## <a name="see-also"></a>Vea también

[Ejemplo de servicio de detección global de la API web (C#)](samples/global-discovery-service-csharp.md)

