---
title: 'Diseño de la personalización escalable: transacciones de bases de datos (Common Data Service) | Microsoft Docs'
description: El segundo de una serie de temas. Este tema se centra en el impacto de las transacciones de bases de datos en el diseño de la personalización escalable
ms.custom: ''
ms.date: 1/15/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: rogergilchrist
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="scalable-customization-design-database-transactions"></a>Diseño de la personalización escalable: transacciones de bases de datos

> [!NOTE]
> Este es el segundo de una serie de temas sobre el diseño de la personalización escalable. Para comenzar, consulte [Diseño de la personalización escalable en Common Data Service](overview.md).

Uno de los conceptos fundamentales que encierran muchos de los retos que surgen aquí es el de las transacciones de bases de datos. En Common Data Service, la base de datos está en el centro de casi todas las solicitudes al sistema y es el sitio donde la coherencia de los datos se aplica principalmente.

- Ninguna de las operaciones de Common Data Service para aplicaciones, bien interna o como parte de las personalizaciones de código, funciona totalmente de forma aislada.
- Todas las operaciones de datos de Common Data Service para aplicaciones interactúan con los mismos recursos de base de datos, bien en el nivel de los datos o de la infraestructura como el procesador, la memoria o el uso de E/S.
- Para protegerse frente a los cambios conflictivos, cada solicitud bloquea recursos para poder verse o modificarse.
- Esos bloqueos se efectúan dentro de las transacciones y no se liberan hasta que la transacción se confirma o anula.

## <a name="transaction-and-locking-awareness"></a>Familiarizarse con las transacciones y los bloqueos

Una razón habitual por la que los problemas surgen en esta área está la falta de conocimiento sobre cómo las personalizaciones pueden afectar a las transacciones.

Aunque los detalles de cómo se hace esto están fuera del alcance de este tema, el elemento más sencillo que se debe considerar es cómo Common Data Service interactúa con los datos en su base de datos. SQL Server determina los bloqueos adecuados que se realizarán las transacciones en esos datos como por ejemplo:
- Cuando se recupera un registro en particular, SQL Server requiere un bloqueo de lectura en ese registro.
- Cuando se recupera una variedad de registros, en algunos escenarios se puede aplicar un bloqueo de lectura en ese intervalo de registros o en la tabla completa.
- Cuando se crea un registro, se genera un bloqueo de escritura en ese registro.
- Cuando se actualiza un registro, se aplica un bloqueo de escritura en el registro.
- Cuando un bloqueo se aplica en una tabla o un registro, también se aplicará en los registros de índice correspondientes.

Sin embargo, es posible influir en el alcance y la duración de estos bloqueos. También es posible indicar a SQL Server que no se requiere un bloqueo para determinados escenarios.

Consideremos el bloqueo de la base de datos de SQL Server y la repercusión de las solicitudes independientes que intentan tener acceso a los mismos datos. En el siguiente ejemplo, al crear una cuenta se han configurado una serie de procesos, algunos con complementos que se desencadenan en cuanto se crea el registro y algunos en un flujo de trabajo asincrónico relacionado que se inicia en la creación.
 
El ejemplo muestra las consecuencias cuando un proceso de actualización de cuenta tiene un procesamiento posterior complejo mientras que otra actividad también interactúa con el mismo registro de cuenta. Si se procesa un flujo de trabajo asincrónico mientras que la transacción de la cuenta está aún en curso, este flujo de trabajo podría bloquearse a la espera de obtener un bloqueo de actualización para cambiar el mismo registro de cuenta, que aún está bloqueado.

![ejemplo de bloqueo y transacciones](media/locking-and-transactions-example.png)

Debe tenerse en cuenta que las transacciones solo se retienen mientras dure una solicitud específica para la plataforma. Los bloqueos no se retienen en una sesión de usuario o mientras se muestra la información en la interfaz de usuario. En cuanto la plataforma ha completado la solicitud, libera la conexión de la base de datos, la transacción relacionada y cualquier bloqueo que haya aplicado. 


## <a name="blocking"></a>Bloqueo

Mientras que el tipo de bloqueo del ejemplo anterior puede ser un inconveniente por sí mismo, también puede traer consecuencias más serias so considera que Common Data Service es una plataforma que puede procesar cientos de acciones simultáneas. Mientras que retener un bloqueo en un registro de cuenta individual puede tener implicaciones razonablemente limitadas, ¿qué sucede cuando se disputa un recurso con más intensidad?

