---
title: 'Diseño de la personalización escalable: Patrones de diseño de transacciones de bases de datos (Common Data Service para aplicaciones) | Microsoft Docs'
description: 'El cuarto de una serie de temas. '
ms.custom: ''
ms.date: 11/18/2018
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
# <a name="scalable-customization-design-transaction-design-patterns"></a>Diseño de la personalización escalable: Patrones de diseño de transacciones

> [!NOTE]
> Este es el cuarto de una serie de temas sobre el diseño de la personalización escalable. Para comenzar, consulte [Diseño de la personalización escalable en Common Data Service para aplicaciones](overview.md).

Esta sección describe los patrones de diseño a evitar o minimizar y sus implicaciones. Cada patrón de diseño debe considerarse en el contexto del problema empresarial que se va a solucionar y puede resultar útil como opciones a investigar.

## <a name="dont-avoid-locking"></a>No evitar el bloqueo

El bloqueo es un componente muy importante de SQL Server y de CDS para aplicaciones, y es esencial para el funcionamiento adecuado y la coherencia del sistema. Por este motivo es importante comprender las implicaciones en el diseño, sobre todo a escala.

## <a name="transaction-usage-nolock-hint"></a>Use de transacciones: Sugerencia Nolock

Una funcionalidad de CDS para aplicaciones que utilizan mucho las vistas es la capacidad de especificar que una consulta pueda realizarse con una sugerencia Nolock, que indica a la base de datos de que no se necesita un bloqueo para esta consulta. 

Las vistas usan este método porque no hay un vínculo directo entre la acción de iniciar la vista y las acciones posteriores. Otras actividades puede producirlas bien ese usuario u otros y no es práctico ni ventajoso bloquear la tabla completa de datos que muestra la vista mientras hasta que el usuario prosiga. 

Como las consultas en un conjunto de datos grande potencialmente puede afectar a otros que intentan interactuar con cualquiera de esos datos, el poder especificar que no es necesario ningún bloqueo puede suponer una ventaja importante para la escalabilidad del sistema. 

Cuando realiza una consulta de la plataforma mediante el SDK, puede ser útil especificar que se puede usar Nolock. Indica que reconoce que esta consulta no necesita aplicar un bloqueo de lectura en la base de datos. Es especialmente útil para consultas donde:

- Hay un ámbito amplio de datos
- Se consultan recursos muy disputados
- La serialización no es importante

No se debe usar Nolock si una acción posterior depende de que no se cambien los resultados, como en el ejemplo de bloqueo de numeración automática anterior. 

Un escenario de ejemplo que puede resultar útil es determinar si un correo electrónico está relacionado con un caso existente. Bloquear a otros usuarios de crear nuevos casos para asegurarse que no existe ninguna posibilidad de que se genere un caso al que el correo electrónico pudiera vincularse, no será un grado práctico de control de la coherencia. 

En su lugar, es más apropiado invertir esfuerzos razonables para consultar casos relacionados y para adjuntar el correo electrónico a un caso existente o crear un nuevo, mientras sigue permitiendo que se generen otros casos. En particular, dado que no hay un vínculo inherente en la temporización entre estas dos acciones, el correo electrónico podría haber llegado fácilmente unos segundos ante y no se habría detectado ningún vínculo. 

Si las sugerencias Nolock fuesen válidas para un escenario particular se basarían normalmente en la posibilidad y el impacto de los conflictos que surjan y la implicación en el negocio de no garantizar la coherencia en las acciones, entre la acción de recuperar y las subsecuentes. Si no hay repercusiones en el negocio por evitar los bloques, usar Nolock sería una forma muy útil de optimización. Si existe un impacto potencial empresarial, el resultado de esto puede afectar las ventajas para el rendimiento y escalabilidad que ofrece evitar los bloqueos. 

## <a name="consider-order-of-locks"></a>Tener en cuenta el orden de los bloqueos

Otro método que puede resultar útil al reducir el impacto del bloqueo y, en particular, al evitar las paradas, es adoptar un enfoque uniforme a la hora de ordenar los bloqueos en una implementación. 

