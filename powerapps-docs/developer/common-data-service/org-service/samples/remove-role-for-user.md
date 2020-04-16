---
title: " Eliminar un rol para un usuario (Common Data Service) | Microsoft Docs"
description: 'En este ejemplo se muestra cómo eliminar un rol para un usuario '
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
ms.openlocfilehash: 5e6719002a2180aed19fa030e03611f5ce6b893c
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155660"
---
# <a name="remove-a-role-for-a-user"></a>Eliminar un rol para un usuario

Este ejemplo muestra cómo desasociar un rol de un usuario mediante el método [IOrganizationService.Disassociate](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.disassociate?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RemoveRoleFromUser).

Este ejemplo requiere un usuario adicional que no está disponible en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. 

**Nombre**: Dan<br/>
**Apellidos**: Park<br/>
**Rol de seguridad**: No hay rol de seguridad<br/>
**Nombre de usuario**: dpark@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [IOrganizationService.Disassociate](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.disassociate?view=dynamics-general-ce-9) está diseñado para usarse en un escenario donde se elimina un vínculo entre registros.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea los registros necesarios para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `query` recupera un rol de Common Data Service.
2. El mensaje `Disassociate` elimina el rol a un equipo.

### <a name="clean-up"></a>Limpiar

Este ejemplo no crea ningún registro. No es necesario ninguna limpieza.
