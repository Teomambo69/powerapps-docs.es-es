---
title: 'Ejemplo: exportar definiciones de cinta de opciones (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo exportar definiciones de la cinta de opciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 009b9a644ac4ae010d4e5e74facc4cdef99a6cc7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155768"
---
# <a name="export-ribbon-definitions"></a>Exportar definiciones de cinta de opciones

Este ejemplo muestra cómo exportar definiciones de la cinta de opciones. Utiliza los mensajes [RetrieveApplicationRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveapplicationribbonrequest?view=dynamics-general-ce-9) y [RetrieveEntityRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveentityribbonrequest?view=dynamics-general-ce-9) Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions).


## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RetrieveApplicationRibbonRequest` está destinado a utilizarse en un escenario que contiene datos necesarios para recuperar los datos que definen el contenido y el comportamiento de la cinta de opciones de la aplicación. El mensaje `RetrieveEntityRibbonRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para recuperar las definiciones de cinta de opciones de una entidad.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `RetrieveApplicationRibbonRequest` recupera la cinta de opciones de la aplicación.
2. El método `RetrieveEntityRibbonRequest` recupera las cintas de opciones de la entidad del sistema

### <a name="clean-up"></a>Limpiar

No se requiere limpieza para este ejemplo
