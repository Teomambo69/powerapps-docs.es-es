---
title: 'Ejemplo: Agregar una entidad de seguridad (usuario o equipo) a una cola (Common Data Service) | Microsoft Docs'
description: Agregar una entidad de seguridad a una cola
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: c41dfe21ad8a706b5502b637e0a9a3c68317c6a0
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934440"
---
# <a name="sample-add-a-security-principal-user-or-team-to-a-queue"></a>Ejemplo: Agregar una entidad de seguridad (usuario o equipo) a una cola 

Este ejemplo muestra cómo otorgar a un usuario o equipo acceso a una cola. [AddPrincipalToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addprincipaltoqueuerequest?view=dynamics-general-ce-9) agrega el principal especificado a la lista de miembros de la cola. Si la entidad de seguridad pasada es un equipo, cada miembro del equipo se agrega a la cola. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AddSecurityPrincipalToQueue).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `AddPrincipalToQueueRequest` está diseñado para usarse en un escenario donde contenga datos necesarios para agregar el principal especificado a la lista de miembros de la cola. Si el principal es un equipo, agregue cada miembro del equipo a la cola.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `Queue` crea una instancia de cola y establece sus valores de propiedad. Las GUID devueltas se almacenan en una variable.
3. `QueryExpression` recupera la unidad de negocio predeterminada para la creación del equipo y del rol.
4. Crea un nuevo equipo y rol de ejemplo necesarios para el ejemplo.
5. Recupera los privilegios `prvReadQueue` y `prvAppendToQueue`.
6. El método `AddPrivilegeRoleRequest` agrega los privilegios `prvReadQueue` y `prvAppendToQueue` al rol de ejemplo.

### <a name="demonstrate"></a>Demostración

El método `AddPrincipalToQueueRequest` agrega el equipo a la cola.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