Un ejemplo sencillo y común es el actualizar o interactuar con los grupos de usuarios. Si tiene solicitudes que actualicen los usuarios relacionados (como agregar integrantes a los equipos o a actualizar todos los participantes en una actividad), no especificar un orden hacer si dos actividades simultáneas intentan actualizar los mismos usuarios, puede provocar el siguiente comportamiento, que da como resultado una parada: 

- La transacción A intenta actualizar al Usuario X y al Usuario Y
- La transacción B intenta actualizar al Usuario Y y al Usuario X

Dado que ambas solicitudes se inician juntas, la Transacción A puede obtener un bloqueo en el Usuario X y la Transacción B puede obtener un bloqueo en el Usuario B, pero en cuanto cada uno de ellos intente obtener un bloqueo en el usuario, se bloquean y después se paran. 

![Ejemplo de problema: parada de transacciones](media/order-of-locks-example-1.png)

Solo con ordenar los recursos a los que tiene acceso de una manera uniforme podrá evitar muchas situaciones de parada. El mecanismo de la acción de ordenar no suele ser importante siembre que sea uniforme y tan eficaz como sea posible. Por ejemplo, ordenar a los usuarios por nombre o incluso por el GUID podría al menos garantizar un nivel de uniformidad que evite las paradas.

En un escenario donde se use este método, la Transacción A obtendría el Usuario X, pero la Transacción B también intentaría obtener el Usuario X antas que al Usuario Y. Mientras que esto significa la Transacción B se bloque hasta que se complete la Transacción A, este escenario evita una parada y se realiza con total corrección.

![Evitar paradas ordenando los recursos de una manera uniforme](media/order-of-locks-example-2.png)

En situaciones más complejas y eficaces, es posible que bloquee antes a usuarios al los que normalmente se haga menos referencia primero y a los que más se hace referencia en último lugar, lo que lleva a siguiente patrón de diseño.

## <a name="hold-contentious-locks-for-shortest-period"></a>Mantener bloqueos polémicos durante menos tiempo

Hay situaciones, como el método de numeración automática, donde no cabe duda de que hay un recurso muy polémico que tiene que ser bloqueado. En este caso, el problema de bloqueo no se puede evitar en su totalidad, pero puede ser minimizado.

Cuando tenga recursos muy polémicos, un buen diseño no es incluir la interacción con ese recurso en el punto funcionalmente lógico en el proceso, pero transferir la interacción con él lo más cerca posible del final de la transacción. 

Con este método, aunque aún haya algún bloqueo en este recurso, reduce la cantidad de tiempo durante el que está bloqueado el recurso, por lo que reduce la posibilidad y el tiempo de bloqueo de otras solicitudes mientras se espera por el recurso. 

![Mantener bloqueos polémicos durante menos tiempo](media/hold-contentious-locks-for-shortest-period.png)

## <a name="reduce-length-of-transactions"></a>Reducir la longitud de las transacciones

De forma similar, un bloqueo se convierte en un problema de bloque si dos procesos necesitan tener acceso al mismo recurso a la vez. Cuanto más breve sea la transacción que mantiene un bloqueo, menos probabilidades habrá de que dos procesos, incluso si tiene acceso al mismo recurso, lo necesiten al mismo tiempo y provoquen una colisión. Cuanto menos tiempo se retengan las transacciones, menos probable será que el bloqueo sea un problema.

En el ejemplo siguiente, se aplican los mismos bloqueos pero otros procesos en la transacción indican que la longitud total de la transacción se amplía, lo que conlleva solicitudes superpuestas para los mismos recursos. Esto significa que el bloqueo se produce y cada solicitud es más lenta en su globalidad.

![Ejemplo de problema: bloqueo porque la transacción se prolonga demasiado](media/reduce-length-of-transactions.png)

Al acortar la duración total de la transacción, la primera transacción se completa y libera sus bloqueos antes de que comience la segunda solicitud, lo que significa que no hay bloqueo y ambas transacciones se completan eficazmente. 

Otras actividades dentro de una solicitud que amplíen la duración de una transacción pueden aumentar la posibilidad de bloqueo, sobre todo si hay muchas solicitudes superpuestas y puede producir ralentizar mucho el sistema. 

