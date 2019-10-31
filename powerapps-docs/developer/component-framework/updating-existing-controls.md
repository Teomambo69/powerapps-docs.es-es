---
title: Actualizar componentes de código existentes mediante útiles de PowerApps component framework| Microsoft Docs
description: Actualizar componentes mediante útiles de PowerApps component framework
keywords: 'PowerApps component framework, componente de código, component Framework'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---
# <a name="updating-existing-code-components"></a>Actualizar componentes de código existentes 

Si usted es participante de Versión preliminar privada de PowerApps component framework para aplicaciones basadas en modelo y ha creado ya componentes de código, deberá realizar algunas actualizaciones de menor importancia para que sea compatible con las nuevas estructuras de proyecto centradas en ALM. 

Algunos cambios son necesarios usar los nuevos útiles de PowerApps CLI con sus componentes de código de PowerApps component framework existentes.

> [!NOTE]
> Este tema es aplicable solo para actualizar componentes código para aplicaciones basadas en modelo porque los útiles de PowerApps CLI no están disponibles en el momento de vista previa privada para aplicaciones basadas en modelo.  

## <a name="creating-an-empty-project"></a>Crear un proyecto vacío

Utilice PowerApps CLI para crear un nuevo proyecto vacío para el componente de código. Más información [Crear componentes usando los útiles](create-custom-controls-using-pcf.md).
Una vez el proyecto se ha creado, migre el origen de componente de código al nuevo proyecto:

1. Copie o reemplace el archivo de origen del componente desde el antiguo archivo de origen en **index.ts**.
2. Copie o reemplace el contenido de **ControlManifest.xml** en el archivo **ControlManifest.Input.xml**.
3. Copie todos los demás recursos de componentes periféricos como css, resx, img en la subcarpeta correspondiente del antiguo proyecto en el nuevo proyecto.

## <a name="updating-manifest-file"></a>Actualizar el archivo de manifiesto

El archivo `ControlManifest.xml` que define las propiedades de componente de código es reemplazado por el archivo `ControlManifest.Input.xml`. Por lo demás debe haber pocos cambios en el esquema entre los dos archivos.
Hay un par de cambios semánticos importantes.

1. La entrada de recurso `code` ahora debe señalar al archivo de origen precompilado del componente de código. El nombre de archivo se establece de forma predeterminada como **index.ts**.
Por ejemplo, si el origen del componente se implementa en un archivo llamado `MyControl.ts`, la entrada `code` en `ControlManifest.Input.xml` debe señalar a ese archivo. El archivo `code` también debe ser un archivo Typescript válido. Esto contrasta con los archivos de manifiesto antiguos que especificaban el archivo de salida JS compilado en la entrada `code`.
2. El atributo `path` del elemento de recurso como `code` o `css` ahora hace referencia a la ruta de acceso local al archivo en el disco. Por ejemplo:

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

El atributo `path` anterior indica que el archivo `YourControlName.css` se encuentra en la subcarpeta `css` en relación con el directorio actual donde `ControlManifest.Input.xml` se encuentra en el disco.
Actualice los archivos ControlManifest.Input.xml de este modo:

1. Edite la entrada `code` en `ControlManifest.Input.xml` al archivo de origen precompilado del componente de código (normalmente será index.ts).
2. Edite las rutas de los recursos para que hagan referencia a las rutas de acceso relativas a los archivos en el disco correctamente.

## <a name="updating-the-project-files"></a>Actualizar los archivos del proyecto

Si ha creado un componente usando la versión anterior de los útiles y desea aprovechar las últimas capacidades, asegúrese de actualizar los archivos del proyecto como se indica a continuación:

1. Actualizar las proyectos existentes para usar los últimos módulos
 
   - Actualice la etiqueta de versión en su `pcfproj` situado en la carpeta de proyecto de PowerApps Component Framework como se muestra a continuación:

      ```XML
      <PackageReference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - Actualice la etiqueta de la versión en su `cdsproj` situado en la carpeta de proyecto de la solución como se muestra continuación:

      ```XML
      <PackageReference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

    > [!NOTE] 
    > Después de realizar los cambios mencionados, ejecute el comando `msbuild /t:restore` para actualizar el proyecto a la versión correcta.


   - Actualice la etiqueta de la versión en su archivo `package.json` situado en la carpeta de proyecto de PowerApps Component Framework:

      ```JSON
      "devDependencies":{
       "pcf-scripts": "^1",
       "pcf-start": "^1"
          }
      ```
   > [!NOTE]
   > Después de realizar los cambios mencionados, ejecute el comando `npm update` para actualizar el proyecto a la versión correcta.

