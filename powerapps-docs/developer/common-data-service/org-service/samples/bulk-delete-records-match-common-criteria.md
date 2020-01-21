---
title: 'Ejemplo: Eliminación de registros en masa que coincidan con criterios comunes (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo eliminar registros en masa, que coinciden con criterios comunes.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6d1bc234c4587a5fe1074245e17f44c962f7f710
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934408"
---
# <a name="sample-bulk-delete-records-that-match-common-criteria"></a>Ejemplo: eliminar registros en masa que coincidan con los criterios comunes

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-bulk-delete-records-match-common-criteria -->

Este ejemplo muestra cómo eliminar registros, en masa, que coinciden con los criterios comunes. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BulkDeleteMatchCriteria).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `BulkDeleteRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para crear la solicitud de eliminación en masa.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea un registro de cuenta de ejemplo.
3. Consulta para que un usuario del sistema envíe un correo electrónico después de que la operación de eliminación en masa se complete.
3. `BulkDeleteRequest` crea el proceso de eliminación en masa y establece las propiedades de la solicitud.
4. El método `InspectBulkDeleteOperation` inspecciona y muestra información sobre la `BulkDeleteOperation` creada.
5. El método `RetrieveBulkDeleteOperation` recupera `BulkDeleteOperation`.

### <a name="demonstrate"></a>Demostración

1. Comprueba si las plantillas estándar de correo electrónico están presentes.
1. El método `PerformBulkDelete` realiza la operación de eliminación en masa principal.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
