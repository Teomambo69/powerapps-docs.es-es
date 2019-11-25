---
title: Tareas de Build tools| Microsoft Docs
description: 'PowerApps build tools son una colección de tareas de compilación de Azure DevOps específicas de PowerApps que eliminan la necesidad de descargar manualmente herramientas y scripts para administrar el ciclo de vida de la aplicación de PowerApps. En este tema se describen las tareas que están disponibles. '
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: Dean-Haas
ms.service: powerapps
ms.topic: article
author: mikkelsen2000
ms.author: pemikkel
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d1455909aa8fef11a2bba4658edba81e40632ceb
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753048"
---
# <a name="build-tools-tasks"></a>Tareas de build tools

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Hay disponibles varios tipos de tareas de compilación que forman parte de PowerApps build tools para ayudar a automatizar el ciclo de vida de las aplicaciones mediante Azure DevOps.
  
## <a name="helper-task"></a>Tarea de ayuda

El instalador de herramientas de PowerApps debe ser la primera tarea en cualquier canalización de compilación y de versión. Esta tarea instala un conjunto de herramientas específicas de PowerApps que necesita el agente para ejecutar las tareas de compilación de PowerApps. Esta tarea no requiere ninguna configuración adicional.

## <a name="quality-check"></a>Comprobación de calidad

La tarea del comprobador de PowerApps ejecuta una comprobación de análisis estático en sus soluciones frente a un conjunto de reglas de prácticas recomendadas para identificar cualquier patrón problemático que pueda haber introducido accidentalmente al generar la solución.