Por ejemplo, cuando se proporciona un número de referencia único a cada cuenta puede causar que un solo recurso que esté registrando los números de referencia usados se bloquee por cada proceso de creación de cuenta. Como se describe en el [ejemplo de numeración automática](auto-numbering-example.md), si muchas cuentas que se generan en paralelo, con superposición de solicitudes que necesitan tener acceso a ese recurso de numeración automática, este se bloqueará hasta que completen la acción. Cuanto más dure cada proceso de creación de cuenta y se produzcan más solicitudes simultáneas, más bloqueos habrá.

Mientras que la primera solicitud que logre el bloqueo de recurso de numeración automática se completará fácilmente, la segunda solicitud necesitará esperar a que finalice la primera para poder comprobar cuál es el siguiente número de referencia único. La tercera solicitud tendrá que esperar a que las dos anteriores solicitudes se completen. Cuantas más solicitudes haya, más prolongado será el bloqueo. Si hay suficientes solicitudes, y cada una dura bastante, puede retrasar las solicitudes posteriores hasta tal punto que se agote el tiempo de espera, aunque individualmente se puedan completar correctamente.

![ejemplo de bloqueo](media/blocking.png)

## <a name="lock-release"></a>Liberación del bloqueo

Hay dos razones principales por las que un bloqueo no se libera, sino que se retiene hasta que se complete la transacción:

- El servidor de base de datos retiene el bloqueo por razones de uniformidad en caso de que la transacción haga más adelante otra solicitud para actualizar el elemento de datos.
- El servidor de base de datos también debe tener en cuenta el hecho de que un error o comando de anular puede provocar la reversión de la totalidad de la transacción, por lo que necesita retener los bloqueos mientras dure la transacción para garantizar la coherencia.

Es importante reconocer que aunque el proceso puede haber completado las interacciones con una determinada porción de datos, el bloqueo será retenido hasta completar y confirmar la transacción completa. Cuanto más se prolongue la transacción, más tiempo se retendrá el bloqueo, evitando completar otros subprocesos que interactúan con esos datos. Como se mostrará más adelante, esto también incluye personalizaciones relacionadas que operan dentro de la misma transacción y pueden prolongar de forma notable la duración de transacciones como los flujos de trabajo síncronos.

En el siguiente ejemplo, el bloqueo de escritura en una entidad personalizada en el complemento previo a la creación para una cuenta está bloqueado hasta que toda la lógica ligada a la creación de la cuenta se complete.

![liberación del bloqueo](media/lock-release.png)

## <a name="intermittent-errors-timing"></a>Errores intermitentes: temporización

El comportamiento intermitente es un síntoma obvio de bloqueo en la actividad simultánea. Si la repetición exacta de la misma acción más adelante se realiza correctamente mientras que antes había fallado, muy probablemente el error o la lentitud fueron producidos por algo que sucedió de forma simultánea.

Es importante tener esto en cuenta ya que la depuración un problema normalmente implica dejar la funcionalidad en su nivel más básico. Sin embargo, cuando el problema ocurre solo intermitentemente, es posible que necesite buscar dónde causa el conflicto la acción que falla con otra del sistema y necesita buscar los posibles puntos conflictivos. Puede mitigar el conflicto optimizando un proceso individual; sin embargo, cuanto más rápido sea el procesamiento, menos posibilidades habrá de que la actividad entre en conflicto con otros procesos. 

## <a name="transaction-control"></a>Control de las transacciones

Mientras que en la mayoría de los casos la forma en que se usan las transacciones puede dejarse a la plataforma que lo administre, hay situaciones donde la lógica necesaria es lo suficientemente compleja que resulta necesario entender y gestionar las transacciones para lograr los resultados deseados. Common Data Service ofrece una variedad de enfoques de personalización diferentes que tienen un impacto distinto en la forma en que se usan las transacciones.

Cuando entienda cómo cada tipo de personalización participa en las transacciones de la plataforma, podrá modelar situaciones complejas de forma eficaz en Common Data Service para aplicaciones y predecir su comportamiento.

Como se mencionó anteriormente, una transacción solo se retiene durante la duración de una solicitud a la plataforma, no es algo se mantenga después de completar el paso de la plataforma. De esta manera se evita que un cliente externo retenga las transacciones durante largos periodos de tiempo y se bloquen otras actividades de la plataforma.

El trabajo de la plataforma es mantener la coherencia en la canalización de las transacciones en la plataforma y cuando sea apropiado permitir a las personalizaciones participar en la misma transacción.

