---
title: 'Ejemplo: Auditar acceso de usuario (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo auditar el acceso de usuarios
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-audit-user-access"></a>Ejemplo: acceso de usuario de auditoría

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-audit-user-access -->

Este código de ejemplo muestra cómo auditar el acceso de usuarios. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/AuditUserAccess).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo primero habilita la auditoría del acceso de usuario a la organización del usuario que inició sesión. A continuación, crea y modifica una entidad cuenta para generar registros de auditoría.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. Se crea una nueva entidad de cuenta y habilita la auditoría en la nueva entidad de cuenta.

### <a name="demonstrate"></a>Demostración

1. Obtiene el identificador de la organización del registro de usuarios del sistema y recupera el registro de la organización.
2. Habilita la auditoría en la organización, incluida la auditoría del acceso del usuario.
3. Hace una solicitud de actualización a la entidad de cuenta para que la auditoría le realice un seguimiento.
4. establecer los marcadores de auditoría de organización y de cuentas de nuevo en los valores antiguos y recuperarlos si se cambiaron realmente.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados durante la [Configuración](#setup). 

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
