---
ms.openlocfilehash: a108a9ee6f9033851b2f55beb071a1e7cae254dd
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224258"
---
La herramienta Package Deployer está disponible como un [paquete NuGet](https://go.microsoft.com/fwlink/?linkid=859205). Para usar Package Deployer, debe descargar y extraer la herramienta en el equipo local con **nuget.exe**.<br/><br/>

Descargue **nuget.exe** desde <https://www.nuget.org/downloads>y guarde el archivo en el equipo, por ejemplo, en **d:\\** . Luego ejecute el siguiente comando en el símbolo del sistema para extraer el contenido del paquete en una carpeta, por ejemplo **PD**, en el equipo:<br/>

`d:\nuget install Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf -Version [VERSION] -O d:\PD`<br/><br/>
    
Después de extraer la herramienta Package Deployer, vaya a la carpeta `[ExtractedLocation]\tools` para buscar el archivo **PackageDeployer.exe**. 
