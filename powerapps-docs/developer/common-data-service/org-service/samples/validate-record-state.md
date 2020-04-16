---
title: " Validar y establecer el estado del registro (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo validar un cambio de estado de una entidad y establecer el estado.
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7dc4321cba939a0882e753cdd7741d923b7b2ae4
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155504"
---
# <a name="validate-record-state-and-set-the-state-of-record"></a>Validar el estado del registro y establecer el estado del registro

Este ejemplo muestra cómo validar un cambio de estado de una entidad y establecer el estado de una entidad. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateandExecuteSavedQuery).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IsValidStateTransitionRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para validar la transición de estado.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea cualquier registro de entidad que requiere este ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `EntityReference` crea una EntityReference para representar un caso abierto. 
2. El método `IsValidStateTransitionRequest` establece la solicitud de transición a un caso abierto.
3. La propiedad `checkState.NewState` verifica si un nuevo estado de resuelto y un nuevo estado de problema resuelto son válidos.
4. El método `IsValidStateTransitionResponse` ejecuta la solicitud.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

