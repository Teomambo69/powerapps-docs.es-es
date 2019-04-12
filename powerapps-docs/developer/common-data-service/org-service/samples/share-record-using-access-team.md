---
title: 'Ejemplo: Compartir un registro mediante un equipo de acceso (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo permitir el acceso a un registro utilizando un equipo de acceso.
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
# <a name="sample-share-a-record-using-an-access-team"></a>Ejemplo: Compartir un registro utilizando un equipo de acceso

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-share-record-using-access-team -->

Este ejemplo muestra cómo permitir el acceso a un registro utilizando un equipo de acceso. Todos los integrantes del equipo recibirán el mismo acceso al registro que se concede al equipo. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ShareRecordUsingAccessTeam).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los usuarios requeridos manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. Reemplace `yourorg` por el nombre de la organización.

**Nombre**: Nancy<br/>
**Apellidos**: Anderson<br/>
**Rol de seguridad**: Comercial<br/>
**UserName**: nanderson@yourorg.onmicrosoft.com<br/>

**Nombre**: David<br/>
**Apellido**: Bristol<br/>
**Rol de seguridad**: Comercial<br/>
**UserName**: dbristol@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `AddMembersTeamRequest`, `GrantAccessRequest`, `RemoveMembersTeamRequest` están diseñados para usarse en un escenario que contenga datos necesarios para agregar, conceder y quitar miembros.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea un registro de cuenta de prueba para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. Recupera a los comerciales que se crean manualmente en **Office 365** que se agregarán al equipo.
1. La `WhoAMIRequest` obtiene el id. del usuario y la unidad de negocio actuales.
1. Crea un equipo de acceso de ejemplo. La `AddMembersTeamRequest` agrega a dos comerciales al equipo de acceso.
1. La `GrantAccessRequest` concede al equipo acceso de lectura y escritura a la cuenta creada en Setup(#setup).
1. La `RetrieveAndDisplayEntityAccess` recupera y muestra información de acceso de la entidad.
1. La `RetrieveAndDisplayPrincipalAccess` recupera y muestra información de acceso principal.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