![Menos bloqueos porque la duración de las transacciones se reduce](media/reduce-length-of-transactions-1.png)

Existen varias formas que de reducir la duración de las transacciones.

## <a name="optimize-requests"></a>Optimizar solicitudes

Cada transacción se compone de una serie de solicitudes de base de datos. Si cada solicitud se a hace tan eficazmente como sea posible, esta reduce la duración total de una transacción y reduce la posibilidad de colisión.

Revise cada consulta realizada para determinar si:

- La consulta solo pide lo que necesita, por ejemplo, columnas, registros o tipos de entidad.
  - Esto maximiza la oportunidad de que un índice se pueda usar para mantener eficazmente la consulta.
  - Reduce el número de tablas y recursos a las que se necesita tener acceso, reduciendo la sobrecarga en otros recursos en el servidor de base de datos y reduciendo la duración de la consulta.
  - Evita el bloqueo potencial de los recursos que no necesita, sobre todo donde se solicita una combinación con otra tabla, pero se puede evitar o no es necesario.
- Hay un índice implementado para ayudar a la consulta, está realizando consultas de forma eficaz y se está realizando una búsqueda de índice más que un análisis.

  Vale la pena tener en cuenta que incluir un índice no evita que se bloquee la creación o actualización de registros en la tabla subyacente. Las entradas en los índices también se bloquean cuando se actualiza el registro relacionado ya que el mismo índice está sujeto a cambio. La existencia de índices no evita este problema completamente.

En el siguiente ejemplo, la recuperación de casos relacionados no está optimizada y hace que la duración sea mayor, ocasionando bloqueos entre los subprocesos.

![La recuperación de casos relacionados no está optimizada](media/optimize-requests-1.png)

Al optimizar la consulta, se emplea menos tiempo en realizarla y la posibilidad de la colisión es más baja, por tanto, se reducirán los bloqueos.

![La recuperación de casos relacionados está optimizada](media/optimize-requests-2.png)

Asegurarse de que el servidor de base de datos puede procesar su consulta de la forma más eficaz posible puede reducir mucho el tiempo total de sus transacciones y reducir los bloqueos potenciales.

## <a name="reduce-chain-of-events"></a>Reducir la cadena de eventos

Como se muestra en ejemplos anteriores, las consecuencias de tener cadenas largas de eventos relacionados puede tener un impacto importante en el tiempo total de transacciones y ,por tanto, aparecen las posibilidades de bloqueo. Este es sobre todo así cuando se desencadenan complementos y flujos de trabajo sincrónicos, que a su vez desencadenan otras acciones, que después desencadenan otros complementos y flujos de trabajo sincrónicos.

Revisar y diseñar una implementación con cuidado para evitar cadenas de eventos largas que se producen de forma sincrónica puede ser beneficioso a la hora de reducir la duración total de una transacción. Esto permite liberar los bloqueos aplicados con mayor rapidez y reducir los posibles bloqueos. 

También se reduce la posibilidad de que bloqueos secundarios se conviertan en un problema importante. En el ejemplo de numeración automática en la creación de la cuenta, el problema principal inicialmente es el acceso a la tabla de numeración automática, pero cuando se efectúan diferentes acciones en una secuencia, es posible que se surja un bloqueo secundario, como actualizaciones de un registro de usuario relacionado. Cuando entran en juego múltiple recursos polémicos, evitar bloqueos es aún más difícil. 

Establecer si algunas actividades deben ser sincrónicas o asincrónicas puede indicar que las mismas actividades se logran pero tienen menor impacto inicial. En particular, para las acciones más prolongadas o aquellas que dependen en gran medida de recursos polémicos, separarlas para la transacción principal ejecutándolas en una acción asincrónica puede tener beneficios importantes. Este método no funcionará si la acción necesita completarse o fracasar en el paso más general de la plataforma, como actualizar un informe de crimen de la policía con el siguiente valor de numeración automática asegurando que se mantiene un esquema de numeración continua y secuencial. En estos escenarios, se deben emplear otros métodos para minimizar el impacto. 

Tal como muestra el siguiente ejemplo, simplemente sacando algunas acciones del proceso asincrónico, lo que significa que las acciones se realizan fuera de las transacciones de plataforma, puede significar que la duración de la transacción será más breve y aumenta la posibilidad de procesos simultáneos.

