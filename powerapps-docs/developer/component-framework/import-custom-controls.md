---
title: Importar componentes  | Microsoft Docs
description: Proceso para importar componentes personalizados
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
---

# <a name="package-a-custom-component"></a>Empaquete un componente personalizado

En este tema se muestra cómo importar componentes personalizados en Common Data Service. Después de desarrollar los componentes personalizados con PowerApps CLI, el siguiente paso es importar esos componentes para poder ver los componentes en tiempo de ejecución.

Siga los pasos indicados a continuación para crear e importar un archivo de solución:

1. Cree un nuevo proyecto de solución en el directorio que elija usando el comando `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher name>` después de `cd <your new folder>`. El proyecto de solución se usa para empaquetar el componente personalizado de un archivo zip de la solución que se usa para importar al entorno.

   > [!NOTE]
   > Los valores `publisher-name` y `publisher-prefix` deben ser únicos a su entorno.
 
2. Cuando se crea el nuevo proyecto de solución, debe hacer referencia a la ubicación donde se ubica el componente creado. Puede agregar la referencia usando el comando siguiente. Esta referencia indica al proyecto de solución qué componentes personalizados se deben agregar durante la compilación, y se pueden agregar referencias a varios componentes en un solo proyecto de solución.

    ```CLI   
    pac solution add-reference --path<path of your PowerApps component framework project on disk>
    ```

3. Para generar un archivo zip del proyecto de la solución, deberá `cd` en el directorio del proyecto de la solución y compilar el proyecto usando el comando `msbuild /t:build /restore`. Este comando usa MSBuild para crear el proyecto de solución extrayendo dependencias NuGet como parte de la restauración. Use `/restore` solo por primera vez que se compila el proyecto de solución. Para cada compilación posterior puede ejecutar el comando `msbuild`.

    > [!NOTE]
    > - Si msbuild 15.9.* no está en la ruta, abra Developer Command Prompt for VS 2017 para ejecutar los comandos `msbuild`.    
    > - Al compilar la solución en la configuración de *depuración*, se genera un paquete de la solución no administrada. Un paquete de la solución administrada se genera compilando la solución en la configuración de *versión*. Estos valores pueden ser reemplazados especificando la propiedad SolutionPackageType en el archivo cdsproj.
    > - Puede establecer la configuración de msbuild en `Release` para emitir una compilación de producción. Ejemplo: `msbuild /p:configuration=Release` 

4. Cuando termine la compilación, los archivos generados de la solución se encuentran en `\bin\debug\`.
5. Ahora puede importar la solución manualmente mediante el portal web.

## <a name="how-to-remove-components-from-a-solution"></a>Cómo quitar componentes de una solución

Si desea quitar un componente personalizado de una solución, siga los pasos indicados a continuación:

1.  Edite el archivo cdsproj en el directorio del proyecto de la solución y quite referencia al componente. A continuación se proporciona un ejemplo de una referencia de componente:

```XML
<ItemGroup>
    <ProjectReference Include="..\pcf_component\pcf_component.pcfproj">
      <Project>0481bd83-ffb0-4b70-b526-e0b3dd63e7ef</Project>
      <Name>pcf_component </Name>
      <Targets>Build</Targets>
      <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
      <OutputItemType>Content</OutputItemType>
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </ProjectReference>
</ItemGroup>
```

2.  Realice una nueva generación (o limpieza) ejecutando el comando
   ```CLI
   msbuild /t:rebuild
   ```

### <a name="see-also"></a>Vea también

[Agregar componentes a entidades o campos](add-custom-controls-to-a-field-or-entity.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
