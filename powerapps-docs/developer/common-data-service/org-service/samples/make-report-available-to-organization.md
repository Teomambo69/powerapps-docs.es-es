---
title: 'Ejemplo: hacer que un informe esté disponible o no disponible para la organización (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo hacer que un informe esté disponible o no disponible para una organización.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 7c248c4393bd2872b3fba32977b47ebd32b15c17
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155728"
---
# <a name="make-a-report-available-or-unavailable-to-organization"></a>Hacer que un informe esté disponible o no disponible para la organización

Este ejemplo muestra cómo hacer que un informe esté disponible o no disponible para una organización. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/MakeReportAvailableToOrganization).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito anteriormente, el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea cualquier registro de entidad que requiere este ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `service.Retrieve` recupera un informe personal existente.
2. Establezca el parámetro `IsPersonal` en False.
3. El método `service.Update` pone el informe a disposición de la organización.
4. Establezca el parámetro `IsPersonal` como verdadero. Esto hace que el informe no esté disponible para la organización.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
