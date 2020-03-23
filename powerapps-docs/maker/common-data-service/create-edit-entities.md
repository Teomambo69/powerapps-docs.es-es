---
title: Creación y edición de entidades en Common Data Service | MicrosoftDocs
description: Aprenda a crear y editar entidades
ms.custom: ''
ms.date: 04/16/2019
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: d700c76009f45c4e28f78732e7ae52ab57693ccb
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040541"
---
# <a name="create-and-edit-entities-in-common-data-service"></a>Crear y editar entidades en Common Data Service

Antes de crear una entidad personalizada, evalúe si el uso de una entidad existente cumplirá sus requisitos. Más información: [¿Crear nuevos metadatos o usar los metadatos existentes?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Hay dos diseñadores que puede usar para crear una entidad:

|Diseñador| Descripción|
|--|--|
|[Portal Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: <br />[Tutorial: Crear una entidad personalizada que tenga componentes en Power Apps](/powerapps/maker/common-data-service/create-custom-entity)<br />[Crear y editar entidades con el portal de Power Apps](create-edit-entities-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes. <br />Más información: [Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> También puede crear entidades en su entorno mediante lo siguiente:
> - Importe una solución que contenga la definición de la entidad.
> - Use Power Query para crear nuevas entidades y rellenarlas con datos. Más información: [Agregar datos a una entidad en Common Data Service mediante Power Query.](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Un programador puede usar [Servicios de metadatos](/powerapps/developer/common-data-service/use-web-services#metadata-services) para escribir un programa.

## <a name="entity-options-not-available-in-the-power-apps-portal"></a>Las opciones de entidad no están disponibles en el portal de Power Apps

La información de este tema le ayudará a elegir el diseñador que puede usar. Puede usar el portal de Power Apps para crear la entidad a menos que necesite satisfacer cualquiera de los siguientes requisitos.

- Controlar el prefijo de personalización

  La parte del nombre de cualquier entidad personalizada que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md).

- Cambiar los iconos para una entidad personalizada

  De forma predeterminada, todas las entidades personalizadas en las aplicaciones basadas en modelos tienen los mismos iconos. Puede crear recursos web de imagen para los iconos que desea para las entidades personalizadas. Más información:  [Cambio de iconos para entidades personalizadas](../model-driven-apps/change-custom-entity-icons.md). 

- Cambiar cualquiera de las propiedades siguientes que solo se pueden habilitar:

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- Cambiar cualquiera de las propiedades siguientes:

  |Opción   |Descripción  |
  |---------|---------|
  |**Áreas que muestran esta entidad**|En la aplicación web, seleccione una de las áreas disponibles del mapa del sitio para mostrar esta entidad. Esto no se aplica a las aplicaciones basadas en modelos.|
  |**Auditoría**|Cuando se habilita la auditoría para la organización, permite capturar los cambios en los registros de entidad a lo largo del tiempo. Al habilitar la auditoría para una entidad, también se habilita la auditoría en todos sus campos. Puede seleccionar (o anular la selección de) los campos en los que desee habilitar la auditoría.|
  |**Color**|Establezca el color que se usará para la entidad en aplicaciones basadas en modelos.|
  |**Administración de documentos**|Después de realizar otras tareas para habilitar la administración de documentos para la organización, si habilita esta característica permite que esta entidad participe en la integración con SharePoint. |
  |**Habilitar para móvil**|Hace que esta entidad esté disponible para las aplicaciones de Dynamics 365 for phones y tablets. También tiene la opción de convertir esta entidad en **Solo lectura en móvil**.<br /><br /> Si los formularios de una entidad requieren una extensión que no es compatible con las aplicaciones Dynamics 365 for phones y tablets, use esta configuración para asegurarse de que los usuarios de aplicaciones móviles no puedan editar los datos de estas entidades.|
  |**Habilitar para Phone Express**|Hace que esta entidad esté disponible para la aplicación Dynamics 365 for phones.|
  |**Panel de lectura en Dynamics 365 for Outlook**|Especifica si la entidad estará visible en el panel de lectura de la aplicación Dynamics 365 for Outlook.|
  |**Usar la Ayuda personalizada**|Si se habilita esta opción, establece una dirección URL de Ayuda para controlar qué página verán los usuarios cuando hagan clic en el botón Ayuda de la aplicación. Use esta opción para dar instrucciones específicas para los procesos de su empresa para la entidad.|


### <a name="see-also"></a>Vea también

[Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)<br />
[Tutorial: Crear una entidad personalizada que tenga componentes en Power Apps](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Editar una entidad](edit-entities.md)<br />
[Documentación para desarrolladores: crear una entidad personalizada](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
