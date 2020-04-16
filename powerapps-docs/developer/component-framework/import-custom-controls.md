---
title: Importar componentes  | Microsoft Docs
description: Este artículo describe cómo importar componentes de código
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 717fb3a5ceba7b2136382736b462206c72a3d8e0
ms.sourcegitcommit: ebb4bb7ea7184e31dc95f0c301ebef75fae5fb14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "3218541"
---
# <a name="package-a-code-component"></a>Empaquete un componente de código

Este artículo describe cómo importar componentes de código en Common Data Service. Después de implementar los componentes de código mediante el CLI Power Apps, el siguiente paso es agrupar todos los elementos de componente de código en un archivo de solución e importar el archivo de solución en Common Data Service para poder ver los componentes de código en tiempo de ejecución.

Para crear e importar un archivo de solución:

1. Cree una nueva carpeta dentro de la carpeta que tiene el archivo `pcfproj` archivar y asígnele el nombre **Soluciones** (o cualquier nombre que elija) con el comando `mkdir Solutions`. Navegue al directorio utilizando el comando `cd Solutions`.

2. Cree nuevos proyectos de soluciones con el siguiente comando. El proyecto de solución se usa para empaquetar el componente de código de un archivo zip de la solución que se usa para importar a Common Data Service.
   
   ```CLI
   pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>
   ```

   > [!NOTE]
   > Los valores `publisher-name` y `publisher-prefix` deben ser únicos a su entorno.
 
3. Cuando se crea el nuevo proyecto de solución, haga referencia a la carpeta **Soluciones** para la ubicación donde se ubica el componente de muestra creado. Puede agregar la referencia usando el comando siguiente. Esta referencia informa al proyecto de la solución sobre qué componentes de código se deben agregar durante la generación. Puede agregar referencias a varios componentes en un solo proyecto de solución.

   ```CLI   
    pac solution add-reference --path <path to your Power Apps component framework project>
   ```

3. Para generar un archivo zip a partir del proyecto de la solución, vaya al directorio del proyecto de la solución y compile el proyecto usando el siguiente comando. Este comando usa *MSBuild* para crear el proyecto de solución extrayendo dependencias *NuGet* como parte de la restauración. Use `/restore` solo por primera vez que se compila el proyecto de solución. Para cada compilación posterior puede ejecutar el comando `msbuild`.

   ```CLI
   msbuild /t:build /restore
   ```

    > [!TIP]
    > - Si msbuild 15.9.* no está en la ruta, abra Developer Command Prompt for VS 2017 para ejecutar los comandos `msbuild`.
    > - Al compilar la solución en la configuración de *depuración*, se genera un paquete de la solución no administrada. Un paquete de la solución administrada se genera compilando la solución en la configuración de *versión*. Estos valores pueden ser reemplazados especificando la propiedad `SolutionPackageType` en el archivo `cdsproj`.
    > - Puede establecer la configuración de msbuild en `Release` para emitir una compilación de producción. Ejemplo: `msbuild /p:configuration=Release`
    > - Si se produce un error que indica *Nombre de proyecto ambiguo* al ejecutar el comando `msbuild` en la solución, asegúrese de que el nombre de la solución y el nombre del proyecto no son iguales.

