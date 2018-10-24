---
title: Metadatos de entidad | Microsoft Docs
description: Obtenga información sobre el uso de metadatos de entidades en Common Data Service for Apps.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 60fafa90df656bb6d135a8cf7e2c2f3b4f8457da
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42840755"
---
# <a name="entity-metadata"></a>Metadatos de entidad

Cada entidad proporciona la capacidad de almacenar datos estructurados. En el caso de los desarrolladores, las entidades se corresponden a las clases que se van a usar al trabajar con datos en Common Data Service for Apps.

## <a name="entity-names"></a>Nombres de entidad
Cada entidad tiene un nombre único que se define cuando se crea. Este nombre se presenta de varias maneras:

|Propiedad de nombre |Descripción|
|---------|---------|
|`SchemaName`|Normalmente, una versión del nombre lógico con mayúsculas y minúsculas como en Pascal. Por ejemplo, Cuenta.|
|`CollectionSchemaName`|Forma plural del nombre de esquema. Por ejemplo, Cuentas.|
|`LogicalName`|Versión en minúsculas del nombre de esquema. Por ejemplo, cuenta.|
|`LogicalCollectionName`|Versión en minúsculas del nombre de esquema de colección. Por ejemplo, cuentas.|
|`EntitySetName`|Se usa para identificar colecciones con la API web. De forma predeterminada, es el mismo que el nombre de colección lógico.<br />Es posible cambiar el nombre del conjunto de entidades actualizando los metadatos mediante programación. Pero esto solo se debe hacer antes de escribir código de API web para la entidad. Más información: [Operaciones y tipos de la API web (Guía para desarrolladores de Dynamics 365 Customer Engagement) > Cambiar el nombre de un conjunto de entidades](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#change-the-name-of-an-entity-set)|

> [!NOTE]
> Cuando se crea una entidad personalizada, el nombre que se elija se anexará al principio con el valor de prefijo de personalización del editor de soluciones asociado a la solución en la que se creó la entidad. Aparte del nombre del conjunto de entidades, no se pueden cambiar los nombres de una entidad después de crearla. Si quiere nombres coherentes para los elementos de metadatos de la solución, debe crearlos en el contexto de una solución que se crea asociada con un editor de soluciones que contiene el prefijo de personalización que se va a usar. Más información: [Crear un editor de soluciones y una solución](introduction-solutions.md#create-a-solution-publisher-and-solution).

Cada entidad también tiene tres propiedades que pueden mostrar valores traducidos:


|Nombre  |Descripción  |
|---------|---------|
|`DisplayName`|Normalmente, el mismo que el nombre de esquema, pero puede incluir espacios. Por ejemplo, Cuenta.|
|`DisplayCollectionName`|Forma plural del nombre para mostrar. Por ejemplo, Cuentas.|
|`Description`|Una frase corta que describe la entidad, por ejemplo *Empresa que representa un cliente o un cliente potencial. La compañía a la que se factura en las transacciones comerciales.*|

Estos son los valores localizables que se usan para hacer referencia a las entidades de una aplicación. Estos valores se pueden cambiar en cualquier momento. Para agregar o editar valores traducidos vea [Traducir texto de entidades y campos personalizados a otros idiomas (Guía de personalización de Dynamics 365)](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).


## <a name="primary-key"></a>Clave principal

El valor de la propiedad `PrimaryIdAttribute` es el nombre lógico del atributo que es la clave principal para la entidad.

De forma predeterminada, todas las entidades tienen un solo atributo de identificador único GUID. Este se denomina normalmente *&lt; nombre lógico de la entidad &gt;*+ `Id`.

## <a name="primary-name"></a>Nombre principal

El valor de la propiedad `PrimaryNameAttribute` es el nombre lógico del atributo en el que se almacena el valor de cadena que identifica el registro de la entidad. Este es el valor que se mostrará en un vínculo para abrir el registro en una interfaz de usuario.

**Ejemplo**: la entidad Contact usa el atributo `fullname` como atributo de nombre principal.

> [!NOTE]
> No todas las entidades tendrán un nombre principal. Algunas entidades no están diseñadas para mostrarse en una interfaz de usuario.

## <a name="entity-images"></a>Imágenes de entidad

El valor de la propiedad `PrimaryImageAttribute` es el nombre lógico del atributo en el que se almacenan los datos de imagen para el registro de la entidad. Cada entidad solo puede tener un atributo de imagen y el nombre lógico de ese atributo siempre es `entityimage`.

**Ejemplo**: el atributo [EntityImage](reference/entities/contact.md#BKMK_EntityImage) de la [entidad Contact](reference/entities/contact.md) puede almacenar una imagen del contacto.

Por motivos de rendimiento, las imágenes de entidad no se incluyen en las operaciones de recuperación a menos que se soliciten explícitamente.

Cada entidad que admita las imágenes de entidad tendrá tres atributos auxiliares.

|SchemaName|Tipo|Descripción|
|--|--|--|
|`EntityImage_Timestamp` |`BigIntType`|El valor representa cuándo se actualizó la imagen por última vez y se usa para ayudar a asegurarse de que la versión más reciente de la imagen se descarga y almacena en caché en el cliente.|
|`EntityImage_URL`|`StringType`|Una dirección URL absoluta para mostrar la imagen de la entidad en un cliente.|
|`EntityImageId`|`UniqueIdentifierType`|El identificador único de la imagen|

Más información: 
- [Atributos de imagen (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/image-attributes)
- [Ejemplo: establecer y recuperar imágenes de entidad (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images)

> [!NOTE]
> Esto es diferente del icono que se muestra para una entidad en las aplicaciones controladas por modelos. La propiedad `IconVectorName` contiene el nombre del recurso web SVG que lo establece.

## <a name="types-of-entities"></a>Tipos de entidades

Las funciones y el comportamiento de las entidades dependen de varias propiedades de entidad. La mayoría de estas propiedades son relativamente simples y tienen nombres descriptivos. Cuatro que requieren una explicación adicional son: *Propiedad*, *las entidades Activity*, *la entidad Activityparty* y *las entidades secundarias*.

### <a name="entity-ownership"></a>Propiedad de entidad

Las entidades se pueden clasificar según la propiedad de los datos que contienen. Se trata de un concepto importante relacionado con cómo se aplica la seguridad a las entidades. Esta información se encuentra en la propiedad `OwnershipType`. En la tabla siguiente se describen los tipos de propiedad diferentes:

|Tipo de propiedad  |Descripción  |
|---------|---------|
|Business|Datos que pertenecen a la unidad de negocio. El acceso a los datos se puede controlar en el nivel de la unidad de negocio.|
|Ninguno|Los datos no pertenecen a otra entidad.|
|Organización|Los datos pertenecen a la organización. El acceso a los datos se controla en el nivel de la organización.|
|Usuario o Equipo|Los datos pertenecen a un usuario o un equipo. Las acciones que se pueden realizar en estos registros se pueden controlar en el nivel de un usuario.|

Al crear entidades, las únicas opciones de propiedad son: **Organización** o **Usuario o Equipo**. Una vez realizada la elección de esta opción no se puede cambiar. Elija **Usuario o Equipo** para obtener el máximo control individualizado sobre quién puede ver o realizar acciones en los registros. Elija **Organización** cuando este nivel de control no sea necesario. 

### <a name="activity-entities"></a>Entidades Activity

Una actividad es una tarea que un usuario realiza o va a realizar. Una actividad es cualquier acción para la que se puede realizar una entrada en un calendario. 

Las actividades se modelan de forma diferente a otros tipos de entidades que almacenan datos empresariales. Los datos sobre las actividades se muestran con frecuencia juntos en una lista, pero cada tipo de actividad requiere propiedades únicas. En lugar de tener una sola entidad Activity con todas las propiedades posibles, hay diferentes tipos de entidades de actividad y cada una de ellas hereda las propiedades de una [entidad ActivityPointer](reference/entities/activitypointer.md) base. Estas entidades tendrán la propiedad `IsActivity` establecida en true.


|Entidad |Descripción  |
|---------|---------|
|[Appointment](reference/entities/appointment.md)|Compromiso que representa un intervalo de tiempo con horas de inicio y fin, y duración.|
|[Email](reference/entities/email.md)|Actividad que se suministra mediante protocolos de correo electrónico.|
|[Fax](reference/entities/fax.md)|Actividad que mantiene un seguimiento del resultado de llamadas y el número de páginas para un fax y que, opcionalmente, almacena una copia electrónica del documento.|
|[Letter](reference/entities/letter.md)|Actividad que realiza el seguimiento de la entrega de una carta. La actividad puede contener la copia electrónica de la carta.|
|[PhoneCall](reference/entities/phonecall.md)|Actividad para realizar el seguimiento de una llamada telefónica.|
|[RecurringAppointmentMaster](reference/entities/recurringappointmentmaster.md)|La cita principal de una serie de citas periódicas.|
|[SocialActivity](reference/entities/socialactivity.md)|Solo para uso interno.|
|[Task](reference/entities/task.md)|Actividad genérica que representa el trabajo que se debe realizar.|

Cada vez que alguien crea uno de estos tipos de registros de entidad de actividad, se creará el registro de entidad `ActivityPointer` correspondiente con el mismo valor de atributo de identificador único `ActivityId`. No se pueden crear, actualizar o eliminar instancias de la entidad `ActivityPointer`, pero se pueden recuperar. Esto es lo que permite que todos los tipos de actividades se presenten juntos en una lista.

Se pueden crear entidades de actividad personalizadas que se comporten de la misma manera.
<!-- TODO: Add link to topic about creating an activity entity -->

### <a name="activityparty-entity"></a>Entidad ActivityParty

Esta entidad se usa para agregar estructura a los atributos de la entidad de actividad `PartyListType` que incluyen referencias a otras entidades. Esta entidad se usará al establecer valores para atributos de entidad de actividad como `Email.to` o `PhoneCall.from`. Dentro de la [entidad ActivityParty](reference/entities/activityparty.md), se establece el atributo [ParticipationTypeMask](reference/entities/activityparty.md#BKMK_ParticipationTypeMask) para definir el rol que la referencia está desempeñando. Los roles incluyen `Sender`, `ToRecipient`, `Organizer` y muchos más.

Se puede consultar la entidad `ActivityParty`, pero no se puede crear, recuperar, actualizar o eliminar una entidad ActivityParty fuera de la actividad con la que está relacionada.
Más información: 
- [Entidad ActivityParty (actividad) (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/activityparty-entity).


### <a name="child-entities"></a>Entidades secundarias

Las entidades donde la propiedad `IsChildEntity` es true nunca tendrán ningún privilegio definido y nunca serán propiedad del Usuario o el Equipo. Las operaciones que se pueden realizar en una entidad secundaria están enlazadas a una entidad a la que se asocian a través de una relación varios a uno. Los usuarios solo pueden realizar operaciones en las entidades secundarias si pueden realizar la misma operación en la entidad relacionada. Las entidades secundarias se eliminan automáticamente cuando se elimina el registro de entidad del que dependen.

Por ejemplo, `PostComment`, `PostLike` y `PostRole` son elementos secundarios de la entidad `Post`.

## <a name="entity-keys"></a>Claves de entidad

Cada definición de clave alternativa describe uno o más atributos combinados que identifican de forma única una instancia de entidad. Normalmente, las claves alternativas solo se aplican para la integración con sistemas externos. Se pueden definir claves alternativas para identificar un registro de forma única. Esto es útil si se van a integrar datos con un sistema que no admite claves de identificador único de GUID. Se puede definir un valor de campo único o una combinación de valores de campo para identificar una entidad. Agregar una clave alternativa aplicará una restricción de unicidad en estos atributos. No se podrá crear o actualizar otro registro de entidad que tenga los mismos valores.

Más información: 
 - [Definir claves alternativas para hacer referencia a registros de Dynamics 365 (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/define-alternate-keys-reference-records)
 - [Sincronización de datos de Dynamics 365 con sistemas externos (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/synchronize-dynamics-365-data-with-external-systems)

## <a name="entity-states"></a>Estados de entidad

La mayoría de las entidades tiene dos propiedades para realizar el seguimiento del estado de un registro. Se trata de `StateCode`, que se denomina **Estado** en las aplicaciones controladas por modelos y `StatusCode`, que se denomina **Razón para el estado** en esas aplicaciones. 

Ambos atributos contienen un conjunto de opciones que muestran los valores válidos. Los valores de atributo `StateCode` y `StatusCode` están vinculados para que solo determinadas opciones `StatusCode` sean válidas para un `StateCode` dado.

Esto puede variar por entidad, pero el modelo común de muchas entidades, y el predeterminado para las entidades personalizadas, es el siguiente:

|Opciones de StateCode  |Opciones de StatusCode  |
|---------|---------|
|0: Activo|1: Activo|
|1: Inactivo|2: Inactivo|

Algunas entidades tendrán otros conjuntos de opciones. 

**Ejemplo**: Opciones `StateCode` y `StatusCode` de la entidad `PhoneCall`


|`StateCode`|`StatusCode`|
|---------|---------|
|0: Abierto|1: Abierto|
|1: Completado|2: Realizado <br />4: Recibido|
|2: Cancelado|3: Cancelado|

El conjunto de códigos de estado válidos para una entidad no es personalizable, pero los códigos de estado sí. Se pueden agregar más opciones `StatusCode` para el `StateCode` correspondiente.

Para las entidades personalizadas, se pueden definir criterios adicionales para las transiciones válidas entre estados. Más información: 
- [Personalizar metadatos de atributos de entidad (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)
- [Definir transiciones de modelo de estado personalizadas (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions).

### <a name="see-also"></a>Vea también

[Entidades de Common Data Service for Apps](entities.md)
