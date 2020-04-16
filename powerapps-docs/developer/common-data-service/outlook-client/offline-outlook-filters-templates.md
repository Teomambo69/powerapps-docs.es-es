---
title: Plantillas y filtros de Outlook y sin conexión (Common Data Service)| Microsoft Docs
description: Los datos que deben sincronizarse entre Common Data Service y Dynamics 365 for Outlook se determinan con los filtros de datos para Office Outlook
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: sriharibs
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8dde102e360535cb297e70881cde206ae232b2bd
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155396"
---
# <a name="offline-and-outlook-filters-and-templates"></a>Plantillas y filtros de Outlook y sin conexión

Los filtros de datos para Office Outlook determinan qué datos se deben sincronizar entre el servidor de aplicaciones Common Data Service y Dynamics 365 for Outlook. Common Data Service es compatible con la capacidad de cambiar el filtro predeterminado mediante el SDK y de insertar estos cambios en cualquier usuario o en todos.  
Puede escribir código que permite a los administradores crear y publicar plantillas de filtro. Esto permite que un administrador de Common Data Service cree los filtros comunes o deseables que pueden publicarse para que los usuarios sincronicen con la base de datos de Outlook Store y sin conexión. Esto también proporciona una manera de personalizar la plantilla de filtro predeterminada que se aplicará a los usuarios que se agregan al sistema una vez que las plantillas se publiquen originalmente. El administrador también tiene la posibilidad de actualizar o eliminar los filtros del usuario después de que se publican.  
Para admitir estas personalizaciones, hay cuatro nuevos tipos de consulta para la consulta guardada (vista). Cuando cree un registro de consulta guardada (vista), especifique uno de estos tipos en el atributo de `SavedQuery.QueryType`, mediante la enumeración de <xref:Microsoft.Crm.Sdk.SavedQueryQueryType> . Solo son accesibles con los métodos descritos aquí; no existe una interfaz de usuario disponible para cambiarlos. Puede especificar distintos filtros para evitar sincronizar todo con Outlook para su teléfono móvil. Las plantillas de filtro son compatibles con la solución de modo que pueden exportarse junto con una solución.  
  
 La siguiente tabla muestra los nuevos tipos de la consulta usados para los filtros y las plantillas de filtro.  
  
|Tipo de consulta|Descripción|  
|----------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookFilters>|Define el subgrupo de una entidad que se sincronizará con Dynamics 365 for Outlook. El subgrupo de datos definido por estos filtros se sincronizará en las carpetas de Outlook como Contactos, Calendario, etc.|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineFilters>|Define el subgrupo de una entidad que se sincronizará con Dynamics 365 for Microsoft Office Outlook con acceso sin conexión. El subgrupo de datos definidos por estos filtros se sincronizará con la base de datos sin conexión.|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookTemplate>|Define una plantilla de filtro que se aplica a los nuevos usuarios para la sincronización con Dynamics 365 for Outlook.|  
|<xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineTemplate>|Define una plantilla de filtro que se aplica a los nuevos usuarios para la sincronización con Dynamics 365 for Microsoft Office Outlook con acceso sin conexión.|  
  
## <a name="instantiate-a-filter"></a>Crear una instancia de un filtro

La entidad de `UserQuery` automáticamente crea una instancia de las plantillas de filtro predeterminadas para cada usuario cuando se crea una suscripción de sincronización. Cuando se inicia la sincronización con Outlook o con la base de datos sin conexión, se recopilan los filtros para ese usuario y se usan para filtrar las recopilaciones de entradas y atributos que se están sincronizando. Si se especifican varios filtros varios para una entidad en particular, el conjunto de entradas resultante será una combinación de resultados de filtros individuales.  

Hay un nuevo privilegio que permite que el administrador tenga acceso a los filtros de otro usuario: `prvAdminFilter`. Esto se denomina Administrar filtros de sincronización del usuario en la aplicación Web. El rol de administrador del sistema incluye este privilegio porque sin él, solo el usuario puede ver sus filtros. Llamar a <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Si llama al método en la consulta del usuario solo recuperará los registros para el usuario que es propietario, a menos que la persona que llama tenga el privilegio de `prvAdminFilter`. La consulta debe presentar las condiciones donde `QueryType` es igual a <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookFilters> o <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineFilters> Y `OwnerId` es igual a `UserId`, donde el `UserId` no es igual a la persona que llama. Si se agregan otras condiciones a la consulta, ésta no funcionará.  

Los usuarios nuevos automáticamente reciben los filtros de las plantillas de filtros que están marcadas como predeterminadas en el atributo de `SavedQuery.IsDefault` . Los administradores deben saber que pueden cambiar este valor para afectar esta situación. Cada entidad puede tener únicamente una plantilla de filtro marcada como predeterminada. Es posible que no haya filtros predeterminados, solo plantillas de filtro. Si crea una entidad personalizada, y establece la propiedad de <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAvailableOffline>, automáticamente se creará una plantilla predeterminada.  

Existe un nuevo tipo de filtro que los administradores pueden definir, llamado filtros del sistema. Estos filtros se definen como registros de `SavedQuery` con el tipo de consulta de <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OutlookFilters> o de <xref:Microsoft.Crm.Sdk.SavedQueryQueryType.OfflineFilters>. Los filtros del sistema se aplican automáticamente a todos los usuarios y los usuarios no pueden modificarlos.  

Hay un límite en el número de filtros que puede agregar. Este valor está controlado por el administrador de implementaciones de Common Data Service para evitar que los usuarios o los administradores creen demasiados filtros, lo que afecta el rendimiento del servidor. El mismo valor del límite se aplica a todas las entidades.  

De forma predeterminada, existen configuraciones ilimitadas de los filtros del sistema y los filtros de los usuarios.  

## <a name="instantiate-a-template"></a>Crear una instancia de plantilla

Puede crear una instancia de uno o más filtros por usuario. Para hacerlo manualmente, use <xref:Microsoft.Crm.Sdk.Messages.InstantiateFiltersRequest> para crear una instancia de filtro, creando un registro de la consulta de usuario. Cada registro de la consulta de usuario contiene una referencia al filtro. Si actualiza el filtro, puede volver a llamar una instancia nuevamente para actualizar o reemplazar los cambios del usuario para el filtro (registro de la consulta de usuario).  
  
## <a name="reset-a-users-filters-to-the-default"></a>Restablecer los filtros de un usuario al valor predeterminado

Puede restablecer los filtros de un usuario al valor predeterminado mediante <xref:Microsoft.Crm.Sdk.Messages.ResetUserFiltersRequest>.  
  
### <a name="see-also"></a>Vea también

[Ampliar Dynamics 365 for Outlook](extend-dynamics-365-outlook.md)<br />
[Referencia de la entidad SavedQuery](../reference/entities/savedquery.md)<br />
[Ejemplo: Recuperar filtros de Outlook](sample-create-retrieve-outlook-filters.md)<br /> 
<xref:Microsoft.Crm.Sdk.Messages.InstantiateFiltersRequest><br />
<xref:Microsoft.Crm.Sdk.Messages.ResetUserFiltersRequest>