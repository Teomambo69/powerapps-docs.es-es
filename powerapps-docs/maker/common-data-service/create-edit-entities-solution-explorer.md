---
title: Creación y edición de entidades mediante el Explorador de soluciones | Microsoft Docs
description: Obtenga información sobre cómo crear una entidad mediante el Explorador de soluciones.
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: 48025088da85bf0685ba1a46efa4f3a989a20a58
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698382"
---
# <a name="create-and-edit-entities-using-solution-explorer"></a>Creación y edición de entidades mediante el Explorador de soluciones

Puede crear fácilmente una entidad mediante el portal de PowerApps para situaciones más comunes, pero no todas las funcionalidades se implementan ahí. Cuando necesite satisfacer los requisitos descritos en [Creación y edición de entidades en Common Data Service para aplicaciones](create-edit-entities.md), puede lograrlos mediante la creación o edición de entidades con el Explorador de soluciones.

## <a name="open-solution-explorer"></a>Abrir el Explorador de soluciones

Parte del nombre de cualquier entidad que se crea es el prefijo de personalización. Esto se establece en función del editor de soluciones de la solución en la que está trabajando. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada, donde el prefijo de personalización es lo que necesita para esta entidad. Más información: [Cambio del prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>Visualización de entidades

En el nodo **Componentes** del Explorador de soluciones, seleccione el nodo **Entidades**.

![Visualización de entidades en el Explorador de soluciones](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>Creación de una entidad

Mientras [visualiza las entidades](#view-entities), seleccione **Nuevo** para abrir el formulario para la nueva entidad.

![Formulario para la nueva entidad en el Explorador de soluciones](media/new-entity-form-solution-explorer.png)

El formulario para la nueva entidad tiene dos pestañas. La pestaña **General** sirve para las opciones de la entidad. La pestaña **Campo principal** sirve para las opciones de la línea única especial del campo de texto que tiene cada entidad que define el texto que se muestra cuando hay un vínculo para abrir la entidad en un campo de búsqueda.

Para obtener información sobre cada sección, vea lo siguiente:
- [Configuración del campo principal](#configure-the-primary-field)
- [Configuración de los campos obligatorios](#configure-required-fields)

> [!NOTE]
> También puede convertir la entidad en una actividad personalizada. Esta selección cambia algunos de los valores de opción predeterminados. Más información: [Creación de una entidad de actividad personalizada](#create-custom-activity-entity)

Una vez configuradas las opciones necesarias para la entidad, haga clic en ![Guardar comando](media/save-entity-icon-solution-explorer.png) para crear la entidad personalizada.

### <a name="configure-the-primary-field"></a>Configuración del campo principal

En la pestaña **Campo principal**, normalmente puede aceptar los valores predeterminados del campo principal, pero tiene las siguientes opciones:

|Campo   |Descripción  |
|---------|---------|
|**Nombre para mostrar**|Escriba la etiqueta localizable que se mostrará para este campo en formularios y listas. El valor predeterminado es **Nombre**.|
|**Nombre**|Establezca el nombre utilizado en el sistema para este campo. El valor predeterminado es `<customization prefix>_name`.|
|**Longitud máxima**|Escriba la longitud máxima de los valores de campo. El valor predeterminado es 100.|

> [!NOTE]
> Estas opciones no se aplican si la entidad es una entidad de actividad. Más información: [Creación de una entidad de actividad personalizada](#create-custom-activity-entity)

### <a name="configure-required-fields"></a>Configuración de los campos obligatorios

En la pestaña **General**, algunas de las opciones son necesarias para poder guardar la entidad.

|Campo   |Descripción  |
|---------|---------|
|**Nombre para mostrar**|Este es el nombre singular de la entidad que se mostrará en la aplicación.<br />Se puede cambiar más adelante.|
|**Nombre en plural**|Es el nombre en plural de la entidad que se mostrará en la aplicación.<br />Se puede cambiar más adelante.|
|**Nombre**|Este campo se rellena automáticamente en función del nombre para mostrar que se escriba. Incluye el prefijo de personalización del editor de soluciones.|
|**Propiedad**|Puede elegir la propiedad de usuario, equipo u organización. Más información: [Entity ownership](types-of-entities.md#entity-ownership) (Propiedad de la entidad)|

## <a name="edit-an-entity"></a>Edición de una entidad

Mientras [visualiza las entidades](#view-entities), seleccione la entidad que desea editar o continúe con la edición de una entidad nueva que acaba de guardar.

> [!NOTE]
> Las entidades estándar o las entidades personalizadas que forman parte de una solución administrada pueden tener limitaciones en los cambios que se pueden aplicar. Si la opción no está disponible o está deshabilitada, no se permite realizar el cambio.

#### <a name="set-once-options"></a>Configuración de opciones una sola vez

Las siguientes opciones se pueden establecer una sola vez y, por tanto, no se pueden cambiar después de configurarlas. Tenga cuidado de establecer estas opciones solo cuando las necesite.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

#### <a name="options-that-you-can-change"></a>Opciones que se pueden cambiar

Las siguientes propiedades pueden cambiarse en cualquier momento.

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)]

También puede realizar los cambios siguientes:
- [Crear y editar los campos de Common Data Service para aplicaciones](create-edit-fields.md)
- [Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)
- [Crear y diseñar formularios](../model-driven-apps/create-design-forms.md)
- [Crear un flujo de procesos empresariales para normalizar procesos](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>Eliminación de una entidad

Como un usuario con el rol de seguridad de administrador del sistema, puede eliminar entidades personalizadas que no forman parte de una solución administrada.  
  
> [!IMPORTANT]
>  Cuando se elimina una entidad personalizada, las tablas de base de datos que almacenan datos de dicha entidad se eliminan y, en consecuencia, se pierden todos los datos que contienen. También se eliminan los registros asociados que tienen una relación jerárquica con la entidad personalizada. Para más información sobre las relaciones jerárquicas, vea [Creación y edición de relaciones entre entidades](create-edit-entity-relationships.md).  
  
> [!NOTE]
> La única manera de recuperar datos de una entidad eliminada es restaurar la base de datos desde un punto anterior a la eliminación de la entidad. Más información: [Copia de seguridad y restauración de instancias](/dynamics365/customer-engagement/admin/backup-restore-instances)

Mientras [visualiza las entidades](#view-entities), haga clic en el comando ![Eliminar](media/delete.gif) en la barra de herramientas.

Durante la visualización de una entidad, use el comando de eliminación de la barra de menús.

![Comando Eliminar](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> Si se elimina una entidad que contiene datos, también se eliminarán todos los datos. Estos datos solo se pueden recuperar mediante la copia de seguridad de la base de datos.

> [!NOTE]
> Si la entidad tiene dependencias, obtendrá un error **No se puede eliminar el componente** con un vínculo **Detalles** que puede usar para encontrar información sobre por qué no se puede eliminar la entidad. En la mayoría de los casos, esto se debe a una dependencia que se debe quitar. 
>
> Puede haber más de una dependencia que bloquea la eliminación de una entidad. Este mensaje de error puede que solo muestre la primera. Para tener una forma alternativa de encontrar dependencias, vea [Identificación de dependencias de entidad](#identify-entity-dependencies).



### <a name="identify-entity-dependencies"></a>Identificación de dependencias de entidad

Puede identificar las dependencias que impedirán que una entidad se elimine antes de intentar eliminarla. 

1. En el Explorador de soluciones con la entidad seleccionada, haga clic en **Mostrar dependencias** en la barra de comandos.

![Comando Mostrar dependencias](media/entity-show-dependencies.png)

2. En la ventana del cuadro de diálogo que se abre, desplácese por la lista hacia la derecha para ver la columna **Tipo de dependencia**.

![Tipo de dependencia publicada](media/published-entity-dependency.png)

Las dependencias **publicadas** bloquearán la eliminación de una entidad. El sistema debe resolver las dependencias **internas**.  

3. Quite estas dependencias publicadas y, después, debe ser capaz de eliminar la entidad.

 > [!NOTE]
 > Una dependencia muy habitual es que otro formulario de entidad tiene un campo de búsqueda para la entidad que va a eliminar. Quitar el campo de búsqueda del formulario resolverá la dependencia.

## <a name="create-custom-activity-entity"></a>Creación de una entidad de actividad personalizada

Para crear la entidad como una entidad de actividad, use los mismos pasos descritos en este tema, excepto seleccionar **Definir como una entidad de actividad**.

![Definir como entidad de actividad](media/create-activity-entity-solution-explorer.png)

Una entidad de actividad es un tipo especial de entidad que realiza el seguimiento de acciones para las que se puede realizar una entrada en un calendario. Más información: [Entidades de actividad](types-of-entities.md#activity-entities).

Si configura esta opción, algunas propiedades de entidad no son compatibles. Una entidad de actividad tiene que ajustarse a los comportamientos estándar que utilizan todas las entidades de actividad.

El campo principal **Nombre** y **Nombre para mostrar** se establecerá en **Asunto**, y esto no se puede modificar.

Las siguientes opciones se establecen de forma predeterminada y no se pueden cambiar:

 - **Comentarios**
 - **Notas (incluye los datos adjuntos)**
 - **Conexiones**
 - **Colas**
 - **Capacidad de trabajar sin conexión de Dynamics 365 para Outlook**

Las opciones siguientes no se pueden establecer:

- **Áreas que muestran esta entidad**
- **Actividades**
- **Enviar correo electrónico**
- **Combinar correspondencia**
- **Auditoría de registro único**
- **Auditoría de registros múltiples**

## <a name="create-a-virtual-entity"></a>Creación de una entidad virtual

Algunas opciones solo se usan al crear una entidad virtual.

|Opción   |Descripción  |
|---------|---------|
|**Entidad virtual**|Si la entidad es una entidad virtual.|
|**Origen de datos**|El origen de datos de la entidad.|

Más información: [Crear y editar entidades virtuales que contienen datos de un origen de datos externo](create-edit-virtual-entities.md)

### <a name="see-also"></a>Vea también
[Creación y edición de entidades en Common Data Service para aplicaciones](create-edit-entities.md)<br />
[Tutorial: Creación de una entidad personalizada que tiene componentes en PowerApps](/powerapps/maker/common-data-service/create-custom-entity)<br />
[Crear una solución](create-solution.md)