---
title: Problemas comunes y soluciones alternativas (Power Apps component framework) | Microsoft Docs
description: Proporciona información sobre problemas conocidos y soluciones alternativas que algunos encuentran al trabajar con Power Apps component framework y CLI
keywords: ''
author: Nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 11/25/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: d9a5d345204d82a1e5f6629a3f0bb7cf2159ddd7
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914487"
---
# <a name="common-issues-and-workarounds"></a>Problemas comunes y soluciones alternativas

Aquí se muestran algunos problemas comunes que puede encontrar al usar Power Apps component framework y Power Apps CLI

**Error Msbuild MSB4036**

1. El nombre de la tarea en el archivo del proyecto es igual que el nombre de la clase de tarea.
2. La clase de tarea es pública e implementa la interfaz de Microsoft.Build.Framework.ITask.
3. La tarea se declara correctamente con *\<UsingTask>* en el archivo de proyecto o en los archivos *.tasks situados en el directorio de la ruta.

**Solución alternativa**:

1. Abra Instalador de Visual Studio. 
1. Para Visual Studio 2017, seleccione **Modificar**. 
1. Seleccione **Componentes individuales**.
1. En Herramientas de código, active **Destinos de NuGet y tareas de compilación**.

> [!NOTE]
> A medida que nos encontremos durante el proceso de desarrollo, agregaremos constantemente problemas y soluciones comunes. Si encuentra un problema y tiene una solución alternativa y cree que es útil, plantee el problema [aquí](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) o plantee una solicitud de extracción para que podamos revisarla y agregarla a la lista.

**Prefijo de publicador**

Si se crea un componente utilizando la versión de CLI anterior a 0.4.3, encontrará un error al intentar volver a importar el archivo de solución en Common Data Service. 

**Solución alternativa**:

- Elimine la solución que contiene el componente relevante de Common Data Service. 
- El componente debe eliminarse del archivo o la cuadrícula si el componente ya está configurado para evitar dependencias.
- Importe la nueva solución con actualizaciones del componente compilado por la última versión de CLI.
- Los componentes recién importados ahora pueden configurarse en formularios o cuadrículas.  

**Problemas al actualizar componentes de código existentes**

1. Si obtiene una notificación 1ES que pregunta cómo se están usando los pcf-scripts, tenga en cuenta que estos scripts se usan solo para crear los componentes del código pero no se empaquetan ni usan por el componente resultante.  
2. Si ha creado un componente de código utilizando la versión de CLI 0.1.817.1 o anterior y desea asegurarse de que se están utilizando los últimos módulos de compilación y depuración, realice las actualizaciones en el archivo `package.json` como se muestra a continuación:
   
   ```JSON
   "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
   ```

3. Error **Error al recuperar información sobre Microsoft.PowerApps.MSBuild.Pcf desde un origen remoto <Feed Url>** cuando la compilación produce un error por problemas de autorización. 

   **Solución alternativa**

   - Abra el archivo `NuGet.Config` de **%APPDATA%\NuGet**. La fuente de la que el usuario obtiene el error debe estar presente en este archivo. 
   - Quite la alimentación del `NuGet.Config file` o genere un token PAT y agréguelo al` Nuget.Config file`. Por ejemplo:

     ```XML
     <?xml version="1.0" encoding="utf-8"?>  
     <configuration>  
     <packageSources>  
         <add key="CRMSharedFeed" value="https://dynamicscrm.pkgs.visualstudio.com/_packaging/CRMSharedFeed/nuget/v3/index.json" />  
      </packageSources>  
      <packageSourceCredentials>  
      <CRMSharedFeed>  
      <add key="Username" value="anything" />  
      <add key="Password" value="User PAT" />  
        </CRMSharedFeed>  
        </packageSourceCredentials>  
       </configuration>
     ```
