---
title: " Asociar rol de seguridad a un usuario ( Common Data Service) | Microsoft Docs"
description: 'Esta muestra expone cómo asignar un rol de seguridad a un usuario '
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
ms.openlocfilehash: 4caaf5201878d4ebd3bbc38835591f31a7064c72
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956358"
---
# <a name="sample-associate-security-role-to-a-user"></a>Ejemplo: asociar un rol de seguridad a un usuario

Este ejemplo muestra cómo asignar un rol de seguridad a un usuario, empleando el mensaje [IOrganizationService.Associate](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice?view=dynamics-general-ce-9). 

Este ejemplo requiere un usuario adicional que no está disponible en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. 

**Nombre**: Dan<br/>
**Apellidos**: Park<br/>
**Rol de seguridad**: usuario sin roles asignados<br/>
**Nombre de usuario**: dpark@yourorg.onmicrosoft.com<br/>

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssociateSecurityRoleToUser).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [IOrganizationService.Associate](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice?view=dynamics-general-ce-9) está diseñado para usarse en un escenario que contiene datos que proporcionan acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea los registros necesarios para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `QueryExpression` recupera un rol de Common Data Service.
2. El mensaje `Associate` asigna el rol a un usuario.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
