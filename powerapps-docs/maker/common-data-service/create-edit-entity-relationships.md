---
title: Información general sobre las relaciones entre entidades para Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 04/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: c765b6d9-4d87-4c2d-aae2-5b1c3b664a71
caps.latest.revision: 28
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 400fb236df41fefc8a9cfa7175ebfd8260ec96bd
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2707491"
---
# <a name="entity-relationships-overview"></a>Información general sobre relaciones entre entidades
Las relaciones de entidad definen cómo pueden relacionarse los registros entre sí en la base de datos. En el nivel más sencillo, si agrega un campo de búsqueda a una entidad se crea una nueva relación 1:N (uno a varios) entre las dos entidades y permite colocar el campo de búsqueda en un formulario. Con el campo de búsqueda, los usuarios pueden asociar varios registros *secundarios* de la entidad a un solo registro de la entidad *primaria*.  
  
Además de simplemente definir cómo pueden relacionarse los registros con otros registros, las relaciones de entidad 1:N también ofrecen datos para abordar las siguientes preguntas:  
  
- ¿Cuándo elimino un registro debo eliminar también los registros relacionados con dicho registro?  
- ¿Cuándo asigno un registro, también es necesario asignar todos los registros relacionados con dicho registro al nuevo propietario?  
- ¿Cómo puedo simplificar el proceso de entrada de datos cuando creo un registro relacionado en el contexto de un registro existente?  
- ¿Cómo deberían los usuarios que visualizan un registro poder ver los registros asociados?  
  
 Las entidades pueden también participar en una relación de N:N (varios a varios) donde cualquier número de registros de dos entidades pueden asociarse entre sí.  

<a name="BKMK_Connections"></a>

## <a name="decide-whether-to-use-entity-relationships-or-connections"></a>Decida si se deben usar relaciones o conexiones de entidad 
Las relaciones de entidad son metadatos que realizan cambios en la base de datos. Estas relaciones permiten que las consultas recuperen datos relacionados de manera muy eficaz. Use las relaciones entre entidades para definir las relaciones formales que definen la entidad o que puedan usar la mayoría de los registros. Por ejemplo, una oportunidad sin un cliente potencial no será muy útil. La entidad Oportunidad también tiene una relación de N:N con la entidad Competidor. Esto permite que varios competidores se agreguen a la oportunidad. Es posible que desee capturar estos datos y para crear un informe que muestre los competidores.  
  
Hay otros tipos menos formales de relaciones entre registros que se denominan *conexiones*. Por ejemplo, puede resultar útil saber si dos contactos están casados, o quizás son amigos fuera del trabajo o quizás un contacto suele trabajar con otra cuenta. La mayoría de los negocios no generarán informes con este tipo de información ni requerirán que se introduzca, por lo que es posible que no valga la pena crear relaciones entre entidades. Más información: [Configurar valores de conexión](configure-connection-roles.md)

  
<a name="BKMK_TypesOfRelationships"></a>
 
## <a name="types-of-entity-relationships"></a>Tipos de relaciones entre entidades
Al mirar el explorador de soluciones es posible que piense que existen tres tipos de relaciones entre entidades. Realmente solo hay dos, como se muestra en la siguiente tabla.  
  
|Tipo de relación|Descripción|  
|-----------------------|-----------------|  
|**1:N (uno a varios)**|Una relación entre entidades en la que un registro de entidad para **Entidad principal** se puede asociar a muchos otros registros de **Entidad relacionada** debido a un campo de búsqueda en la entidad relacionada.<br /><br /> Al ver un registro de entidad principal puede ver una lista de los registros de entidad relacionados asociados a este.<br /><br /> En el portal de PowerApps, **Entidad actual** representa la entidad principal.|  
|**N:N (varios a varios)**|Una relación de entidad que depende de una **Entidad relación** especial, a veces denominada una entidad de intersección, para que se puedan relacionar muchos registros de una entidad con muchos registros de otra entidad.<br /><br /> Para ver los registros de cualquier entidad en una relación de N:N puede ver una lista de los registros de la otra entidad relacionados con esta.|  
  
