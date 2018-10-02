---
title: Creación y edición entidades en Common Data Service para aplicaciones | MicrosoftDocs
description: Aprenda a crear y editar entidades
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-entities-in-common-data-service-for-apps"></a>Creación y edición entidades en Common Data Service para aplicaciones

Antes de crear una entidad personalizada, evalúe si el uso de una entidad existente cumplirá sus requisitos. Más información: [¿Crear nuevos metadatos o usar los metadatos existentes?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Hay dos diseñadores que puede usar para crear una entidad:

|Diseñador| Descripción|
|--|--|
|[Portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: <br />[Tutorial: Crear una entidad personalizada que tenga componentes en PowerApps](/powerapps/maker/common-data-service/create-custom-entity)<br />[Crear y editar entidades con el portal PowerApps](create-edit-entities-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes. <br />Más información: [Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> También puede crear entidades en su entorno mediante lo siguiente:
> - Importe una solución que contenga la definición de la entidad.
> - Use Power Query para crear nuevas entidades y rellenarlas con datos. Más información: [Agregar datos a una entidad en Common Data Service mediante Power Query](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Un programador puede usar [Servicios de metadatos](/powerapps/developer/common-data-service/use-web-services#metadata-services) para escribir un programa.


## <a name="entity-options-not-available-in-the-powerapps-portal"></a>Las opciones de entidad no están disponibles en el portal de PowerApps

La información de este tema le ayudará a elegir el diseñador que puede usar. Puede usar el portal de PowerApps para crear la entidad a menos que necesite satisfacer cualquiera de los siguientes requisitos.

- Controlar el prefijo de personalización

  La parte del nombre de cualquier entidad personalizada que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md).

- Crear entidad propiedad de la organización

  De forma predeterminada, el portal de PowerApps creará entidades propiedad de un **Usuario o equipo**. Use el explorador de soluciones para establecer la propiedad en **Organización**. Más información: [Propiedad de entidad](types-of-entities.md#entity-ownership).

- Crear una entidad de actividad

  Una entidad de actividad es un tipo especial de entidad que realiza un seguimiento de las acciones para los que se puede realizar entrada en un calendario. Más información: [Entidades de actividad](types-of-entities.md#activity-entities).

- Cambiar los iconos para una entidad personalizada

  De forma predeterminada, todas las entidades personalizadas en las aplicaciones basadas en modelos tienen los mismos iconos. Puede crear recursos web de imagen para los iconos que desea para las entidades personalizadas. Más información:  [Cambio de iconos para entidades personalizadas](../model-driven-apps/change-custom-entity-icons.md). 

- Cambiar cualquiera de las propiedades siguientes que solo se pueden habilitar:

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- Cambiar cualquiera de las propiedades siguientes:

  <!-- Based on ../../includes/cc_entity-changeable-options-table.md 
Removed these:

  /|**Description**/|Provide a meaningful description of the purpose of the entity./|

  /|**Primary Image**/|System entities that support images will already have an **Image** field. You can choose whether to display data in this field as the image for the record by setting this field to **[None]** or **Default Image**.<br /><br /> For custom entities you must first create an image field. Each entity can have only one image field. After you create one, you can change this setting to set the primary image. More information: [Image fields](../maker/common-data-service/types-of-fields.md#image-fields) /|-->

  |Opción   |Descripción  |
  |---------|---------|
  |**Equipos de acceso**|Cree plantillas de equipo para esta entidad. |
  |**Permitir creación rápida**|Después de la creado y publicación de un **Formulario de creación rápida** para esta entidad, los usuarios tendrán la opción de crear un nuevo registro usando el botón **Crear** en el panel de navegación. Más información: [Crear y diseñar formularios](../model-driven-apps/create-design-forms.md)<br /><br /> Cuando esta opción está habilitada para una entidad de actividad personalizada, dicha actividad personalizada será visible en el grupo de entidades de actividad cuando los usuarios usen el botón **Crear** en el panel de navegación. Sin embargo, debido a que las actividades no admiten formularios de creación rápida, el formulario principal se utilizará cuando se haga clic en el icono de entidad personalizada.|
  |**Áreas que muestran esta entidad**|En la aplicación web seleccione una de las áreas del mapa del sitio disponibles para mostrar esta entidad. Esto no se aplica las aplicaciones basadas en modelos.|
  |**Auditoría**|Cuando se habilita la auditoría para la organización, permite que se los cambios en los registros de la entidad se capturen con el tiempo. Al habilitar la auditoría de una entidad, también se habilita la auditoría de todos sus campos. Puede seleccionar o anular la selección de los campos en los que desea habilitar la auditoría.|
  |**Seguimiento de cambios**|Habilita la sincronización de datos con alto rendimiento detectando qué datos se han modificado desde que los datos se extrajeron inicialmente o se sincronizaron por última vez.  |
  |**Color**|Establezca color que se usará para la entidad en aplicaciones basadas en modelos.|
  |**Administración de documentos**|Después de realizar otras tareas para habilitar la administración de documentos para la organización, habilitar esta característica permite que esta entidad participe en la integración con SharePoint. |
  |**Detección de duplicados**|Si la detección de duplicados está habilitada para la organización, habilitar esta opción le permite crear reglas de detección de duplicados para esta entidad.|
  |**Habilitar para móvil**|Haga que esta entidad esté disponible para las aplicaciones de Dynamics 365 para teléfonos y tabletas. También tiene la opción de convertir esta entidad en **Solo lectura en móvil**.<br /><br /> Si los formularios de una entidad requieren una extensión que no es compatible con las aplicaciones Dynamics 365 for phones y tablets, use este valor para asegurarse de que los usuarios de aplicaciones móviles no pueden editar los datos de estas entidades.|
  |**Habilitar para Phone Express**|Haga que esta entidad esté disponible para la aplicación Dynamics 365 for phones.|
  |**Combinar correspondencia**|Los usuarios pueden usar esta entidad con la combinación de correspondencia.|
  |**Capacidad de trabajar sin conexión Dynamics 365 para Outlook**|Si los datos de esta entidad estarán disponibles mientras la aplicación Dynamics 365 for Outlook no está conectada a la red.|
  |**Panel de lectura en Dynamics 365 para Outlook**|Si la entidad será visible en el panel de lectura de la aplicación Dynamics 365 for Outlook.|
  |**Use Ayuda personalizada**|Cuando se habilitado, establece una dirección URL de Ayuda para controlar qué página verán los usuarios cuando hagan clic en el botón Ayuda en la aplicación. Use esta opción para dar instrucciones específicas para los procesos de su empresa para la entidad.|


### <a name="see-also"></a>Vea también

[Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)<br />
[Tutorial: Crear una entidad personalizada que tenga componentes en PowerApps](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Editar una entidad](edit-entities.md)<br />
[Documentación para desarrolladores: crear una entidad personalizada](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
