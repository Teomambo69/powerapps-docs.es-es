---
title: Usar propiedades administradas (Common Data Service para aplicaciones) | Microsoft Docs
description: Las propiedades administradas le ayudan a definir qué componentes de la solución administrada se pueden personalizar
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-managed-properties"></a>Usar propiedades administradas

Puede controlar cuáles componentes de la solución administrada se pueden personalizar mediante el uso de propiedades administradas. Debe permitir tanta personalización como sea posible para esos componentes de la solución que representan entidades empresariales. Esto permite que las organizaciones personalicen la solución según sus requisitos. Limite o elimine la personalización de los componentes críticos de la solución que ofrecen la funcionalidad básica para que pueda respaldarla y mantenerla de manera previsible.  
  
 Las propiedades administradas se proporcionan para proteger la solución de modificaciones que pueden causar problemas. Las propiedades administradas no proporcionan administración de derechos digitales (DRM), ni capacidades para otorgar la licencia de la solución o controlar quién puede instalarla.  
  
## <a name="apply-managed-properties"></a>Aplicación de las propiedades administradas  
 Las propiedades administradas se aplican cuando la solución no está administrada. Las propiedades administradas se harán efectivas una vez que empaquete la solución administrada y la instale en una organización diferente. Una vez instalada la solución administrada, las propiedades administradas no se pueden actualizar excepto mediante una actualización de la solución realizada por el editor original.  
  
 La mayoría de los componentes de la solución muestran un botón **Propiedades administradas** al ver una lista de los componentes de la solución. Puede ver o actualizar las propiedades administradas de un componente de la solución cuando hace clic en este botón. Para tener acceso a las propiedades administradas de las soluciones que no muestran este botón, seleccione **Propiedades administradas** en la lista desplegable **Más acciones**.  
  
 De forma predeterminada, todos los componentes de la solución son personalizables. Para cambiar las propiedades administradas de un componente de la solución, haga clic en el botón **Propiedades administradas** en la barra de herramientas del componente de la solución. Cada componente de la solución tiene una propiedad **Se puede personalizar** (`IsCustomizable`). Siempre que el valor de esta propiedad sea True, se pueden especificar más propiedades específicas al tipo de componente de la solución. Si establece la propiedad `IsCustomizable.Value` en el valor False, después de instalar la solución como una solución administrada, el componente de la solución no se podrá personalizar. La siguiente tabla muestra las propiedades administradas de cada componente de la solución.  
  
|Componente|Nombre|Propiedad|  
|---------------|------------------|--------------|  
|Entity|Se puede personalizar|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsCustomizable>.                                 `Value`|  
|Entity|Se puede modificar el nombre para mostrar|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsRenameable>.                              `Value`|  
|Entity|Puede ser entidad relacionada en una relación|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanBeRelatedEntityInRelationship>.                                 `Value` (Solo lectura)|  
|Entity|Puede ser entidad principal en la relación|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanBePrimaryEntityInRelationship>.                                 `Value` (Solo lectura)|  
|Entity|Puede estar en relación de varios a varios|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanBeInManyToMany>.                               `Value` (Solo lectura)|  
|Entity|Se pueden crear nuevos formularios|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateForms>.                              `Value`|  
|Entity|Se pueden crear nuevos gráficos|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateCharts>.                               `Value`|  
|Entity|Se pueden crear nuevas vistas|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanCreateViews>.                              `Value`|  
|Entity|Puede cambiar cualquier otra propiedad de entidad no representada por una propiedad administrada|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.CanModifyAdditionalSettings>.                                `Value`|  
|Campo (atributo)|Se puede personalizar|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsCustomizable>.                                 `Value`|  
|Campo (atributo)|Se puede modificar el nombre para mostrar|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsRenameable>.                              `Value`|  
|Campo (atributo)|Se puede cambiar el nivel de requisito|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.RequiredLevel>.                                `CanBeChanged`<br /><br /> Nota:<br /><br /> `RequiredLevel` es la única propiedad administrada para usar la propiedad `CanBeChanged`.|  
|Campo (atributo)|Puede cambiar cualquier otra propiedad de atributo no representada por una propiedad administrada|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanModifyAdditionalSettings>.                                 `Value`|  
|Relación de entidad|Se puede personalizar|<xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.IsCustomizable>.                              `Value`|  
|Formulario|Se puede personalizar|`SystemForm.IsCustomizable.Value`|  
|Gráfico|Se puede personalizar|`SavedQueryVisualization.IsCustomizable.Value`|  
|Vista|Se puede personalizar|`SavedQuery.IsCustomizable.Value`|  
|Conjunto de opciones|Se puede personalizar|<xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadataBase.IsCustomizable>.                              `Value`|  
|Recurso web|Se puede personalizar|`WebResource.IsCustomizable.Value`|  
|Flujo de trabajo|Se puede personalizar|`Workflow.IsCustomizable.Value`|  
|Ensamblado|Se puede personalizar|`SdkMessageProcessingStep.IsCustomizable.Value`|  
|Registro de ensamblados|Se puede personalizar|`ServiceEndpoint.IsCustomizable.Value`|  
|Plantilla de correo electrónico|Se puede personalizar|`Template.IsCustomizable.Value`|  
|Plantilla de artículo de KB|Se puede personalizar|`KbArticleTemplate.IsCustomizable.Value`|  
|Plantilla de contrato|Se puede personalizar|`ContractTemplate.IsCustomizable.Value`|  
|Plantilla de combinación de correspondencia|Se puede personalizar|`MailMergeTemplate.IsCustomizable.Value`|  
|Panel|Se puede personalizar|`SystemForm.IsCustomizable.Value`|  
|Roles de seguridad|Se puede personalizar|`Role.IsCustomizable.Value`|  
  
