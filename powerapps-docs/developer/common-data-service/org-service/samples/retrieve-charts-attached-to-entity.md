---
title: " Recuperar gráficos asociados a una entidad (Common Data Service) | Microsoft Docs"
description: 'En este ejemplo se muestra cómo recuperar gráficos asociados a una entidad '
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: ''
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
ms.openlocfilehash: 7d58caf3be322ab0d0f6b3153021423b926df413
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934232"
---
# <a name="retrieve-all-charts-attached-to-an-entity"></a>Recuperar todos los gráficos asociados a una entidad

Este ejemplo muestra cómo recuperar todas las visualizaciones que pertenecen a la organización asociadas a una entidad mediante el método [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com//dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9).

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveChartsAttachedToEntity).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]


## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService` está diseñado para usarse en un escenario donde contiene datos que proporcionan acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

El método `newSavedQuery` crea un consulta para recuperar todas las visualizaciones que pertenecen a la organización asociadas a la entidad de la cuenta.


### <a name="clean-up"></a>Limpiar

Este ejemplo no crea ningún registro. No es necesario ninguna limpieza.
