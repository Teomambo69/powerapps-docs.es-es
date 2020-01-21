---
title: " Asignar un panel a otro usuario (Common Data Service) | MicrosoftDocs"
description: 'Este ejemplo muestra cómo asignar un panel de propiedad del usuario a otro usuario '
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
ms.openlocfilehash: bbfd3f468bc59c4cbd455bda93ed8e0deae07729
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934432"
---
# <a name="assign-a-user-owned-dashboard-to-another-user"></a>Asignar un panel propiedad del usuario a otro usuario

Este ejemplo muestra cómo asignar una a visualización de propiedad del usuario a otro usuario mediante el mensaje [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9). Debido a que no puede eliminar un panel que pertenece a un usuario que esté asignado a otro usuario, este ejemplo muestra cómo usar la suplantación para eliminar el panel propiedad del usuario. Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssignUserOwnedDashboardToAnother).

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
2. El método `CreateRequiredRecords` crea registros de entidad que requiere este ejemplo.
3. El método `mySavedQuery` toma la vista pública predeterminada para las oportunidades.
4. El método `visualizationQuery` recupera las visualizaciones fuera del sistema. Este ejemplo supone que tiene las **Oportunidades principales**. 
5. El método `_otherUSerId` crea el usuario al que se asignará el tablero.

### <a name="demonstrate"></a>Demostración

El método `AssignRequest` asigna la visualización o el gráfico al usuario recién creado.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.