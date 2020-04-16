---
title: 'Ejemplo: Cambios de los datos de la entidad de auditoría (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo auditar cambios de datos en entidades.
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
ms.openlocfilehash: 907ac09f9cd530c26c2e577351736d52f005a65a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155928"
---
# <a name="sample-audit-entity-data-changes"></a>Ejemplo: cambios en los datos de la entidad de auditoría

Este ejemplo muestra cómo habilitar y deshabilitar la auditoría en las entidades y los atributos, recuperar el historial de cambios de los datos de la entidad auditada y eliminar los registros de auditoría. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AuditEntityData).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveRecordChangeHistoryRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para recuperar el historial de auditoría de una entidad.


## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea una entidad de cuenta de ejemplo.

### <a name="demonstrate"></a>Demostración

1. Obtiene el identificador de la organización del registro de usuario del sistema.
2. Habilitar la auditoría en la organización y también en la entidad Cuenta de ejemplo.
3. `RetrieveRecordChangeHistoryRequest` recupera el historial de auditoría para la entidad de cuenta y muestra el resultado.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
