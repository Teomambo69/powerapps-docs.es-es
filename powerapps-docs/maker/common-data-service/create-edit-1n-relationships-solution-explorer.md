---
title: 'Creación y edición de relaciones de entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones | MicrosoftDocs'
description: Aprenda a crear relaciones entre entidades de uno a varios o de varios a uno con el explorador de soluciones de PowerApps
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-and-edit-1n-one-to-many-or-n1-many-to-one-entity-relationships-using-solution-explorer"></a>Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones 

El explorador de soluciones proporciona una forma de crear y editar relaciones entre entidades de 1:N (uno a varios) o N:1 (varios a uno) para Common Data Service para aplicaciones.

El [portal PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) permite configurar las opciones más comunes, pero algunas opciones solo se pueden configurar usando el explorador de soluciones. Más información: 
- [Crear relaciones 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)
- [Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) en el portal de PowerApps](create-edit-1n-relationships-portal.md)
  
## <a name="open-solution-explorer"></a>Abra el explorador de soluciones

La parte del nombre de cualquier relación personalizada que cree es el prefijo de personalización. Esto se establece en función del editor de soluciones para la solución en la que trabaja. Si le interesa el prefijo de personalización, asegúrese de que está trabajando en una solución no administrada donde el prefijo de personalización es el que desea para esta entidad. Más información: [Cambiar el prefijo del editor de soluciones](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>Ver relaciones entre entidades

En el explorador de soluciones, expanda **Entidades** y seleccione una entidad. En esa entidad, seleccione **Relaciones de 1:N** o **Relaciones de N:1**.

![Ver relaciones entre entidades](media/view-1n-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>Crear relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione **Nueva relación de uno a varios** o **Nueva relación de varios a uno** de la barra de comandos.

> [!NOTE]
> Si los comandos no están disponibles, la entidad no es válida para crear una relación personalizada.

Cualquier opción abrirá un formulario como el siguiente. La diferencia es si está establecido el campo **Entidad principal** o **Entidad relacionada**.

![Formulario de nueva relación de uno a varios](media/new-1n-entity-relationship-form-solution-explorer.png)

- Con **Relación de 1:N**, la **Entidad principal** se establece como entidad actual
- Con **Relación de N:1**, la **Entidad relacionada** se establece como entidad actual

Los siguientes campos deben establecerse para guardar la relación entre entidades:

|Campo obligatorio|Descripción|
|--|--|
|**Entidad principal**|Esta entidad será el tipo de destino del campo de búsqueda creado en la entidad relacionada.|
|**Entidad relacionada**|Esta entidad tendrá un campo de búsqueda agregado para asociar los registros de entidad con el registro de entidad principal.|
|**Nombre**|El nombre de la relación. Se generará un valor en función de los valores de entidad principales y relacionados. Se agregará al campo el prefijo de personalización del editor de soluciones.|
|**Nombre para mostrar del campo de búsqueda**|El texto localizable del campo de búsqueda que se creará para la entidad relacionada. Suele ser el mismo que el nombre para mostrar de la entidad principal. <br /> Se puede cambiar posteriormente.|
|**Nombre de campo de búsqueda**|El nombre del campo de búsqueda que se creará en la entidad relacionada. Se generará un valor en función del **Nombre para mostrar del campo de búsqueda**. Se agregará al campo el prefijo de personalización del editor de soluciones.|

Puede hacer clic en ![Botón Guardar relación entre entidades](media/save-entity-icon-solution-explorer.png) para guardar la entidad y para continuar editando. Más información: [Editar relaciones](#edit-relationships)

> [!NOTE]
> Si los valores de **Nombre** o **Nombre del campo de búsqueda** ya existen en el sistema se mostrará un error cuando guarde. Edite los valores de modo que sean únicos y vuelva a intentarlo.

## <a name="edit-relationships"></a>Editar relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione la entidad que desea editar. Las siguientes propiedades de relación entre entidades pueden editarse una vez creada la relación.

> [!NOTE]
> El editor de una solución administrada puede evitar algunas personalizaciones de relaciones que forman parte de la solución.

### <a name="entity-relationship-properties"></a>Propiedades de relación entre entidades

Estas las propiedades son sobre la relación.

|Campo|Descripción|
|--|--|
|**Búsqueda**|Si esta relación debe ser visible en Búsqueda avanzada en aplicaciones basadas en modelos. Seleccione **No** si es una relación que no es importante para su empresa.|
|**Jerárquica**|Esta opción se habilita únicamente para relaciones que hacen referencia a sí mismas. Si la entidad debe ser considerada para definir una jerarquía de la entidad.<br />**Importante**: Una vez que establece esta propiedad, puede configurar campos consolidados, procesos, y vistas para que dependan de esta propiedad. Si cambia posteriormente este valor, las capacidades que dependen de la jerarquía no funcionarán. <br />Más información: [Definir y consultar datos relacionados jerárquicamente](define-query-hierarchical-data.md)|

### <a name="lookup-field"></a>Campo de búsqueda

Son propiedades del campo de búsqueda creado en la entidad relacionada. Las propiedades se pueden editar aquí o editando el campo de búsqueda directamente. Algunas propiedades de campo no son editables desde la relación. Más información: [Editar un campo](create-edit-field-solution-explorer.md#edit-a-field)

|Campo|Descripción|
|--|--|
|**Nombre para mostrar**|El texto localizable del campo de búsqueda que se creará para la entidad relacionada.|
|**Requisito de campo**|Si el campo debe tener datos antes de que se pueda guardar un formulario en una aplicación basada en modelos. Más información: [Opciones de requisito de campo](create-edit-field-solution-explorer.md#field-requirement-options)|
|**Descripción**|Escriba instrucciones para indicar al usuario para qué sirve el campo. Estas descripciones aparecen como información sobre herramientas para el usuario en aplicaciones basadas en modelos cuando mantienen el mouse sobre la etiqueta del campo.|

### <a name="navigation-pane-item-for-primary-entity"></a>Elemento del panel de navegación para una entidad principal

Desde la entidad principal puede navegar para ver registros relacionados. Estos datos se usan en aplicaciones basadas en modelos para controlar cómo se muestran los registros de entidades relacionadas. Estos valores también se pueden editar mediante el editor de formularios.

|Campo|Descripción|
|--|--|
|**Opción de visualización**|Cómo se debe mostrar la lista de entidades relacionadas. Más información: [Opciones de visualización](#display-options)|
|**Etiqueta personalizada**|Especifique el texto localizable que se usará en lugar del nombre plural cuando seleccione **Usar etiqueta personalizada** como **Opción de visualización**.|
|**Área de visualización**|Seleccione una de las agrupaciones disponibles para mostrar esta lista. Las opciones disponibles son: **Detalles** (para el grupo *Común* ), **Marketing**, **Ventas** y **Servicio**. |
|**Orden de visualización**|Controla dónde se incluirá el elemento de navegación en el área de visualización seleccionada. El intervalo de números admitidos empieza con 10.000. Los elementos del panel de navegación con un valor inferior aparecerán encima de otras relaciones con un valor más alto.|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>Opciones de visualización

Estas son las opciones de visualización disponibles:

|Opción|Descripción|
|--|--|
|**No mostrar**|No muestra las entidades relacionadas para esta relación.|
|**Usar etiqueta personalizada**|Cuando se selecciona esta opción, se habilita el campo **Etiqueta personalizada** para que pueda especificar el texto localizable que se usará en lugar del nombre plural.|
|**Usar nombre plural**|Use el nombre plural para mostrar definido para la entidad relacionada.|

### <a name="relationship-behavior"></a>Comportamiento de las relaciones

Aquí es donde puede definir los comportamientos estándar para entidades relacionadas. Esta información es importante porque ayuda a garantizar la integridad de los datos segura y puede automatizar los procesos de negocio para su empresa.

Veamos un ejemplo.  
  
Digamos que tiene un nuevo comercial y que desea asignarle varias oportunidades existentes actualmente asignadas a otro comercial. Cada registro de oportunidad puede tener varias actividades de tareas asociadas. Puede buscar fácilmente las oportunidades activas que desea reasignar y asignarlas al nuevo comercial. ¿Qué sucedería con cualquiera de estas actividades de tareas asociadas con las oportunidades? ¿Desea abrir todas las tareas y decidir si también deben asignarse al nuevo comercial? Probablemente no. En su lugar, puede permitir que la relación aplique algunas reglas estándar automáticamente. Estas reglas solo se aplican a los registros de tareas asociados a oportunidades que está reasignando. Sus opciones son:  
  
- Reasignar todas las tareas activas.  
- Reasignar todas las tareas. 
- No reasignar ninguna de las tareas.  
- Reasignar todas las tareas asignadas actualmente al propietario anterior de la oportunidad.  
  
La relación puede controlar el modo en que las acciones realizadas en un registro para el registro de entidad principal se ponen en cascada en los registros de entidad relacionados.   

Existen varios tipos de comportamientos que se pueden aplicar cuando se producen determinadas acciones.

#### <a name="behaviors"></a>Comportamientos

Estos son los comportamientos disponibles para configurar.

|Comportamiento|Descripción|
|--|--|
|**Poner activa en cascada**|Realiza la acción en todos los registros de entidad relacionados activos.|
|**Poner todas en cascada**|Realiza la acción en todos los registros de entidad relacionados.|
|**No poner ninguna en cascada**|No hacer nada.|
|**Quitar vínculo**|Quite el valor de búsqueda para todos los registros relacionados.|
|**Restringir**|Impide que el registro de entidad principal se elimine cuando existen registros de entidad relacionados.|
|**Poner en cascada las que pertenecen al usuario**|Realiza una acción en todos los registros de entidad relacionados que pertenecen al mismo usuario que el registro de entidad principal.|

#### <a name="actions"></a>Acciones

Estos son las acciones que pueden desencadenar determinados comportamientos:

|Campo|Descripción|Opciones|
|--|--|--|
|**Asignar**|¿Qué debe suceder cuando el registro de entidad principal se asigna a otra persona?|Poner todas en cascada<br />Poner activa en cascada<br />Poner en cascada las que pertenecen al usuario<br />No poner ninguna en cascada|
|**Cambiar primario**|¿Qué debe suceder cuando cambia el valor de búsqueda de una entidad relacionada en una relación jerárquica?<br />Más información: [Relaciones jerárquicas entre entidades](#parental-entity-relationships)|Poner todas en cascada<br />Poner activa en cascada<br />Poner en cascada las que pertenecen al usuario<br />No poner ninguna en cascada|
|**Compartir**|¿Qué debe suceder cuando el registro de entidad principal se comparte?|Poner todas en cascada<br />Poner activa en cascada<br />Poner en cascada las que pertenecen al usuario<br />No poner ninguna en cascada|
|**Eliminar**|¿Qué debe suceder cuando el registro de entidad principal se elimina?|Poner todas en cascada<br />Quitar vínculo<br />Restringir|
|**Dejar de compartir**|¿Qué debe suceder cuando un registro de entidad principal deja de compartirse?|Poner todas en cascada<br />Poner activa en cascada<br />Poner en cascada las que pertenecen al usuario<br />No poner ninguna en cascada|
|**Combinar**|¿Qué debe suceder cuando un registro de entidad principal se combina?|Poner todas en cascada<br />No poner ninguna en cascada|
|**Vista de informe**|¿Cuál es el comportamiento deseado de la vista de informe asociada a esta relación? |Poner todas en cascada<br />Poner activa en cascada<br />Poner en cascada las que pertenecen al usuario<br />No poner ninguna en cascada|

<!-- TODO: I find no official docs related to rollup views, but plenty of hits online: https://www.google.com/search?q=Dynamics+365++%27rollup+view%27 -->



#### <a name="type-of-behavior-options"></a>Opciones de tipo de comportamiento

Use el campo **Tipo de comportamiento** para elegir entre un conjunto de comportamientos estándar o si desea configurarlos independientemente. 

|Opción|Descripción|
|--|--|
|**Jerárquica**|**Asignar**: Poner todas en cascada<br />**Cambiar primario**: Poner todas en cascada<br />**Compartir**: Poner todas en cascada<br />**Eliminar**: Poner todas en cascada<br />**Dejar de compartir**: Poner todas en cascada<br />**Combinar**: No poner ninguna en cascada<br />**Vista de informe**: No poner ninguna en cascada \| Poner todas en cascada<br />|
|**De referencia**|**Asignar**: No poner ninguna en cascada<br />**Cambiar primario**: No poner ninguna en cascada<br />**Compartir**: No poner ninguna en cascada<br />**Eliminar**: Quitar vínculo<br />**Dejar de compartir**: No poner ninguna en cascada<br />**Combinar**: No poner ninguna en cascada<br />**Vista de informe**: No poner ninguna en cascada \| Poner todas en cascada<br />|
|**De referencia, restringir eliminación**|**Asignar**: No poner ninguna en cascada<br />**Cambiar primario**: No poner ninguna en cascada<br />**Compartir**: No poner ninguna en cascada<br />**Eliminar**: Restringir<br />**Dejar de compartir**: No poner ninguna en cascada<br />**Combinar**: No poner ninguna en cascada<br />**Vista de informe**: No poner ninguna en cascada \| Poner todas en cascada<br />|
|**En cascada configurable**|Puede configurar el comportamiento que desea para cada acción en función de las opciones disponibles|

> [!NOTE]
> Es posible que no pueda seleccionar la opción **Jerárquica** si una de las entidades ya participa en una relación jerárquica entre entidades. Más información: [Relaciones jerárquicas entre entidades](#parental-entity-relationships)
> 
> Si usa **En cascada configurable** para establecer los comportamientos de las acciones para que coincidan con los comportamientos de las acciones asociadas con otro **Tipo de comportamiento** cuando guarda la relación, el **Tipo de comportamiento** se establece automáticamente en el tipo coincidente.  



## <a name="delete-relationships"></a>Eliminar relaciones

Mientras [ve relaciones entre entidades](#view-entity-relationships), seleccione la relación entre entidades que desea eliminar y haga clic en el comando ![Eliminar comando](media/delete.gif).

Al eliminar la relación se eliminará el campo de búsqueda en la entidad relacionada.

> [!NOTE]
> No podrá eliminar una relación que tenga dependencias. Por ejemplo, si ha agregado el campo de búsqueda a un formulario para la entidad relacionada, debe quitar el campo del formulario antes de eliminar la relación.

## <a name="parental-entity-relationships"></a>Relaciones jerárquicas entre entidades

Cada par de entidades que pueden tener una relación de 1:N pueden tener varias relaciones de 1:N entre ellas. Sin embargo, generalmente solo una de esas relaciones se puede considerar como una relación jerárquica entre entidades.

Una relación jerárquica entre entidades es cualquier relación de 1:N en la que una de las opciones en cascada en la columna **Jerárquica** de la siguiente tabla es verdadera.

|Para|Jerárquica|No jerárquica|  
|------------|--------------|------------------|  
|**Asignar**|Poner todas en cascada<br />Poner en cascada las que pertenecen al usuario<br />Poner activa en cascada|No poner ninguna en cascada|  
|**Eliminar**|Poner todas en cascada|RemoveLink<br />Restringir|  
|**Cambiar primario**|Poner todas en cascada<br />Poner en cascada las que pertenecen al usuario<br />Poner activa en cascada|No poner ninguna en cascada|  
|**Compartir**|Poner todas en cascada<br />Poner en cascada las que pertenecen al usuario<br />Poner activa en cascada|No poner ninguna en cascada|  
|**Dejar de compartir**|Poner todas en cascada<br />Poner en cascada las que pertenecen al usuario<br />Poner activa en cascada|No poner ninguna en cascada|  

Por ejemplo, si crea una nueva entidad personalizada y agrega una relación de 1:N entre entidades con la entidad de cuenta en la que la entidad personalizada es la entidad relacionada, puede configurar las acciones para que dicha relación entre entidades use las opciones de la columna **Jerárquica**. Si más adelante agrega otra relación de 1:N entre entidades con la entidad personalizada como la entidad de referencia, solo puede configurar las acciones para que usen las opciones de la columna **No jerárquica**.

Normalmente, esto significa que para cada par de entidad solo hay una relación jerárquica. Hay algunos casos en los que la búsqueda en la entidad relacionada puede permitir que una relación sea más de un tipo de entidad.

Por ejemplo, si una entidad tiene una búsqueda de cliente que pueda hacer referencia a un contacto o a la entidad de cuenta. Hay dos relaciones jerárquicas entre entidades de 1:N diferentes.

Cualquier entidad de actividad tiene un conjunto similar de relaciones jerárquicas entre entidades para entidades que pueden asociarse a través del campo de búsqueda Referente a.

<a name="BKMK_RelationshipBehaviorLimitations"></a>   

### <a name="limitations-on-behaviors-you-can-set"></a>Limitaciones en comportamientos que puede establecer
  
Dado que son relaciones jerárquicas, existen limitaciones que debe tener presentes cuando defina las relaciones de entidad.  
  
- Una entidad personalizada no puede ser la entidad principal en una relación con una entidad del sistema relacionada que esté en cascada. Esto quiere decir que no puede tener una relación con alguna acción establecida en **Poner todas en cascada**, **Poner activa en cascada** o **Poner en cascada las que pertenecen al usuario** entre una entidad personalizada principal y una entidad del sistema relacionada.  
- Ninguna relación nueva puede tener alguna acción establecida en **Poner todas en cascada**, **Poner activa en cascada** o **Poner en cascada las que pertenecen al usuario** si la entidad relacionada de esa relación ya existe como entidad relacionada en otra relación que tenga alguna acción establecida en **Poner todas en cascada**, **Poner activa en cascada** o **Poner en cascada las que pertenecen al usuario**. Esto evita que se creen relaciones entre varias entidades principales.  

### <a name="see-also"></a>Vea también

[Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)<br />
[Crear y editar relaciones 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) en el portal de PowerApps](create-edit-1n-relationships-portal.md)<br />
[Crear relaciones N:N (varios a varios)](create-edit-nn-relationships.md)