El tipo de relación **N:1 (varios a uno)** existe en la interfaz de usuario porque el diseñador muestra una vista agrupada por entidades. Las relaciones de 1:N existen realmente *entre* entidades y hacen referencia a cada entidad como **Entidad principal/actual** o **Entidad relacionada**. La entidad relacionada, a veces denominada la entidad *secundaria*, tiene un campo de búsqueda que permite almacenar una referencia en un registro desde la entidad principal, a veces denominada la entidad *principal*. Una relación de N:1 es simplemente una relación de 1:N vista desde la entidad relacionada.  
 
## <a name="entity-relationship-behavior"></a>Comportamiento de relación de entidades
Los comportamientos de las entidades relacionadas es importante porque ayuda a garantizar la integridad de los datos segura y puede automatizar los procesos de negocio para su empresa.

### <a name="preserve-data-integrity"></a>Preservación de la integridad de los datos
Algunas entidades existen para admitir otras entidades. No tienen sentido por sí solas. Tendrán normalmente un campo de búsqueda requerido para vincularlo a la entidad principal que admiten. ¿Qué debe suceder cuando el registro principal se elimina?

Puede usar el comportamiento de la relación para definir esto según las reglas para su negocio. Las dos opciones son:

- Evitar eliminar la entidad principal para poder reconciliar los registros de entidades relacionadas, quizás asociándolas a otra entidad principal.
- Permitir que eliminen a las entidades relacionadas automáticamente con la eliminación del registro de entidad principal.

Si la entidad relacionada no admite una entidad principal, puede permitir que eliminen a la entidad principal y el valor de búsqueda se vaciará.

### <a name="automate-business-processes"></a>Automatización de los procesos de negocio
Digamos que tiene un nuevo comercial y que desea asignarle varias cuentas existentes actualmente asignadas a otro comercial. Cada registro de cuenta puede tener varias actividades de tareas asociadas. Puede buscar fácilmente las cuentas activas que desea reasignar y asignarlas al nuevo comercial. ¿Qué sucedería con cualquiera de estas actividades de tareas asociadas con las cuentas? ¿Desea abrir todas las tareas y decidir si también deben asignarse al nuevo comercial? Probablemente no. En su lugar, puede permitir que la relación aplique algunas reglas estándar automáticamente. Estas reglas solo se aplican a los registros de tareas asociados a cuentas que está reasignando. Sus opciones son:  
  
- Reasignar todas las tareas activas.  
- Reasignar todas las tareas. 
- No reasignar ninguna de las tareas.  
- Reasignar todas las tareas asignadas actualmente al propietario anterior de la cuenta.  
  
La relación puede controlar el modo en que las acciones realizadas en un registro para el registro de entidad principal se ponen en cascada en los registros de entidad relacionados.  

### <a name="behaviors"></a>Comportamientos
Existen varios tipos de comportamientos que se pueden aplicar cuando se producen determinadas acciones.

|Comportamiento|Descripción|
|--|--|
|**Poner activa en cascada**|Realiza la acción en todos los registros de entidad relacionados activos.|
|**Poner todas en cascada**|Realiza la acción en todos los registros de entidad relacionados.|
|**No poner ninguna en cascada**|No hacer nada.|
|**Quitar vínculo**|Quite el valor de búsqueda para todos los registros relacionados.|
|**Restringir**|Impide que el registro de entidad principal se elimine cuando existen registros de entidad relacionados.|
|**Poner en cascada las que pertenecen al usuario**|Realiza una acción en todos los registros de entidad relacionados que pertenecen al mismo usuario que el registro de entidad principal.|

### <a name="actions"></a>Acciones
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


### <a name="parental-entity-relationships"></a>Relaciones jerárquicas entre entidades
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
[Información general sobre los metadatos y las entidades](create-edit-metadata.md)<br />
[Crear y editar relaciones 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)<br />
[Crear relaciones entre entidades de varios a varios (N:N)](create-edit-nn-relationships.md)

