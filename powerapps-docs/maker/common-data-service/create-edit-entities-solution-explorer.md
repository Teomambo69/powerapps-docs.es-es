---
title: Creación y edición de entidades mediante el explorador de soluciones | MicrosoftDocs
description: Aprenda a crear entidades con el explorador de soluciones
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2ec1fb0471ad1f47f4afad083ad89e87633ce9ed
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707315"
---
# <a name="create-and-edit-entities-using-solution-explorer"></a>Crear y editar entidades con el explorador de soluciones

Puede crear fácilmente una entidad mediante el portal de PowerApps para la mayoría de las situaciones comunes, pero no todas las capacidades se implementan ahí. Cuando necesite cumplir los requisitos descritos en [Creación y edición de entidades en Common Data Service](create-edit-entities.md), puede cumplirlas creando o editar entidades mediante el Explorador de soluciones.

## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier entidad que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>Ver entidades

En el nodo **Componentes** del explorador de soluciones, seleccione el nodo **Entidades**.

![Ver entidades en el explorador de soluciones](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>Creación de entidades

Mientras [ve entidades](#view-entities), seleccione **Nuevo** para abrir el nuevo formulario de entidad.

![nuevo formulario de entidad en el explorador de soluciones](media/new-entity-form-solution-explorer.png)

El nuevo formulario de entidad tiene dos pestañas. La pestaña **General** es para opciones de la entidad. La pestaña **Campo principal** es para opciones sobre el campo especial de una sola línea de texto que cada entidad tiene y que define el texto que se muestra cuando hay un vínculo para abrir la entidad en un campo de búsqueda.

Para obtener información acerca de cada sección, vea lo siguiente:
- [Configurar el campo principal](#configure-the-primary-field)
- [Configurar campos obligatorios](#configure-required-fields)

> [!NOTE]
> También puede convertir la entidad en una actividad personalizada. Esta opción cambia algunos de los valores de opción predeterminados. Más información: [Crear una entidad de actividad personalizada](#create-custom-activity-entity)

Después de establecer las opciones necesarias para la entidad, haga clic en ![Comando Guardar](media/save-entity-icon-solution-explorer.png) para crear la entidad personalizada.

### <a name="configure-the-primary-field"></a>Configurar el campo principal

En la pestaña **Campo principal** normalmente puede aceptar los valores predeterminados para el campo principal, pero tiene las siguientes opciones:

|Campo   |Descripción  |
|---------|---------|
|**Nombre para mostrar**|Especifique la etiqueta localizable que mostrará para este campo en formularios y listas. El valor predeterminado es **Nombre**.|
|**Nombre**|Establezca el nombre usado en el sistema para este campo. El valor predeterminado es `<customization prefix>_name`|
|**Longitud máxima**|Introduzca la longitud máxima para los valores de campo. El valor predeterminado es 100.|

> [!NOTE]
> Estas opciones no se aplican si la entidad es una entidad de actividad. Más información: [Crear una entidad de actividad personalizada](#create-custom-activity-entity)

### <a name="configure-required-fields"></a>Configurar campos obligatorios

En la pestaña **General**, algunas de las opciones son necesarias para poder guardar la entidad.

|Campo   |Descripción  |
|---------|---------|
|**Nombre para mostrar**|Este es el nombre singular de la entidad que aparecerá en la aplicación.<br />Se puede cambiar posteriormente.|
|**Nombre plural**|Este es el nombre plural de la entidad que aparecerá en la aplicación.<br />Se puede cambiar posteriormente.|
|**Nombre**|Este campo se rellena previamente según el nombre para mostrar que escriba. Incluye el prefijo de personalización del editor de soluciones.|
|**Propiedad**|Puede elegir que sea propiedad del usuario o el equipo, o propiedad de la organización. Más información: [Propiedad de entidad](types-of-entities.md#entity-ownership).|

## <a name="edit-an-entity"></a>Editar una entidad

Mientras [ve entidades](#view-entities), seleccione la entidad que desee modificar, o continúa editando una nueva entidad que acaba de guardar.

> [!NOTE]
> Las entidades estándar o las entidades personalizadas que son parte de una solución administrada pueden tener limitaciones sobre los cambios que puede aplicar. Si la opción no está disponible o está deshabilitada, usted no está autorizado a realizar el cambio.

#### <a name="set-once-options"></a>Establecer opciones de una vez

Las siguientes opciones se pueden configurar una vez y no se pueden cambiar después de configurarlas. Procure establecer estas opciones solo cuando las necesite.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

#### <a name="options-that-you-can-change"></a>Opciones que puede cambiar

Puede cambiar las propiedades siguientes en cualquier momento.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)]

También puede realizar los siguientes cambios:
- [Crear y editar campos para Common Data Service](create-edit-fields.md)
- [Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)
- [Creación y diseño de formularios](../model-driven-apps/create-design-forms.md)
- [Crear un flujo de proceso de negocio para estandarizar los procesos](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>Eliminación de una entidad

Como usuario con el rol de seguridad de administrador del sistema, puede eliminar entidades personalizadas que no sean parte de una solución administrada.  
  
> [!IMPORTANT]
>  Cuando se elimina una entidad personalizada, las tablas de base de datos que almacenan los datos de la entidad se eliminan y se pierden todos los datos que contienen. Los registros asociados con una relación jerárquica con la entidad personalizada también se eliminan. Para obtener más información sobre las relaciones jerárquicas, consulte [Creación y edición de relaciones entre entidades](create-edit-entity-relationships.md).  
  
> [!NOTE]
> La única forma de recuperar datos de una entidad que se haya eliminado es restaurar la base de datos desde un punto anterior a la eliminación de la entidad. Más información: [Copia de seguridad y restauración de instancias](/dynamics365/customer-engagement/admin/backup-restore-instances)

Mientras [ve entidades](#view-entities), haga clic en el comando ![comando Eliminar](media/delete.gif) en la barra de herramientas.

Mientras ve una entidad use el comando eliminar de la barra de menús.

![Comando Eliminar](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> Si elimina una entidad que contiene datos se quitarán todos los datos. Estos datos se pueden recuperar sólo mediante la copia de seguridad de la base de datos.

> [!NOTE]
> Si hay dependencias de entidad recibirá un error **No se puede eliminar el componente** con un vínculo **Detalles** que puede usar para detectar información sobre por qué la entidad no se puede eliminar. En la mayoría de los casos, será debido a una dependencia que debe quitarse. 
>
> Puede haber más de una dependencia que bloquee la eliminación de una entidad. Este mensaje de error puede mostrar sólo la primera. Para una forma alternativa de detectar dependencias, consulte [Identificar dependencias de entidad](#identify-entity-dependencies)



### <a name="identify-entity-dependencies"></a>Identificar dependencias de entidad

Puede identificar dependencias que impiden eliminar una entidad antes de intentar eliminarla. 

1. En el explorador de soluciones con la entidad seleccionada, haga clic en **Mostrar dependencias** en la barra de comandos.

![Comando Mostrar dependencias](media/entity-show-dependencies.png)

2. En la ventana de diálogo que se abre, desplace la lista a la derecha para ver la columna **Tipo de dependencia**.

![Tipo de dependencia publicada](media/published-entity-dependency.png)

Las dependencias **publicadas** impedirán eliminar una entidad. Las dependencias**internas** debe resolverlas el sistema.  

3. Quite estas dependencias publicadas y debe poder eliminar la entidad.

 > [!NOTE]
 > Una dependencia muy común es que otro formulario de entidad tiene un campo de búsqueda para la entidad que desea eliminar. Al quitar el campo de búsqueda del formulario se resolverá la dependencia.

## <a name="create-custom-activity-entity"></a>Crear una entidad de actividad personalizada

Para crear la entidad como entidad de actividad, siga los mismos pasos descritos en este tema, pero seleccione **Definir como entidad de actividad**.

![Definir como entidad de actividad](media/create-activity-entity-solution-explorer.png)

Una entidad de actividad es un tipo especial de entidad que realiza un seguimiento de las acciones para los que se puede realizar entrada en un calendario. Más información: [Entidades de actividad](types-of-entities.md#activity-entities).

Cuando establece esta opción algunas propiedades de la entidad no son compatibles. Una entidad de actividad debe ajustarse a comportamientos estándar que todas las entidades de actividad usan.

El campo principal **Nombre** y **Nombre para mostrar** se establecerán como **Asunto** y no puede cambiarlo.

Las siguientes opciones se establecen de forma predeterminada y no se pueden cambiar:

 - **Comentarios**
 - **Notas (incluye archivos adjuntos)**
 - **Conexiones**
 - **Colas**
 - **Funcionalidad sin conexión para Dynamics 365 for Outlook**

Las siguientes opciones no se pueden establecer:

- **Áreas que muestran esta entidad**
- **Actividades**
- **Enviar correo electrónico**
- **Combinar correspondencia**
- **Auditoría de un solo registro**
- **Auditoría de varios registros**

## <a name="create-a-virtual-entity"></a>Crear una entidad virtual

Algunas opciones se usan únicamente al crear una entidad virtual.

|Opción   |Descripción  |
|---------|---------|
|**Entidad virtual**|Si la entidad es una entidad virtual.|
|**Origen de datos**|El origen de los datos de la entidad.|

Más información: [Crear y editar entidades virtuales que contienen datos desde un origen de datos externo](create-edit-virtual-entities.md)

### <a name="see-also"></a>Vea también
[Crear y editar entidades en Common Data Service](create-edit-entities.md)<br />
[Tutorial: Crear una entidad personalizada que tenga componentes en PowerApps](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Crear una solución](create-solution.md)
