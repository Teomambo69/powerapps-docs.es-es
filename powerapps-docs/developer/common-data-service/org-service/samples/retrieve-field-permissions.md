---
title: 'Ejemplo: Recuperar permisos de campo (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo recuperar campos protegidos para un usuario
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 53b73e6a30875d6f8c2620517e83ebd3230597e9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155640"
---
# <a name="sample-retrieve-field-permissions"></a>Ejemplo: recuperar permisos de campo

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-retrieve-field-permissions -->

El ejemplo muestra cómo recuperar campos protegidos para un usuario según los pasos descritos en [Entidades de seguridad de campo](https://docs.microsoft.com/dynamics365/customer-engagement/developer/field-security-entities). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveFieldPermission).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. Reemplace `yourorg` por el nombre de la organización.

**Nombre**: Samantha <br/>
**Apellidos**: Smith<br/>
**Rol de seguridad**: director de marketing<br/>
**Nombre de usuario**: ssmith@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

La clase `FieldPermission` está diseñada para usarse en un escenario donde contiene los datos que definen los tipos de permiso de campo posibles.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. Obtiene información de usuarios que ha creado manualmente en **Office 365**.
1. El método `QueryExpression` recupera el rol de seguridad necesario para asignar al usuario.
1. El método `Team` crea instancias de un registro de entidad de equipo y establece sus valores de la propiedad.

### <a name="demonstrate"></a>Demostración

1. El método `FieldSecurityProfile` crea un perfil de seguridad de campo.
1. El método `AssociateRequest` agrega el equipo y el usuario al perfil.
1. El método `CreateEntityRequest` crea una nueva entidad de actividad personalizada para el ejemplo.
1. El método `RolePrivilege` agrega privilegios para la nueva entidad personalizada.
1. El método `AddPrivilegeRoleRequest` crea y ejecuta el método `RolePrivilege`.
1. El método `FieldPermission` crea el objeto de permiso de campo para la identidad.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
