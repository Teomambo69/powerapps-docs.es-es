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
ms.openlocfilehash: 1d53a01d91822743311d350ddfce7733aba3f661
ms.sourcegitcommit: 6fce86edacd9bfe49f8114a2a69bc18302cd01f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "3260662"
---
# <a name="common-issues-and-workarounds"></a>Problemas comunes y soluciones alternativas

Aquí se muestran algunos problemas comunes que puede encontrar al usar Power Apps component framework y Power Apps CLI

## <a name="msbuild-error-msb4036"></a>Error Msbuild MSB4036

- El nombre de la tarea en el archivo del proyecto es igual que el nombre de la clase de tarea.
- La clase de tarea es pública e implementa la interfaz de Microsoft.Build.Framework.ITask.
- La tarea se declara correctamente con *\<UsingTask>* en el archivo de proyecto o en los archivos *.tasks situados en el directorio de la ruta.

**Solución alternativa**:

- Abra Instalador de Visual Studio.
- Para Visual Studio 2017, seleccione **Modificar**.
- Seleccione **Componentes individuales**.
- En Herramientas de código, active **Destinos de NuGet y tareas de compilación**.

> [!NOTE]
> A medida que nos encontremos durante el proceso de desarrollo, agregaremos constantemente problemas y soluciones comunes. Si encuentra un problema y tiene una solución alternativa y cree que es útil, plantee el problema [aquí](https://powerusers.microsoft.com/t5/Power-Apps-Component-Framework/bd-p/pa_component_framework) o plantee una solicitud de extracción para que podamos revisarla y agregarla a la lista.

## <a name="publisher-prefix"></a>Prefijo de publicador

Si se crea un componente utilizando la versión de CLI anterior a 0.4.3, encontrará un error al intentar volver a importar el archivo de solución en Common Data Service. 

**Solución alternativa**:

- Elimine la solución que contiene el componente relevante de Common Data Service. 
- El componente debe eliminarse del archivo o la cuadrícula si el componente ya está configurado para evitar dependencias.
- Importe la nueva solución con actualizaciones del componente compilado por la última versión de CLI.
- Los componentes recién importados ahora pueden configurarse en formularios o cuadrículas.  

## <a name="issues-while-updating-existing-code-components"></a>Problemas al actualizar componentes de código existentes

- Si obtiene una notificación 1ES que pregunta cómo se están usando los pcf-scripts, tenga en cuenta que estos scripts se usan solo para crear los componentes del código pero no se empaquetan ni usan por el componente resultante.
- Si ha creado un componente de código utilizando la versión de CLI 0.1.817.1 o anterior y desea asegurarse de que se están utilizando los últimos módulos de compilación y depuración, realice las actualizaciones en el archivo `package.json` como se muestra a continuación:
   
   ```JSON
   "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
   ```

## <a name="error-failed-to-retrieve-information-about-microsoftpowerappsmsbuildpcf-from-remote-source-feed-url-when-the-build-fails-for-authorization-issues"></a>Error: No se pudo recuperar la información sobre Microsoft.PowerApps.MSBuild.Pcf desde un origen remoto <Feed Url> cuando la compilación produce un error por problemas de autorización. 

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

## <a name="web-resource-size-is-too-large"></a>El tamaño del recurso web es demasiado grande

Error  **Error en la importación de la solución: el tamaño del contenido de recursos web es demasiado grande**.

**Solución alternativa**

- Construya el `.pcfproj` como configuración de lanzamiento que establece el paquete web en modo producción usando el comando 
  ```CLI
  msbuild /property:configuration=Release
  ```
- Ejecute el comando msbuild con una propiedad adicional como se muestra a continuación: 
  ```CLI
  msbuild /p:PcfBuildMode=production
  ```
- Edite el `.pcfproj` para construir siempre el paquete web en modo de producción configurando la propiedad `PcfBuildMode` a la producción:
  ```XML
  <PropertyGroup>
    <Name>TS_ReactStandardControl</Name>
    <ProjectGuid>0df84c56-2f55-4a80-ac9f-85b7a14bf378</ProjectGuid>
    <OutputPath>$(MSBuildThisFileDirectory)out\controls</OutputPath>
    <PcfBuildMode>production</PcfBuildMode>
  </PropertyGroup>
  ```

## <a name="when-running-power-apps-checker-with-the-solution-built-using-cli-tooling-in-default-configuration"></a>Al ejecutar el comprobador de Power Apps con la solución creada mediante herramientas CLI en la configuración predeterminada

**Error: No use la función 'eval' o sus equivalentes funcionales**. Esta advertencia se muestra por diseño, ya que la configuración predeterminada de `msbuild` es `Configuration=Debug`. Esto a su vez indica a webpack (módulo usado para agrupar el componente de código) que empaquete en modo de desarrollo, lo que emite `eval()`. 

**Solución alternativa**

Vuelva a generar el archivo de solución utilizando cualquiera de los comandos siguientes y vuelva a importar la solución en Common Data Service.

```CLI
msbuild/property:configuration:Release
```

```CLI
npm run build -- --buildMode production
```

## <a name="power-apps-component-framework-datasets-getvalue-by-property-alias-doesnt-work"></a>La función getValue de los conjuntos de datos de Power Apps component framework por alias de propiedad no funciona

La función getValue de las API del conjunto de datos de Power Apps component framework solo busca registros por el nombre de la columna del conjunto de datos y no por el alias de la propiedad establecido en el manifiesto. Si intenta obtener valor por alias de propiedad, se devolverá un valor vacío.

**Solución alternativa**

Use el nombre de la columna del conjunto de datos (el componente puede obtener el nombre de la columna del conjunto de datos buscando en la matriz de columnas usando el alias). 

   ***Comportamiento esperado*** 

   ```TypeScript
   long  = dataSet.records[currentRecordId].getValue("Longitude") //based on property set in manifest"-122.3514661"
   ```

   ***Solución actual***

   ```TypeScript
   lat = dataSet.records[currentRecordId].getValue("Address_x0020_1_x003a__x0020_Latitude")//based on the dataset column name
   ```

## <a name="power-apps-component-framework-datasets-sharepoint-issue"></a>Problema de SharePoint con los conjuntos de Power Apps component framework

El componente del conjunto de datos de Power Apps component framework actualmente no muestra correctamente los registros de SharePoint. Mientras que la solicitud de red se desarrollará correctamente con los registros de datos correctos devueltos, la deserialización fallará y se devolverá un conjunto de datos vacío.

**Solución alternativa**

De momento, no hay solución. Estamos trabajando para crear una solución para nuestros trenes de desarrollo.

