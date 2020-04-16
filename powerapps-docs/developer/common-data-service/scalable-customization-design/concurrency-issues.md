---
title: 'Diseño de la personalización escalable: problemas de simultaneidad (Common Data Service) | Microsoft Docs'
description: 'El tercero de una serie de temas. '
ms.custom: ''
ms.date: 1/15/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 971e847a511ab253a97ca1c5543e144a72275a79
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155312"
---
# <a name="scalable-customization-design-concurrency-issues"></a>Diseño de personalización escalable: problemas de simultaneidad

> [!NOTE]
> Este es el tercero de una serie de temas sobre el diseño de la personalización escalable. Para comenzar, consulte [Diseño de la personalización escalable en Common Data Service](overview.md).
> El tema anterior [Diseño de personalización escalable: transacciones de bases de datos](database-transactions.md) describe cómo se aplican las transacciones de base de datos y el efecto que tienen en los diversos tipos de personalizaciones.

Cuando tiene solicitudes simultáneas, la posibilidad de colisiones en los bloqueos se incrementa. Cuanto más dure la transacción, más tiempo se mantendrán los bloqueos. Las probabilidades de colisión aumentan incluso más y el impacto total sería mayor en los usuarios finales. 

También debe conocer las diversas formas en que se puede realizar una actividad en la aplicación, y cada una de ellas hace bloqueos que podrían producir conflictos con otras acciones dentro del sistema. En estos casos, el bloqueo impide que se produzcan incoherencias de datos al superponer acciones aparece en los mismos datos. 

Algunos ámbitos fundamentales para los que considerar el diseño, y comprobarlo si surgen problemas, son:

![superponer solicitudes](media/concurrency-considerations.png)

- **Actividad controlada por el usuario**: directamente a través de la interfaz de usuario.
- **Acciones asincrónicas**: actividad que se produce posteriormente como resultado de otras acciones. Cuando esta actividad se vaya a procesar no se conocerá en el momento en se desencadena la acción de inicio.
- **Actividades por lotes**: controlado bien desde Common Data Service (como los trabajos de eliminación de forma masiva o el procesamiento de sincronización en el servidor) o bien por orígenes externos como la integración desde otro sistema.

## <a name="async-operations-in-parallel"></a>Operaciones asincrónicas en paralelo

Un error común es que los flujos de trabajo o los complementos asincrónicos se procesan en serie desde una cola y no debería haber conflictos entre ellos. Esto no es preciso, ya que Common Data Service procesa múltiples actividades asincrónicas en paralelo tanto en cada instancia de servicio asíncrono, como a través de las instancias de servicio difundidas por los diferentes servidores para aumentar el rendimiento. Cada servicio asincrónico recupera realmente trabajos que se van a realizar por lotes de aproximadamente 20 por servicio, en función de la configuración y la carga.

Si inicia múltiples actividades asincrónicas desde el mismo evento en el mismo registro, seguramente se procesarán en paralelo. Cuando se activan en el mismo registro, un modelo común se actualiza al mismo registro primario; por lo tanto, hay muchas posibilidades de conflicto. 

Cuando se desencadena un evento, como la creación de una cuenta, la lógica asincrónica de Common Data Service podría crear entradas en la [Entidad AsyncOperation (trabajo del sistema)](../reference/entities/asyncoperation.md) para cada proceso o acción que se emprenda. El servicio asincrónico controla esta tabla, selecciona solicitudes de esperada por lotes y, después, los procesa. Debido a que los flujos de trabajo se desencadenan a la vez, existen muchas probabilidades de que se seleccionen en el mismo lote y se procesarán a la vez. 

## <a name="why-its-important-to-understand-transactions"></a>Por qué es importante entender las transacciones

El [ejemplo de numeración automática](auto-numbering-example.md) proporciona una situación que muestra cómo las transacciones de base de datos y los problemas de simultaneidad necesitan considerarse al diseñar personalizaciones escalables.

## <a name="serialization-and-timeouts"></a>Serialización y tiempos de espera

Un alto nivel de serialización es lo que por lo general hace que los bloqueos se conviertan en tiempos de espera y un rendimiento deficiente. Cuando tiene muchas solicitudes simultáneas, una vez que se serializan y les lleva mucho tiempo procesarse, cada solicitud se prolongará más y más hasta que empieza a agotar tiempos de espera y, por tanto, a experimentar errores. 

El tiempo de espera del complemento empieza con cuando se inicia. Un tiempo de espera de SQL se calcula en la solicitud de la base de datos, por lo que si una consulta se bloquea esperando durante mucho tiempo, puede agotarse el tiempo de espera.

![Serialización y tiempos de espera](media/serialization-and-timeouts.png)

## <a name="chain-of-actions"></a>Cadena de acciones

Además de entender las consultas de específica a actividades directamente desencadenadas, también es necesario considerar donde puede ocurrir una cadena de eventos relacionados.
 
Cada solicitud de mensaje que se realiza en un complemento o como un paso en un flujo de trabajo sincrónico no solo activa la acción directo, sino que también puede hacer que se activen otros complementos y flujos de trabajo sincrónicos. Cada una de estas actividades asincrónicas se producirá en la misma transacción, incrementando la duración de esa transacción y los bloqueos retenidos probablemente mucho más tiempo de lo que puedan realizarse.

![cadena de acciones](media/chain-of-actions.png)

El efecto total puede ser mucho más grande del logrado inicialmente. Esto puede ocurrir a menudo involuntariamente en casos en los que varias personas estén creando la implementación, o se desarrolla a lo largo del tiempo. 

## <a name="running-into-platform-constraints"></a>Encontrar restricciones de la plataforma

Es donde las restricciones de la plataforma pueden ocurrir. Y en realidad este tipo de comportamiento existe para proteger a la totalidad del sistema de este tipo de comportamiento.

Siempre que se dé este nivel de retraso en el procesamiento, tendrá consecuencias involuntarias en otras áreas del sistema y en otros usuarios. Es por tanto importante evitar que este tipo de actividad interfiera con el rendimiento del sistema.

Mientras que la forma fácil de evitar errores podría ser reducir las restricciones de plataforma, no se estaría abordando la consecuencia más relevante en la escalabilidad y el rendimiento globales del sistema. Esto debe solucionarse corrigiendo problemas y evitando el comportamiento que desencadena las restricciones en primer lugar. 

## <a name="impact-on-usage"></a>Repercusión en el uso

Lo que suele también tener un impacto en el uso es una serie en cascada de implicaciones de este comportamiento.

![repercusión en el uso](media/impact-on-usage.png)

El problema inicial son los bloqueos que afectan al sistema. Esto hace que los tiempos de respuesta de usuario sean más lentos, lo que se amplifica en forma de tiempos de respuesta del usuario impredecibles y no fiables, a menudo en un área específica del sistema.

En casos extremos o con cargas más pesadas que de costumbre, esto puede darse en cualquier procesamiento por lotes de fondo con un rendimiento deficiente. Finalmente, puede convertirse en errores que se producen en el sistema.

Es común que cuando se investigan los errores de tiempo de espera de SQL, los usuarios también comuniquen tiempos de respuesta deficientes e impredecibles, y no es estableció una conexión que relacionara ambos problemas. 


## <a name="next-steps"></a>Pasos siguientes

Comprenda los patrones de diseño que puede aplicar (o evitar) para minimizar los problemas de rendimiento. Más información: [Diseño de personalización escalable: Patrones de diseño de transacciones](transaction-design-patterns.md)