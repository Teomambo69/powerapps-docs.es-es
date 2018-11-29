---
title: <Topic Title> (Common Data Service para aplicaciones) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="asynchronous-service"></a>Servicio asincrónico

El servicio asincrónico ejecuta operaciones a largo plazo independientemente del funcionamiento del núcleo de Common Data Service para aplicaciones principal. Esto permite un rendimiento general del sistema y una escalabilidad mejorados. El servicio asincrónico representa una cola primero en entrar, primero en salir (FIFO) administrada, para la ejecución de complementos registrados asincrónicos, de flujos de trabajo y operaciones como correo masivo, importación masiva y propagación de actividad de la campaña. Estas operaciones se registran con el servicio asincrónico y se ejecutan periódicamente cuando el servicio procesa la cola.


Después de que se produzca un evento y se hayan procesado todas las extensiones síncronas, la plataforma serializa el contexto de todas las extensiones asincrónicas y lo guarda en la base de datos como **trabajo del sistema** en [Entidad de AsyncOperation](reference/entities/asyncoperation.md). El trabajo del sistema define y sigue la ejecución de operaciones asincrónicas. A medida que se puede disponer de los recursos, los trabajos del sistema se procesan y las operaciones que definen se ejecutan. Cualquier operación de datos definida en la extensión se procesará de nuevo por la canalización de ejecución de eventos, pero este vez como operación sincrónica.

## <a name="execution-order-and-dependencies"></a>Orden y dependencias de ejecución

