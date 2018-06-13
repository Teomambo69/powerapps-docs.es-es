---
title: Compatibilidad con PowerShell (versión preliminar) | Microsoft Docs
description: Descripción de los distintos cmdlets de PowerShell y un tutorial de cómo instalarlos y ejecutarlos.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 788f9ec1ce1ac8604606d2d2ad836a0cd12360d4
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34552999"
---
# <a name="powershell-support-for-powerapps-preview"></a>Compatibilidad con PowerShell para PowerApps (versión preliminar)
Con el lanzamiento de la versión preliminar de los cmdlets de PowerShell para creadores y administradores de aplicaciones, puede automatizar muchas de las tareas de supervisión y administración que hoy solo son posibles manualmente en [PowerApps ](https://web.powerapps.com) o en el [Centro de administración de PowerApps](https://admin.powerapps.com).

## <a name="installation"></a>Instalación
Para ejecutar los cmdlets de PowerShell para creadores de aplicaciones, siga estos pasos:

1. Descargue el [archivo de scripts de PowerShell](https://go.microsoft.com/fwlink/?linkid=872358).

2. Descomprima el archivo en una carpeta.

3. Abra una ventana de comandos de PowerShell (como administrador) en la misma carpeta.

4. Ejecute el siguiente comando de PowerShell de un solo uso (esto supone que nunca ha ejecutado comandos de PowerShell en la máquina actual):

    ```
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force
    ```

5. Importe los módulos necesarios con los siguientes comandos:

    ```
    Import-Module .\Microsoft.PowerApps.Administration.PowerShell.psm1 -Force
    Import-Module .\Microsoft.PowerApps.PowerShell.psm1 -Force
    ```

6.  Actualmente, hay un [problema conocido](https://powerusers.microsoft.com/t5/Administering-PowerApps/Getting-errors-when-I-try-to-import-the-preview-powerapps/td-p/109036) que también puede requerir que desbloquee los archivos de PowerShell manualmente con el comando siguiente:

    ```
    dir . | Unblock-File
    ```
7. Antes de acceder a cualquiera de los comandos, proporcione sus credenciales con el comando siguiente. Estas credenciales se actualizan durante un máximo de ~8 horas antes de que se le pida que inicie sesión de nuevo para continuar usando los cmdlets.

    ```
    Add-PowerAppsAccount
    ```


## <a name="powerapps-cmdlets-for-app-creators-preview"></a>Cmdlets de PowerApps para creadores de aplicaciones (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Los usuarios que tienen una licencia válida de PowerApps pueden hacer las operaciones en estos cmdlets, pero solo tendrán acceso a los recursos (por ejemplo, aplicaciones, flujos, etc.) que se crearon o compartieron con ellos.

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
> Use los comandos siguientes para entender la sintaxis y ver ejemplos de cada uno de los cmdlets:
>```
>Get-Help Get-PowerAppsEnvironment
>Get-Help Get-PowerAppsEnvironment -Examples
>Get-Help Get-PowerAppsEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>Cmdlets de PowerApps para administradores (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Para hacer las operaciones de administración en los cmdlets de administración, necesitará lo siguiente:

* Una licencia de PowerApps plan 2 de pago o una licencia de prueba PowerApps plan 2. También puede registrarse para obtener una licencia de evaluación gratuita de 30 días en [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Las licencias de evaluación gratuita se pueden renovar si han caducado.

* Permisos de [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o de [Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) si tiene que buscar en los recursos de otro usuario. (Tenga en cuenta que los administradores de entorno solo tienen acceso a los entornos y los recursos de entorno para los cuales tienen permisos).

### <a name="cmdlet-list"></a>Lista de cmdlets
| Propósito | Cmdlets
| --- | ---
| Leer y eliminar entornos | Get-AdminEnvironment <br> Remove-AdminEnvironment
| Leer, actualizar y eliminar los permisos de entorno <br><br> *Estos cmdlets solo funcionan para entornos que no tienen una base de datos de Common Data Service (CDS) for Apps.* | Get-AdminEnvironmentRoleAssignment <br> Set-AdminEnvironmentRoleAssignment <br> Remove-AdminEnvironmentRoleAssignment
| Leer y quitar aplicaciones de lienzo | Get-AdminApp <br> Remove-AdminApp
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-AdminAppRoleAssignment <br> Remove-AdminAppRoleAssignment <br> Set-AdminAppRoleAssignment <br> Set-AdminAppOwner
| Leer, actualizar y eliminar flujos | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow  <br> Remove-AdminFlowOwnerRole
| Leer y eliminar conexiones | Get-AdminConnection <br> Remove-AdminConnection
| Leer, actualizar y eliminar permisos de conexiones | Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br> Remove-AdminConnectionRoleAssignment
| Leer y eliminar conectores personalizados | Get-AdminConnector <br> Remove-AdminConnector
| Leer, actualizar y eliminar los permisos de conector personalizado | Get-AdminConnectorRoleAssignment <br> Set-AdminConnectorRoleAssignment <br> Remove-AdminConnectorRoleAssignment
| Leer la configuración de usuario de PowerApps de un usuario, la configuración de la aplicación de usuario y las notificaciones | Get-AdminPowerAppsUserDetails
| Leer y eliminar la configuración de Microsoft Flow de un usuario, que no es visible para el usuario, pero que admite la ejecución del flujo | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails
| Crear, leer, actualizar y eliminar las directivas de prevención de pérdida de datos de la organización | Get-AdminApiPolicy <br> Add-AdminApiPolicy <br> Remove-AdminApiPolicy <br> Set-AdminApiPolicy <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup

> [!NOTE]
> Use los comandos siguientes para entender la sintaxis y ver un ejemplo de cada uno de los cmdlets:
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>¿Preguntas?

Si tiene algún comentario, sugerencia o pregunta, publíquelos en el [panel de la comunidad de administración de PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps).