| **Parámetros** | **Descripción** |
| --- | --- |
| Servicio del comprobador de PowerApps  |   Seleccione el extremo de servicio para el comprobador de PowerApps. El punto de conexión de servicio se define en **Conexiones del servicio** en **Configuración de proyecto**.  **NOTA:** El tipo de conexión de servicio que se debe usar para esta tarea específica solo es 'Comprobador de PowerApps', que es una conexión de entidades de servicio. Encontrará más información sobre cómo configurar entidades de servicio para poder usar la tarea [aquí](https://aka.ms/buildtoolsconnection).  |
| Ubicación del archivo a analizar  | Especifique si desea hacer referencia a un archivo local o hacer referencia a un archivo desde una dirección URL de Sas. 
| Archivos locales para analizar/Uri de Sas para archivo a analizar |  Especifique la ruta de acceso y el nombre de los archivos zip para analizar.   Pueden emplearse comodines. Por ejemplo, **\*.zip para todos los archivos zip en todas las subcarpetas. Puede elegir especificar los archivos directamente o hacer referencia a un archivo desde un uri de Sas.   |
|  Conjunto de reglas |   Especifique qué conjunto de reglas desea aplicar. Están disponibles los dos conjuntos de reglas siguientes:  **Comprobador de soluciones:** Es el mismo conjunto de reglas que se ejecuta desde el [Portal de creadores](https://make.powerapps.com/).    **AppSource:** Es el conjunto de reglas extendido que se usa para certificar una aplicación para poder publicarla en [AppSource](https://appsource.microsoft.com/).   |

### <a name="configure-service-connection-for-powerapps-checker"></a>Configurar la conexión de servicio para el comprobador de PowerApps

Para poder configurar la tarea del Comprobador de PowerApps, primero debe definir las entidades de servicio usadas para conectarse al servicio del comprobador de PowerApps. Encontrará más información sobre el servicio y la autenticación subyacentes del comprobador de PowerApps [aquí](https://docs.microsoft.com/powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module), sin embargo, los pasos indicados a continuación cubren todo lo que necesita para comenzar.

A continuación se indica cómo generar la aplicación Azure Active Directory (AAD) necesaria utilizando el [Módulo AzureAD PowerShell](https://docs.microsoft.com/powershell/module/azuread/?view=azureadps-2.0), agregar un secreto de cliente y después usarlo para configurar la cadena de conexión del comprobador de PowerApps.

> [!NOTE]
> Se requieren privilegios para crear entidades de servicio en un inquilino de AAD con licencia para PowerApps (P1/P2) o D365 CE para completar estos pasos. 

1. Abra un comando de PowerShell con derechos de administración.
![Ventana de comandos de Powershell](media/pscommand.png "PVentana de comandos de Powershell")
2. Ejecute el siguiente comando en PowerShell: *Install-Module -Name AzureAD*.
![Comando Install-Module](media/pscommand-install.png "IPantalla del comando Install-Module")
 
3.  Esto le pide que confíe en los módulos de PSGallery. Seleccione **A (Sí a todo)**.
1. Copie y pegue lo siguiente en el mensaje de PowerShell:

```powershell 
function New-PowerAppsCheckerAzureADApplication
{
    [CmdletBinding()]
    param(
        [Parameter(Mandatory = $true)]
        [Guid]
        $TenantId,
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string]
        $ApplicationDisplayName
    )
    # Using AzureAD as the RM modules, AzureRm.Resource and AzureRm.Profile, do not allow for setting RequiredResourceAccess
    Import-Module AzureAD | Out-Null
    try
    {
        Connect-AzureAD -TenantId $TenantId | Out-Null
    }
    catch [Microsoft.Open.Azure.AD.CommonLibrary.AadAuthenticationFailedException]
    {
        Write-Error "Received a failure result from the connecting to AzureAD, $($_.Exception.Message). Stopping."
        return
    }
    $graphSignInAndReadProfileRequirement = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
    $acc1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "e1fe6dd8-ba31-4d61-89e7-88639da4683d","Scope"
    $graphSignInAndReadProfileRequirement.ResourceAccess = $acc1
    $graphSignInAndReadProfileRequirement.ResourceAppId = "00000003-0000-0000-c000-000000000000"

    $powerAppsCheckerApiRequirement = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
    $acc1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "d533b86d-8f67-45f0-b8bb-c0cee8da0356","Scope"
    $acc2 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "640bd519-35de-4a25-994f-ae29551cc6d2","Scope"
    $powerAppsCheckerApiRequirement.ResourceAccess = $acc1,$acc2
    $powerAppsCheckerApiRequirement.ResourceAppId = "c9299480-c13a-49db-a7ae-cdfe54fe0313"

    $application = New-AzureADApplication -DisplayName $ApplicationDisplayName -PublicClient $true -ReplyUrls "urn:ietf:wg:oauth:2.0:oob" -RequiredResourceAccess $graphSignInAndReadProfileRequirement, $powerAppsCheckerApiRequirement
    if ($application -eq $null -or $application.AppId -eq $null)
    {
        Write-Error "Unable to create the application as requested."
    }
    else
    {
        Write-Host "The application $($application.AppId):$ApplicationDisplayName was created in the tenant, $TenantId. You may need to have an administrator grant consent. If running in a userless process, you will need to add a secret or certificate in which to authenticate." 
    }
    return $application
}

# Login to AAD as your user
Connect-AzureAD

# Establish your tenant ID
$tenantId = (Get-AzureADTenantDetail).ObjectId

# Create the AAD application registration using the AzureAD module and the sample script
$newApp = New-PowerAppsCheckerAzureADApplication -ApplicationDisplayName "PowerApps Checker Client" -TenantId $tenantId

# Next step => create a secret via the Admin portal, CLI, or PowerShell module.
 ```

5.  Cuando se le solicite, seleccione **A (Ejecutar siempre)**.
![Pantalla de comandos de Powershell](media/pscommand-always-run.png "PCaptura de pantalla de comandos de Powershell")
6. Un diálogo de inicio de sesión aparece. Inicie sesión como usuario. Tenga en cuenta que puede tenga que iniciar sesión dos veces en algunos casos.
7. Una vez completado el script, muestran el identificador y el inquilino de la aplicación en la ventana de comandos.
8. Continuación, inicie sesión en [Azure AD](https://portal.azure.com) para obtener el secretos de cliente.
9. En Microsoft Azure, seleccione **Azure Active Directory –> Registros de aplicaciones -> Cliente del comprobador de PowerApps**.
![Seleccionar cliente del comprobador en Azure](media/azure-select-checker.png "ACaptura de pantalla de Azure")
10. En el panel izquierdo de navegación, en **Administrar**, seleccione **Certificados y secretos**.
11. En la pantalla **Certificados y secretos**, en **Secretos de cliente**, seleccione **Nuevo secreto de cliente**. 
12. Escriba una descripción para el secreto de cliente, seleccione el valor de caducidad y después haga clic en **Agregar**.
13. Copie el valor del secreto de cliente que aparece en la siguiente pantalla. 
![Copiar secreto de cliente](media/client-secret-copy.png "ClCaptura de pantalla de secreto del cliente")
    > [!NOTE]
    > Esta es la única vez en la que se muestra el secreto de cliente
14. Abra la conexión de servicio del comprobador de PowerApps y pegue el secreto de cliente en el campo **Clave de entidad de servicio** y, a continuación haga clic en **Aceptar**.

Su conexión está lista ahora para que la utilice la [Tarea de compilación del comprobador de PowerApps](https://aka.ms/buildtoolsdoc). 

## <a name="solution-tasks"></a>Tareas de solución

Este conjunto de tareas realiza acciones con soluciones, e incluye las siguientes tareas:

### <a name="powerapps-import-solution"></a>Importar solución de PowerApps

La tarea Importar solución importa una solución en un entorno de destino.

| **Parámetros** | **Descripción** |
|----|----|
| Dirección URL de entorno de PowerApps  | El extremo de servicio del entorno de destino al que desea importar la solución. Por ejemplo, *https://powerappsbuildtools.crm.dynamics.com*.  Se pueden definir extremos de servicio en **Conexiones del servicio** en **Configuración de proyecto**. |
| Archivo de entrada de la solución  | La ruta de acceso y el nombre del archivo solution.zip para importar en el entorno de destino. Por ejemplo: *$(Build.ArtifactStagingDirectory)\$(SolutionName).zip*.
 |
> [!NOTE] 
> Las variables le ofrecen un modo adecuado para obtener bits clave de datos en diferentes partes de la canalización. Una lista completa de variables predefinidas está disponible [aquí](https://docs.microsoft.com/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml).

### <a name="powerapps-export-solution"></a>Exportar solución de PowerApps

La tarea Exportar solución exporta una solución desde un entorno de origen.

| **Parámetros** | **Descripción** |
|----------|-------------|
| Dirección URL de entorno de PowerApps | El punto de conexión de servicio para el entorno de origen desde el que desea exportar la solución.  Se define en **Conexiones del servicio ->Conexión del servicio genérico** en **Configuración del proyecto**. |
| Nombre de la solución | Nombre de la solución a exportar. Use siempre el ‘Nombre’ de la solución. No el 'Nombre para mostrar'. |
| Archivo de salida de la solución | La ruta de acceso y el nombre del archivo solution.zip para exportar al entorno de origen. Por ejemplo: *$(Build.ArtifactStagingDirectory)\$(SolutionName).zip*. |

> [!NOTE] 
> Las variables le ofrecen un modo adecuado para obtener bits clave de datos en diferentes partes de la canalización. Una lista completa de variables predefinidas está disponible aquí.
 
### <a name="powerapps-unpack-solution"></a>Desempaquetar solución de PowerApps

La tarea Desempaquetar solución toma un archivo de la solución comprimido y lo descompone en varios archivos XML y otros archivos de forma que estos archivos se puedan administrar más fácilmente mediante un sistema de control de origen.

| **Parámetros** | **Descripción** |
|------------|---------|
| Archivo de entrada de la solución | La ruta de acceso y el nombre del archivo solution.zip para desempaquetar. |
| Carpeta de destino para desempaquetar la solución | La ruta de acceso y la carpeta de destino a la que desea desempaquetar la solución. |
| Tipo de solución | El tipo de solución que desea desempaquetar:  **No administrada** (recomendado): *Únicamente la solución no administrada se debe desempaquetar en el informe*, **Administrada**, **Ambos** |


### <a name="powerapps-pack-solution"></a>Empaquetar solución de PowerApps

Empaqueta una solución representada en el control de origen en un archivo solution.zip que se puede importar en un entorno.

| **Parámetros** | **Descripción** |
|------------|---------|
| Archivo de salida de la solución | La ruta de acceso y el nombre del archivo solution.zip en las que empaquetar la solución. |
| Carpeta de origen de la solución a empaquetar | La ruta de acceso y la carpeta de origen de la solución a empaquetar. |
| Tipo de solución | El tipo de solución que desee empaquetar:  **No administrada** (recomendado): , **Administrada**, **Ambas** |

### <a name="publish-customizations"></a>Publicación de personalizaciones

La tarea Publicar personalizaciones publica todas las personalizaciones en un entorno.

| **Parámetros** | **Descripción** |
|------------|---------|
| Dirección URL de entorno de PowerApps | El punto de conexión de servicio del entorno en el que desea publicar personalizaciones.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |

### <a name="powerapps-set-solution-version"></a>Establecer versión de la solución de PowerApps 

La tarea Establecer versión de la solución actualiza la versión de una solución.

| **Parámetros** | **Descripción** |
|---------------------------|----|
| Dirección URL de entorno de PowerApps  | El punto de conexión de servicio del entorno en el que desea implementar el paquete.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |
| Nombre de la solución  | El nombre de la solución para la que desea establecer el número de versión |
| Número de versión de la solución | Número de versión para establecer, con el formato `major.minor.build.revision` por ejemplo. **1.0.0.1** |

### <a name="powerapps-deploy-package"></a>Implementar paquete de PowerApps

La tarea Implementar paquete implementa un paquete en un entorno. La implementación de un paquete en lugar de un único archivo de solución proporciona una opción para implementar varias soluciones, datos y código en un entorno.

| **Parámetros** | **Descripción** |
|---------------------------|----|
| Dirección URL de entorno de PowerApps  | El punto de conexión de servicio del entorno de destino que alberga la solución que desea actualizar.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |

## <a name="environment-management-tasks"></a>Tareas de administración de entornos

Las tareas de administración de entornos se usan para automatizar funciones de administración comunes de entorno, e incluyen las siguientes tareas:

### <a name="powerapps-create-environment"></a>Crear entorno de PowerApps

La tarea Crear entorno crea un entorno.

> [!NOTE]
> Un nuevo entorno solo puede ser aprovisionado si su licencia o capacidad permite la creación de entornos adicionales.

| **Parámetros** | **Descripción** |
|---------|-----------|
| Región de implementación | La región en la que se debe implementar el entorno. |
| Tipo de instancia | El tipo de instancia a implementar. Las opciones están Espacio aislado o Producción. |
| Idioma base | El idioma base en el entorno. |
| Nombre de dominio | Esta es la cadena específica del entorno que forma parte de la dirección URL. Por ejemplo, para un entorno con la siguiente dirección URL: *https://powerappsbuildtasks.crm.dynamics.com*, el nombre del dominio sería “powerappsbuildtasks”.  NOTA: Si está especificando un nombre de dominio que ya está en uso – la tarea anexará un valor numérico a la dirección URL, empezando por 0. Para el ejemplo anterior, la dirección URL podría convertirse en *https://powerappsbuildtasks0.crm.dynamics.com*. |
| Nombre descriptivo | El nombre descriptivo del entorno. |

### <a name="powerapps-delete-environment"></a>Eliminar entorno de PowerApps

La tarea Eliminar entorno elimina un entorno.

| **Parámetros** | **Descripción** |
|---------|-----------|
| Dirección URL de entorno de PowerApps  | El punto de conexión de servicio del entorno que desea eliminar.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |

### <a name="powerapps-backup-environment"></a>Copia de seguridad del entorno de PowerApps

La tarea Copia de seguridad del entorno realiza una copia de seguridad de un entorno. 

| **Parámetros** | **Descripción** |
|---------|-----------|
| Dirección URL de entorno de PowerApps  | El punto de conexión de servicio del entorno del que desea realizar copia de seguridad.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |
| Etiqueta de la copia de seguridad  | La etiqueta que desea asignar a la copia de seguridad.  |

### <a name="powerapps-copy-environment"></a>Copiar entorno de PowerApps

La tarea Copiar entorno copia un entorno a un entorno de destino. Dos tipos de copias están disponibles: completa y mínima. Completa copia datos y metadatos de la solución (personalizaciones), mientras que Mínima solo copia los metadatos de la solución pero no los datos reales.

> [!NOTE]
> Esta tarea solo está disponible para entornos D365 CE.  

| **Parámetros** | **Descripción** |
|---------|-----------|
| Dirección URL de entorno de origen de PowerApps  | El punto de conexión de servicio del entorno del que desea copiar.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |
| Dirección URL de entorno de destino de PowerApps  | El punto de conexión de servicio del entorno al que desea copiar.  Se define en **Conexiones del servicio** en **Configuración del proyecto**. |