## <a name="how-model-driven-apps-use-transactions"></a>Cómo utilizan las transacciones las aplicaciones basadas en modelos

Antes de poder saber cómo las personalizaciones interactúan con la plataforma, resulta útil saber cómo las solicitudes basadas en modelos utilizan las solicitudes a la plataforma, y cómo afecta al uso de las transacciones.

|Operación|Descripción|
|--|--|
|Formularios (Retrieve)|&bull; Aplica un bloqueo de lectura en el registro que se muestra.<br />&bull; Poca repercusión en otros usos.|
|Crear|&bull; Efectúa una solicitud de creación en la plataforma.<br />&bull; Poca repercusión en otras actividades, como nuevo registro sin que nada lo bloquee.<br />&bull; Potencialmente puede bloquear consultas con bloqueo para la totalidad de la tabla hasta que se complete.<br />&bull; A menudo puede desencadenar acciones relacionadas en la personalización, lo que puede tener repercusiones.|
|Update|&bull; Efectúa una solicitud de actualización en la plataforma.<br />&bull; Resulta más probable que tenga conflictos. Un bloqueo de actualización bloqueará cualquier otra cosas que actualice o lea ese registro. También bloquea cualquier cosa que aplique un bloqueo amplio de lectura en la tabla.<br />&bull; A menudo desencadena otras actividades.|
|Ver (RetrieveMultiple)|&bull; Se pensaría que iba a bloquear cantidad de otra actividad.<br />&bull; Pero pasa deliberadamente sugerencias `nolock` a las consultas<br />&bull; Por lo general no bloquea otras actividades.<br />&bull; Aunque una optimización deficiente de la consulta puede afectar al uso de los recursos de la base de datos y probablemente agotar tiempos de espera.|

## <a name="event-pipeline-platform-step"></a>Canalización de eventos: paso de la plataforma

Cuando se inicia una canalización de eventos, una transacción de SQL se crea para incluir el paso de la plataforma. Esto garantiza que toda la actividad de bases de datos realizada por la plataforma ser realiza de forma uniforme. La transacción se crea al inicio de la canalización de eventos y se confirma o anula cuando se complete el procesamiento, dependiendo de si se realiza correctamente. 

![paso de la plataforma en la canalización de eventos](media/event-pipeline-platform-step.png)

## <a name="customization-requests"></a>Solicitudes de personalización

También es posible participar en la transacción iniciada de la plataforma dentro de las personalizaciones. Cada tipo de personalización participa en transacciones de forma diferente. En las siguientes secciones se describirán. 
    