![Sacar algunas acciones de los procesos asincrónicos acorta la transacción](media/reduce-chain-of-events.png)

## <a name="avoid-multiple-updates-to-the-same-record"></a>Evitar diversas actualizaciones en el mismo registro

Pese a que diseñar varios niveles de actividad funcional es una buena práctica para analizar las acciones necesarias para los flujos de actividad lógicos y de fácil seguimiento, en muchos casos esto conduciría a muchas actualizaciones independientes el mismo registro.
 
En la administración de casos, primero se activa la actualización de un caso con un propietario predeterminado en función del cliente y después tener un proceso independiente para enviar automáticamente comunicaciones a ese cliente y actualizar la última fecha de contacto para el caso es una acción perfectamente lógica para hacer funcionalmente. 

La dificultad, sin embargo, es que esto significa que hay varias solicitudes a CDS para aplicaciones para actualizar el mismo registro, que tiene varias implicaciones:

- Cada petición es una actualización independiente de la plataforma, lo que aumenta la carga total al servidor de CDS para aplicaciones y la duración total de la transacción, lo que aumenta la posibilidad de bloqueo.
- También significa que el registro de casos se bloqueará en la primera acción realizada en ese caso, lo que indica que el bloqueo está retenido en el resto de la transacción. Si acceden al caso múltiples procesos en paralelo de varios registros, esto podría bloquear otras actividades. 

La consolidación de actualizaciones en el mismo registro para un solo paso de actualización, y después en la transacción, puede ser muy ventajoso para la escalabilidad total, sobre todo si el registro es muy polémico o muchas personas obtienen acceso a él rápidamente tras la creación, por ejemplo, como con un caso.

Decidir si consolidar actualizaciones en el mismo registro para un solo proceso estaría basado en el equilibrar la complejidad de la implementación con respecto a las posibilidades de conflicto que podrían traer consigo las actualizaciones independientes. Pero para sistemas de gran volumen, esto puede ser muy ventajoso para recursos muy polémicos. 

## <a name="only-update-things-you-need-to"></a>Actualizar solo lo que se necesita

Pese a que sea importante no reducir las ventajas de un sistema de CDS para aplicaciones excluyendo actividades que pueden ser beneficiosas, a menudo se efectúan solicitudes para incluir personalizaciones que agregan muy poco valor empresarial pero entrañan una gran complejidad técnica.
 
Si cada vez que se crea una tarea también se actualiza el registro de usuario con el número de tareas que han asignado, esto podría presentar un nivel secundario de bloqueo ya que el registro del usuario ahora estría muy disputado. Agregaría otro recurso que cada solicitud tendría que bloquear o por el que esperar, pese a que no fuera fundamental para la acción. En este ejemplo, considere detenidamente si almacenar el recuento de tareas con respecto al usuario es importante o si el recuento se puede calcular a petición o almacenarse en otra parte como usando las funcionalidades de jerarquía y campo consolidado para CDS para aplicaciones de forma nativa. 

![Ejemplo de problema que ilustra las actualizaciones que no son necesarias](media/only-update-things-you-need-to.png)

Como se mostrará más tarde, actualizar registros de usuario del sistema puede tener consecuencias negativas desde una perspectiva de la escalabilidad. 

## <a name="multiple-customizations-triggered-on-same-event"></a>Múltiples personalizaciones aplicadas al mismo evento

Desencadenar múltiples acciones en el mismo evento puede provocar una mayor oportunidad de colisión ya que por la naturaleza de las solicitudes esas acciones tienen posibilidad de interactuar con los mismos objetos relacionados o el objeto primario.

![Múltiples personalizaciones aplicadas al mismo evento](media/multiple-triggers-on-same-event.png)

Es un patrón que debe ser considerado detenidamente o evitado ya que es muy fácil pasar por alto conflictos, sobre todo si diferentes personas implementan procesos diferentes.

## <a name="when-to-use-different-types-of-customization"></a>Cuándo usar los diferentes tipos de personalización

