---
title: 'Ejemplo: Detectar dependencias de solución (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo detectar las dependencias de las soluciones.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7e960b1a593f0c3d940f3a43ab2e369f459d3648
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956207"
---
# <a name="sample-detect-solution-dependencies"></a>Ejemplo: detectar las dependencias de solución

Este ejemplo muestra cómo detectar dependencias antes de eliminar un componente de la solución.

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `RetrieveDependentComponentsRequest` y `RetrieveDependenciesForDeleteRequest` se proporcionan para se pueden usar en un escenario donde se contienen datos para detectar dependencias de solución. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SolutionDependencies).

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Publisher` crea al editor de ejemplo que tendrá la `own` de las dos soluciones.
1. El método `Solution` crea la solución principal.
1. `OptionSetMetadata` crea el conjunto de opciones global y lo asocia a la solución.
1. `ExportSolutionRequest` exportac la solución como administrada para poder importarla más adelante.
1. `DeleteOptionSetRequest` elimina el conjunto de opciones creado anteriormente, para que pueda importarse con la solución administrada.
1. `ImportSolutionRequest` reimporta la solución como administrada.

### <a name="demonstrate"></a>Demostración

1. `QueryByAttribute` consulta todos los componentes de la solución para obtener una solución.
1. `RetrieveDependentComponentsRequest` recupera todas las dependencias para el componente. Si no hay dependencias puede omitir este componente. Si hay dependencias sobre este componente de la solución, y la misma solución se administra, no podrá eliminar la solución.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar las soluciones creadas en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
