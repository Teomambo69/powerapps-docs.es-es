---
title: 'Ejemplo: habilitar la seguridad de campo para una entidad(Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo habilitar la seguridad de campo para una entidad.
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
ms.openlocfilehash: e905c2a1e687eef65535c9dcaa0a05432150b1ba
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934304"
---
# <a name="sample-enable-field-security-for-an-entity"></a>Ejemplo: habilitar la seguridad de campo para una entidad

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-enable-field-security-entity -->

En este ejemplo se muestra cómo habilitar la seguridad de campo para una entidad.  Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/FieldSecurity). 

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo, cree un perfil de usuario **tal cual** se muestra abajo. 

**Nombre**: Samantha<br/>
**Apellidos**: Smith<br/>
**Rol de seguridad**: director de marketing<br/>
**Nombre de usuario**: ssmith@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito anteriormente, el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Obtiene el usuario que ha creado manualmente en **Office 365**.
3. Recupere el rol de seguridad necesario para asignar al usuario. 
4. Recupere la unidad de negocio predeterminada necesaria para crear el equipo.
5. Cree instancias de un registro de entidad de equipo y establezca los valores de la propiedad. 

### <a name="demonstrate"></a>Demostración

1. Crea un perfil de seguridad de campo y crea el objeto de la solicitud y establece los monikers con la relación teamprofiles_assocation.
2. Crea la entidad de actividad personalizada y los atributos con los mensajes `CreateEntityRequest` y `CreateAttributeRequest`.
3. Cree el permiso de campo para el atributo de identidad.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