Cada tipo de personalización tiene distintas implicaciones en el uso. En la siguiente tabla resalta algunos patrones comunes, cuándo se debe considerar y usar cada uno y cuándo el uso no es apropiado.

Un interacción entre diferentes comportamientos necesita a menudo considerarse para que ver algunas de las características y escenarios comunes a tener en cuenta, pero cada escenario necesario ser evaluado y elegir el método correcto en función de todos los factores relevantes.

|Fase previa y posterior|Sincrónico y asincrónico|Tipo de personalización|Cuándo usar|Cuándo no usar|
|--|--|--|--|--|
|Validación previa|Sincrónico|Complemento|Validación a corto plazo de los valores de entrada|Acciones de ejecución prolongada.<br /><br />Cuando se crean elementos relacionados que se deben revertirse si los pasos posteriores no se realizan correctamente.|
|Operación previa|Sincrónico|Flujo de trabajo/Complemento|Validación a corto plazo de los valores de entrada.<br /><br />Cuando se crean elementos relacionados que se deben revertirse como parte de un error en el paso de la plataforma.|Acciones de ejecución prolongada.<br /><br />Cuando se crea un elemento y el GUID resultante deberá ser almacenado según el elemento que creará o actualizará el paso de la plataforma.|
|Operación posterior |Sincrónico|Flujo de trabajo/Complemento|Acciones corta ejecución que sigan naturalmente el paso de la plataforma y necesiten revertirse si se producen errores en los pasos posteriores, por ejemplo, la creación de una tarea para el propietario de una cuenta recién creada.<br /><br />Creación de los elementos relacionados que necesita el GUID del elemento creado y que deben revertir el paso de la plataforma en caso de error.|Acciones de ejecución prolongada.<br /><br />Si el error no debería afectar a la terminación del paso de la canalización de la plataforma.|
|No en la canalización de eventos|Asincrónico|Flujo de trabajo/Complemento|Acciones de duración media de podrían tener una repercusión en la experiencia de usuario.<br /><br />Acciones que no se pueden revertir de ninguna forma en de error.<br /><br />Acciones que no deberían forzar la reversión del paso de la plataforma en caso de error.|Acciones de ejecución muy prolongada.<br /><br />No se deben administrar en CDS para aplicaciones.<br /><br />Acciones de coste muy bajo. La sobrecarga de generar el comportamiento de asincrónico para acciones de coste muy bajo puede ser prohibitiva; en lo posible realícelas de forma sincrónica y evite la sobrecarga de un procesamiento asincrónico.|
|N/D<br />Toma el contexto de la ubicación desde donde se invoca||Acciones personalizadas|Combinaciones de acciones iniciadas desde un origen externo, por ejemplo, en un recurso web|Cuando se desencadene siempre en respuesta a un evento de la plataforma, use el complemento/flujo de trabajo en esos casos.|

## <a name="plug-insworkflows-arent-batch-processing-mechanisms"></a>Los complementos y los flujos de trabajo no son mecanismos de procesamiento por lotes

Las acciones muy duraderas o de gran volumen no están dirigidas a ejecutarse desde complementos o flujos de trabajo. CDS para aplicaciones no está diseñada para ser una plataforma de cálculo y en particular no está diseñada especialmente como el controlador para generar grandes grupos de actualizaciones no relacionadas.

Si tiene necesidad de hacer eso, descárguelo y ejecútelo desde un servicio independiente, como un rol de trabajador de Azure. 

## <a name="setting-up-security"></a>Configuración de la seguridad

Un área muy común de ampliación es la escalabilidad de configurar la seguridad. Se trata de una operación costosa, por lo que cuando se hace con respecto al volumen puede producir siempre dificultadas si no se entiende y considera con atención. 

### <a name="team-setup"></a>Configuración del equipo

- Agregue siempre usuarios en el mismo orden: evitar paradas
- Solo actualice usuarios si necesitan actualizarse: evitar invalidad la memoria caché de usuarios innecesariamente

### <a name="owner-v-access-teams"></a>Propietario frente a obtener acceso a equipos

- Si los equipos de los usuarios cambian periódicamente, tenga cuidado con el uso de los equipos de propietario; cada vez que se cambian invalidan la memoria caché del usuario en el servidor web
- Lo idóneo es realizar cambios cuando no funciona el usuario, reducir el impacto, por ejemplo durante la noche

