---
title: 'Ejemplo: Uso de simultaneidad optimista con operaciones de actualización y eliminación (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo usar simultaneidad optimista para operaciones de actualización y eliminación.
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
ms.openlocfilehash: e673548562159db58a7473f20fc0a18865fedcea
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155528"
---
# <a name="sample-use-optimistic-concurrency-with-update-and-delete-operations"></a>Ejemplo: Uso de simultaneidad optimista con operaciones de actualización y eliminación

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/sample-use-optimistic-concurrency-update-delete-operations -->

Este ejemplo muestra cómo usar simultaneidad optimista para operaciones de actualización y eliminación. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OptimisticConcurrency).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La clase `UpdateRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para actualizar un registro existente.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Account` crea un registro de cuenta.

### <a name="demonstrate"></a>Demostración

1. Recupera el registro de cuenta que se crea en [Configuración](#setup).
1. Actualiza el registro de cuenta incrementando el atributo `creditlimit`.
1. El método `UpdateRequest` establece el comportamiento de simultaneidad de la solicitud para comprobar una coincidencia de versión de fila.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.
