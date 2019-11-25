---
title: 'Ejemplo: Trabajar con soluciones (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo trabajar con soluciones.
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
ms.openlocfilehash: 6c696da27bf309dc4fe0db53e29564fc50289172
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749844"
---
# <a name="sample-work-with-solutions"></a>Ejemplo: trabajar con soluciones

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-work-solutions -->

Este ejemplo muestra cómo cómo realizar las siguientes acciones con soluciones:

- Crear un editor.
- Recuperar el editor predeterminado.
- Crear una solución.
- Recuperar una solución.
- Agregar un componente de la solución existente.
- Quitar un componente de la solución.
- Exportar o empaquetar una solución.
- Instalar o actualizar una solución.
- Eliminar una solución.

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/WorkwithSolutions).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo trabajar con soluciones. Este ejemplo cubre cómo crear un editor, crear una solución, exportar e importar la solución y también cómo eliminar la solución.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Publisher` define un nuevo editor. 
1. El método `Solution` crea una nueva solución.
1. El método `OptionSetMetadata` agrega un componente de la solución.
1. El método `ExportSolutionRequest` exporta la solución creada en [Configuración](#setup).
1. El método `DeleteSolutionRequest` elimina la solución y los componentes.


### <a name="demonstrate"></a>Demostración
1. El método `querySDKSamplePublisher` comprueba si el editor está ya en el sistema.
1. El método `querySampleSolutionResults` comprueba si la solución está ya en el sistema.
1. El método `ExportSolutionRequest` exporta la solución. 
1. El método `ImportSolutionRequest` importa la solución.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar todos los datos creados en el ejemplo.

La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.