### <a name="lots-of-team-memberships-bus"></a>Gran cantidad de pertenencia a los equipos/Unidades de negocio

- Considere detenidamente los escenarios con muchos equipos/unidades de negocio que incrementan la complejidad de cálculo

### <a name="cascading-behavior"></a>Comportamiento en cascada

- Considere el uso compartido en cascada, por ejemplo, la asignación

### <a name="careful-updating--of-user-records"></a>Actualización pormenorizada de los registros de usuario

- No actualice periódicamente los registros de usuario del sistema a menos que algo fundamental haya cambiado ya que esto obliga a la memoria caché del usuario a recargarse y los privilegios de seguridad se vuelven a calcular, una actividad que consume muchos recursos
- No use el usuario del sistema para registrar el número de actividades abiertas que tiene el usuario, por ejemplo

## <a name="diagram-related-actions"></a>Diagrama de las acciones relacionadas

Una actividad que es muy beneficiosa como medida preventiva, así como herramienta para diagnosticar problemas de bloqueo, es hacer un diagrama de las acciones relacionados desencadenadas en la plataforma de CDS para aplicaciones. Al hacerlo ayuda a resaltar las dependencias intencionales e involuntarias y se desencadena en el sistema. Si no puede hacerlo para su solución, puede que no tenga una clara imagen de lo cómo funciona la implementación realmente. Crear un diagrama así puede poner de manifiesto consecuencias involuntarias y es una buena práctica en cualquier momento en una implementación. 

El siguiente ejemplo resalta cómo en un principio dos procesos funcionaban a la perfección juntos, pero con el mantenimiento continuado se agrega un nuevo paso para crear una tarea que puede provocar un bucle involuntario. El uso de esta técnica de documentación puede resaltar esto en la fase de diseño y evitar que el sistema se vea afectado.

![Diagrama de las acciones relacionadas](media/diagram-related-actions.png)

<!-- NOTE: Excluding content on isolation modes and transaction diagnosis as it is for on-premises only. -->

## <a name="review-system-captured-statistics"></a>Revisar las estadísticas capturadas sistema

Existen varias formas de determinar lo que ocurre si el problema ocurre fuera del nivel de la base de datos. Lo primero es el análisis del rendimiento de los complementos. La [entidad PluginTypeStatistic](../reference/entities/plugintypestatistic.md) puede invocarse para dar una indicación de la frecuencia con la que se ejecuta el complemento y las estadísticas sobre cuánto tiempo tarda normalmente en ejecutarse.

Cuando determinados errores aparecen, usar los archivos de seguimiento del servidor para comprender dónde pueden darse los problemas relacionados en la plataforma también puede ser útil. Más información: [Usar seguimiento](../debug-plug-in.md#use-tracing)

## <a name="summary"></a>Resumen

El contenido en [Diseño de la personalización escalable en Common Data Service para aplicaciones](overview.md) y los temas posteriores [Transacciones de base de datos](database-transactions.md), [Problemas de simultaneidad](concurrency-issues.md) y este mismo ha descrito los conceptos siguientes con los ejemplos y estrategias que le ayudarán a entender cómo diseñar e implementar de las personalizaciones escalables para CDS para aplicaciones.

Algunos conceptos clave para recordar incluyen lo siguiente: 

### <a name="locks-transactions"></a>Bloqueos/transacciones

- Los bloqueos y las transacciones son esenciales para un sistema en buen estado
- Pero cuando se usan de forma incorrecta, puede acarrear problemas

### <a name="platform-constraints"></a>Restricciones de la plataforma

- Las restricciones de la plataforma se manifiestan por lo general en forma de error
- Pero en raras ocasiones es la restricción la causa del problema
- Están ahí para proteger la plataforma y otras actividades de sufrir las consecuencias

### <a name="design-for-transaction-use"></a>Diseño para el uso de transacciones

- Si las implementaciones se diseñen con el comportamiento de las transacciones en mente, esto puede traducirse en una escalabilidad mucho mayor y un rendimiento mejorado del usuario