Los trabajos del sistema se evalúan como cola mediante la fecha [CreatedOn](reference/entities/asyncoperation.md#BKMK_CreatedOn). Si no hay condiciones para diferir la ejecución se ejecutarán en cuanto los recursos estén disponibles. No está garantizado que la ejecución se realice en el orden establecido por la fecha `CreatedOn`, ya que diferentes tipos de operaciones requieren diferentes recursos.

Un trabajo del sistema puede depender de otro trabajo del sistema, por lo que comenzará solo después de que el otro trabajo del sistema se complete. Esta dependencia está establecida por el valor de atributo [DependencyToken](reference/entities/asyncoperation.md#BKMK_DependencyToken). Se establecen las dependencias cuando se crea un trabajo del sistema. Si el valor `DependencyToken` es nulo, el trabajo del sistema no tiene ninguna dependencia. Los trabajos del sistema dependientes tendrán el mismo valor de `DependencyToken` y se ejecutarán en el orden en que se crearon. Si se pospone un trabajo del sistema, todos los trabajos del sistema dependientes posteriores continuarán esperando hasta que el trabajo pospuesto del sistema se ejecute.

> [!NOTE]
> Este sistema de dependencia no se puede usar por complementos registrados para ejecutarse de forma asincrónica porque los trabajos del sistema para ellos son creados por el sistema.

## <a name="managing-system-jobs"></a>Administración de trabajos del sistema

Puede realizar las operaciones siguientes para administrar trabajos del sistema mediante la [Entidad AsyncOperation](reference/entities/asyncoperation.md).

- Recuperar trabajos del sistema
- Eliminar trabajos del sistema
- Administrar estados de trabajos del sistema
- Posponer trabajos del sistema

> [!NOTE]
> Crear trabajos del sistema con código no se admite. Aunque la entidad `AsyncOperation` admita varios atributos grabables y cree operaciones, solo los siguientes atributos son compatibles con la actualización:
> - [Código de estado](reference/entities/asyncoperation.md#BKMK_StateCode)
> - [Código de estado](reference/entities/asyncoperation.md#BKMK_StatusCode)
> - [PostPoneUntil](reference/entities/asyncoperation.md#BKMK_PostponeUntil)



## <a name="retrieve-system-jobs"></a>Recuperar trabajos del sistema

Puede ver tareas del sistema en la aplicación navegando a **Configuración** > **Sistema** > **Trabajos del sistema** y también puede buscarlas usando la Búsqueda avanzada.

Usando código, puede recuperar trabajos del sistema como cualquier otra entidad. La siguiente tabla muestra una lista de los atributos seleccionados que son importantes para comprender los trabajos del sistema:

|**Atributo**|**Descripción**|
|--|--|
|`AsyncOperationId`|Identificador único del trabajo del sistema.|
|`CompletedOn`|Fecha y hora en que se completó el trabajo del sistema.|
|`CreatedBy`|Identificador único del usuario que creó el trabajo del sistema.|
|`CreatedOn`|Fecha y hora en que se creó el trabajo del sistema.|
|`Data`|Datos sin estructurar asociados al trabajo del sistema.|
|`DependencyToken`|La ejecución de todas las operaciones con el mismo símbolo (token) de dependencia está serializada. Más información: [Orden y dependencias de ejecución](#execution-order-and-dependencies) |
|`Depth`|Número de llamadas de SDK realizadas desde la primera llamada.|
|`ErrorCode`|Código de error devuelto de un trabajo del sistema cancelado.|
|`ExecutionTimeSpan`|Tiempo que tardó el trabajo del sistema en ejecutarse.|
|`FriendlyMessage`|Mensaje proporcionado por el trabajo del sistema.|
|`IsWaitingForEvent`|Indica que el trabajo del sistema está esperando un evento.|
|`Message`|Mensaje relacionado con el trabajo del sistema.|
|`MessageName`|Nombre del mensaje que inició este trabajo del sistema.|
|`ModifiedBy`|Identificador único del usuario que modificó el trabajo del sistema por última vez.|
|`ModifiedOn`|Fecha y hora en que se modificó el trabajo del sistema por última vez.|
|`Name`|Nombre del trabajo del sistema.|
|`OperationType`|Tipo del trabajo del sistema. Más información: [Tipos de operación](#operation-types)|
|`OwnerId`|Identificador único del usuario o equipo propietario del trabajo del sistema.|
|`OwningBusinessUnit`|Identificador único de la unidad de negocio propietaria del trabajo del sistema.|
|`OwningExtensionId`|Identificador único de la extensión propietaria a la que está asociado el trabajo del sistema.|
|`OwningTeam`|Identificador único del equipo propietario del registro.|
|`OwningUser`|Identificador único del usuario propietario del registro.|
|`PostponeUntil`|Indica si el trabajo del sistema solo debería ejecutarse después de la fecha y la hora especificadas. Más información: [Posponer trabajos del sistema](#postpone-system-jobs)|
|`PrimaryEntityType`|Tipo de entidad a la que está asociado el trabajo del sistema en primer lugar.|
|`RecurrencePattern`|Patrón de la periodicidad del trabajo del sistema. Más información: [Horas de inicio y patrones de la periodicidad](#recurrence-start-times-and-patterns)|
|`RecurrenceStartTime`|Hora de inicio en UTC del patrón de la periodicidad. Más información: [Horas de inicio y patrones de la periodicidad](#recurrence-start-times-and-patterns)|
|`RegardingObjectId`|Identificador único del objeto al que está asociado el trabajo del sistema.|
|`RetryCount`|Número de veces para reintentar el trabajo del sistema.|
|`Sequence` |Orden en el que se enviaron las operaciones.|
|`StartedOn`|Fecha y hora en que se inició el trabajo del sistema.|
|`StateCode`|Estado del trabajo del sistema. Más información: [Administrar estados de trabajos del sistema](#manage-system-job-states)|
|`StatusCode`|Razón para el estado del trabajo del sistema. Más información: [Administrar estados de trabajos del sistema](#manage-system-job-states)|
|`UTCConversionTimeZoneCode` |Código de la zona horaria que estaba en uso cuando se creó el registro.|
|`WorkflowStageName` |Nombre de una fase del flujo de trabajo. |

### <a name="examples"></a>Ejemplos

Puede usar los siguientes ejemplos para recuperar datos de trabajo del sistema

#### <a name="web-api"></a>API web

Use la siguiente consulta de la API web para recuperar los atributos de la tabla anterior. Para obtener más información, consulte [Consultar datos mediante la API web](webapi/query-data-web-api.md)

```
<organization URL>/api/data/v9.0/asyncoperations?
$select=
asyncoperationid,
completedon,
createdon,
data,
dependencytoken,
depth,
errorcode,
executiontimespan,
friendlymessage,
iswaitingforevent,
message,
messagename,
modifiedon,
name,
operationtype,
_ownerid_value,
postponeuntil,
primaryentitytype,
recurrencepattern,
recurrencestarttime,
_regardingobjectid_value,
retrycount,
sequence,
startedon,
statecode,
utcconversiontimezonecode,
workflowstagename
&$expand=
createdby($select=fullname),
modifiedby($select=fullname),
owningbusinessunit($select=name),
owningextensionid($select=name),
owningteam($select=name),
owninguser($select=fullname)

```

> [!NOTE]
> Con la API web hay una propiedad de un solo valor de navegación para cada entidad que admite los trabajos del sistema. El nombre de esta propiedad de navegación sigue el patrón `regardingobjectid_<entity logical name>`.

#### <a name="fetchxml"></a>FetchXML

Use la siguiente consulta FetchXML para recuperar los atributos de la tabla anterior. Más información: [Usar FetchXML para crear una consulta](use-fetchxml-construct-query.md)

```xml
<fetch>
  <entity name="asyncoperation" >
    <attribute name="asyncoperationid" />
    <attribute name="completedon" />
    <attribute name="createdby" />
    <attribute name="createdon" />
    <attribute name="data" />
    <attribute name="dependencytoken" />
    <attribute name="depth" />
    <attribute name="errorcode" />
    <attribute name="executiontimespan" />
    <attribute name="friendlymessage" />
    <attribute name="iswaitingforevent" />
    <attribute name="message" />
    <attribute name="messagename" />
    <attribute name="modifiedby" />
    <attribute name="modifiedon" />
    <attribute name="name" />
    <attribute name="operationtype" />
    <attribute name="ownerid" />
    <attribute name="owningbusinessunit" />
    <attribute name="owningextensionid" />
    <attribute name="owningteam" />
    <attribute name="owninguser" />
    <attribute name="postponeuntil" />
    <attribute name="primaryentitytype" />
    <attribute name="recurrencepattern" />
    <attribute name="recurrencestarttime" />
    <attribute name="regardingobjectid" />
    <attribute name="retrycount" />
    <attribute name="sequence" />
    <attribute name="startedon" />
    <attribute name="statecode" />
    <attribute name="utcconversiontimezonecode" />
    <attribute name="workflowstagename" />
  </entity>
</fetch>
```

> [!NOTE]
> Cada entidad que admite trabajos del sistema tiene una relación de varios a uno mencionada con la entidad `AsyncOperation` mediante el atributo de búsqueda `RegardingObjectId`. El nombre de esta relación sigue el patrón `<entity schema name>_AsyncOperations`.

### <a name="operation-types"></a>Tipos de operación

El atributo [OperationType](reference/entities/asyncoperation.md#BKMK_OperationType) describe categorías de trabajos del sistema. La plataforma inicia muchos de estos tipos para realizar tareas de mantenimiento. 

> [!NOTE]
> No puede realizar operaciones de cancelación, pausa, o reanudación en trabajos del sistema generados por la plataforma. 

Algunos de los tipos de estos trabajos generados por la plataforma se incluyen en la tabla siguiente:

|**Valor de OperationType**|**Etiqueta de OperationType**|
|--|--|
|9|Recolección de datos SQM|
|16|Recopilar estadísticas de la organización|
|18|Calcular tamaño de almacenamiento de la organización|
|19|Recopilar estadísticas de la base de datos de la organización|
|20|Recopilar estadísticas del tamaño de la organización|
|22 |Calcular tamaño de almacenamiento máximo de la organización|
|24|Actualizar intervalos de estadísticas|
|25 |Índice del catálogo de texto completo de la organización|
|27|Actualizar estados de contrato|
|31|Notificador de límite de almacenamiento|

### <a name="recurrence-start-times-and-patterns"></a>Horas de inicio y patrones de la periodicidad

Los trabajos del sistema periódicos requieren la información sobre cuándo deberían empezar y con qué frecuencia se repetirán. Estos valores se almacenan en los atributos `RecurrenceStartTime` y `RecurrencePattern` de la entidad `AsyncOperation`.

Puesto que no creará entidades `AsyncOperation` directamente con código, solo necesitará interpretar estos valores si consulta los datos. Establecerá solo estas propiedades indirectamente usando los mensajes que crearán nuevos trabajos del sistema. Los mensajes `BulkDelete` y `BulkDeleteDuplicates` incluyen ambos los parámetros o las propiedades de las Acciones API web o las clases de solicitud de servicio de la organización. Más información: clase <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest>, clase <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" />, clase <xref:Microsoft.Crm.Sdk.Messages.BulkDeleteRequest> y <xref href="Microsoft.Dynamics.CRM.BulkDelete?text=BulkDelete Action" />.

`RecurrenceStartTime` es simplemente un valor de fecha y hora para indicar cuándo el trabajo del sistema debe iniciarse. Si no se configura, se espera que el trabajo del sistema se inicie inmediatamente.

El atributo `RecurrencePattern` almacena información sobre con qué frecuencia se espera que se produzcan los trabajos del sistema. Este valor se puede establecer con la plataforma cuando se crea una nueva entidad de asyncoperation. Puede configurar esta opción para cambiar el patrón.

Los valores de este atributo usan partes de [Estándar de Internet RFC2445 (Internet Calendaring and Scheduling Core Object Specification)](http://www.rfc-editor.org/info/rfc2445).

La tabla siguiente proporciona algunos ejemplos:

|Patrón de periodicidad|Frecuencia de ejecución del trabajo|
|--|--|
|`FREQ=MONTHLY;`|Una vez al mes|
|`FREQ=WEEKLY;`|Una vez a la semana|
|`FREQ=DAILY;`|Una vez al día|
|`FREQ=DAILY;INTERVAL=3;`|Cada tres días|
|`FREQ=HOURLY;`|Una vez a la hora|

Si un valor `INTERVAL` no se configura, se interpreta como `1`.

## <a name="delete-system-jobs"></a>Eliminar trabajos del sistema

Puede eliminar trabajos del sistema en la aplicación o en código igual que cualquier otra entidad si tiene los privilegios necesarios para hacerlo.

> [!NOTE]
> Al registrar complementos asincrónicos, hay una opción de eliminar automáticamente operaciones de éxito. Se recomienda que la use. Más información: [Escribir un complemento](write-plug-in.md)

La práctica normal es crear un trabajo de eliminación en masa periódico que elimine los trabajos con éxito. Más información [Eliminar una cantidad grande de datos específicos con la eliminación en masa](/dynamics365/customer-engagement/admin/delete-bulk-records)

## <a name="manage-system-job-states"></a>Administrar estados de trabajos del sistema

El estado del trabajo del sistema cambiará varias veces hasta completar la operación. A continuación se describen las opciones `StateCode` y `StatusCode` que representan los valores disponibles de Estado y Razón para el estado:

|Valor de StateCode|Etiqueta de StateCode|Valor de StatusCode|Etiqueta de StatusCode|
|--|--|--|--|
|`0`|Preparada|`0`|Esperando recursos|
|`1`|Suspendida|`10`|En espera|
|`2`|Bloqueado|`20`|En curso|
|`2`|Bloqueado|`21`|Pausando|
|`2`|Bloqueado|`22`|Cancelando|
|`3`|Finalizado|`30`|Correcto|
|`3`|Finalizado|`31`|Error|
|`3`|Finalizado|`32`|Cancelado|

Puede cambiar el estado de los trabajos del sistema en la aplicación navegando a **Configuración** > **Sistema** > **Trabajos del sistema** con los comandos disponibles en el menú **Más acciones**.

![Comandos de acción disponibles para los trabajos del sistema en la aplicación](media/system-jobs-more-actions-commands.png)

> [!NOTE]
> Las acciones que puede realizar mediante esta interfaz de usuario también se pueden realizar con código. No puede realizar operaciones de cancelación, pausa, o reanudación en trabajos del sistema generados por la plataforma. Más información: [Tipos de operación](#operation-types)

Junto con las opciones de administrar las vistas, las siguientes opciones de administración de trabajos del sistema están disponibles: 

|Opción|Descripción|
|--|--|
|Eliminar|Uso del ![comando eliminar](../../maker/common-data-service/media/delete.gif) comando.<br />Elimina un trabajo del sistema|
|Eliminación en masa|Uso del menú **Más acciones**.<br />Abre el asistente para definir condiciones y crear un nuevo trabajo del sistema de eliminación en masa para eliminar los trabajos del sistema coincidentes.|
|Cancelar|Uso del menú **Más acciones**.<br />Cancela el trabajo del sistema.|
|Reanudar|Uso del menú **Más acciones**.<br />Reanuda un trabajo del sistema en pausa.|
|Posponer|Uso del menú **Más acciones**.<br />Reprograma un trabajo del sistema|
|Pausa|Uso del menú **Más acciones**.<br />Pausa un trabajo del sistema.|

Si la operación solicitada se producirá depende del estado del trabajo del sistema. Por ejemplo, no puede pausar un trabajo que ya se ha completado o no ha comenzado aún. La siguiente tabla describe las condiciones para cada cambio y qué se producirá cuando se seleccionen.

|Opción|Valores StateCode válidos|Cambiar|
|--|--|--|
|Eliminar|cualquiera|Se elimina el trabajo del sistema|
|Cancelar|0 (Preparado) <br /> 1 (Suspendido) <br /> 2 (Bloqueado)|`StateCode` ha cambiado a 3 (completado) y `StatusCode` ha cambiado a 32 (cancelado)|
|Reanudar|1 (Suspendido)|StateCode cambió a 0 (listo)|
|Posponer|0 (Preparado) <br />2 (Bloqueado)|El diálogo Posponer trabajo solicita al usuario un valor datetime para posponer el trabajo del sistema. Más información: [Posponer trabajos del sistema](#postpone-system-jobs)|
|Pausa|2 (Bloqueado)|StateCode cambió a 1 (suspendido)|


## <a name="postpone-system-jobs"></a>Posponer trabajos del sistema

El atributo `PostPoneUntil` contiene un valor datetime cuando el trabajo del sistema cambiará el estado de 1 (suspendido) a 0 (listo). Junto con los atributos `StateCode` y `StatusCode`, son los únicos atributos compatibles con la actualización cuando se usa la entidad `AsyncOperation`.

### <a name="see-also"></a>Vea también

[Escribir un complemento](write-plug-in.md)<br />
[Escriba complementos para ampliar los procesos de negocio](plug-ins.md) <br />

