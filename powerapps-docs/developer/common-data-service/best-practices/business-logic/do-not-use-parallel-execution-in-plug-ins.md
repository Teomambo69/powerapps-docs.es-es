---
title: No utilizar ejecución en paralelo en complementos y actividades de flujo de trabajo | MicrosoftDocs
description: No se admite el subprocesamiento múltiple o paralelo en complementos o actividades de flujo de trabajo personalizadas.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: ryjones
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/14/2019
ms.author: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8478d5f4a71eee57651ef21b8e324e4299f972fe
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749732"
---
# <a name="do-not-use-parallel-execution-within-plug-ins-and-workflow-activities"></a>No utilizar ejecución en paralelo en complementos y actividades de flujo de trabajo

**Categoría**: Diseño, rendimiento, seguridad, compatibilidad

**Potencial de impacto**: alto

<a name='symptoms'></a>

## <a name="symptoms"></a>Síntomas

El subprocesamiento múltiple o las llamadas en paralelo en complementos o actividades de flujo de trabajo personalizadas pueden producir daños en esas conexiones.  Por ejemplo, ejecutar subprocesamiento en paralelo puede registrar excepciones como:

`Generic SQL error.`
`The transaction active in this session has been committed or aborted by another session.`

Además, objetos seguros sin procesamiento como elementos del [Espacio de nombres System.Collections](/dotnet/api/system.collections) pueden quedar dañados por los subprocesos paralelos.

<a name='guidance'></a>

## <a name="guidance"></a>Instrucciones

El servicio de espacio aislado se ha diseñado para ejecutar llamadas en un orden determinado como parte de una transacción.  No se admite el desarrollo de complementos o actividades de flujo de trabajo personalizados para realizar llamadas subprocesamiento múltiple o paralelo.  Desarrolle los complementos y actividades de flujo de trabajo personalizadas sabiendo que las llamadas se realizarán de forma secuencial y pueden requerir reversión.

> [!NOTE]
> El uso de la ejecución paralela desde un programa cliente es una práctica admitida para optimizar el rendimiento según sea necesario. Esta instrucciones son específicas del código escrito para ejecutarse en un flujo de trabajo o una actividad de flujo de trabajo personalizada.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Patrones problemáticos

Los complementos y las actividades de flujo de trabajo personalizadas se ejecutan en una sola transacción y varios subprocesos introducidos por la ejecución paralela pueden afectar negativamente a la transacción. Los siguientes son ejemplos de patrones y prácticas que no deberían utilizarse en complementos y actividades de flujo de trabajo personalizadas:

- Uso de [patrón asincrónico basado en tareas (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)
- Uso de [Biblioteca paralela de tareas (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)
- Uso de [subprocesamiento administrado](/dotnet/standard/threading/index)


<a name='additional'></a>

## <a name="additional-information"></a>Información adicional

Usar y actualizar objetos de contexto de canalización compartidos puede hacer que estos objetos contengan resultados inesperados o queden dañados. El efecto de esto sería un error en el complemento o la actividad de flujo de trabajo personalizada. 

<a name='seealso'></a>

### <a name="see-also"></a>Vea también

[Procesamiento en paralelo, simultaneidad, y programación asincrónica en .NET](/dotnet/standard/parallel-processing-and-concurrency)<br />