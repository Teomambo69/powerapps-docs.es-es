---
title: Compatibilidad con PowerShell | Microsoft Docs
description: Compatibilidad con PowerShell para PowerApps
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/17/2018
ms.author: jamesol
ms.openlocfilehash: 274d34ca56cc993ec26fa4f4ced77bb2aba9985f
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="powershell-support-for-powerapps-preview"></a>Compatibilidad con PowerShell para PowerApps (versión preliminar)

Con el lanzamiento de la versión preliminar de los cmdlets de PowerShell para creadores y administradores de aplicaciones, puede automatizar muchas de las tareas de supervisión y administración que hoy solo son posibles manualmente en el [sitio web de PowerApps ](https://web.powerapps.com) o en el [Centro de administración de PowerApps](https://admin.powerapps.com).

## <a name="installation"></a>Instalación
Para ejecutar los cmdlets de PowerShell para creadores de aplicaciones, primero debe realizar los siguientes pasos:

1. Descargue el archivo de scripts de PowerShell [aquí](https://go.microsoft.com/fwlink/?linkid=872358).

2. Descomprima el archivo en una carpeta.

3. Abra una ventana de comandos de PowerShell en esa misma carpeta, como administrador.

4. Después ejecute el siguiente comando de PowerShell de un solo uso (esto supone que nunca ha ejecutado comandos de PowerShell en la máquina actual):

    ```
    Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force
    ```

5. A continuación, importe los módulos necesarios con los siguientes comandos:

    ```
    Import-Module .\Microsoft.PowerApps.Administration.PowerShell.psm1 -Force
    Import-Module .\Microsoft.PowerApps.PowerShell.psm1 -Force
    ```

6. Por último, antes de acceder a cualquiera de los comandos, deberá proporcionar sus credenciales mediante el siguiente comando. Estas credenciales se actualizarán durante un máximo de ~8 horas antes de que se le pida que inicie sesión de nuevo para continuar usando los cmdlets.

    ```
    Add-PowerAppsAccount
    ```

## <a name="powerapps-cmdlets-for-app-makers-preview"></a>Cmdlets de PowerApps para creadores de aplicaciones (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Cualquier usuario con una licencia válida de PowerApps podrá realizar las operaciones en estos cmdlets. Pero solo tendrán acceso a los recursos (por ejemplo, aplicaciones o flujos) que se hayan creado o compartido con ellos.

### <a name="cmdlet-list"></a>Lista de cmdlets
| Propósito | Cmdlet |
| --- | --- |
| Leer entornos | Get-PowerAppsEnvironment <br> Get-FlowEnvironment
| Leer, actualizar y eliminar una aplicación de lienzo | Get-App <br> Remove-App <br> Publish-App <br> Set-AppDisplayName <br> Get-AppVersion <br> Restore-AppVersion
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-AppRoleAssignment <br> Set-AppRoleAssignment <br> Remove-AppRoleAssignment
| Leer, actualizar y eliminar un flujo | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow
| Leer, actualizar y eliminar permisos de flujo | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole
| Leer y responder a las aprobaciones de flujo | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest
| Leer y eliminar conexiones | Get-Connection <br> Remove-Connection
| Leer, actualizar y eliminar permisos de conexiones | Get-ConnectionRoleAssignment <br> Set-ConnectionRoleAssignment <br> Remove-ConnectionRoleAssignment
| Leer y eliminar conectores | Get-Connector <br> Remove-Connector
| Leer, actualizar y eliminar los permisos de conector personalizado | Get-ConnectorRoleAssignment <br> Set-ConnectorRoleAssignment <br> Remove-ConnectorRoleAssignment

> [!NOTE]
> Los siguientes comandos se pueden utilizar para entender la sintaxis y ver muestras de cada uno de los cmdlets:
>```
>Get-Help Get-PowerAppsEnvironment
>Get-Help Get-PowerAppsEnvironment -Examples
>Get-Help Get-PowerAppsEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>Cmdlets de PowerApps para administradores (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Para realizar las operaciones de administración en los cmdlets de administración, necesitará una cuenta con los siguientes permisos:

- Una licencia de PowerApps plan 2 de pago o una licencia de prueba PowerApps plan 2. También puede registrarse para obtener una licencia de evaluación gratuita de 30 días en [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Licencias de evaluación gratuita se pueden renovar si han caducado.

- [También se necesitan los privilegios de administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o [ de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) si necesita buscar en los recursos de otro usuario. De lo contrario, solo tendrá acceso a aquellos entornos y recursos del entorno en los que tenga privilegios de administrador de entorno.

### <a name="cmdlet-list"></a>Lista de cmdlets
| Propósito | Cmdlets
| --- | ---
| Leer y eliminar entornos | Get-AdminEnvironment <br> Remove-AdminEnvironment
| Leer, actualizar y eliminar los privilegios de entorno <br><br> *Estos cmdlets solo funcionan para entornos que no tienen una base de datos de Common Data Service for Apps.* | Get-AdminEnvironmentRoleAssignment <br> Set-AdminEnvironmentRoleAssignment <br> Remove-AdminEnvironmentRoleAssignment
| Leer y quitar aplicaciones de lienzo | Get-AdminApp <br> Remove-AdminApp
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-AdminAppRoleAssignment <br> Remove-AdminAppRoleAssignment <br> Set-AdminAppRoleAssignment <br> Set-AdminAppOwner
| Leer, actualizar y eliminar flujos | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow  <br> Remove-AdminFlowOwnerRole

> [!NOTE]
> Los siguientes comandos se pueden utilizar para entender la sintaxis y ver muestras de cada uno de los cmdlets:
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>¿Preguntas?

Si tiene algún comentario, sugerencia o pregunta, envíelos mediante el [panel de la comunidad de administración de PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps).
