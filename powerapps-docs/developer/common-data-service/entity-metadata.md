---
title: Metadatos de entidad | Microsoft Docs
description: Conozca el uso de metadatos de entidad en Common Data Service para aplicaciones.
services: ''
suite: powerapps
documentationcenter: na
author: mayadumesh
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
<!-- 
Was Mike Carter
This topic was not migrated it was written for PowerApps 

Overlap with content in https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/introduction-entities

-->
# <a name="entity-metadata"></a>Metadatos de la entidad

Cada entidad proporciona la capacidad de almacenar datos estructurados. Para los desarrolladores, las entidades se corresponden con las clases que usará al trabajar con datos en Common Data Service para aplicaciones.

## <a name="entity-names"></a>Nombres de entidad
Cada entidad tiene un nombre único definido cuando se crea. Este nombre aparece de diversas formas:

|Nombre de propiedad |Descripción|
|---------|---------|
|`SchemaName`|Normalmente, una versión con estilo de mayúsculas y minúsculas Pascal del nombre lógico. Por ejemplo, Cuenta|
|`CollectionSchemaName`|Versión plural del nombre del esquema. Por ejemplo, Cuentas|
|`LogicalName`|Todas las versiones en minúscula del nombre de esquema. Por ejemplo, cuenta|
|`LogicalCollectionName`|Todas las versiones en minúscula del nombre de esquema de la colección. Por ejemplo, cuentas|
|`EntitySetName`|Se utiliza para identificar colecciones con la API web. De forma predeterminada, coincide con el nombre lógico de la recopilación.<br />Es posible cambiar el nombre del conjunto de entidades mediante programación actualizando los metadatos. Pero esto se debe realizar únicamente antes de que cualquier código de la API web se escriba para la entidad. Más información: [Tipos de API web y operaciones > Cambiar el nombre de un conjunto de entidades](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#change-the-name-of-an-entity-set)|

> [!NOTE]
> Al crear una entidad personalizada, el nombre que elija estará antepuesto con el valor del prefijo de personalización del editor de soluciones asociado con la solución donde se creó la entidad. Aparte del nombre del conjunto de entidades, no podrá cambiar los nombres de una después de que se haya creado. Si desea los nombres coherentes para elementos de metadatos en la solución, debe crearlos en el contexto de una solución que cree asociada con un editor de soluciones que contenga el prefijo de personalización que desee usar. Más información: [Crear un editor de soluciones y una solución](introduction-solutions.md#create-a-solution-publisher-and-solution)

Cada entidad también tiene tres propiedades que pueden mostrar valores localizados:


|Nombre  |Descripción  |
|---------|---------|
|`DisplayName`|Normalmente, es igual al nombre de esquema, pero puede incluir espacios. Por ejemplo, Cuenta|
|`DisplayCollectionName`|Versión plural del nombre. Por ejemplo, Cuentas|
|`Description`|Frase sucinta que describe a la entidad, por ejemplo, *Empresa que representa a un cliente o cliente potencial. La empresa a la que se factura en transacciones comerciales.*|

Estos son los valores localizables que se usan para referirse a las entidades en una aplicación. Estos valores se puede cambiar en cualquier momento. Para agregar o editar valores localizados, consulte [Guía de personalización de CDS for Apps: traducir texto de entidad y de campo personalizados a otros idiomas](/dynamics365/customer-engagement/customize/export-customized-entity-field-text-translation).


## <a name="primary-key"></a>Clave principal

El valor de la propiedad `PrimaryIdAttribute` es el nombre lógico del atributo que es la clave principal de la entidad.

De forma predeterminada, todas las entidades tienen un solo atributo de identificador único GUID. Esto normalmente se denomina *&lt; nombre lógico de la entidad &gt;*+ `Id`.

## <a name="primary-name"></a>Nombre principal

El valor de la propiedad `PrimaryNameAttribute` es el nombre lógico del atributo que almacena el valor de la cadena que identifica el registro de entidad. Este es el valor que se mostrará en un vínculo para abrir el registro en una interfaz de usuario.

**Ejemplo**: la entidad contacto utiliza el atributo `fullname` como el atributo de nombre principal de la entidad.

> [!NOTE]
> No todas las entidades tienen un nombre principal. Algunas entidades no tienen como fin mostrarse en una interfaz de usuario.

## <a name="entity-images"></a>Imágenes de entidad

El valor de la propiedad `PrimaryImageAttribute` es el nombre lógico del atributo que almacena los datos de la imagen para el registro de entidad. Cada entidad solo puede tener un atributo de imagen y el nombre lógico de ese atributo es siempre `entityimage`.

**Ejemplo**: el atributo [EntityImage](reference/entities/contact.md#BKMK_EntityImage) de la [entidad Contact](reference/entities/contact.md) puede almacenar una imagen del contacto.

Por motivos de rendimiento, las imágenes de la entidad no se incluyen en las operaciones de recuperación a menos que se soliciten explícitamente.

Cada entidad que admite imágenes de entidad tendrá tres atributos de respaldo.

|SchemaName|Escriba|Descripción|
|--|--|--|
|`EntityImage_Timestamp` |`BigIntType`|El valor representa el momento en que la imagen se actualizó por última vez y se usa para asegurarse de que la versión más reciente de la imagen se descarga y se almacena en caché en el cliente.|
|`EntityImage_URL`|`StringType`|Dirección URL absoluta para mostrar la imagen de la entidad en un cliente.|
|`EntityImageId`|`UniqueIdentifierType`|El identificador único de la imagen.|

Más información: 
- [Atributos de imagen de la guía para desarrolladores de Common Data Service para aplicaciones](/dynamics365/customer-engagement/developer/image-attributes)
- [Ejemplo de la guía para desarrolladores de Common Data Service: establecer y recuperar imágenes de entidad](/dynamics365/customer-engagement/developer/sample-set-retrieve-entity-images)

> [!NOTE]
> Esto es distinto del icono que se muestra para una entidad en aplicaciones basadas en modelos. La propiedad `IconVectorName` contiene el nombre del recurso web de SVG que establece esto.

## <a name="types-of-entities"></a>Tipos de entidades

Las funcionalidades y el comportamiento de las entidades depende de varias propiedades de la entidad. La mayoría de estas propiedad son relativamente sencillas y tienen nombres descriptivos. Las cuatro que requieren una explicación adicional son: *Propiedad*, *Entidades Activity*, *Entidad Activityparty* y *Entidades secundarias*.

### <a name="entity-ownership"></a>Propiedad de la entidad

Las entidades se pueden categorizar por cómo se poseen los datos dentro de ellas. Esto es un concepto importante relativo a cómo la seguridad se aplica a las entidades. Esta información está en la propiedad `OwnershipType`. La siguiente tabla describe los diferentes tipos de propiedad:

|Tipo de propiedad  |Descripción  |
|---------|---------|
|Empresa|El datos pertenecen a la unidad de negocio. El acceso a los datos se puede controlar en el nivel de unidad de negocio.|
|Ninguno|Los datos no son propiedad de otra entidad.|
|Organización|Los datos pertenecen a la organización. El acceso a los datos se controla en el nivel de organización.|
|Usuario o equipo|Los datos pertenecen a un usuario o un equipo. Las acciones que se pueden realizar en estos registros se pueden controlar en un nivel de usuario.|

Al crear nuevas entidades, las únicas opciones de propiedad son: **Organización** o **Usuario o equipo**. Una vez que realice su elección para esta opción, no puede cambiarla. Elija **Usuario o equipo** para un control más específico sobre quién puede ver o realizar acciones en registros. Elija **Organización** si este nivel de control no es necesario. 

### <a name="activity-entities"></a>Entidades de actividad

Actividad es una tarea realizada o que va a realizar un usuario. Una actividad es cualquier acción para la que se puede crear una entrada en un calendario. 

Las actividades se modelan de forma distinta de otros tipos de entidades que almacenan datos profesionales. Los datos sobre actividades con frecuencia se muestran juntos en una lista, no obstante, cada tipo de actividad requiere propiedades únicas. En lugar de tener una sola entidad Activity con cada propiedad posible, hay tipos diferentes de entidades de actividad y cada uno de ellos hereda propiedades de una [entidad ActivityPointer](reference/entities/activitypointer.md) básica. Estas entidades tendrán una propiedad `IsActivity` establecida en True.


|Entidad |Descripción  |
|---------|---------|
|[Cita](reference/entities/appointment.md)|Compromiso que representa un intervalo de tiempo con las fechas de inicio y fin, y la duración.|
|[Correo electrónico](reference/entities/email.md)|Actividad entregada con protocolos de correo electrónico.|
|[Fax](reference/entities/fax.md)|Actividad que mantiene un seguimiento del resultado de llamadas y el número de páginas para un fax y que, opcionalmente, almacena una copia electrónica del documento.|
|[Carta](reference/entities/letter.md)|Actividad que realiza un seguimiento de la entrega de una carta. Actividad que puede contener la copia electrónica de la carta.|
|[PhoneCall](reference/entities/phonecall.md)|Actividad para mantener un seguimiento de una llamada de teléfono.|
|[Maestro recurrente de la cita](reference/entities/recurringappointmentmaster.md)|Cita principal de una serie de citas periódicas.|
|[Actividad social](reference/entities/socialactivity.md)|Solo para uso interno.|
|[Tarea](reference/entities/task.md)|Actividad genérica que representa el trabajo que se debe realizar.|

Siempre que un usuario cree uno de estos tipos de registros de entidad de actividad, el registro de entidad `ActivityPointer` correspondiente se creará con el mismo valor de identificador único `ActivityId`. No puede crear, actualizar o eliminar las instancias de la entidad `ActivityPointer`, pero puede recuperarlas. Esto es lo que permite que todos los tipos de actividad aparezcan se combinados juntos en una lista.

Puede crear entidades de actividad personalizadas que se comportan del mismo modo.
<!-- TODO: Add link to topic about creating an activity entity -->

### <a name="activityparty-entity"></a>Entidad ActivityParty

Esta entidad se utiliza para agregar estructura a los atributos de la entidad de actividad `PartyListType` que incluye referencias a otras entidades. Usará esta entidad al establecer los valores para los atributos de la entidad de actividad, como `Email.to` o `PhoneCall.from`. Dentro de la [entidad ActivityParty](reference/entities/activityparty.md), establece el atributo [ParticipationTypeMask](reference/entities/activityparty.md#BKMK_ParticipationTypeMask) para definir el rol que ejecuta la referencia. Los roles incluyen `Sender`, `ToRecipient`, `Organizer` y muchos otros.

Puede consultar la entidad `ActivityParty`, pero no puede crear, recuperar, actualizar o eliminar un grupo de actividad fuera de la actividad con la que está relacionada.
Más información: 
- [Entidad ActivityParty](/dynamics365/customer-engagement/developer/activityparty-entity).


### <a name="child-entities"></a>Entidades secundarias

Las entidades donde la propiedad `IsChildEntity` está en True nunca tendrán privilegios definidos y nunca serán propiedad de un usuario o equipo. Las operaciones que se pueden realizar en una entidad secundaria están vinculadas a una entidad a la que están asociadas mediante una relación de varios a uno. Los usuarios solo podrán realizar operaciones en las entidades secundarias si pueden realizar la misma operación en la entidad relacionada. Las entidades secundarias se eliminan automáticamente cuando el registro de entidad del que dependen se elimina.

Por ejemplo, `PostComment`, `PostLike` y `PostRole` son cada uno elementos secundarios de la entidad `Post`.

## <a name="entity-keys"></a>Claves de entidad

Cada definición de clave alternativa describe uno o varios atributos en la combinación que identificará de forma exclusiva una instancia de entidad. Las claves alternativas se aplican normalmente solo para la integración con sistemas externos. Puede definir las claves alternativas para identificar de forma única un registro. Esto es valioso si está integrando datos con un sistema que no admita las claves de identificador único de GUID. Puede definir un solo valor de campo o combinación de valores de campo para identificar una entidad de forma única. Agregar una clave alternativa aplicará una restricción de unicidad en estos atributos. No podrá crear o actualizar otro registro de entidad para tener los mismos valores.

Más información: 
 - [Guía de personalización de Common Data Service para aplicaciones: definir claves alternativas para hacer referencia a registros de CDS for Apps](/dynamics365/customer-engagement/customize/define-alternate-keys-reference-records)
 - [Guía para desarrolladores sobre cómo definir claves alternativas para una entidad: sincronizar los datos de CDS for Apps con sistemas externos](/dynamics365/customer-engagement/developer/synchronize-dynamics-365-data-with-external-systems)

## <a name="entity-states"></a>Estados de entidad

La mayoría de las entidades tienen dos propiedades para realizar un seguimiento del estado de un registro. Estas son `StateCode`, que se denomina **Estado** en aplicaciones basadas en modelos y `StatusCode`, que se denomina **Razón para el estado** en aplicaciones basadas en modelos. 

Los dos atributos contienen un conjunto de opciones que muestran los valores válidos. Los valores de atributo `StateCode` y `StatusCode` están vinculados para que solo determinadas opciones de `StatusCode` sean válidas para un `StateCode` determinado.

Esto puede variar en función de la entidad, pero el modelo común para varias entidades y los valores predeterminados para entidades personalizadas son estos:

|Opciones de StateCode  |Opciones de StatusCode  |
|---------|---------|
|0: Activo|1: Activa|
|1: Inactivo|2: Inactiva|

Algunas entidades tendrán diferentes conjuntos de opciones. 

**Ejemplo**: entidad `PhoneCall` y las opciones `StateCode` y `StatusCode`


|`StateCode`|`StatusCode`|
|---------|---------|
|0: Abierta|1: Abierta|
|1: Finalizada|2: Realizada <br />4: Recibida|
|2: Cancelada|3: Cancelada|

El conjunto de los códigos de estado válidos para una entidad no se puede personalizar, pero los códigos de la razón para el estado sí se pueden personalizar. Puede agregar opciones `StatusCode` adicionales para un `StateCode` correspondiente.

Para las entidades personalizadas, puede definir criterios adicionales para transiciones válidas entre estados. Más información: 
- [Personalizar metadatos de atributos de entidad](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)
- [Definir transiciones de modelo de estado personalizadas](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions).

### <a name="see-also"></a>Vea también

[Entidades de Common Data Service para aplicaciones](entities.md)
