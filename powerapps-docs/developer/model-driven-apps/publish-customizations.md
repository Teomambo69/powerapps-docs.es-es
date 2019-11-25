---
title: Publicar personalizaciones (aplicaciones basadas en modelos) | Microsoft Docs
description: La publicación de personalizaciones permite que la aplicación web tenga conocimiento de los datos que afectan la interfaz de usuario.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 27809198af9348b246dd7d0c2a5401880c13eb73
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749592"
---
# <a name="publish-customizations"></a>Publica personalizaciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-dev/publish-customizations -->

La publicación de personalizaciones permite que la aplicación web tenga conocimiento de los datos que afectan la interfaz de usuario.  
  
<a name="BKMK_WhenToPublishCustomizations"></a>   
## <a name="when-to-publish-customizations"></a>Cuándo publicar personalizaciones  
 Las personalizaciones se publican automáticamente cuando se crean nuevos elementos o se eliminan los elementos existentes.  
  
 Debe publicar los cambios después de actualizar los metadatos o las entidades del esquema que afectan a la interfaz de usuario. Puede optar por esperar y publicar un conjunto de cambios relacionados simultáneamente.  
  
 Solo las personalizaciones publicadas se exportan con una solución. Siempre debe publicar personalizaciones antes de exportar una solución.  
  
 Cuando realiza personalizaciones que aparecerán en Dynamics 365 for tablets, debe siempre publicar explícitamente las personalizaciones para asegurarse de que cada elemento se sincronizará con la aplicación Dynamics 365 for tablets.  
  
> [!NOTE]
>  La publicación de personalizaciones pueden interferir en el funcionamiento normal del sistema. En un entorno de producción, se recomienda programar la publicación de personalizaciones cuando menos afecte a los usuarios.  
  
## <a name="publishing-programmatically"></a>Publicación mediante programación  
 La siguiente tabla enumera los dos mensajes que puede usar para publicar personalizaciones.  
  
|Mensaje|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>|Publicar todas las personalizaciones.|  
|<xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest>|Publica las personalizaciones especificadas.|  
  
 Cuando se usa el mensaje de `PublishXmlRequest`, especifica los artículos que desea publicar mediante el parámetro <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest.ParameterXml>. `ParameterXML` debe cumplir con el [esquema de solicitud de publicación](publish-request-schema.md).  
  
<a name="BKMK_RetrieveUnpublishedMetadata"></a>   
## <a name="retrieving-unpublished-metadata"></a>Recuperar metadatos sin publicar  
 Si desea crear una aplicación para editar los elementos personalizables en aplicaciones orientadas a modelos, debe recuperar cualquier definición sin publicar de esos elementos. Si un desarrollador define algunos cambios pero no los publica, la aplicación debe poder recuperarlos para presentarlos en la interfaz de usuario. 
  
 Use los siguientes dos métodos para recuperar los metadatos sin publicar en:  
  
 **Parámetro RetrieveAsIfPublished**  
 Recupera la entidad, el atributo, la relación entre entidades y los datos del conjunto de opciones mediante los siguientes mensajes:  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>  
  
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>  
  
  **Solicitud de RetrieveUnpublished**  
  Recupera los elementos de la interfaz de usuario personalizada, como formulario, plantilla, visualización y las definiciones de recurso web, mediante los siguientes mensajes:  
  
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUnpublishedRequest>  
  
- <xref:Microsoft.Crm.Sdk.Messages.RetrieveUnpublishedMultipleRequest>  
  
### <a name="see-also"></a>Vea también  
 [Personalizar basadas en modelos](/dynamics365/customer-engagement/developer/customize-dev/customize-applications)<br/>
 [Ampliar el modelo de metadatos](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)<br/>
 [Publicar esquema de solicitud](publish-request-schema.md)<br/>
 [Personalizar formularios de entidad](customize-entity-forms.md)<br/>
 [Personalizar vistas de entidad](customize-entity-views.md)<br/>
 [Personalizar conjuntos de opciones globales](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)<br/>
 [Cambiar navegación de la aplicación con el mapa del sitio](/dynamics365/customer-engagement/developer/customize-dev/change-application-navigation-using-sitemap)

