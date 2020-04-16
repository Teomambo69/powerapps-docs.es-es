---
title: " Determinar si un usuario tiene un rol (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo determinar si un usuario tiene un rol específico.
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
ms.openlocfilehash: f403df191d8845edcc48ebef7e961130217152ff
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155828"
---
# <a name="determine-whether-a-user-has-a-role"></a>Determinar si un usuario tiene un rol

Este ejemplo muestra cómo determinar si se ha asociado a un usuario de Common Data Service con un rol específico. Esto se realiza mediante una consulta con el método [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9).  Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/DetermineWhetherUserHasRole).

Este ejemplo requiere un usuario adicional que no está disponible en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. 

**Nombre**: Dan<br/>
**Apellidos**: Park<br/>
**Rol de seguridad**: No hay rol de seguridad<br/>
**Nombre de usuario**: dpark@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [IOrganizationService.RetrieveMultiple](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrievemultiple?view=dynamics-general-ce-9) está diseñado para usarse en un escenario donde recupere una recopilación de registros.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea un usuario sin un rol de seguridad asignado como se muestra arriba.

### <a name="demonstrate"></a>Demostración

1. El método `retrieve` recupera un usuario de Common Data Service.
2. El mensaje `query` se utiliza para averiguar un rol.

### <a name="clean-up"></a>Limpiar

Este ejemplo no crea ningún registro. No es necesario ninguna limpieza.
