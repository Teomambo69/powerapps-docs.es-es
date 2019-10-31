---
title: Importar componentes  | Microsoft Docs
description: Proceso para importar componentes de código
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.topic: article
author: Nkrb
---

# <a name="package-a-code-component"></a>Empaquete un componente de código

En este tema se muestra cómo importar componentes de código en Common Data Service. Después de implementar los componentes de código mediante el CLI PowerApps, el siguiente paso es agrupar todos los elementos de componente de código en un archivo de solución e importar el archivo de solución en Common Data Service para poder ver los componentes de código en tiempo de ejecución.

Siga los pasos indicados a continuación para crear e importar un archivo de solución:

1. Cree una nueva carpeta y llámela **Soluciones** (puede elegir cualquier nombre de su elección) usando el comando `mkdir Solutions`. Navegue al directorio utilizando el comando `cd Solutions`.

2. Cree un nuevo proyecto de soluciones usando el comando `pac solution init --publisher-name <enter your publisher name> --publisher-prefix <enter your publisher name>`. El proyecto de solución se usa para empaquetar el componente de código en un archivo zip de la solución que se usa para importar al Common Data Service.

   > [!NOTE]
   > Los valores `publisher-name` y `publisher-prefix` deben ser únicos a su entorno.
 
3. Cuando se crea el nuevo proyecto de solución, esta carpeta **Solución** debe hacer referencia a la ubicación donde se ubica el componente de ejemplo creado. Puede agregar la referencia usando el comando siguiente. Esta referencia indica al proyecto de solución qué componentes de código se deben agregar durante la compilación, y se pueden agregar referencias a varios componentes en un solo proyecto de solución.

   ```CLI   
    pac solution add-reference --path <path to your PowerApps component framework project>
   ```

3. Para generar un archivo zip del proyecto de la solución, deberá ir al directorio del proyecto de la solución y compilar el proyecto usando el comando `msbuild /t:build /restore`. Este comando usa *MSBuild* para crear el proyecto de solución extrayendo dependencias *NuGet* como parte de la restauración. Use `/restore` solo por primera vez que se compila el proyecto de solución. Para cada compilación posterior puede ejecutar el comando `msbuild`.

    > [!NOTE]
    > - Si msbuild 15.9.* no está en la ruta, abra Developer Command Prompt for VS 2017 para ejecutar los comandos `msbuild`.
    > - Al compilar la solución en la configuración de *depuración*, se genera un paquete de la solución no administrada. Un paquete de la solución administrada se genera compilando la solución en la configuración de *versión*. Estos valores pueden ser reemplazados especificando la propiedad `SolutionPackageType` en el archivo `cdsproj`.
    > - Puede establecer la configuración de msbuild en `Release` para emitir una compilación de producción. Ejemplo: `msbuild /p:configuration=Release`.
    > - Si se produce un error que indica *Nombre del proyecto ambiguo* al ejecutar el comando `msbuild` en la solución. A continuación compruebe que el nombre de la solución y el nombre del proyecto no son iguales.

4. Los archivos de solución generados se encuentran en la carpeta `\bin\debug\` después de la generación correcta.
5. [Importe manualmente la solución en Common Data Service](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/customize/import-update-upgrade-solution) mediante el portal web o consulte las secciones [Autenticarse en la organización](#authenticating-to-your-organization) e [Implementación](#deploying-code-components) para importar con los comandos de CLI de PowerApps.

## <a name="authenticating-to-your-organization"></a>Autenticarse en la organización

Puede implementar los componentes del código directamente desde el CLI de PowerApps autenticándose en la organización de Common Data Service y después insertando los componentes actualizados. Siga los pasos indicados a continuación para crear el perfil de autenticación, conectarse a Common Data Service, e insertar los componentes actualizados. 
 
1. Cree el perfil de autenticación utilizando el comando: 
 
    ```CLI
    pac auth create --url <your Common Data Service org’s url> 
    ```
 
2. Si ha creado antes una perfil de autenticación, puede ver todos los perfiles existentes mediante el comando: 

   ```CLI
    pac auth list 
   ```
 
3. Para cambiar entre los perfiles de autenticación creados previamente, use el comando: 
   
   ```CLI
    Pac auth select --index <index of the active profile>
    ``` 
 
4. Para obtener información sobre la organización, use el comando a continuación. La conexión se realizará mediante el perfil de autenticación predeterminado. 

    ```CLI
    pac org who 
    ```
 
5. Para eliminar un perfil de autenticación determinado, use el comando `pac auth delete --index < index of the profile >`. 
6. Si desea borrar todos los perfiles de autenticación del equipo local, use el comando `pac auth clear`. Esta acción es irreversible ya que elimina completamente el archivo `authprofile.json` y el archivo de caché de token del equipo local. 

## <a name="deploying-code-components"></a>Implementar componentes de código 

Una vez que haya creado correctamente un perfil de autenticación, puede comenzar a insertar los componentes de código a la instancia de Common Data Service con los últimos cambios. La capacidad `push` acelera el desarrollo del ciclo de desarrolladores internos porque omite los requisitos de controld e versiones de componentes de código y no requiere crear su solución (cdsproj) para importar componente de código. Para usar la capacidad `push`, siga los pasos indicados a continuación:

1. Asegúrese de que tiene un perfil de autenticación válido creado.
2. Navegue al directorio raíz donde se crea el proyecto de componente de código.
3. Ejecute el comando `pac pcf push --publisher-prefix <your publisher prefix>`.

   > [!NOTE]
   > El prefijo del editor que usa con el comando `push` debe coincidir con el prefijo del editor de la solución en la que se incluirán los componentes.

## <a name="how-to-remove-components-from-a-solution"></a>Cómo quitar componentes de una solución

Si desea quitar un componente de código de un archivo de solución:

1.  Edite el archivo `cdsproj` en el directorio del proyecto de la solución y quite las referencias al componente. A continuación se proporciona un ejemplo de una referencia de componente:

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

2. Realice una nueva generación (o limpieza) usando el comando
   
    ```CLI
    msbuild /t:rebuild
    ```

### <a name="see-also"></a>Vea también

[Agregar componentes a aplicaciones basadas en modelo](add-custom-controls-to-a-field-or-entity.md)<br/>
[Agregar componentes a una aplicación](component-framework-for-canvas-apps.md#add-components-to-a-canvas-app)<br/>
[Referencia de la API de PowerApps component framework](reference/index.md)<br/>
[Información general sobre PowerApps component framework](overview.md)
