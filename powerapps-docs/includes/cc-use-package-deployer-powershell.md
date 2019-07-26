---
ms.openlocfilehash: 215a6d9fb0890bd6d93843b0b649ada4203e5600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224204"
---
Los archivos de PowerShell para la herramienta Package Deployer están disponibles como un [paquete NuGet](https://go.microsoft.com/fwlink/?linkid=859211). Para usarlos, debe descargar y extraer la herramienta en el equipo local con **nuget.exe**.<br/><br/>

Descargue **nuget.exe** desde <https://www.nuget.org/downloads>y guarde el archivo en el equipo, por ejemplo, en **d:\\** . Luego ejecute el siguiente comando en el símbolo del sistema para extraer el contenido del paquete en una carpeta, por ejemplo **PD-PowerShell**, en el equipo:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell -Version [VERSION] -O d:\PD-PowerShell`<br/><br/>
    
Después de extraer los archivos de PowerShell para la herramienta Package Deployer, vaya a la carpeta `[ExtractedLocation]\tools` para buscar los archivos necesarios. 
