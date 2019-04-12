---
title: Herramientas de descarga desde NuGet (Common Data Service) | Microsoft Docs
description: 'Descargue el registro de complementos, la implementación de paquetes y otras herramientas principales de Nuget.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: feb3e634-7c60-46fd-8b92-3f5682b1570b
author: shmcarth
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="download-tools-from-nuget"></a>Descargar herramientas de NuGet 

Puede descargar herramientas de NuGet que se utilizan para programar mediante el script de powershell que se encuentra a continuación. Estas herramientas son:

|Herramienta|Paquetes NuGet|
|-|-|
|Herramienta de generación de código `CrmSvcUtil.exe`|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools)|
|Herramienta Configuration Migration `DataMigrationUtility.exe`|[Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf)|
|Package Deployer `PackageDeployer.exe`|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.WPF](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf)|
|Herramienta de registro de complementos `PluginRegistration.exe` |[Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool)|
|Herramienta SolutionPackager `SolutionPackager.exe`|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools)|

## <a name="download-tools-using-powershell"></a>Descargar herramientas mediante PowerShell

1. En el menú de inicio de Windows, escriba `Windows Powershell` y ábralo.
1. Desplácese a la carpeta donde desea instalar las herramientas. Por ejemplo, si desea instalarlas en una carpeta `devtools` en la unidad D, escriba `cd D:\devtools`.
1. Copie y pegue el siguiente script de PowerShell en la ventana de PowerShell y presione Intro.

    ```powershell
    $sourceNugetExe = "https://dist.nuget.org/win-x86-commandline/latest/nuget.exe"
    $targetNugetExe = ".\nuget.exe"
    Remove-Item .\Tools -Force -Recurse -ErrorAction Ignore
    Invoke-WebRequest $sourceNugetExe -OutFile $targetNugetExe
    Set-Alias nuget $targetNugetExe -Scope Global -Verbose
        
    ##
    ##Download Plugin Registration Tool
    ##
    ./nuget install Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool -O .\Tools
    md .\Tools\PluginRegistration
    $prtFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool.'}
    move .\Tools\$prtFolder\tools\*.* .\Tools\PluginRegistration
    Remove-Item .\Tools\$prtFolder -Force -Recurse
    
    ##
    ##Download CoreTools
    ##
    ./nuget install  Microsoft.CrmSdk.CoreTools -O .\Tools
    md .\Tools\CoreTools
    $coreToolsFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.CoreTools.'}
    move .\Tools\$coreToolsFolder\content\bin\coretools\*.* .\Tools\CoreTools
    Remove-Item .\Tools\$coreToolsFolder -Force -Recurse

    ##
    ##Download Configuration Migration
    ##
    ./nuget install  Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf -O .\Tools
    md .\Tools\ConfigurationMigration
    $configMigFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf.'}
    move .\Tools\$configMigFolder\tools\*.* .\Tools\ConfigurationMigration
    Remove-Item .\Tools\$configMigFolder -Force -Recurse
    
    ##
    ##Download Package Deployer 
    ##
    ./nuget install  Microsoft.CrmSdk.XrmTooling.PackageDeployment.WPF -O .\Tools
    md .\Tools\PackageDeployment
    $pdFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf.'}
    move .\Tools\$pdFolder\tools\*.* .\Tools\PackageDeployment
    Remove-Item .\Tools\$pdFolder -Force -Recurse

    ##
    ##Remove NuGet.exe
    ##
    Remove-Item nuget.exe    
    ```

1. Encontrará las herramientas en las siguientes carpetas:

- `[Your folder]\Tools\ConfigurationMigration`
- `[Your folder]\Tools\CoreTools`
- `[Your folder]\Tools\PackageDeployment`
- `[Your folder]\Tools\PluginRegistration`

Para obtener la versión más reciente de estas herramientas, repita estos pasos.

## <a name="see-also"></a>Vea también

[Herramientas del desarrollador](developer-tools.md)<br />
[Visual Studio y .NET Framework](org-service/visual-studio-dot-net-framework.md)<br />
[Crear clases de entidad en tiempo de compilación](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)<br />
[Crear extensiones para la herramienta de generación de código](org-service/extend-code-generation-tool.md)<br />
[Examinar los metadatos de la organización](browse-your-metadata.md)<br />
[Implemente los paquetes mediante Dynamics 365 Package Deployer y Windows PowerShell](/dynamics365/customer-engagement/admin/deploy-packages-using-package-deployer-windows-powershell)<br />
[Registro de un complemento](register-plug-in.md)<br />