### <a name="update-managed-properties"></a>Actualización de las propiedades administradas  
 Después de publicar la solución administrada, puede decidir que desea cambiar las propiedades administradas. Solo puede cambiar las propiedades administradas para hacerlas menos restrictivas. Por ejemplo, después de publicar la versión inicial, puede decidir permitir la personalización de una entidad.  
  
 Para actualizar las propiedades administradas de la solución, publique una actualización de la solución con las propiedades administradas modificadas. La solución administrada solo se puede actualizar mediante otra solución administrada asociada con el mismo registro de editor que la solución administrada original. Si la actualización incluye un cambio en las propiedades administradas para hacerlas más restrictivas, esos cambios en las propiedades administradas se ignorarán pero se aplicarán los otros cambios de la actualización.  
  
 Puesto que el editor original es un requisito para actualizar las propiedades administradas de una solución administrada, ninguna solución no administrada se podrá asociar con un editor que se haya utilizado para instalar una solución administrada.  
  
> [!NOTE]
>  Esto significa que no podrá desarrollar una actualización de la solución con una organización en la que está instalada la solución administrada.  
  
## <a name="check-managed-properties"></a>Comprobación de las propiedades administradas  
 Use <xref:Microsoft.Crm.Sdk.Messages.IsComponentCustomizableRequest> para comprobar si un componente de la solución es personalizable. O bien, puede comprobar las propiedades del componente de la solución, pero debe tener en cuenta que la resolución final del significado depende de los valores de varias propiedades. Cada componente de la solución tiene una propiedad `IsCustomizable`. Cuando se instala un componente de la solución como parte de una solución administrada, el valor de la propiedad `IsManaged` será True. Las propiedades administradas se aplican únicamente para las soluciones administradas. Al comprobar las propiedades administradas para determinar si un componente de la solución individual es personalizable, debe comprobar las propiedades `IsCustomizable` y `IsManaged`. Un componente de la solución en el que el valor de `IsCustomizable` y de `IsManaged` es False, se puede personalizar.  
  
 La entidad y el atributo tienen más propiedades administradas además de `IsCustomizable`. Estas propiedades administradas no se actualizan si el valor de `IsCustomizable` se establece en False. Esto significa que, además de comprobar la propiedad administrada individual, también debe comprobar la propiedad `IsCustomizable` para ver si se está aplicando la propiedad administrada.  
  
### <a name="see-also"></a>Vea también  
 [Propiedades administradas](/dynamics365/customer-engagement/developer/introduction-solutions#BKMK_ManagedProperties)   
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Mantener soluciones administradas](maintain-managed-solutions.md)   
 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 <xref:Microsoft.Crm.Sdk.Messages.IsComponentCustomizableRequest>