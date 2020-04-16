---
title: 'Ejemplo: obtener límites del historial de informes (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo obtener límites del historial de informes.
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
ms.openlocfilehash: 80dc150533914c64983aa6ec4450fde23dbb6b0a
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155760"
---
# <a name="get-report-history-limits"></a>Obtener límites del historial de informes

Este ejemplo muestra cómo obtener los límites del historial de informes utilizando el mensaje [GetReportHistoryLimitRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.getreporthistorylimitrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GetReportHistoryLimit).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `GetReportHistoryLimitRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para recuperar el límite del historial para un informe.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `QueryByAttribute` consulta un informe existente.
2. El método `GetReportHistoryLimitRequest` obtiene los datos del límite del historial.

### <a name="clean-up"></a>Limpiar

No se requiere limpieza para este ejemplo.
