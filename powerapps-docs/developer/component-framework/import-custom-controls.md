---
title: Importar componentes | Microsoft Docs
description: En este tema se describe cómo importar componentes de código
keywords: ''
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
ms.openlocfilehash: 3042202fd1790d117c2a503bd6e69eaaea15c08a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346817"
---
# <a name="package-a-code-component"></a>Empaquetar un componente de código

En este tema se describe cómo importar componentes de código en Common Data Service. Después de implementar los componentes de código mediante la CLI de PowerApps, el paso siguiente consiste en agrupar todos los elementos de componente de código en un archivo de solución e importar el archivo de solución en Common Data Service para que pueda ver los componentes de código en tiempo de ejecución.

Para crear e importar un archivo de solución:

1. Cree una nueva carpeta y asígnele el nombre **Solution** (o cualquier nombre de su elección) mediante el `mkdir Solutions` de comandos. Navegue al directorio mediante el `cd Solutions` de comandos.

2. Cree un nuevo proyecto de soluciones mediante el `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher prefix>` de comandos. El proyecto de solución se utiliza para agrupar el componente de código en un archivo zip de la solución que se usa para la importación en Common Data Service.

   > [!NOTE]
   > Los valores `publisher-name` y `publisher-prefix` deben ser únicos en su entorno.
 
3. Una vez creado el nuevo proyecto de solución, haga referencia a la carpeta de la **solución** en la ubicación donde se encuentra el componente de ejemplo creado. Puede Agregar la referencia mediante el comando que se muestra a continuación. Esta referencia informa al proyecto de la solución sobre qué componentes de código deben agregarse durante la compilación. Puede Agregar referencias a varios componentes en un único proyecto de solución.

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. Para generar un archivo zip desde el proyecto de la solución, vaya al directorio del proyecto de la solución y compile el proyecto mediante el `msbuild /t:build /restore` de comandos. Este comando usa *msbuild* para compilar el proyecto de la solución mediante la extracción de las dependencias de *NuGet* como parte de la restauración. Utilice la `/restore` solo por primera vez cuando se compile el proyecto de la solución. Para cada compilación después de eso, puede ejecutar el comando `msbuild`.


    > [!NOTE]
    > - Si MSBuild 15,9. * no está en la ruta de acceso, abra Símbolo del sistema para desarrolladores para VS 2017 para ejecutar los comandos de `msbuild`.
    > - Al compilar la solución en la configuración de *depuración* , se genera un paquete de solución no administrada. Un paquete de solución administrada se genera al compilar la solución en la configuración de *lanzamiento* . Esta configuración se puede invalidar especificando la propiedad `SolutionPackageType` en el archivo de `cdsproj`.
    > - Puede establecer la configuración de MSBuild en `Release` para emitir una compilación de producción. Ejemplo: `msbuild /p:configuration=Release`
    > - Si se produce un error que indica un *nombre de proyecto ambiguo* al ejecutar el comando `msbuild` en la solución, asegúrese de que el nombre de la solución y el nombre del proyecto no son los mismos.

4. Los archivos de solución generados se encuentran dentro de la carpeta `\bin\debug\` una vez que la compilación se ha realizado correctamente.
5. [Importe manualmente la solución en Common Data Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) mediante el portal web o consulte las secciones sobre [autenticación en su organización](#authenticating-to-your-organization) e [implementación](#deploying-code-components) para importarlas mediante los comandos de la CLI de PowerApps.

## <a name="authenticating-to-your-organization"></a>Autenticación en su organización

Puede implementar los componentes de código directamente desde la CLI de PowerApps autenticando en la organización de Common Data Service y, a continuación, insertando los componentes actualizados. Siga los pasos que se indican a continuación para crear el perfil de autenticación, conectarse a Common Data Service e inserte los componentes actualizados. 
 
1. Cree el perfil de autenticación con el siguiente comando: 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. Si creó anteriormente un perfil de autenticación, puede ver todos los perfiles existentes con el siguiente comando: 

   ```CLI
    pac auth list 
   ```
 
3. Para cambiar entre los perfiles de autenticación creados anteriormente, use el siguiente comando: 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 

4. Para obtener la información básica sobre la organización, use el siguiente comando. La conexión se realizará mediante el perfil de autenticación predeterminado. 

    ```CLI
    pac org who 
    ```
 
5. Para eliminar un perfil de autenticación determinado, use el `pac auth delete --index < index of the profile >` de comandos. 
6. Si desea borrar todos los perfiles de autenticación del equipo local, use el comando `pac auth clear`. Esta acción es irreversible porque elimina completamente el archivo de `authprofile.json` archivo y la caché del token del equipo local. 

## <a name="deploying-code-components"></a>Implementar componentes de código 

Después de haber creado correctamente un perfil de autenticación, puede empezar a insertar los componentes de código en la instancia de Common Data Service con todos los cambios más recientes. La capacidad de `push` acelera el desarrollo del ciclo del desarrollador interno porque omite los requisitos de control de versiones del componente de código y no requiere que compile la solución (cdsproj) para importar el componente de código. Para usar la capacidad de `push`, haga lo siguiente:

1. Asegúrese de que tiene un perfil de autenticación válido creado.
2. Navegue hasta el directorio raíz donde se crea el proyecto de componente de código.
3. Ejecute el `pac pcf push --publisher-prefix <your publisher prefix>` de comandos.

   > [!NOTE]
   > El prefijo del publicador que se usa con el comando `push` debe coincidir con el prefijo publicador de la solución en la que se incluirán los componentes.

## <a name="how-to-remove-components-from-a-solution"></a>Cómo quitar componentes de una solución

Si desea quitar un componente de código de un archivo de solución:

1.  Edite el archivo de `cdsproj` en el directorio del proyecto de la solución y quite las referencias al componente. A continuación se muestra un ejemplo de una referencia de componente:

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

2. Realice una recompilación (o limpieza) con el siguiente comando:
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>Vea también

[Agregar componentes de código a un campo o una entidad en aplicaciones controladas por modelos](add-custom-controls-to-a-field-or-entity.md)<br/>
[Agregar componentes a una aplicación de lienzo](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)
