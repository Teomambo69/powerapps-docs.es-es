---
title: " Combinar dos registros (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo combinar dos registros.
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
ms.openlocfilehash: f918af6304134366df54ccf70acf90e861d61428
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155720"
---
# <a name="merge-two-record"></a>Combinar dos registros

En este ejemplo se muestra cómo combinar dos registros. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/MergeTwoRecords).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `MergeRequest` está diseñado para usarse en un escenario que contiene los datos que son necesarios para fusionar la información de dos entidades de registro del mismo tipo.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea cualquier registro de entidad que requiere este ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `MergeRequest` crea la solicitud. 
2. El mensaje `Account` crea otra cuenta para contener nuevos datos para combinarlos con la entidad.


### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

