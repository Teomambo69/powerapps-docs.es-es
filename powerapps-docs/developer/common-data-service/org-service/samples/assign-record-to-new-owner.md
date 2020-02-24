---
title: " Asignar un registro a un nuevo propietario (Common Data Service) | MicrosoftDocs"
description: Este ejemplo muestra cómo asignar registros a un nuevo propietario.
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
ms.openlocfilehash: 0e6df124f8fcd9baf4658263bc65d510af3ac003
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956359"
---
# <a name="assign-a-record-to-a-new-owner"></a>Asignar un registro a un nuevo propietario

Este ejemplo muestra cómo asignar una cuenta a otro usuario mediante el mensaje [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9).

Este ejemplo usa el método `IOrganization.Update` en lugar de la [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) porque existe un esfuerzo para quitar mensajes especializados. Más información: [Realizar operaciones especializadas con actualizar](https://docs.microsoft.com/powerapps/developer/common-data-service/special-update-operation-behavior)

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignRecordToNewOwner).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9) está diseñado para usarse en un escenario donde contenga los datos necesarios para actualizar un registro existente.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

1. Comprobaciones para la versión actual de la organización. 
1. Crea los datos necesarios que requiere este ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `Retrieve` recupera los registros de cuenta creados en la configuración(#setup).
1. El mensaje `Update` actualiza el atributo `ownerid` al usuario que desea poseer el registro. 

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.