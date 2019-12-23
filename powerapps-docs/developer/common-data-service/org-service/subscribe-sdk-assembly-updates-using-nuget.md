---
title: Suscripción a actualizaciones de ensamblados de SDK mediante NuGet (Common Data Service) | Microsoft Docs
description: Los ensamblados de SDK .NET y algunas herramientas de línea de comandos están disponibles a través de un sitio web de distribución de software llamado nuget.org. El uso de paquetes NuGet en su proyecto de aplicación le permite mantener el proyecto actualizado con las últimas versiones de los ensamblados y herramientas de SDK.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 15790d37a187eafa73a5dc837aa090833f3d95ee
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2859993"
---
# <a name="subscribe-to-sdk-assembly-updates-using-nuget"></a>Suscribirse a las actualizaciones de ensamblados de SDK mediante NuGet

Los ensamblados de SDK .NET y algunas herramientas de línea de comandos están disponibles a través de un sitio web de distribución de software llamado [nuget.org](https://www.nuget.org). El uso de paquetes NuGet en su proyecto de aplicación le permite mantener el proyecto actualizado con las últimas versiones de los ensamblados y herramientas de SDK. Visual Studio ha admitido esta capacidad desde la versión 2010 y hay incluso un cliente independiente NuGet para los desarrolladores que no desarrollan en Visual Studio. Otra ventaja de usar paquetes NuGet en los proyectos es que las referencias y las dependencias de ensamblados se gestionan automáticamente.  
  
<a name="BKMK_GetNuGetPackages"></a>

## <a name="where-to-find-the-nuget-sdk-packages"></a>Dónde encontrar los paquetes de SDK NuGet

El SDK de NuGet se encuentra en el perfil [crmsdk](https://www.nuget.org/profiles/crmsdk). Estos son los paquetes de Common Data Service. Seleccione cualquier paquete de la lista para navegar hasta la página de detalles del paquete. Los siguientes son los paquetes actuales de NuGet relevantes para Common Data Service.  


|Paquete|Descripción|
|---------|---------|
|[Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)|Contiene los ensamblados de Microsoft.Xrm.Sdk.dll y Microsoft.Crm.Sdk.Proxy.dll, además de herramientas|
|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools/)|Contiene las herramientas SDK creadas por el equipo de Microsoft Dynamics 365.|
|[Microsoft.CrmSdk.Deployment](https://www.nuget.org/packages/Microsoft.CrmSdk.Deployment/)|Contiene el ensamblado Microsoft.Xrm.Sdk.Deployment.dll|
|[Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)|Contiene el ensamblado Microsoft.Crm.Outlook.dll|
|[Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/)|Código de Ayuda de C# creado por el equipo de documentación para desarrolladores de Power Apps. Este código es para su uso con la API de Web. Estas clases proporcionan autenticación de servicios web tanto para implementaciones locales y en línea, gestión de errores y configuración de cadenas de conexión. Estas clases se utilizan en nuestros ejemplos de la API web|
|[Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/)|Contiene el ensamblado Microsoft.Xrm.Sdk.Workflow.dll|
|[Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/)|Contiene el ensamblado Microsoft.Xrm.Tooling.Connector |
|[Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell/)|Contiene los ensamblados para Xrm.Tooling.Connector Powershell |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell/)| Contiene los ensamblados para Package Deployer Powershell        |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf/)|Contiene el Dynamics 365 Package Deployer|
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)|Contiene el ensamblado Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll|
|[Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool/)|Contiene la herramienta de registro de complemento necesaria para administrar ensamblados de complemento, ensamblados de flujo de trbajo, entidades virtuales y extremos de servicio para Microsoft Dynamics 365.|
|[Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/)|Contiene los ensamblados de Microsoft.Xrm.Tooling.CrmConnectControl.dll, Microsoft.Xrm.Tooling.Ui.Styles.dll y Microsoft.Xrm.Tooling.WebResourceUtility.dll|

## <a name="how-to-install-a-package-in-your-project"></a>Cómo instalar un paquete en el proyecto  
 Para obtener información sobre cómo instalar paquetes de NuGet en el proyecto, consulte [Administrar paquetes de NuGet mediante el cuadro de diálogo](https://docs.nuget.org/docs/start-here/managing-nuget-packages-using-the-dialog).  

## <a name="download-tools-from-nuget"></a>Descargar herramientas de NuGet

Puede descargar herramientas usadas en desarrollo desde NuGet mediante el script de powershell encontrado en este tema: [Descargar herramientas de NuGet](../download-tools-nuget.md)
  
### <a name="see-also"></a>Vea también  
 [NuGetDocumentación](/nuget/)   
 [InstalaciónNuGet](https://docs.nuget.org/docs/start-here/installing-nuget)