---
title: " Crear, recuperar, actualizar y eliminar paneles (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo crear, recuperar, actualizar y eliminar paneles propiedad del usuario.
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
ms.openlocfilehash: 0efb3e9b29f23e3d24fbaeb938751c20fe69566c
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934360"
---
# <a name="create-retrieve-update-and-delete-a-chart"></a>Crear, recuperar, actualizar y eliminar un gráfico

Este ejemplo muestra cómo crear, recuperar, actualizar y eliminar un panel propiedad del usuario mediante el uso de los siguientes métodos:

- [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDOperationsDashboard).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService` está diseñado para usarse en un escenario donde contiene datos que proporcionan acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `mySavedQuery` toma la vista pública predeterminada para oportunidades. 
2. El método `visualizationQuery` recupera las visualizaciones fuera del sistema. Este ejemplo supone que tiene las **Oportunidades principales**. 
3. El método `dashboard` establece el panel de control y especifica el FormXml.
4. El método `chartPicker` habilita el selector de gráficos en el gráfico.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.