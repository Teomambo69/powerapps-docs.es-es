---
title: " Crear, recuperar, actualizar y eliminar gráficos (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo crear, recuperar, actualizar y eliminar visualizaciones propiedad del usuario.
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
ms.openlocfilehash: 7c05e2b8618e4b1a542d3657bf822bd44e5e0287
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155868"
---
# <a name="create-retrieve-update-and-delete-a-chart"></a>Crear, recuperar, actualizar y eliminar un gráfico

Este ejemplo muestra cómo crear, recuperar, actualizar y eliminar una visualización propiedad del usuario mediante el uso de los siguientes métodos:

- [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDOperationsChart).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService` está diseñado para usarse en un escenario donde contiene datos que proporcionan acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `CreateRequiredRecords` crea registros de entidad que son obligatorios para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `presentationXml` establece la cadena XML de presentación. 
2. El método `dataXml` establece la cadena XML de datos.
3. El método `newUserOwnedVisualization` crea la instancia de la entidad de visualización.
4. El método `retrievedOrgOwnedVisualization` recupera la visualización.
5. El método `newDataXml` actualiza el nombre y la cadena de descripción de datos.


### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.