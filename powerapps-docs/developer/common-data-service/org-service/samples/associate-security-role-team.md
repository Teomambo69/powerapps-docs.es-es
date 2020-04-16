---
title: " Asociar rol de seguridad a un equipo (Common Data Service) | Microsoft Docs"
description: 'En este ejemplo se muestra cómo asignar un rol de seguridad a un equipo '
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
ms.openlocfilehash: 6ea2984f5fd8ad276581307edf3ff76ca1abeef8
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155952"
---
# <a name="sample-associate-security-role-to-a-team"></a>Ejemplo: asociar rol de seguridad a un equipo 

Este ejemplo muestra cómo asignar un rol de seguridad a un equipo con el mensaje de [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9). Tenga en cuenta que este ejemplo no tiene en cuenta que un equipo o usuario solo puede asignar un rol desde la unidad de negocio. El rol que se asignará es el primero de la recopilación que es devuelto por el método de RetrieveMultiple. Si ese registro es de una unidad de negocio diferente del equipo que realiza la solicitud, la asignación no se realizará correctamente.

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AssociateSecurityRoleToTeam).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje [AssignRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.assignrequest?view=dynamics-general-ce-9) está diseñado para usarse en un escenario que contiene datos que son necesarios para asignar el registro especificado a un nuevo propietario (usuario o equipo) cambiando el atributo OwnerId del registro.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `CreateRequiredRecords` crea los registros necesarios para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `query` recupera un rol de Common Data Service.
2. El mensaje `Associate` asigna el rol a un equipo.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
