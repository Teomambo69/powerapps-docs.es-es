---
title: 'Diseño de la personalización escalable: ejemplo de numeración automática (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo es necesario tener en cuenta las transacciones y las configuración en una personalización de código.
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
# <a name="scalable-customization-design-auto-numbering-example"></a>Diseño de la personalización escalable: ejemplo de numeración automática

> [!NOTE]
> Este ejemplo describe una serie de temas sobre diseño de la personalización escalable. Para comenzar, consulte [Diseño de la personalización escalable en Common Data Service para aplicaciones](overview.md).

Un escenario que muestra el error de comunicación habitual de cómo se administran las transacciones en CDS para aplicaciones es la implementación de un esquema de numeración automática.

En este escenario el requisito se normalmente:

- Genere un número único siguiendo un modelo determinado.
- Permita muchas solicitudes simultáneas para crear el tipo relacionado de registros; por ejemplo, cuentas que necesiten una única referencia.
- Permita una numeración secuencial de los números únicos.
- Asegúrese de que la generación de números sea sistemática, pero escalable, y que no provoque errores en situaciones de carga. También debe asegurarse de que no se generen números duplicados.
- Genere el número en la creación del registro pertinente.

El método típico implica las siguientes variaciones:

- Almacenar el último número utilizado en un almacén de datos de indexado automático de números; por ejemplo, una entidad personalizada con una fila por tipo de datos.
- Recupere el último número usado e incremente ese número.
- Registre el nuevo número para el registro recién generado.
- Vuelva a almacenar el nuevo número como el último número utilizado en el almacén de indexado automático de números.

En las siguientes secciones se describen diferentes métodos que se pueden utilizar en CDS para aplicaciones y se resaltan las implicaciones, mostrando la importancia y las ventajas de entender la forma en que se usan las transacciones. 

## <a name="approach-1-out-of-a-transaction"></a>Método 1: Fuera de una transacción

El enfoque más sencillo es identificar que cualquier uso de un recurso necesario habitualmente introduciría una posible interrupción. Dado que tiene una repercusión en la escalabilidad, es posible que quiera evitar una transacción de plataforma a la hora de generar un número automático.
Consideremos el escenario de generación de numeración automáticamente fuera de transacciones de canalización en un complemento antes de la validación.

![Método 1: Fuera de una transacción](media/autonumber-approach-1.png)

Cuando se ejecuta de forma aislada funciona correctamente. Sin embargo, no protege realmente frente a errores de simultaneidad. Como muestra el siguiente diagrama, si dos solicitudes en paralelo solicitan el número más reciente y después ambas incrementan y actualizan el valor terminará con números duplicados. Puesto que no hay bloqueos para el número recuperado, es posible que se produzca una condición race y que ambos subprocesos acaben tiendo el mismo valor. 

![condición race](media/autonumber-approach-1-a.png)

En muchos casos, aunque se produzcan muchas solicitudes, debido al margen de superposición limitado, esto podría funcionar bien, pero se trataría de suerte en lugar de un buen diseño para evitar duplicados.

## <a name="approach-2-in-a-plug-in-transaction"></a>Método 2: Dentro de una transacción de complementos

Si ejecuta la numeración automática desde un complemento registrado en la transacción (txn), tiene que funcionar... ¿no es así?

![Método 2: Dentro de una transacción de complementos](media/autonumber-approach-2.png)

En una situación igual a la de superponer solicitudes para intentar generar números a la vez, sería posible otorgar a ambas un bloqueo de lectura compartida en la tabla de numeración automática. Lamentablemente, en el momento que la aplicación intenta actualizar esto a un bloqueo exclusivo, no será posible porque habrá otro bloqueo de lectura compartida que lo evita.

![el bloqueo de lectura compartida evita el acceso](media/autonumber-approach-2-a.png)

En función de cómo se generan las consultas, el comportamiento exacto puede variar, pero confiar en esas condiciones y no estar seguro de los resultados donde la exclusividad es esencial, no es lo idóneo. Incluso si esto no genera un error, la capacidad compartida de lectura podría permitir que se genere un número duplicado si los modos de aislamiento no son correctos. Como muestra el siguiente diagrama, los dos registros terminan con el mismo valor numérico generado automáticamente de 8.

![ambos registros terminan con el mismo valor numérico generado automáticamente](media/autonumber-approach-2-b.png)

## <a name="approach-3-pre-lock-in-a-plug-in-transaction"></a>Método 3: Bloqueo previo en una transacción de complementos

Entender la forma en que funcionan las transacciones implica poder generar una forma segura de hacerlo. 

En este método, desde el principio de la transacción, se realiza una actualización del marcador en el registro de numeración automática a algún campo determinado (por ejemplo, UpdateInProgress), que se utiliza simplemente con el fin de mantener la coherencia. Eso se hace escribiendo una actualización que indica que hay una actualización a punto de iniciarse. Este proceso posteriormente solicita y adopta un bloqueo de escritura exclusivo en esa fila en la tabla de numeración automática, de forma que bloquea a otros procesos de iniciar el método de numeración automática. 

A su vez, esto le permite aumentar y volver a escribir de forma segura la numeración automática actualizada sin que puedan interferir otros procesos. 

![Método 3: Bloqueo previo en una transacción de complementos](media/autonumber-approach-3.png)

Todo ello implica serializar no solo las actualizaciones de numeración automática, sino también las solicitudes de creación de cuenta, ya que ambos pasos se producen en la misma transacción de plataforma. Si la creación de cuentas es rápida, puede ser perfectamente un método válido y garantiza que la creación de la cuenta y la numeración automática se ejecutan de forma sistemática; si se produce un error en uno de los procesos, ambos fallarán y se revertirán.
 
De hecho, en los casos donde otras acciones en la transacción son rápidas, es el método más uniforme y más eficaz para implementar la numeración automática en las personalizaciones. 

Si sin embargo, también especifica otros complementos o flujos de trabajo síncronos y cada uno de ellos tarde más tiempo en completarse, la serialización puede convertirse en un verdadero problema de escalabilidad, ya que el proceso de numeración automática además de bloquearse a sí misma, también bloquea la espera para la finalización de otras actividades. 

![el proceso de numeración automática no solo se bloquea a sí mismo, sino que también bloquea la espera para que finalicen otras actividades](media/autonumber-approach-3-a.png)

Normalmente, la generación de la numeración automática se realizará en un complemento anterior al evento. Debe incluir el número en los parámetros de entrada para el paso de creación y evitar una segunda actualización en el procesamiento posterior para registrar el número que se generó automáticamente en la cuenta.

Teniendo en cuenta las consecuencias de la escalabilidad, si hay otros procesamientos complejos en el proceso de creación de la cuenta, una alternativa sería trasladar la generación automática de números a un proceso posterior a la creación, que siga garantizando un proceso uniforme de actualización. La ventaja sería que reduce el tiempo dentro de la transacción durante el que se retiene el bloqueo de registro de numeración automática ya que el bloque se pasa al final del proceso. Si la tabla de numeración automática es el recurso más discutido y este método se adopta para todos los procesos que acceden a ella, esto reduce la cantidad de contención total.

El equilibrio aquí es la necesidad de realizar una actualización adicional en la cuenta, a la vez que se reduce el tiempo total de bloqueo a la espera del registro de numeración automática.

![trasladar la generación automática de números a un proceso posterior a la creación](media/autonumber-approach-3-b.png)
