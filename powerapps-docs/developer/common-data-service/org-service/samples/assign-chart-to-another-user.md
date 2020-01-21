---
title: " Asignar un gráfico a otro usuario (Common Data Service) | MicrosoftDocs"
description: 'Este ejemplo muestra cómo asignar una a visualización de propiedad del usuario a otro usuario '
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
ms.openlocfilehash: 22ba3d9186e6e052770e303e5c1b18cef9fa45ed
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934436"
---
# <a name="assign-a-chart-to-another-user"></a>Asignar un diálogo a otro usuario

Este ejemplo muestra cómo asignar una a visualización de propiedad del usuario a otro usuario mediante el mensaje [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignChartToAnotherUser).

Este ejemplo requiere un usuario adicional que no está disponible en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. 

**Nombre**: Kevin<br/>
**Apellidos**: Cook<br/>
**Rol de seguridad**: jefe de ventas<br/>
**Nombre de usuario**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) está diseñado para usarse en un escenario que contiene los datos que son necesarios para asignar el registro especificado a un nuevo propietario (usuario o equipo) cambiando el atributo OwnerId del registro.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea una cuenta de ejemplo y algunos registros de oportunidad para la visualización.
3. El método `newUserOwnedVisualization` crea la instancia de la entidad de visualización.

### <a name="demonstrate"></a>Demostración

El método `AssignRequest` asigna la visualización o el gráfico al usuario recién creado.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.