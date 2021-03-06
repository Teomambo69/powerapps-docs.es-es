---
title: " Asignar un registro a un equipo (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo asignar registros a un equipo.
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
ms.openlocfilehash: 1dbf2a9c068c9085e1d3dc2e88db23f33ef58f38
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155956"
---
# <a name="assign-a-record-to-a-team"></a>Asignación de registros a un equipo

Este ejemplo muestra cómo asignar un registro a un equipo con el mensaje de [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9).

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignRecordToTeam).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) está diseñado para usarse en un escenario que contiene los datos que son necesarios para asignar el registro especificado a un nuevo propietario (usuario o equipo) cambiando el atributo OwnerId del registro.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

1. Comprobaciones para la versión actual de la organización. 
1. Crea los datos necesarios que requiere este ejemplo.

### <a name="demonstrate"></a>Demostración

El mensaje `AssignRequest` asigna el registro de cuenta creado para el ejemplo a un equipo. 

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar todos los datos creados en el ejemplo. La eliminación es opcional en caso de que desee examinar los datos creados por el ejemplo. Puede eliminar manualmente los datos para obtener los mismos resultados.