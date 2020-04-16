---
title: " Actualizar un rol de conexión (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo actualizar un rol de conexión
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
ms.openlocfilehash: e858b2722a2af2a24bf2ef65bb2a9ba53caf058e
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155548"
---
# <a name="update-a-connection-role-early-bound"></a>Actualizar un rol de conexión (con enlace en tiempo de compilación)

Este ejemplo muestra cómo modificar las propiedades del rol de conexión, como un nombre, descripción y categoría de rol. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/UpdateConnectionRole).

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

El mensaje `Update` actualiza la función de conexión.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.