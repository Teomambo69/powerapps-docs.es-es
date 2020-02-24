---
title: 'Ejemplo: operaciones de flujo de trabajo (Common Data Service) | MicrosoftDocs'
description: Este ejemplo muestra cómo realizar una serie de operaciones de flujo de trabajo, como crear, eliminar, activar, establecer estado y más.
ms.custom: ''
ms.date: 1/14/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 051e08f11afaf9a291f28d8229311cf667e1db56
ms.sourcegitcommit: 1c4ab1859febccf79a835bd2f168e7e12a953a18
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "2957659"
---
# <a name="sample-workflow-operations"></a>Ejemplo: Operaciones de flujo de trabajo

Este ejemplo muestra cómo realizar una serie de operaciones de flujo de trabajo, como crear, eliminar, activar, establecer estado y más.

Descargue el ejemplo: [Flujos de trabajo](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Workflow)

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

Consulte [Cómo ejecutar ejemplos](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) para obtener información general sobre cómo ejecutar este ejemplo.

Observe que hay cinco ejemplos separados, cada una en su propio archivo C#, en el [proyecto](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Workflow/Workflow) de la solución. Para ejecutar cada ejemplo, configúrelo como el objeto de inicio en las propiedades del proyecto antes de ejecutar el ejemplo.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Las operaciones demostradas por estos ejemplos son las siguientes:

- Crear un flujo de trabajo síncrono (en tiempo real) o asíncrono
- Eliminar un flujo de trabajo
- Ejecutar un flujo de trabajo
- Activar o desactivar un flujo de trabajo
- Establecer u obtener el estado de un flujo de trabajo
- Crear un flujo de trabajo a partir de una plantilla

Puede ver los flujos de trabajo creados en **Configuración > Procesos** (en Centro de procesos) cuando visualiza su organización utilizando un navegador web.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Cada ejemplo crea las instancias de entidad que requiera el código de demostración. Esto se realiza en el método `CreateRequiredRecords()`.

### <a name="demonstrate"></a>Demostración

El código de demostración principal para cada muestra se encuentra en la región `Demonstrate` del método `Main()` en cada archivo de clase.

### <a name="clean-up"></a>Limpiar

El método `DeleteRequiredRecords()` muestra una opción en la ventana de la consola para eliminar los registros creados por los ejemplos.

La eliminación es opcional en caso de que desee examinar las entidades de entidad (registros) creados por el ejemplo o ejemplos. Por lo general, no respondería a la solicitud de eliminación en la ventana de la consola hasta después de ver los nuevos registros de la organización en su navegador. Puede eliminar manualmente los registros creados en cualquier momento después de que finalice el programa para lograr el mismo resultado.
