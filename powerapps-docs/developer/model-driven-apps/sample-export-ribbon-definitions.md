---
title: 'Ejemplo: Exportar definiciones de cinta de opciones (aplicaciones basadas en modelos) | Microsoft Docs'
description: El ejemplo muestra cómo exportar definiciones de cinta de opciones. Utiliza los mensajes RetrieveApplicationRibbonRequest y RetrieveEntityRibbonRequest.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a08a64d2e74298093e7c3b260b00f82d0b5aa51a
ms.sourcegitcommit: 6c73e316f866af6a34619f95a5ac64ad1664b48a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/01/2020
ms.locfileid: "3326426"
---
# <a name="sample-export-ribbon-definitions"></a>Ejemplo: exportar definiciones de cinta

Este ejemplo muestra cómo exportar definiciones de la cinta de opciones. Utiliza los mensajes [RetrieveApplicationRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveapplicationribbonrequest?view=dynamics-general-ce-9) y [RetrieveEntityRibbonRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrieveentityribbonrequest?view=dynamics-general-ce-9) Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExportRibbonDefinitions).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../common-data-service/includes/cc-how-to-run-samples.md)]

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

  
### <a name="see-also"></a>Vea también  
 [Personalizar comandos y la cinta de opciones](customize-commands-ribbon.md)   
 [Pasar parámetros a una dirección URL con la cinta de opciones](pass-parameters-url-by-using-ribbon.md)   
 [Esquema central de cinta de opciones](ribbon-core-schema.md) [Esquema de tipos de cinta de opciones](ribbon-types-schema.md) [Esquema WSS de cinta de opciones](ribbon-wss-schema.md) <xref:Microsoft.Crm.Sdk.Messages.RetrieveApplicationRibbonRequest>   
 <xref:Microsoft.Crm.Sdk.Messages.RetrieveEntityRibbonRequest>
