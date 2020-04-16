---
title: " Recuperar información de licencia (Common Data Service) | Microsoft Docs"
description: 'En este ejemplo se muestra cómo recuperar la información de licencia. '
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
ms.openlocfilehash: cd2a6e5551c4eea8f20fa8ef6cc71a8f6bf71664
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155636"
---
# <a name="retrieve-license-information"></a>Recuperar información de licencia

En este ejemplo se muestra cómo usar el mensaje [IDeploymentService.RetrieveDeploymentLicenseTypeRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievedeploymentlicensetyperequest?view=dynamics-general-ce-9) y el mensaje [IOrganizationService.RetrieveLicenseInfoRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievelicenseinforequest?view=dynamics-general-ce-9) para recuperar información sobre licencias.

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveLicenseInformation).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [IDeploymentService.RetrieveDeploymentLicenseTypeRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievedeploymentlicensetyperequest?view=dynamics-general-ce-9) está diseñado para usarse en un escenario que contiene datos que son necesarios para recuperar el tipo de licencia para una implementación de Common Data Service.

El mensaje [IOrganizationService.RetrieveLicenseInfoRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.retrievelicenseinforequest?view=dynamics-general-ce-9) está diseñado para usarse en un escenario que contiene datos que son necesarios para recuperar el número de licencias usadas y disponibles para una implementación de Common Data Service.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `deploymentTypeRequest` crea una solicitud para recuperar los tipos de licencia de implementación.
2. El mensaje `licenseInfoRequest` crea una solicitud para recuperar la solicitud de información con licencia.

### <a name="clean-up"></a>Limpiar

Este ejemplo no crea ningún registro. No es necesario ninguna limpieza.