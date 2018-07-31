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
ms.openlocfilehash: b6ee687fdfe6da8550d76193a7c9219aae5ae291
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218841"
---
# <a name="powershell-support-for-powerapps-preview"></a>Compatibilidad con PowerShell para PowerApps (versión preliminar)
Con el lanzamiento de la versión preliminar de los cmdlets de PowerShell para creadores y administradores de aplicaciones, puede automatizar muchas de las tareas de supervisión y administración que hoy solo son posibles manualmente en [PowerApps ](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) o en el [Centro de administración de PowerApps](https://admin.powerapps.com).

## <a name="installation"></a>Instalación
Para ejecutar los cmdlets de PowerShell para creadores de aplicaciones, siga estos pasos:

1. Descargue el [archivo de scripts de PowerShell](https://go.microsoft.com/fwlink/?linkid=2006349).

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
    # This call will open a prompt to collect the credentials (AAD account & password) that will be used by the commands
    Add-PowerAppsAccount
    ```

    ```
    # Here is how you can pass in credentials (avoiding opening a prompt)
    $pass = ConvertTo-SecureString "password" -AsPlainText -Force
    Add-PowerAppsAccount -Username foo@bar.com -Password $pass
    ```


## <a name="powerapps-cmdlets-for-app-creators-preview"></a>Cmdlets de PowerApps para creadores de aplicaciones (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Los usuarios que tienen una licencia válida de PowerApps pueden hacer las operaciones en estos cmdlets, pero solo tendrán acceso a los recursos (por ejemplo, aplicaciones, flujos, etc.) que se crearon o compartieron con ellos.

### <a name="cmdlet-list"></a>Lista de cmdlets
> [!NOTE]
> En la última versión hemos actualizado algunos de los nombres de función de cmdlet para poder agregar los prefijos adecuados y, de este modo, evitar colisiones. Consulte la tabla que hay a continuación para ver información general sobre lo que ha cambiado.

| Propósito | Cmdlet |
| --- | --- |
| Leer entornos | Get-PowerAppEnvironment *(anteriormente, Get-PowerAppsEnvironment)* <br> Get-FlowEnvironment
| Leer, actualizar y eliminar una aplicación de lienzo | Get-App <br> Remove-App <br> Publish-App <br> Set-AppDisplayName <br> Get-AppVersion <br> Restore-AppVersion
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-PowerAppRoleAssignment *(anteriormente, Get-AppRoleAssignment)* <br> Set-PowerAppRoleAssignment *(anteriormente, Set-AppRoleAssignment)* <br> Remove-PowerAppRoleAssignment *(anteriormente, Remove-AppRoleAssignment)*
| Leer, actualizar y eliminar un flujo | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow
| Leer, actualizar y eliminar permisos de flujo | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole
| Leer y responder a las aprobaciones de flujo | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest
| Leer y eliminar conexiones | Get-PowerAppConnection *(anteriormente, Get-Connection)* <br> Remove-PowerAppConnection *(anteriormente, Remove-Connection)*
| Leer, actualizar y eliminar permisos de conexiones | Get-PowerAppConnectionRoleAssignment *(anteriormente, Get-ConnectionRoleAssignment)* <br> Set-PowerAppConnectionRoleAssignment *(anteriormente, Set-ConnectionRoleAssignment)* <br> Remove-PowerAppConnectionRoleAssignment *(anteriormente, Remove-ConnectionRoleAssignment)*
| Leer y eliminar conectores | Get-PowerAppConnector *(anteriormente, Get-Connector)* <br> Remove-PowerAppConnector *(anteriormente, Remove-Connector)*
| Leer, actualizar y eliminar los permisos de conector personalizado | Get-PowerAppConnectorRoleAssignment *(anteriormente, Get-ConnectorRoleAssignment)* <br> Set-PowerAppConnectorRoleAssignment *(anteriormente, Set-ConnectorRoleAssignment)* <br> Remove-PowerAppConnectorRoleAssignment *(anteriormente, Remove-ConnectorRoleAssignment)*


> [!NOTE]
> Use los comandos siguientes para entender la sintaxis y ver ejemplos de cada uno de los cmdlets:
>```
>Get-Help Get-PowerAppEnvironment
>Get-Help Get-PowerAppEnvironment -Examples
>Get-Help Get-PowerAppEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>Cmdlets de PowerApps para administradores (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Para hacer las operaciones de administración en los cmdlets de administración, necesitará lo siguiente:

* Una licencia de PowerApps plan 2 de pago o una licencia de prueba PowerApps plan 2. También puede registrarse para obtener una licencia de evaluación gratuita de 30 días en [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Las licencias de evaluación gratuita se pueden renovar si han caducado.

* Permisos de [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o de [Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) si tiene que buscar en los recursos de otro usuario. (Tenga en cuenta que los administradores de entorno solo tienen acceso a los entornos y los recursos de entorno para los cuales tienen permisos).

### <a name="cmdlet-list"></a>Lista de cmdlets
> [!NOTE]
> En la última versión hemos actualizado algunos de los nombres de función de cmdlet para poder agregar los prefijos adecuados y, de este modo, evitar colisiones. Consulte la tabla que hay a continuación para ver información general sobre lo que ha cambiado.

| Propósito | Cmdlets
| --- | ---
| Lectura, actualización y eliminación de entornos y bases de datos de Common Data Service for Apps | New-AdminPowerAppEnvironment **\*Nuevo\*** <br> Set-AdminPowerAppEnvironmentDisplayName **\*Nuevo\*** <br> Get-AdminPowerAppEnvironment *(anteriormente, Get-AdminEnvironment)* <br> Remove-AdminPowerAppEnvironment *(anteriormente, Remove-AdminEnvironment)* <br> New-AdminPowerAppCdsDatabase **\*Nuevo\*** <br> Get-AdminPowerAppCdsDatabaseLanguages **\*Nuevo\*** <br> Get-AdminPowerAppCdsDatabaseCurrencies **\*Nuevo\*** <br> Get-AdminPowerAppEnvironmentLocations **\*Nuevo\***
| Leer, actualizar y eliminar los permisos de entorno <br><br> *Estos cmdlets ahora solo funcionan para entornos que no tengan ninguna base de datos de Common Data Service (CDS) for Apps.* | Get-AdminPowerAppEnvironmentRoleAssignment *(anteriormente, Get-AdminEnvironmentRoleAssignment)* <br> Set-AdminPowerAppEnvironmentRoleAssignment *(anteriormente, Set-AdminEnvironmentRoleAssignment)* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *(anteriormente, Remove-AdminEnvironmentRoleAssignment)*
| Lectura, actualización y eliminación de aplicaciones de lienzo | Get-AdminPowerApp *(anteriormente, Get-AdminApp)* <br> Remove-AdminPowerApp *(anteriormente, Remove-AdminApp)* <br> Get-AdminPowerAppConnectionReferences **\*Nuevo\*** <br> Set-AdminPowerAppAsFeatured **\*Nuevo\*** <br> Clear-AdminPowerAppAsFeatured **\*Nuevo\*** <br> Set-AdminPowerAppAsHero **\*Nuevo\*** <br> Clear-AdminPowerAppAsHero **\*Nuevo\*** <br> Set-AdminPowerAppApisToBypassConsent **\*Nuevo\*** <br> Clear-AdminPowerAppApisToBypassConsent **\*Nuevo\***
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-AdminPowerAppRoleAssignment *(anteriormente, Get-AdminAppRoleAssignment)* <br> Remove-AdminPowerAppRoleAssignment *(anteriormente, Remove-AdminAppRoleAssignment)* <br> Set-AdminPowerAppRoleAssignment *(anteriormente, Set-AdminAppRoleAssignment)* <br> Set-AdminPowerAppOwner *(anteriormente, Set-AdminAppOwner)*
| Leer, actualizar y eliminar flujos | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals **\*Nuevo\***
| Leer, actualizar y eliminar permisos de flujo | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole
| Leer y eliminar conexiones | Get-AdminPowerAppConnection *(anteriormente, Get-AdminConnection)* <br> Remove-AdminPowerAppConnection *(anteriormente, Remove-AdminConnection)*
| Leer, actualizar y eliminar permisos de conexiones | Get-AdminPowerAppConnectionRoleAssignment *(anteriormente, Get-AdminConnectionRoleAssignment)* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *(anteriormente, Set-AdminConnectionRoleAssignment)* <br> Remove-AdminPowerAppConnectionRoleAssignment *(anteriormente, Remove-AdminConnectionRoleAssignment)*
| Leer y eliminar conectores personalizados | Get-AdminPowerAppConnector *(anteriormente, Get-AdminConnector)* <br> Remove-AdminPowerAppConnector *(anteriormente, Remove-AdminConnector)*
| Leer, actualizar y eliminar los permisos de conector personalizado | Get-AdminPowerAppConnectorRoleAssignment *(anteriormente, Get-AdminConnectorRoleAssignment)*<br> Set-AdminPowerAppConnectorRoleAssignment *(anteriormente, Set-AdminConnectorRoleAssignment)* <br> Remove-AdminPowerAppConnectorRoleAssignment *(anteriormente, Remove-AdminConnectorRoleAssignment)*
| Leer la configuración de usuario de PowerApps de un usuario, la configuración de la aplicación de usuario y las notificaciones | Get-AdminPowerAppsUserDetails
| Leer y eliminar la configuración de Microsoft Flow de un usuario, que no es visible para el usuario, pero que admite la ejecución del flujo | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails
| Crear, leer, actualizar y eliminar las directivas de prevención de pérdida de datos de la organización | Get-AdminDlpPolicy *(anteriormente, Get-AdminApiPolicy)* <br> Add-AdminDlpPolicy *(anteriormente, Add-AdminApiPolicy)* <br> Remove-AdminDlpPolicy *(anteriormente, Remove-AdminApiPolicy)* <br> Set-AdminDlpPolicy *(anteriormente, Set-AdminApiPolicy)* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup

> [!NOTE]
> Use los comandos siguientes para entender la sintaxis y ver un ejemplo de cada uno de los cmdlets:
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>¿Preguntas?

Si tiene algún comentario, sugerencia o pregunta, publíquelos en el [panel de la comunidad de administración de PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps).
