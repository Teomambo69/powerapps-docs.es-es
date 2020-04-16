---
title: " Inicializar un registro desde registro existente (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo crear un nuevo registro a partir de un registro existente.
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
ms.openlocfilehash: fec83820324efc2e8a155f13dee4c74f5d3da806
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155748"
---
# <a name="initialize-a-record-from-existing-record"></a>Inicializar un registro de un registro existente

Este ejemplo muestra cómo usar el mensaje [IOrganizationService.InitializeFromRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9) para crear nuevos registros a partir de un registro existente. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/InitializeRecordFromExisting).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService.InitializeFromRequest` está diseñado para usarse en un escenario que contiene los datos necesarios para inicializar un nuevo registro desde un registro existente.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea cualquier registro de entidad que requiere este ejemplo.


### <a name="demonstrate"></a>Demostración

1. El método `InitializeFromRequest` crea la solicitud y establece propiedades para el objeto de solicitud. 
2. El método `InitializeFromResponse` ejecuta la solicitud.


### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