4. Los archivos de solución generados se encuentran en la carpeta `\bin\debug\` después de la generación correcta.
5. Manualmente [importe la solución a Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) usando el portal web o automáticamente usando las [Power Apps Build Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools)

## <a name="connecting-to-your-environment"></a>Conexión al entorno

Puede implementar los componentes del código directamente desde Power Apps CLI conectándose al entorno de Common Data Service y luego enviando los componentes actualizados.

Use los siguientes pasos para crear el perfil de autenticación, conéctese a Common Data Service, e inserte los componentes actualizados. 
 
1. Cree el perfil de autenticación utilizando el comando: 
 
    ```CLI
    pac auth create --url <https://xyz.crm.dynamics.com> 
    ```
 
2. Si ha creado antes una perfil de autenticación, puede ver todos los perfiles existentes mediante el comando: 

   ```CLI
    pac auth list 
   ```
 
3. Para cambiar entre los perfiles de autenticación creados previamente, use el comando: 
   
   ```CLI
    pac auth select --index <index of the active profile>
    ``` 

4. Para obtener la información básica sobre el entorno, use el siguiente comando. La conexión se establecerá mediante el perfil predeterminado de autenticación. 

    ```CLI
    pac org who 
    ```
 
5. Para eliminar un perfil de autenticación determinado, use el comando `pac auth delete --index <index of the profile>`. 
6. Si desea borrar todos los perfiles de autenticación del equipo local, use el comando `pac auth clear`. Esta acción es irreversible porque elimina completamente el archivo `authprofile.json` y el archivo caché del símbolo del equipo local. 

## <a name="deploying-code-components"></a>Implementar componentes de código 

Una vez que haya creado correctamente un perfil de autenticación, puede comenzar a insertar los componentes de código a la instancia de Common Data Service con los últimos cambios. La capacidad `push` acelera el desarrollo del ciclo del desarrollador interno porque omite los requisitos de versiones de componentes de código y no requiere que compile su solución (cdsproj) para importar el componente de código. Para utilizar la capacidad `push`, haga lo siguiente:

1. Asegúrese de que tiene un perfil de autenticación válido creado.
2. Navegue al directorio raíz donde se crea el proyecto de componente de código.
3. Ejecute el comando.

   ```CLI
   pac pcf push --publisher-prefix <your publisher prefix>
   ```

   > [!NOTE]
   > El prefijo del editor que usa con el comando `push` debe coincidir con el prefijo del editor de la solución en la que se incluirán los componentes.

## <a name="create-a-solution-project-based-on-an-existing-solution-in-common-data-service"></a>Crear un proyecto de solución basado en una solución existente en Common Data Service

Para crear un proyecto de solución basado en una solución existente en Common Data Service, ejecute el comando `pac solution clone`. Para ello:

1. Asegúrese de que tiene un perfil de autenticación válido creado.
2. Ejecute el comando. 

   ```CLI
   pac solution clone –name(-n) <name of the solution to be exported> --version(-v) <version of your solution> --include(-i) <settings that should be included>
   ```

Más información: [Opciones de configuración](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.exportsolutionrequest?view=dynamics-general-ce-9)

## <a name="create-a-plug-in-project-and-add-a-reference-to-it-in-your-solution"></a>Crear un proyecto de complemento y agregar una referencia al mismo en su solución 

> [!NOTE]
> El comando del complemento se encuentra en versión preliminar pública y Power Apps CLI ahora es compatible con la creación de un proyecto de complemento y su empaquetamiento en una solución agregando una referencia al proyecto de complemento. El comando `pac plugin init` crea los archivos de plantilla (csproj, Plugin.cs & ServiceHelper.cs) en el directorio. Para ello: 

1.    Asegúrese de que tiene un perfil de autenticación válido creado.
2.    Vaya al directorio raíz donde desea que se cree el proyecto.
3.    Ejecute el comando. 

     ```CLI
     pac auth create –url <https://xyz.crm.dynamics.com>
     ```
4.    Ejecutar el comando para crear el proyecto de complemento

    ```CLI
    pac plugin init
    ```

5.    Agregue una referencia a su proyecto de solución utilizando el siguiente comando para que el proyecto de complementos se compile cuando se haya compilado la solución.

    ```CLI
    pac solution add-reference –path <path to your plugin project>
    ```

6.    Ejecute el comando para compilar la solución y el complemento al que se hace referencia.
    ```CLI
    msbuild
    ```

## <a name="remove-components-from-a-solution"></a>Quitar componentes de una solución

Si desea quitar un componente de código de un archivo de la solución:

1. Edite el archivo `cdsproj` en el directorio del proyecto de la solución y quite las referencias al componente. A continuación se proporciona un ejemplo de una referencia de componente:

   ```XML
   <ItemGroup>
       <Projectreference Include="..\pcf_component\pcf_component.pcfproj">
         <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
         <Name>pcf_component </Name>
         <Targets>Build</Targets>
         <referenceOutputAssembly>false</referenceOutputAssembly>
         <OutputItemType>Content</OutputItemType>
         <CopyToOutputDirectory>Always</CopyToOutputDirectory>
       </Projectreference>
   </ItemGroup>
   ```

2. Realice una nueva compilación (o limpieza) ejecutando el comando siguiente:
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>Vea también

[Agregar componentes de código a un campo o entidad en aplicaciones basadas en modelo](add-custom-controls-to-a-field-or-entity.md)<br/>
[Agregar componentes a una aplicación de lienzo](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