2. Si ha creado anteriormente un perfil auth, necesita reconstruirlo de nuevo. Esto se debe a que una nueva propiedad se agregó al perfil para permitir una nube privada. Puede hacerlo de este modo:
 
    - Ejecutando el comando '`pac auth clear`'
    - Ejecutando el comando '`pac auth create --url <your org url>`'

## <a name="updating-your-project-with-the-latest-node-modules"></a>Actualizando el proyecto con los últimos módulos del nodo

Los proyectos heredados requieren que se recuperen los últimos módulos npm para aprovechar las últimas capacidades de CLI. Para actualizar los módulos del nodo que ha descargado anteriormente, vaya al directorio del proyecto en el símbolo del sistema del desarrollador y ejecute el comando `npm update`. 

## <a name="using-es6-module-syntax"></a>Uso de la sintaxis de módulo ES6

Las herramientas de generación esperan que el origen de componente se exporte usando el formato de módulo ES6 estándar. Los componentes heredados se exportan normalmente como módulos internos (también llamados espacios de nombres). Para alinearse con las nuevas herramientas de generación el archivo de origen de componente debe se deben modificar de este modo:

1. Abra el archivo de origen que implementa el componente de código (por ejemplo index.ts).
2. Use la sintaxis de exportación ES6 estándar quitando la declaración de módulo

     Antes:
     ```TypeScript
     module SampleNamespace
     {
    export class TSLinearInputControl implements ComponentFramework.StandardControl<InputsOutputs.IInputBag, InputsOutputs.IOutputBag> {
          <your class implementation>
           }
            }
     
      ```
    Después:
    ```TypeScript
     export class YourControlName implements ComponentFramework.StandardControl<IInputs, IOutputs> { 
          <your class implementation>
          }
   ```

## <a name="using-generated-manifest-typing-file"></a>Uso del archivo de escritura del manifiesto generado

Los proyectos heredados requieren la creación y edición manual de un archivo de escritura `inputsOutputs.d.ts`, establecido normalmente en la subcarpeta `private_typing`. Los útiles PowerApps CLI ahora generan automáticamente este archivo en la compilación. 

La generación de código garantiza que las definiciones de `type` usadas en el código de origen del componente permanezcan en sincronizadas con `types` definidos en el archivo de manifiesto del componente.  
El archivo de escritura cambia de nombre a `ManifestTypes.d.ts` y ahora se genera en una subcarpeta llamada `generated`. Además, los tipos `InputsOutputs.IInputBag` y `InputsOutputs.IOutputBag` cambian de nombre a `IInputs` y `IOutputs` respectivamente.
Para utilizar el nuevo archivo de escritura:

1. Importe el nuevo archivo `ManifestTypes.d.ts` agregando la siguiente línea en la parte superior del archivo de origen del componente: { IInputs, IOutputs } from `./generated/ManifestTypes`.
2. Cambie el nombre de todas las referencias de **InputsOutputs.IInputBag** a **IInputs**.
3. Cambie el nombre de todas las referencias de **InputsOutputs.IOutputBag** a IOutputs**.
4. Compile el proyecto para generar un nuevo archivo **ManifestTypes.d.ts** usando el comando `npm run build`.

## <a name="troubleshooting-and-workarounds"></a>Solución de problemas y soluciones alternativas

1. Si obtiene una notificación 1ES que pregunta cómo se están usando los pcf-scripts, tenga en cuenta que estos scripts se usan solo para crear los componentes del código pero no se empaquetan ni usan por el componente resultante.  
2. Si ha creado previamente un componente de código usando la versión 0.1.817.1 o anterior de los útiles y desea asegurarse de que se están usando los últimos módulos de compilación y de depuración, realice actualizaciones en el package.json como se muestra:
   
    ```JSON
     "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
    ```
3. El usuario recibe el error `Failed to retrieve information about Microsoft.PowerApps.MSBuild.Pcf from remote source <Feed Url>` cuando la generación produce error por problemas de autorización. La solución alternativa para este problema es:

   - Abrir el archivo NuGet.Config de **%APPDATA%\NuGet**. La fuente de la que el usuario obtiene el error debe estar presente en este archivo. 
   - Quite la fuente del archivo NuGet.Config o genere un símbolo PAT y agréguelo al archivo de Nuget.Config. Por ejemplo:

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

### <a name="see-also"></a>Vea también

[Limitaciones de PowerApps component framework](limitations.md)<br/>
[Referencia de la API de PowerApps component framework](reference/index.md)<br/>
[Información general sobre PowerApps component framework](overview.md)
