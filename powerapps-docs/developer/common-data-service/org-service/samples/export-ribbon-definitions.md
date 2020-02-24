---
title: 'Ejemplo: exportar definiciones de cinta de opciones (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo exportar definiciones de la cinta de opciones
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 49d48cd432fb2b45395bbcff558a98378b889d40
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956353"
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
