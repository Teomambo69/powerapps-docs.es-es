---
title: Información sobre relaciones entre entidades para Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
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
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
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
|**1:N (uno a varios)**|Una relación entre entidades en la que un registro de entidad para **Entidad principal** se puede asociar a muchos otros registros de **Entidad relacionada** debido a un campo de búsqueda en la entidad relacionada.<br /><br /> Al ver un registro de entidad principal puede ver una lista de los registros de entidad relacionados asociados a este.|  
|**N:N (varios a varios)**|Una relación de entidad que depende de una **Entidad relación** especial, a veces denominada una entidad de intersección, para que se puedan relacionar muchos registros de una entidad con muchos registros de otra entidad.<br /><br /> Para ver los registros de cualquier entidad en una relación de N:N puede ver una lista de los registros de la otra entidad relacionados con esta.|  
  
El tipo de relación **N:1 (varios a uno)** existe en la interfaz de usuario porque el diseñador muestra una vista agrupada por entidades. Las relaciones de 1:N existen realmente *entre* entidades y hacen referencia a cada entidad como **Entidad principal** o **Entidad relacionada**. La entidad relacionada, a veces denominada la entidad *secundaria*, tiene un campo de búsqueda que permite almacenar una referencia en un registro desde la entidad principal, a veces denominada la entidad *principal*. Una relación de N:1 es simplemente una relación de 1:N vista desde la entidad relacionada.  
 
## <a name="see-also"></a>Vea también

[Información general sobre los metadatos y las entidades](create-edit-metadata.md)<br />
[Crear y editar relaciones 1: N (uno a varios) o N:1 (varios a uno)](create-edit-1n-relationships.md)<br />
[Crear relaciones entre entidades de varios a varios (N:N)](create-edit-nn-relationships.md)

