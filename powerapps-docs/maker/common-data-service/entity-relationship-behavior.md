---
title: Comportamiento de las relaciones entre entidades (Common Data Service para aplicaciones) | MicrosoftDocs
description: <Description>
ms.custom: ''
ms.date: 08/01/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
---
# <a name="entity-relationship-behavior"></a>Comportamiento de relación de entidades

Los comportamientos de las entidades relacionadas es importante porque ayuda a garantizar la integridad de los datos segura y puede automatizar los procesos de negocio para su empresa.

## <a name="preserve-data-integrity"></a>Preservación de la integridad de los datos

Algunas entidades existen para admitir otras entidades. No tienen sentido por sí solas. Tendrán normalmente un campo de búsqueda requerido para vincularlo a la entidad principal que admiten. ¿Qué debe suceder cuando el registro principal se elimina?

Puede usar el comportamiento de la relación para definir esto según las reglas para su negocio. Las dos opciones son:

- Evitar eliminar la entidad principal para poder reconciliar los registros de entidades relacionadas, quizás asociándolas a otra entidad principal.
- Permitir que eliminen a las entidades relacionadas automáticamente con la eliminación del registro de entidad principal.

Si la entidad relacionada no admite una entidad principal, puede permitir que eliminen a la entidad principal y el valor de búsqueda se vaciará.

## <a name="automate-business-processes"></a>Automatización de los procesos de negocio
  
Digamos que tiene un nuevo comercial y que desea asignarle varias cuentas existentes actualmente asignadas a otro comercial. Cada registro de cuenta puede tener varias actividades de tareas asociadas. Puede buscar fácilmente las cuentas activas que desea reasignar y asignarlas al nuevo comercial. ¿Qué sucedería con cualquiera de estas actividades de tareas asociadas con las cuentas? ¿Desea abrir todas las tareas y decidir si también deben asignarse al nuevo comercial? Probablemente no. En su lugar, puede permitir que la relación aplique algunas reglas estándar automáticamente. Estas reglas solo se aplican a los registros de tareas asociados a cuentas que está reasignando. Sus opciones son:  
  
- Reasignar todas las tareas activas.  
- Reasignar todas las tareas. 
- No reasignar ninguna de las tareas.  
- Reasignar todas las tareas asignadas actualmente al propietario anterior de la cuenta.  
  
La relación puede controlar el modo en que las acciones realizadas en un registro para el registro de entidad principal se ponen en cascada en los registros de entidad relacionados.  

## <a name="behaviors"></a>Comportamientos

Existen varios tipos de comportamientos que se pueden aplicar cuando se producen determinadas acciones.

|Comportamiento|Descripción|
|--|--|
|**Poner activa en cascada**|Realiza la acción en todos los registros de entidad relacionados activos.|
|**Poner todas en cascada**|Realiza la acción en todos los registros de entidad relacionados.|
|**No poner ninguna en cascada**|No hacer nada.|
|**Quitar vínculo**|Quite el valor de búsqueda para todos los registros relacionados.|
|**Restringir**|Impide que el registro de entidad principal se elimine cuando existen registros de entidad relacionados.|
|**Poner en cascada las que pertenecen al usuario**|Realiza una acción en todos los registros de entidad relacionados que pertenecen al mismo usuario que el registro de entidad principal.|

## <a name="actions"></a>Acciones

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

## <a name="limitations-on-behaviors-you-can-set"></a>Limitaciones en comportamientos que puede establecer
  
Dado que son relaciones jerárquicas, existen limitaciones que debe tener presentes cuando defina las relaciones de entidad.  
  
- Una entidad personalizada no puede ser la entidad principal en una relación con una entidad del sistema relacionada que esté en cascada. Esto quiere decir que no puede tener una relación con alguna acción establecida en **Poner todas en cascada**, **Poner activa en cascada** o **Poner en cascada las que pertenecen al usuario** entre una entidad personalizada principal y una entidad del sistema relacionada.  
- Ninguna relación nueva puede tener alguna acción establecida en **Poner todas en cascada**, **Poner activa en cascada** o **Poner en cascada las que pertenecen al usuario** si la entidad relacionada de esa relación ya existe como entidad relacionada en otra relación que tenga alguna acción establecida en **Poner todas en cascada**, **Poner activa en cascada** o **Poner en cascada las que pertenecen al usuario**. Esto evita que se creen relaciones entre varias entidades principales.  
