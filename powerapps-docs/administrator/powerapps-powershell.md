---
title: Compatibilidad con PowerShell (versión preliminar) | Microsoft Docs
description: Descripción de los distintos cmdlets de PowerShell y un tutorial de cómo instalarlos y ejecutarlos.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 01/18/2019
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 0152296adbe01abae2b831576c312a43d1f2a2b8
ms.sourcegitcommit: 3ce7c17f90f87756a072210c8abfbd93733a6d4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397776"
---
# <a name="powershell-support-for-powerapps-preview"></a>Compatibilidad con PowerShell para PowerApps (versión preliminar)
Con el lanzamiento de la versión preliminar de los cmdlets de PowerShell para creadores y administradores de aplicaciones, puede automatizar muchas de las tareas de supervisión y administración que hoy solo son posibles manualmente en [PowerApps ](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) o en el [Centro de administración de PowerApps](https://admin.powerapps.com).

## <a name="cmdlets"></a>Cmdlets
Los [cmdlets](https://docs.microsoft.com/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet) son funciones escritas en el lenguaje de script de PowerShell que ejecutan comandos en el entorno de Windows PowerShell. La ejecución de estos cmdlets de PowerApps le permitirá interactuar con la plataforma de aplicaciones empresariales sin tener que pasar por el portal de administración en un explorador web. Estos cmdlets se pueden combinar con otras funciones de PowerShell para escribir scripts complejos que pueden optimizar el flujo de trabajo. Tenga en cuenta que puede usar los cmdlets aunque no sea un administrador del inquilino, pero estará limitado a los recursos de los que disponga. Los cmdlets que comienzan con la palabra "Admin" están diseñados para usarse con una cuenta de usuario administrativo.

Los cmdlets están disponibles en Galería de PowerShell como dos módulos independientes: 
- [Administrador](https://www.powershellgallery.com/packages/Microsoft.PowerApps.Administration.PowerShell/2.0.1)
- [Creador](https://www.powershellgallery.com/packages/Microsoft.PowerApps.PowerShell/1.0.1) 

## <a name="installation"></a>Instalación
Para ejecutar los cmdlets de PowerShell para creadores de aplicaciones, siga estos pasos:

1. Ejecute PowerShell como administrador.

   > [!div class="mx-imgBorder"] 
   > ![Ejecución de PowerShell como administrador](media/open-powershell-as-admin75.png "Run PowerShell as an administrator")

2. Importe los módulos necesarios con los siguientes comandos:

    ```
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    ```
3. Si se le pide que acepte el cambio del valor *InstallationPolicy* del repositorio, escriba "A" y presione **Entrar** en cada módulo para aceptar [A] Sí a todo.

   ![Aceptación del valor de InstallationPolicy](media/accept-installationpolicy-value75.png "Accept InstallationPolicy value")

4. Antes de acceder a cualquiera de los comandos, tiene la opción de proporcionar sus credenciales mediante el comando siguiente. Estas credenciales se actualizan durante un máximo de alrededor de 8 horas antes de que se le pida que vuelva a iniciar sesión para seguir usando los cmdlets.

    ```
    # This call opens prompt to collect credentials (Azure Active Directory account and password) used by the commands 
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

### <a name="cmdlet-list---maker-cmdlets"></a>Lista de cmdlets: cmdlets de creador
> [!NOTE]
> En la última versión hemos actualizado algunos de los nombres de función de cmdlet para poder agregar los prefijos adecuados y, de este modo, evitar colisiones. Consulte la tabla que hay a continuación para ver información general sobre lo que ha cambiado.

| Propósito | Cmdlet |
| --- | --- |
| Leer entornos | Get-PowerAppEnvironment *(anteriormente, Get-PowerAppsEnvironment)* <br> Get-FlowEnvironment |
| Leer, actualizar y eliminar una aplicación de lienzo | Get-PowerApp *(anteriormente Get-App)* <br> Remove-PowerApp *(anteriormente Remove-App)* <br> Publish-PowerApp *(anteriormente Publish-App)* <br> Set-AppDisplayName *(anteriormente Set-PowerAppDisplayName)*<br> Get-PowerAppVersion *(anteriormente Get-AppVersion)* <br> Restore-PowerAppVersion *(anteriormente Restore-AppVersion)* |
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-PowerAppRoleAssignment *(anteriormente, Get-AppRoleAssignment)* <br> Set-PowerAppRoleAssignment *(anteriormente, Set-AppRoleAssignment)* <br> Remove-PowerAppRoleAssignment *(anteriormente, Remove-AppRoleAssignment)* |
| Leer, actualizar y eliminar un flujo | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow |
| Leer, actualizar y eliminar permisos de flujo | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole |
| Leer y responder a las aprobaciones de flujo | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest |
| Leer y eliminar conexiones | Get-PowerAppConnection *(anteriormente, Get-Connection)* <br> Remove-PowerAppConnection *(anteriormente, Remove-Connection)* |
| Leer, actualizar y eliminar permisos de conexiones | Get-PowerAppConnectionRoleAssignment *(anteriormente, Get-ConnectionRoleAssignment)* <br> Set-PowerAppConnectionRoleAssignment *(anteriormente, Set-ConnectionRoleAssignment)* <br> Remove-PowerAppConnectionRoleAssignment *(anteriormente, Remove-ConnectionRoleAssignment)* |
| Leer y eliminar conectores | Get-PowerAppConnector *(anteriormente, Get-Connector)* <br> Remove-PowerAppConnector *(anteriormente, Remove-Connector)* |
| Leer, actualizar y eliminar los permisos de conector personalizado | Get-PowerAppConnectorRoleAssignment *(anteriormente, Get-ConnectorRoleAssignment)* <br> Set-PowerAppConnectorRoleAssignment *(anteriormente, Set-ConnectorRoleAssignment)* <br> Remove-PowerAppConnectorRoleAssignment *(anteriormente, Remove-ConnectorRoleAssignment)* |

## <a name="powerapps-cmdlets-for-administrators-preview"></a>Cmdlets de PowerApps para administradores (versión preliminar)

### <a name="prerequisite"></a>Requisito previo
Para hacer las operaciones de administración en los cmdlets de administración, necesitará lo siguiente:

* Una licencia de PowerApps plan 2 de pago o una licencia de prueba PowerApps plan 2. También puede registrarse para obtener una licencia de evaluación gratuita de 30 días en [http://web.powerapps.com/trial](http://web.powerapps.com/trial). Las licencias de evaluación gratuita se pueden renovar si han caducado.

* Permisos de [administrador global de Office 365](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) o de [Azure Active Directory ](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) si tiene que buscar en los recursos de otro usuario. (Tenga en cuenta que los administradores de entorno solo tienen acceso a los entornos y los recursos de entorno para los cuales tienen permisos).

### <a name="cmdlet-list---admin-cmdlets"></a>Lista de cmdlets: cmdlets de administrador

| Propósito | Cmdlets
| --- | ---
| Lectura, actualización y eliminación de entornos y bases de datos de Common Data Service for Apps | New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> Get-AdminPowerAppEnvironment *(anteriormente, Get-AdminEnvironment)* <br> Remove-AdminPowerAppEnvironment *(anteriormente, Remove-AdminEnvironment)* <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations |
| Eliminar la base de datos de CDS | Remove-LegacyCDSDatabase **\*Novedad\*** | 
| Leer, actualizar y eliminar los permisos de entorno <br><br> *Estos cmdlets ahora solo funcionan para entornos que no tengan ninguna base de datos de Common Data Service (CDS) for Apps.* | Get-AdminPowerAppEnvironmentRoleAssignment *(anteriormente, Get-AdminEnvironmentRoleAssignment)* <br> Set-AdminPowerAppEnvironmentRoleAssignment *(anteriormente, Set-AdminEnvironmentRoleAssignment)* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *(anteriormente, Remove-AdminEnvironmentRoleAssignment)* |
| Lectura, actualización y eliminación de aplicaciones de lienzo | Get-AdminPowerApp *(anteriormente, Get-AdminApp)* <br> Remove-AdminPowerApp *(anteriormente, Remove-AdminApp)* <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent |
| Leer, actualizar y eliminar permisos de aplicaciones de lienzo | Get-AdminPowerAppRoleAssignment *(anteriormente, Get-AdminAppRoleAssignment)* <br> Remove-AdminPowerAppRoleAssignment *(anteriormente, Remove-AdminAppRoleAssignment)* <br> Set-AdminPowerAppRoleAssignment *(anteriormente, Set-AdminAppRoleAssignment)* <br> Set-AdminPowerAppOwner *(anteriormente, Set-AdminAppOwner)* |
| Leer, actualizar y eliminar flujos | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals |
| Leer, actualizar y eliminar permisos de flujo | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole |
| Leer y eliminar conexiones | Get-AdminPowerAppConnection *(anteriormente, Get-AdminConnection)* <br> Remove-AdminPowerAppConnection *(anteriormente, Remove-AdminConnection)* |
| Leer, actualizar y eliminar permisos de conexiones | Get-AdminPowerAppConnectionRoleAssignment *(anteriormente, Get-AdminConnectionRoleAssignment)* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *(anteriormente, Set-AdminConnectionRoleAssignment)* <br> Remove-AdminPowerAppConnectionRoleAssignment *(anteriormente, Remove-AdminConnectionRoleAssignment)* |
| Leer y eliminar conectores personalizados | Get-AdminPowerAppConnector *(anteriormente, Get-AdminConnector)* <br> Remove-AdminPowerAppConnector *(anteriormente, Remove-AdminConnector)* |
| Leer, actualizar y eliminar los permisos de conector personalizado | Get-AdminPowerAppConnectorRoleAssignment *(anteriormente, Get-AdminConnectorRoleAssignment)*<br> Set-AdminPowerAppConnectorRoleAssignment *(anteriormente, Set-AdminConnectorRoleAssignment)* <br> Remove-AdminPowerAppConnectorRoleAssignment *(anteriormente, Remove-AdminConnectorRoleAssignment)* |
| Leer la configuración de usuario de PowerApps de un usuario, la configuración de la aplicación de usuario y las notificaciones | Get-AdminPowerAppsUserDetails |
| Leer y eliminar la configuración de Microsoft Flow de un usuario, que no es visible para el usuario, pero que admite la ejecución del flujo | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails |
| Crear, leer, actualizar y eliminar las directivas de prevención de pérdida de datos de la organización | Get-AdminDlpPolicy *(anteriormente, Get-AdminApiPolicy)* <br> New-AdminDlpPolicy *(anteriormente Add-AdminApiPolicy)* <br> Remove-AdminDlpPolicy *(anteriormente, Remove-AdminApiPolicy)* <br> Set-AdminDlpPolicy *(anteriormente, Set-AdminApiPolicy)* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup <br/>Add-CustomConnectorToPolicy<br/> Remove-CustomConnectorFromPolicy|

## <a name="tips"></a>Recomendaciones

- Use Get-Help "Nombre_del_cmdlet" para obtener una lista de ejemplos.

     ![Comando Get-Help](media/get-help-cmdlet.png "Get-Help command")

- Para desplazarse por las opciones posibles para las etiquetas de entrada, haga clic en el tabulador después de escribir el carácter de guion (-), después del nombre del cmdlet.

Comandos de ejemplo:

```
Get-Help Get-AdminPowerAppEnvironment
Get-Help Get-AdminPowerAppEnvironment -Examples
Get-Help Get-AdminPowerAppEnvironment -Detailed
```

## <a name="operation-examples"></a>Ejemplos de operaciones

A continuación se muestran algunos escenarios comunes en los que se muestra cómo usar los cmdlets de PowerApps nuevos y existentes.

- [Comandos de entornos](#environments-commands)
- [Comandos de PowerApps](#powerapps-commands)
- [Comandos de flujo](#flow-commands)
- [Comandos de conexión de API](#api-connection-commands)
- [Comandos de directiva de prevención de pérdida de datos (DLP)](#data-loss-prevention-dlp-policy-commands)

### <a name="environments-commands"></a>Comandos de entornos

Use estos comandos para obtener información sobre los entornos del inquilino y actualizarlos.

#### <a name="display-a-list-of-all-environments"></a>Mostrar una lista de todos los entornos

```
Get-AdminPowerAppEnvironment
```

Devuelve una lista de todos los entornos del inquilino, con detalles de cada uno de ellos (por ejemplo, el nombre del entorno (GUID), el nombre para mostrar, la ubicación, el creador, etc.).

#### <a name="display-details-of-your-default-environment"></a>Mostrar los detalles del entorno predeterminado

```
Get-AdminPowerAppEnvironment –Default
```

Devuelve los detalles solo del entorno predeterminado del inquilino.

#### <a name="display-details-of-a-specific-environment"></a>Mostrar los detalles de un entorno específico

```
Get-AdminPowerAppEnvironment –EnvironmentName ‘EnvironmentName’
```

**Nota**: El campo *NombreDelEntorno* es un identificador único, distinto de *NombreParaMostrar* (vea los dos primeros campos de la salida en la imagen siguiente).

![Comando Get-AdminEnvironment](media/get-adminenvironment.png "Get-AdminEnvironment command")

### <a name="powerapps-commands"></a>Comandos de PowerApps

Estas operaciones se usan para leer y modificar datos de PowerApps en el inquilino.

#### <a name="display-a-list-of-all-powerapps"></a>Mostrar una lista de todas las aplicaciones PowerApps

```
Get-AdminPowerApp
```

Devuelve una lista de todas las aplicaciones PowerApps en el inquilino, con detalles de cada una (p. ej., nombre de la aplicación (GUID), nombre para mostrar, creador, etc.).

#### <a name="display-a-list-of-all-powerapps-that-match-the-input-display-name"></a>Mostrar una lista de todas las aplicaciones PowerApps que coinciden con el nombre para mostrar de entrada

```
Get-AdminPowerApp 'DisplayName'
```

Devuelve una lista de todas las aplicaciones PowerApps en el inquilino que coinciden con el nombre para mostrar. 

**Nota**: Use caracteres de comillas (") alrededor de los valores de entrada que contengan espacios.

#### <a name="feature-an-application"></a>Destacar una aplicación

```
Set-AdminPowerAppAsFeatured –AppName 'AppName'
```

Las aplicaciones destacadas se agrupan y se insertan en la parte superior de la lista en el reproductor móvil de PowerApps.

**Nota**: Al igual que en los entornos, el campo *NombreDeLaAplicación* es un identificador único, distinto de *NombreParaMostrar*. Si quiere realizar operaciones en función del nombre para mostrar, algunas funciones permiten usar la canalización (vea la función siguiente).

#### <a name="make-an-application-a-hero-app-using-the-pipeline"></a>Convertir una aplicación en prominente, mediante la canalización

```
Get-AdminPowerApp 'DisplayName' | Set-AdminPowerAppAsHero
```

Una aplicación prominente aparecerá en la parte superior de la lista en el reproductor móvil de PowerApps. Solo puede haber una aplicación prominente.

La canalización (que se representa como el carácter "|" entre dos cmdlets) toma la salida del primer cmdlet y la pasa como el valor de entrada del segundo, suponiendo que la función se haya escrito para dar cabida a la característica de canalización.

**Nota**: Una aplicación ya debe ser una aplicación destacada antes de cambiarla a prominente.

#### <a name="display-the-number-of-apps-each-user-owns"></a>Mostrar el número de aplicaciones que posee cada usuario

```
Get-AdminPowerApp | Select –ExpandProperty Owner | Select –ExpandProperty displayname | Group
```

Puede combinar funciones nativas de PowerShell con los cmdlets de PowerApps para manipular los datos aún más. Aquí se usa la función Select para aislar el atributo Owner (un objeto) del objeto Get-AdminApp. Después, se aísla el nombre del objeto propietario mediante la canalización de esa salida a otra función Select. Por último, al pasar la salida de la segunda función Select a la función Group, se devuelve una tabla en la que se incluye un recuento del número de aplicaciones de cada propietario.

![Comando Get-AdminPowerApp](media/get-adminpowerapp.png "Get-AdminPowerApp command")

#### <a name="display-the-number-of-apps-in-each-environment"></a>Mostrar el número de aplicaciones en cada entorno

```
Get-AdminPowerApp | Select -ExpandProperty EnvironmentName | Group | %{ New-Object -TypeName PSObject -Property @{ DisplayName = (Get-AdminPowerAppEnvironment -EnvironmentName $_.Name | Select -ExpandProperty displayName); Count = $_.Count } }
```

![Comando Get-AdminPowerApp](media/get-adminpowerapp-environment.png "Get-AdminPowerApp command")

#### <a name="download-powerapps-user-details"></a>Descargar detalles de usuario de PowerApps

```
Get-AdminPowerAppsUserDetails -OutputFilePath '.\adminUserDetails.txt' –UserPrincipalName ‘admin@bappartners.onmicrosoft.com’
```

El comando anterior almacena los detalles de usuario de PowerApps (información de uso básica sobre el usuario de entrada a través de su nombre principal de usuario) en el archivo de texto especificado. Creará un archivo si no existe ninguno con ese nombre, y sobrescribirá el archivo de texto si ya existe.

#### <a name="set-logged-in-user-as-the-owner-of-a-powerapp"></a>Establecer el usuario conectado como propietario de una aplicación de PowerApp

```
Set-AdminPowerAppOwner –AppName 'AppName' -AppOwner $Global:currentSession.userId –EnvironmentName 'EnvironmentName'
```

Cambia el rol de propietario de una aplicación de PowerApps al usuario actual y reemplaza el propietario original como un tipo de rol "puede ver".

**Nota**: Los campos NombreDeLaAplicación y NombreDelEntorno son los identificadores únicos globales (GUID), no los nombres para mostrar.

### <a name="flow-commands"></a>Comandos de flujo

Use estos comandos para ver y modificar datos relacionados con Microsoft Flow.

#### <a name="display-all-flows"></a>Mostrar todos los flujos

```
Get-AdminFlow
```

Devuelve una lista de todos los flujos en el inquilino.

#### <a name="display-flow-owner-role-details"></a>Mostrar detalles del rol de propietario de flujo

```
Get-AdminFlowOwnerRole –EnvironmentName 'EnvironmentName' –FlowName ‘FlowName’
```

Devuelve los detalles del propietario del flujo especificado.

**Nota**: Como sucede en los *entornos* y *PowerApps*, *NombreDelFlujo* es el identificador único (GUID), que es diferente del nombre para mostrar del flujo.

#### <a name="display-flow-user-details"></a>Mostrar detalles del flujo de usuario

```
Get-AdminFlowUserDetails –UserId $Global:currentSession.userId
```

Devuelve los detalles del usuario con respecto al uso del flujo. En este ejemplo, se usa como entrada el identificador del usuario actual que ha iniciado la sesión de PowerShell.

#### <a name="remove-flow-user-details"></a>Quitar los detalles del flujo de usuario

```
Remove-AdminFlowUserDetails –UserId 'UserId'
```

Elimina por completo los detalles de un usuario de flujo de la base de datos de Microsoft. Se deben eliminar todos los flujos de los que sea propietario el usuario de entrada antes de poder quitar los detalles del flujo de usuario.

**Nota**: El campo UserId es el identificador de objeto del registro de Azure Active Directory del usuario, que se puede encontrar en [Azure Portal](https://portal.azure.com), en **Azure Active Directory** > **Usuarios** > **Perfil** > **Id. de objeto**. Debe ser un administrador para acceder a estos datos desde aquí.

#### <a name="export-all-flows-to-a-csv-file"></a>Exportar todos los flujos a un archivo CSV

```
Get-AdminFlow | Export-Csv -Path '.\FlowExport.csv'
```

Exporta todos los flujos del inquilino a un archivo .csv de vista tabular.

### <a name="api-connection-commands"></a>Comandos de conexión de API

Puede ver y administrar las conexiones de API en el inquilino.

#### <a name="display-all-native-connections-in-your-default-environment"></a>Mostrar todas las conexiones nativas en el entorno predeterminado

```
Get-AdminPowerAppEnvironment -Default | Get-AdminConnection
```

Muestra una lista de todas las conexiones de API que tiene en el entorno predeterminado. Las conexiones nativas se encuentran en la pestaña **Datos** > **Conexiones** del portal de creadores.

#### <a name="display-all-custom-connectors-in-the-tenant"></a>Mostrar todos los conectores personalizados en el inquilino

```
Get-AdminPowerAppConnector
```

Devuelve una lista de todos los detalles del conector personalizado en el inquilino.

### <a name="data-loss-prevention-dlp-policy-commands"></a>Comandos de directiva de prevención de pérdida de datos (DLP)

Estos cmdlets controlarán las directivas DLP en el inquilino.

#### <a name="display-all-policies"></a>Mostrar todas las directivas

```
Get-AdminDlpPolicy
```

Devuelve una lista de todas las directivas.

#### <a name="display-a-filtered-list-of-policies"></a>Mostrar una lista filtrada de las directivas

```
Get-AdminDlpPolicy 'DisplayName'
```

Usa el nombre para mostrar para filtrar las directivas

#### <a name="display-all-business-data-only-api-connectors-in-a-policy"></a>Mostrar todos los conectores de API "Solo datos empresariales" de una directiva

```
Get-AdminDlpPolicy 'PolicyName' | Select –ExpandProperty BusinessDataGroup
```

Enumera las conexiones de API que se encuentran en el campo *Solo datos empresariales*(o *BusinessDataGroup*) de una directiva de entrada.

#### <a name="add-a-connector-to-the-business-data-only-group"></a>Agregar un conector al grupo "Solo datos empresariales"

```
Add-ConnectorToBusinessDataGroup -PolicyName 'PolicyName' –ConnectorName 'ConnectorName'
```

Agrega un conector al grupo "Solo datos empresariales" de una directiva DLP determinada. Aquí puede ver la lista de conectores por *NombreParaMostrar* y *NombreDelConector* (que se usa como entrada).

## <a name="version-history"></a>Historial de versiones
| Versión | Date | Actualizaciones |
| --- | --- | --- |
| 1.0 | 23/04/2018 | <ol> <li> Lanzamiento inicial de los cmdlets de PowerApps para creadores de aplicaciones (versión preliminar), incluidos los cmdlets de administración de entornos, aplicaciones, flujos, aprobaciones de flujo, conexiones y conectores personalizados </li> <li> Lanzamiento inicial de los cmdlets de PowerApps para administradores (versión preliminar) incluidos los cmdlets administrativos de entornos, aplicaciones y flujos </li></ol>|
| 2.0 | 24/05/2018 | <ol> <li> Correcciones de errores menores en los cmdlets de creadores y de administradores de aplicaciones </li> <li> Se agregan los nuevos cmdlets administrativos siguientes: <br> Get-AdminConnection <br> Remove-AdminConnection <br> Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br>Remove-AdminConnectionRoleAssignment <br>Get-AdminConnector  <br>Remove-AdminConnector <br>Set-AdminConnectorRoleAssignment  <br>Get-AdminConnectorRoleAssignment  <br>Remove-AdminConnectorRoleAssignment <br>Get-AdminPowerAppsUserDetails <br>Get-AdminFlowUserDetails <br>Remove-AdminFlowUserDetails <br>Get-AdminApiPolicy  <br>Add-AdminApiPolicy <br>Remove-AdminApiPolicy <br>Set-AdminApiPolicy <br>Add-ConnectorToBusinessDataGroup  <br>Remove-ConnectorFromBusinessDataGroup </li> </ol>
| 3.0 | 30/07/2018 | <ol> <li> Se agrega la posibilidad de paso de credenciales al cmdlet Add-PowerAppsAccount (para habilitar el scripting periódico). </li> <li>  Correcciones de errores menores en los cmdlets de creadores y de administradores de aplicaciones </li> <li> Se agrega el prefijo "PowerApp" o "Flow" a cada cmdlet para creadores de aplicaciones. </li> <li>  Se agrega el prefijo "AdminPowerApp" o "AdminFlow" a cada cmdlet para administradores. </li> <li> Se agregan los nuevos cmdlets administrativos siguientes: <br> New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent <br> Remove-AdminFlowApprovals </li></ol>
| 4.0 | 15/08/2018 | Se agrega un parámetro opcional al cmdlet New-AdminPowerAppCdsDatabase para realizar la función sincrónica de forma predeterminada (es decir, no se devolverá hasta que se haya aprovisionado correctamente la base de datos).
| 5.0 | 24/08/2018 | Se ha corregido un problema por el que los cmdlets de administradores de Flow no devolvían datos en algunos casos en función de la configuración de seguridad.
| 6.0 | 09/01/2019 | <ol><li>Ahora los cmdlets están disponibles en la Galería de PowerShell como dos módulos independientes: Administrador y Creador.</li> <li>Se ha agregado un cmdlet administrativo: Remove-LegacyCDSDatabase</li><li> Se han agregado ejemplos de operaciones</li><li>Se ha agregado la capacidad de administrar conectores HTTP y personalizados en la prevención de pérdida de datos (DLP)</li></ol>|

## <a name="questions"></a>¿Preguntas?

Si tiene algún comentario, sugerencia o pregunta, publíquelos en el [panel de la comunidad de administración de PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps).
