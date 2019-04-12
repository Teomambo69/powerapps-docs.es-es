---
title: Identificación de la dirección URL de la organización mediante la API web (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo usar la API web para detectar en el tiempo de ejecución las organizaciones o instancias a las que pertenece el usuario que ha iniciado sesión
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 2db13b4e-0e7c-4f25-b7be-70a612fb96e2
caps.latest.revision: 18
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="discover-the-url-for-your-organization-using-the-web-api"></a>Detecte la dirección URL de su organización con la API web.

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Con el servicio de detección de la API web, puede usar los parámetros `$filter` y `$select` estándar para una solicitud de servicio de API web para personalizar la lista devuelta de datos de la instancia.
<!-- TODO should only talk about the global discovery service -->
Además de los servicios de detección específicos del centro de datos, que están disponibles en el extremo 2011 (SOAP) y a través de la API web, también hay un servicio de detección global de la API web que abarca todos los centros de datos operativos. Para obtener más información acerca del servicio de detección en el extremo de 2011, consulte [Servicio de detección](../org-service/discovery-service.md)

  
## <a name="information-provided-by-the-discovery-service"></a>Información proporcionada por el servicio de detección 
 
 La información de la organización se almacenan en la entidad `Instance` del servicio de detección.  Para ver el tipo de información incluida en esa entidad, envíe una solicitud HTTP GET al servicio para una de sus instancia.  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
```  
  
En el ejemplo anterior, el servicio de detección global Common Data Service se utiliza para obtener la información de la organización de la instancia con un nombre único de "myorg". Se tratará con mayor detenimiento más información acerca de esta solicitud más adelante en este tema.  
  
### <a name="scope-of-the-returned-information"></a>Ámbito de la información devuelta

Para el servicio de detección global, el conjunto de entidades `Instances` devuelve el conjunto de instancias al que el usuario tiene acceso en todas las geografías, cuando no se aplica ningún filtro.   Los datos de devolución tiene un ámbito como se describe a continuación.  
  
-   Incluye todas las instancias en la nube comercial donde el usuario se aprovisiona y habilita, salvo que no se devuelven instancias de nubes soberanas
-   No incluye las instancias donde está deshabilitada la cuenta del usuario
-   No incluye las instancias en las que los usuarios se han filtrado basándose en un grupo de seguridad de la instancia
-   No incluye instancias donde el usuario tiene acceso como resultado de ser administrador delegado
-   Si el usuario que llama no tiene acceso a ninguna instancia, la respuesta devuelve simplemente una lista vacía

## <a name="how-to-access-the-discovery-services"></a>Cómo obtener acceso a los servicios de detección

En general, la dirección de la API web del servicio de detección tiene el siguiente formato: `<service base address>/api/discovery/`.  A continuación, se identifican las direcciones para cada tipo de implementación. Encontrará con facilidad las direcciones de la API web y el número de versión para su implementación en la aplicación web de Common Data Service si navega hasta **Configuración > Personalización > Recursos de desarrollador**  
  
### <a name="common-data-service-discovery-services"></a>Servicios de descarga de Common Data Service  

La dirección base del servicio de detección global es: `https://globaldisco.crm.dynamics.com/`. Esto da como resultado la dirección de servicio de `https://globaldisco.crm.dynamics.com/api/discovery/`.  
  
<!-- TODO:
The service base address of the Discovery service for a datacenter is : `https://disco.crm[N].dynamics.com/`. This results in the Discovery service address of `https://disco.crm[N].dynamics.com/api/discovery/`. Each datacenter has an N number associated with it. For a complete list of available Common Data Service datacenters, and their N numbers,  see [Download endpoints using Developer resources page](../developer-resources-page.md).   -->
  
## <a name="using-the-discovery-service"></a>Uso del servicio de detección  

Se usa un conjunto de entidad denominado `Instances` para recopilar información de la instancia. Puede usar `$select` y `$filter` con el conjunto de entidades Instancias para filtrar los datos devueltos. También puede usar `$metadata` para obtener el documento de metadatos del servicio.  
  
### <a name="authentication"></a>Autenticación

Las instancias de la API web de Common Data Service del servicio de detección requieren autenticación con tokens de acceso de OAuth. Las instancias de IFD o locales de la API web de detección adoptan el modelo de autenticación de su implementación, admitiendo los tokens de OAuth o autenticación integrada de Windows (IWA) de un proveedor de tokens de confianza. La autenticación de sesión de aplicación web no es compatible.  
  
Cuando se configura el servicio de detección para la autenticación de OAuth, una solicitud enviada a la API web de servicio sin un token de acceso desencadena un desafío del portador con la autoridad del extremo "común" y el id. de recurso del servicio.  De manera similar, cuando se configura una implementación local para OAuth, un desafío del portador devuelve la dirección URL de la entidad local y el id. de recurso del servicio.  
  
### <a name="web-api-versioning"></a>Control de versiones de la API web

Se admite el control de versiones del servicio de detección para un centro de datos o una implementación local o de IFD y consta de números de versión como se usan por el servicio de la organización. Sin embargo, el servicio de detección global de Common Data Service no está vinculado al número de versión de la implementación de Common Data Service. En su lugar, el servicio global usa sus propios números de versión. En el momento de redactar este documento,el servicio de detección global de Common Data Service es la versión 1.0 (v1.0). Por ejemplo:  
  
```http  
GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
```  
  
### <a name="cors-support"></a>Soporte técnico de CORS

La API web del servicio de detección admite la norma CORS para acceso de origen cruzado como hace la Web API.  Para obtener más información sobre el soporte técnico de CORS, consulte [Usar OAuth con uso compartido de recursos entre orígenes para conectar una aplicación de una sola página](../oauth-cross-origin-resource-sharing-connect-single-page-application.md).  
  
### <a name="examples"></a>Ejemplos  
  
-   Obtenga los detalles de una instancia determinada. Si sale del GUID, se devuelven todas las instancias a las que el usuario autenticado tiene acceso.  
  
    ```http  
    GET https://disco.crm.dynamics.com/api/discovery/v8.1/Instances(<guid>)  
    GET https://dev.crm.external.contoso.com/api/discovery/v8.1/Instances(<guid>)  
    ```  
  
-   Puede usar el atributo UniqueName como clave alternativa.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances(UniqueName='myorg')  
    ```  
  
-   Recupere una lista de instancias disponible, filtrada por tipo de producción.  
  
    ```http  
    GET https://globaldisco.crm.dynamics.com/api/discovery/v1.0/Instances?$select=DisplayName,Description&$filter=Type+eq+0   
    ```  
  
-   Recupere el valor de la propiedad del id. de la instancia específica.  
  
    ```http  
    GET https://disco.crm.dynamics.com/api/discovery/v8.1/Instances(UniqueName='myorg')/Id/$value  
    ```

<!-- TODO: Add a see also section -->