---
title: " Consolidar registros relacionados con un registro específico (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo consolidar registros relacionados con un registro especificado.
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
ms.openlocfilehash: 7756f3b180e57277a6350eca261898ecec264032
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155596"
---
# <a name="rollup-records-related-to-a-specific-record"></a>Consolidar registros relacionados con un registro específico

Este ejemplo muestra cómo resumir oportunidades según la cuenta primaria. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RollupSpecificRecords).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RollupRequest` está diseñado para usarse en un escenario que contiene los datos necesarios para crear una solicitud de consolidación.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

1. Comprobaciones para la versión actual de la organización.
2. Crea ejemplos de registros de cuenta y oportunidad.

### <a name="demonstrate"></a>Demostración

1. La `QueryExpression` consulta las oportunidades por cuenta primaria.
2. El método `RollupRequest` crea la solicitud de consolidación.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
