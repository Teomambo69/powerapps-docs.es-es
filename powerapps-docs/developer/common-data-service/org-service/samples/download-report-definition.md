---
title: " Descargar definición de informe (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo descargar la definición del informe
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
ms.openlocfilehash: 938a3dc5fd22c5fb600ad019fa3408ce415146b1
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155820"
---
# <a name="download-report-definition"></a>Descargar definición de informe

Este ejemplo muestra cómo descargar un archivo de definición de informes (.rdl) mediante el mensaje [DownloadReportDefinitionRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.downloadreportdefinitionrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DownloadReportDefinition).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `DownloadReportDefinitionRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para descargar una definición de informe.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `QueryByAttribute` consulta un informe existente.
2. El método `DownloadReportDefinitionRequest` descarga la definición del informe.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.