- [Complementos de sincronización (antes o después de la operación: en el contexto de la transacción)](#sync-plug-ins-pre-or-post-operation-in-transaction-context)
- [Complementos de sincronización (antes y después de la operación: en el contexto de la transacción)](#sync-plug-ins-pre-and-post-operation-in-transaction-context)
- [Complementos de sincronización (**PreValidation**: en un contexto externo a la transacción)](#sync-plug-ins-prevalidation-outside-transaction-context)
- [Complementos de sincronización (**PreValidation**: en el contexto de la transacción)](#sync-plug-ins-prevalidation-in-transaction-context)
- [Complementos asincrónicos](#async-plug-ins)
- [Resumen de uso de transacciones del complemento](#plug-in-transaction-use-summary)
- [Flujos de trabajo sincrónicos](#synchronous-workflows)
- [Flujos de trabajo asincrónicos](#asynchronous-workflows)
- [Actividad de flujo de trabajo personalizado](#custom-workflow-activity)
- [Acciones personalizadas](#custom-actions)
- [Solicitudes de servicio web](#web-service-requests)

### <a name="sync-plug-ins-pre-or-post-operation-in-transaction-context"></a>Complementos de sincronización (antes o después de la operación: en el contexto de la transacción)

Cuando los complementos se registran para un evento, se pueden registrados en una etapa **PreOperation** o **PostOperation** que esté dentro de la transacción. Cualquier solicitud de mensajes desde el complemento se realizará dentro de la transacción. Esto significa que la duración de la transacción y los bloqueos aplicados, se ampliarán.

![Complementos de sincronización (antes o después de la operación: en el contexto de la transacción)](media/sync-plug-ins-pre-or-post-operation-in-transaction-context.png)

### <a name="sync-plug-ins-pre-and-post-operation-in-transaction-context"></a>Complementos de sincronización (antes y después de la operación: en el contexto de la transacción)

Los complementos pueden registrarse en las etapas **PreOperation** y **PostOperation**. En este caso la transacción se puede ampliar incluso más porque se prolongará desde el principio del complemento **PreOperation** hasta que el complemento **PostOperation** se complete.

![Complementos de sincronización (antes y después de la operación: en el contexto de la transacción)](media/sync-plug-ins-pre-and-post-operation-in-transaction-context.png)

### <a name="sync-plug-ins-prevalidation-outside-transaction-context"></a>Complementos de sincronización (**PreValidation**: en un contexto externo a la transacción)

Un complemento también se puede registrar para que se aplique fuera de las transacciones de la plataforma si se registrado en la etapa **PreValidation**.

> [!NOTE]
> NO crea su propia transacción. Como resultado, se actúa de forma independiente en cada solicitud de mensaje en el complemento dentro de la base de datos.

![Complementos de sincronización (**PreValidation**: en un contexto externo a la transacción)](media/sync-plug-ins-pre-validation-outside-transaction-context.png)

Este escenario se aplica solo cuando se invoca **PreValidation** como la primera etapa de un evento de la canalización. Aunque el complemento se registra en la etapa **PreValidation**, es posible que participará en una transacción como la siguiente sección describe. No se puede asumir que un complemento **PreValidation** no participa en una transacción, aunque es posible comprobar en el contexto de la ejecución si éste es el caso.

### <a name="sync-plug-ins-prevalidation-in-transaction-context"></a>Complementos de sincronización (**PreValidation**: en el contexto de la transacción)

El escenario relacionado se produce cuando se registra un complemento **PreValidation** pero el evento relacionado de la canalización se activa por la solicitud de mensaje desde una transacción existente. 

Tal como muestra el siguiente diagrama, crear una cuenta puede hacer que un complemento **PreValidation** se desarrolle inicialmente fuera de una transacción cuando se realiza la creación inicial. Si, como parte del complemento posterior, una solicitud de mensaje se realiza para crear una cuenta secundaria relacionada porque esa segunda canalización de eventos se inicia desde dentro de la canalización principal, participará en la misma transacción. 

En este caso, el complemento **PreValidation** detectará que ya existe una transacción y participará en esa transacción aunque se haya registrado en la etapa **PreValidation**. 

![Complementos de sincronización (**PreValidation**: en el contexto de la transacción)](media/sync-plug-ins-pre-validation-in-transaction-context.png)

Como se indicó anteriormente, el complemento puede comprobar el contexto de ejecución para la propiedad <xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction>, que indicará si este complemento se desarrolla en una transacción o no.

### <a name="async-plug-ins"></a>Complementos asincrónicos

Un complemento también se puede registrar para que se desarrolle de forma asincrónica. En este caso, el complemento también actúa fuera de la transacción de plataforma.

> [!NOTE]
> El complemento no crea su propia transacción; se actúa de forma independiente en cada solicitud de mensaje en el complemento.

![foo](media/async-plug-ins.png)


### <a name="plug-in-transaction-use-summary"></a>Resumen de uso de transacciones del complemento

Para resumir:

- Los complementos sincrónicos participan normalmente en las transacciones.
- Los complementos asincrónicos nunca participan en una transacción de plataforma; cada solicitud se realiza de forma independiente.
- Los complementos **PreValidation** no crean una transacción pero participan si ya existe una.

|Evento|Nombre de la fase|La transacción aún no existe|La transacción ya existe|
|--|--|--|--|
|Anterior al evento|**PreValidation**|No se crearon transacciones. No participa en la transacción; cada solicitud usa una transacción independiente para la base de datos|Participa en la transacción existente|
|Anterior al evento|**PreOperation**|Participa en la transacción existente|Participa en la transacción existente|
|Posterior al evento|**PostOperation**|Participa en la transacción existente|Participa en la transacción existente|
|Asincrónico|N/D|No se crearon transacciones. No participa en la transacción; cada solicitud usa una transacción independiente para la base de datos|N/D|

### <a name="synchronous-workflows"></a>Flujos de trabajo sincrónicos

Desde la perspectiva de las transacciones, los flujos de trabajo sincrónicos actúan complementos anteriores y posteriores. Por lo tanto, se desarrollan en la transacción de canalización de la plataforma y pueden tener el mismo efecto en la duración de toda la transacción.

![Flujos de trabajo sincrónicos](media/synchronous-workflows.png)

### <a name="asynchronous-workflows"></a>Flujos de trabajo asincrónicos

Los flujos de trabajo asincrónicos se desencadenan fuera de la transacción de plataforma.

> [!NOTE]
> El flujo de trabajo TAMPOCO crea su propia transacción por tanto se actúa de forma independiente sobre cada solicitud de mensaje en el flujo de trabajo.

En el siguiente diagrama se muestra el flujo de trabajo asincrónico que se desarrolla fuera de la transacción de la plataforma y de cada paso que inicia su propia transacción independiente.

![Flujos de trabajo asincrónicos](media/asynchronous-workflows.png)

### <a name="custom-workflow-activity"></a>Actividad de flujo de trabajo personalizado

Las actividades de flujo de trabajo personalizadas se desarrollan en el contexto principal del flujo de trabajo.

- Flujo de trabajo de la sincronización: actúa dentro de la transacción
- Flujo de trabajo asincrónico: actúa fuera de la transacción

En el siguiente diagrama se muestran las actividades personalizadas que actúan primero en un flujo de trabajo sincrónico y después en un flujo de trabajo asincrónico.

![Actividad de flujo de trabajo personalizado](media/custom-workflow-activity.png)

### <a name="custom-actions"></a>Acciones personalizadas

Las acciones personalizadas pueden crear sus propias transacciones. Esta una característica fundamental. Una acción personalizada puede crear una transacción independiente fuera del paso de la plataforma dependiendo de si está configurada para establecer Habilitar reversión.

- Habilitar reversión establecido
    - Si se invoca a través de solicitud de mensaje desde un complemento que se ejecuta dentro de la transacción, y está establecido Habilitar reversión, la acción personalizada se desarrollará en la transacción existente.
    - La acción personalizada creará de lo contrario una nueva transacción y se ejecutará dentro de ella.
- Habilitar reversión no establecido
    - La acción personalizada no se desarrollará en una transacción.

![acciones personalizadas](media/custom-actions.png)

### <a name="web-service-requests"></a>Solicitudes de servicio web

Cuando las solicitudes se realizan de forma externa a través de servicios web, se crea una canalización y la gestión de la transacción se desarrolla dentro de la canalización como se indicó anteriormente, pero una transacción no se mantendrá después de devolver la respuesta. Dado que se desconoce el tiempo que puede transcurrir hasta la solicitud siguiente, la plataforma no permite bloquear recursos que bloquearían otras actividades.

Cuando se realizan múltiples solicitudes en un complemento con el mismo contexto de ejecución, el contexto de ejecución común es el que mantiene la referencia de la transacción y garantiza con complementos sincrónicos que cada solicitud se realiza dentro de la misma transacción. La capacidad de mantener un contexto de ejecución en las solicitudes no está disponible fuera de los complementos, por lo que una transacción no se puede mantener a través de solicitudes independientes realizadas de forma externa.

Hay dos mensajes especiales donde se pueden pasar múltiples acciones a la plataforma de Common Data Service como parte de una sola solicitud de servicio web.

|Mensaje|Descripción|
|--|--|
|`ExecuteMultiple`|Esto permite que múltiples acciones independientes se pasen dentro de la misma solicitud de servicio web. Cada una de estas solicitudes se realiza de forma independiente dentro de la plataforma, por tanto, no hay contextos de transacción retenidos entre las solicitudes.|
|`ExecuteTransaction`|Esto permite procesar diversas acciones dentro de la misma transacción de base de datos, de forma similar a las múltiples solicitudes de mensaje realizadas desde un complemento de forma sincrónica.<br /> <br />Esta capacidad también tendrá implicaciones similares a la realización de múltiples solicitudes de mensaje, es decir, si cada acción se prolonga durante mucho tiempo (por ejemplo realizando consultas costosas o desencadenando una cadena extensa de complementos o flujos de trabajo sincrónicos relacionados), podría provoca problemas de bloqueo a un nivel más general de la plataforma.|

#### <a name="web-api-odata-requests-in-plug-ins"></a>Solicitudes de API web (OData) en complementos

No use las solicitudes de API web (OData) dentro de un complemento a la misma organización que el complemento. Use siempre los métodos <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Esto hace posible que el contexto de la transacción se pase para que la operación pueda participar en la transacción de la canalización.

## <a name="next-steps"></a>Pasos siguientes

Además de las transacciones de base de datos, es importante apreciar el impacto que múltiples operaciones de datos simultáneas pueden tener en el sistema. Más información: [Diseño de la personalización escalable: problemas de simultaneidad](concurrency-issues.md)


