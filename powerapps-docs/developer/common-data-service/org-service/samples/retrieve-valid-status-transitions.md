---
title: 'Ejemplo: Recuperar transiciones de estado válidas (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar transiciones de estado válidas.
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
ms.openlocfilehash: e6eb7b939430b2f21f961bfd85b0d3b6179eb3d7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155604"
---
# <a name="sample-retrieve-valid-status-transitions"></a>Ejemplo: recuperar transiciones de estado válidas

Este ejemplo muestra cómo recuperar transiciones de estado válidas independientemente de si las transiciones de estado personalizadas se han definido para la entidad. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveValidTransitions).
 
## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El método `GetValidStatusOptions` está diseñado para usarse en un escenario donde contiene los datos que devuelven transiciones de opción de estado válidas con independencia de si las transiciones de estado están habilitadas para la entidad.
## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `MetadataFilterExpression` comprueba los metadatos de la entidad.

### <a name="demonstrate"></a>Demostración

1. El método `MetadataFilterExpression` recupera las opciones de estado para la entidad `Incident`.
1. El método `RetrieveMetadataChangeRequest` recupera los metadatos.
1. El método `GetValidStatusOptions` obtiene las transiciones de estado válidas para cada opción de estado.

### <a name="clean-up"></a>Limpiar

Este ejemplo no crea ningún registro. No es necesaria ninguna limpieza.
