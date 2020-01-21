---
title: 'Ejemplo: habilitar la detección de duplicados y recuperar los duplicados (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo habilitar la detección de duplicados y recuperar registros duplicados.
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
ms.openlocfilehash: c43c9a25b4b662a00f2886c23cb05be1bb105f7d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934308"
---
# <a name="sample-enable-duplicate-detection-and-retrieve-duplicates"></a>Ejemplo: habilitar la detección de duplicados y recuperar los duplicados

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-enable-duplicate-detection-and-retrieve-duplicates -->

En este ejemplo se muestra cómo habilitar la detección de duplicados y recuperar registros duplicados. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EnableDuplicateDetection).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La propiedad `IsDuplicateDetectionEnabled` está diseñada para usarse en un escenario para habilitar la regla de detección de duplicados para una organización y también para una entidad.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea algunos registros de cuenta para recuperar los duplicados.
1. El método `RetrieveDuplicateRequest` recupera los registros duplicados. 
1. La clase `EnableDuplicateDetectionForOrg` habilita la detección de duplicados para una organización. 
1. Para habilitar la detección de duplicados, establezca `IsDuplicateDetectionEnabled = true`.
1. El método `RetrieveEntityRequest` recupera los metadatos de la entidad. 
1. Establezca `IsDuplicateDetectionEnabled = true` para actualizar el marcador de detección de duplicados.
1. Las actualizaciones de `UpdateEntityRequest` con la detección de duplicados establecidas en `true`.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
