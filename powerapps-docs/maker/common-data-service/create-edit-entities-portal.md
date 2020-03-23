---
title: Crear y editar entidades con el portal de Power Apps | MicrosoftDocs
description: Aprenda a crear y editar entidades con el portal de Power Apps
ms.custom: ''
ms.date: 05/30/2018
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
ms.openlocfilehash: 199399fe75103df2d8fde902d54a803ec56fc395
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040587"
---
# <a name="create-and-edit-entities-using-power-apps-portal"></a>Crear y editar entidades con el portal de Power Apps

El [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) proporciona una forma fácil de crear y de editar entidades para Common Data Service.

El portal permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. Más información: 
- [Crear y editar entidades en Common Data Service](create-edit-entities.md)
- [Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)

## <a name="view-entities"></a>Ver entidades

1. Desde el [portal de Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Datos** > **Entidades**.

![Ver entidades](media/view-entities-portal.png)

Puede filtrar las entidades que ve mediante las vistas siguientes en una lista: 

![Vistas de entidad](media/entity-views-portal.png)

 |Vista|Descripción|
 |--|--|
 |**Todo**| Muestra todas las entidades|
 |**Administrada**| Muestra solo entidades administradas y estándar|
 |**Personalizada**|Muestra solo entidades personalizadas|
 |**Predeterminado**|Muestra únicamente las entidades estándar |

También puede seleccionar **Grupo** para agrupar entidades por las **Etiquetas** aplicadas a ellas.

## <a name="create-an-entity"></a>Crear una entidad

Mientras [ve entidades](#view-entities), en la barra de menú seleccione **Nueva entidad**. Se abrirá el panel Nueva entidad.

![Panel Nueva entidad](media/new-entity-panel.png)

Escriba datos para los campos siguientes:

|Campo|Descripción|
|--|--|
|**Nombre**|Este es el nombre singular de la entidad que aparecerá en la aplicación. Se puede cambiar posteriormente.|
|**Nombre plural para mostrar**|Este es el nombre plural de la entidad que aparecerá en la aplicación. Se puede cambiar posteriormente.|
|**Nombre**|Este campo se rellena previamente según el **Nombre para mostrar** que escriba. Incluye el prefijo de personalización para el editor de soluciones de Common Data Service. No se puede cambiar esto una vez guardada la entidad.|
|**Nombre principal**|Este es el único campo visible en este momento.| Edítelo si desea cambiar el **Nombre para mostrar** o el **Nombre** del campo.
|**Nombre para mostrar**|Este es el principal identificador de texto fácil de usar para su registro (generalmente un nombre o un número). El valor de este campo se muestra a los usuarios cuando necesitan seleccionar en una lista de registros.
|**Nombre**|Este campo se rellena previamente según el **Nombre para mostrar** que escriba. Incluye el prefijo de personalización para el editor de soluciones de Common Data Service. No se puede cambiar esto una vez guardada la entidad.|

Seleccione **Habilitar archivos adjuntos** para agregar notas y archivos a los registros de esta entidad.

Seleccione **Más valores**. Estas configuraciones son opcionales para una entidad.

|Campo|Descripción|
|--|--|
|**Descripción**|Proporcione una descripción significativa del objetivo de la entidad.|
|**Tipo y propiedad de entidad**|Cambie el tipo de entidad a Entidad de actividad para crear entidades que puedan administrar tareas. El tipo de **Propiedad** define quién puede realizar operaciones en un registro.|
|**Colaboración**|Habilite características para ayudar a los usuarios a trabajar juntos más fácilmente en esta entidad.|
|**Crear y actualizar configuración**|Puede habilitar formularios de creación rápida, dando a su aplicación una experiencia de entrada de datos optimizada. La detección de duplicados le permite establecer directivas de detección de duplicados y crear reglas detección de duplicados. El seguimiento de cambios proporciona una forma de mantener los datos sincronizados de manera eficiente.|
|**Dynamics 365 for Outlook**|Configure cómo aparece esta entidad en Outlook.|

Seleccione **Crear** para continuar, se cerrará el panel **Nueva entidad** y se mostrará la lista de campos.

El campo **Nombre principal** de la entidad se muestra en la lista de campos. Seleccione el campo **Nombre principal** para editarlo si desea cambiar el **Nombre para mostrar** o el **Nombre** del campo. Los valores predeterminados se muestran debajo:

![Panel Nombre principal](media/primary-name-panel.png)

## <a name="edit-an-entity"></a>Editar una entidad

Mientras [ve entidades](#view-entities), seleccione la entidad que desea editar.

Seleccione **Configuración** en el menú si desea editar el **Nombre para mostrar**, **Nombre plural para mostrar** o **Descripción** de la entidad.

![Configuración de la entidad](media/entity-settings-portal.png)

Para otros elementos elija de las pestañas.

### <a name="fields"></a>Campos

Vea [Crear y editar campos](create-edit-fields.md)

### <a name="relationships"></a>Relaciones

Vea [Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)

### <a name="business-rules"></a>Reglas de negocio

Vea [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

### <a name="views"></a>Vistas

Vea [Creación o edición de vistas](../model-driven-apps/create-edit-views.md)

### <a name="forms"></a>Formularios

Vea [Creación y diseño de formularios](../model-driven-apps/create-design-forms.md)

### <a name="dashboards"></a>Paneles

Vea [Crear o editar paneles](../model-driven-apps/create-edit-dashboards.md)

### <a name="charts"></a>Gráficos

Vea [Crear un gráfico del sistema](../model-driven-apps/create-edit-system-chart.md)

### <a name="keys"></a>Claves

Vea [Definir claves alternativas para hacer referencia a registros](define-alternate-keys-reference-records.md)

### <a name="data"></a>Datos

Vea los datos en la entidad.
Use el menú **Seleccionar vista** para elegir entre las vistas disponibles para la entidad o para mostrar todos los campos.

![Seleccionar vista](media/entity-data-select-view.png)

Use los comandos **Página siguiente** y **Página anterior** en la parte inferior del formulario para ver más datos.

## <a name="delete-an-entity"></a>Eliminación de una entidad

Como usuario con el rol de seguridad de administrador del sistema, puede eliminar entidades personalizadas que no sean parte de una solución administrada.  
  
> [!IMPORTANT]
>  Cuando se elimina una entidad personalizada, las tablas de base de datos que almacenan los datos de la entidad se eliminan y se pierden todos los datos que contienen. Los registros asociados con una relación jerárquica con la entidad personalizada también se eliminan. Para obtener más información sobre las relaciones jerárquicas, consulte [Creación y edición de relaciones entre entidades](create-edit-entity-relationships.md).  
  
> [!NOTE]
> La única forma de recuperar datos de una entidad que se haya eliminado es restaurar la base de datos desde un punto anterior a la eliminación de la entidad. Más información: [Copia de seguridad y restauración de instancias](/dynamics365/customer-engagement/admin/backup-restore-instances)

Mientras [ve entidades](#view-entities), seleccione la entidad y seleccione **Eliminar entidad** en el menú.

![Eliminación de entidades mediante el portal de Power Apps](media/delete-entity-powerapps-portal.png)

Si la entidad tiene las dependencias que impiden que sea eliminado verá un mensaje de error. Para identificar y quitar cualquier dependencia, deberá usar el explorador de soluciones. Más información [Identificar dependencias de la entidad](create-edit-entities-solution-explorer.md#identify-entity-dependencies)

### <a name="see-also"></a>Vea también

[Crear y editar entidades en Common Data Service](create-edit-entities.md)<br />
[Crear y editar entidades con el explorador de soluciones](create-edit-entities-solution-explorer.md)


