---
title: 'Ejemplo: Compartir registros utilizando GrantAccess, ModifyAccess y RevokeAccess (Common Data Service) | Microsoft Docs'
description: 'Este ejemplo muestra cómo compartir un registro usando un mensaje de concesión, modificación y revocación de acceso.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-share-records-using-grantaccess-modifyaccess-and-revokeaccess-messages"></a>Ejemplo: compartir registros utilizando los mensajes GrantAccess, ModifyAccess y RevokeAccess

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-share-records-using-grantaccess-modifyaccess-revokeaccess-messages 

Change sample to make sure it works with Common Data Service
-->

Este ejemplo muestra cómo compartir un registro con los siguientes mensajes:

[GrantAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.grantaccessrequest?view=dynamics-general-ce-9)

[ModifyAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.modifyaccessrequest?view=dynamics-general-ce-9)

[RevokeAccessRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.revokeaccessrequest?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GrantModifyRevokeAccess).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree 2 perfiles de usuario **tal cual** se muestra abajo. Reemplace `yourorg` por el nombre de la organización.

**Nombre**: Dan<br/>
**Apellidos**: Wilson<br/>
**Rol de seguridad**: Delegado<br/>
**UserName**: dwilson@yourorg.onmicrosoft.com<br/>

**Nombre**: Christen<br/>
**Apellidos**: Anderson<br/>
**Rol de seguridad**: Delegado<br/>
**UserName**: canderson@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `GrantAccessRequest`, `ModifyAccessRequest`, `RevokeAccessRequest` están diseñados para usarse en un escenario donde contengan los datos necesarios para conceder, modificar y revocar acceso.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea un identificador único para evitar conflictos de nombre.
3. Recupera el usuario creado manualmente en **Office 365** para este ejemplo.
4. Recupera la unidad de negocio raíz para crear el equipo del ejemplo.
5. La `WhoAMIRequest` obtiene la información del usuario actual.
6. Crea el equipo y agrega los usuarios al equipo. 
7. Crea un registro de cuenta y también crea una tarea, carta para asociarla a la cuenta.

### <a name="demonstrate"></a>Demostración

1. Recupera y muestra el acceso que tiene el usuario que llama a la cuenta creada.
2. Recupera y muestra el acceso que tiene el primer usuario a la cuenta creada. 
3. El método `GrantAccessRequest` concede al primer usuario acceso de `read` a la cuenta creada.
4. El método `ModifyAccessRequest` concede al primer usuario acceso de `delete` a la cuenta creada.
5. El método `RevokeAccessRequest` concede al primer usuario acceso de `revoke` a la cuenta creada.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
