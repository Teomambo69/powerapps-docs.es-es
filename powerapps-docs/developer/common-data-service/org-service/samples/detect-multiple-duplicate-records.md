---
title: 'Ejemplo: Detectar varios registros duplicados (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo detectar y registrar varios registros duplicados para un tipo de entidad especificado.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 2efe8b44f2ea8cbe943466441df75dcb876a3bb3
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934344"
---
# <a name="sample-detect-multiple-duplicate-records"></a>Ejemplo: detectar varios registros duplicados

Este ejemplo muestra cómo detectar y registrar varios registros duplicados para un tipo de entidad especificado.

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `BulkDetectDuplicatesRequest` está diseñado para usarse en un escenario en el que contiene los datos necesarios para enviar un trabajo asincrónico del sistema que detecta y registra varios registros duplicados. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DetectMultipleDuplicateRecords).

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. La clase `CreateRequiredRecords` crea algunos registros de entidad duplicados de ejemplo.
1. El método `DuplicateRule` crea una regla de detección de duplicados.
1. El método `DuplicateRuleCondition` crea una condición de regla de detección de duplicados para detectar registros duplicados.
1. El método `PublishDuplicateRuleRequest` publica la regla de detección de duplicados.
1. `PublishDuplicateRuleRequest` vuelve antes de que la publicación finalice, por lo que conservamos el estado del trabajo asincrónico hasta que está `Completed`.

### <a name="demonstrate"></a>Demostración

El método `BulkDetectDuplicatesRequest` crea el objeto BulkDetectDuplicatesRequest.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

