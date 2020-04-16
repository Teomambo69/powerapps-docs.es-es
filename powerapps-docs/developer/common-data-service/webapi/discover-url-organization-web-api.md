---
title: Detectar la dirección URL de su organización (Common Data Service)| Microsoft Docs
description: Use el Servicio de detección para buscar las organizaciones (instancias) a las que pertenece el usuario conectado
ms.custom: ''
ms.date: 1/16/2020
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
ms.reviewer: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bc68a5ae74c72f2dbc9a8240253574348d85a7cd
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155092"
---
# <a name="discover-the-url-for-your-organization"></a>Detectar la URL de su organización

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Al acceder al servicio de detección con la API OData v4 RESTful, puede agregar los parámetros estándar `$filter` y `$select` a la solicitud de servicio para personalizar la lista devuelta de datos de instancia.

> [!IMPORTANT]
> - A partir del 2 de marzo de 2020, el servicio de detección *regional* [quedará obsoleto](/power-platform/important-changes-coming#regional-discovery-service-is-deprecated). Las aplicaciones deben usar el servicio de detección global que se documenta en este tema.  
> - Para los usuarios de Dynamics 365 US Government, está disponible un extremo de servicio de detección *global* para usuarios de **GCC** y **GCC High** y la dirección URL es diferente de la dirección URL del servicio de detección global habitual. Más información: [Direcciones URL de Dynamics 365 Government](https://docs.microsoft.com/dynamics365/customer-engagement/admin/government/microsoft-dynamics-365-government#dynamics-365-us-government-urls).

  
## <a name="information-provided-by-the-discovery-service"></a>Información proporcionada por el servicio de detección 
 
La información de la organización se almacenan en la entidad `Instance` del servicio de detección.  Para ver el tipo de información incluida en esa entidad, envíe una solicitud HTTP GET al servicio para una de sus instancia.  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
```  
  
En el ejemplo anterior, el servicio de detección global se utiliza para obtener la información de la organización de la instancia con un nombre único de "myorg". Se tratará con mayor detenimiento más información acerca de esta solicitud más adelante en este tema.  

### <a name="scope-of-the-returned-information"></a>Ámbito de la información devuelta

Para el servicio de detección global, el conjunto de entidades `Instances` devuelve el conjunto de instancias al que el usuario tiene acceso en todas las geografías, cuando no se aplica ningún filtro.   Los datos de devolución tiene un ámbito como se describe a continuación.  
  
-   Incluye todas las instancias en la nube comercial donde el usuario se aprovisiona y habilita, salvo que no se devuelven instancias de nubes soberanas
-   No incluye las instancias donde está deshabilitada la cuenta del usuario
-   No incluye las instancias en las que los usuarios se han filtrado basándose en un grupo de seguridad de la instancia
-   No incluye instancias donde el usuario tiene acceso como resultado de ser administrador delegado
-   Si el usuario que llama no tiene acceso a ninguna instancia, la respuesta devuelve simplemente una lista vacía

## <a name="how-to-access-the-discovery-service"></a>Cómo acceder al servicio de detección

En general, la dirección web del servicio de detección tiene el siguiente formato: `<service base address>/api/discovery/`.  Encontrará con facilidad las direcciones web y el número de versión para su implementación en la aplicación web de Common Data Service si navega hasta **Configuración > Personalización > Recursos de desarrollador**  
  
### <a name="common-data-service-discovery-services"></a>Common Data Service Servicios de detección  

La dirección base del servicio de detección global es: `https://globaldisco.crm.dynamics.com/`. Esto da como resultado la dirección de servicio de `https://globaldisco.crm.dynamics.com/api/discovery/`.  
  
## <a name="using-the-discovery-service"></a>Uso del servicio de detección  

Se usa un conjunto de entidad denominado `Instances` para recopilar información de la instancia. Puede usar `$select` y `$filter` con el conjunto de entidades Instancias para filtrar los datos devueltos. También puede usar `$metadata` para obtener el documento de metadatos del servicio.  
  
### <a name="authentication"></a>Autenticación

Para acceder al servicio de detección se requiere autenticación con un token de acceso de OAuth.

Cuando se configura el servicio de detección para la autenticación de OAuth, una solicitud enviada al servicio sin un token de acceso desencadena un desafío del portador con la autoridad del extremo "común" y el id. de recurso del servicio.

### <a name="cors-support"></a>Soporte técnico de CORS

El servicio de detección admite la norma CORS para acceso de origen cruzado. Para obtener más información sobre el soporte técnico de CORS, consulte [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página](../oauth-cross-origin-resource-sharing-connect-single-page-application.md).  
  
### <a name="examples"></a>Ejemplos  
  
-   Obtenga los detalles de una instancia determinada. Si sale del GUID, se devuelven todas las instancias a las que el usuario autenticado tiene acceso.  
  
    ```http      
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(<guid>)
    ```  
  
-   Puede usar el atributo UniqueName como clave alternativa.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances(UniqueName='myorg')  
    ```  
  
-   Recupere una lista de instancias disponible, filtrada por tipo de producción.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v2.0/Instances?$select=DisplayName,Description&$filter=Type+eq+0   
    ```  
  
## <a name="see-also"></a>Vea también

[Ejemplo de servicio de detección (C#)](samples/global-discovery-service-csharp.md)

