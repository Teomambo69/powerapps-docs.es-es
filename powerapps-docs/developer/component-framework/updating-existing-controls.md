---
title: Actualizar componentes de código existentes mediante las herramientas del marco de componentes de PowerApps | Microsoft Docs
description: Actualizar componentes mediante las herramientas del marco de componentes de PowerApps
keywords: Marco de componentes de PowerApps, componente de código, marco de componentes
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 05e32fb7e098dad3aabf36f2efdaf311c1bea327
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340239"
---
# <a name="update-existing-code-components"></a>Actualizar componentes de código existentes 

Si es un participante de versión preliminar privada del marco de componentes de PowerApps para aplicaciones controladas por modelos y ya ha compilado componentes de código, debe realizar algunas actualizaciones secundarias para que sea compatible con las nuevas estructuras de proyecto centradas en ALM. 

Se necesitan algunos cambios para usar las nuevas herramientas de la CLI de PowerApps con los componentes de código del marco de componentes de PowerApps existentes.

> [!NOTE]
> Este tema solo es aplicable para actualizar componentes de código para aplicaciones controladas por modelos porque las herramientas de la CLI de PowerApps no están disponibles en el momento de la versión preliminar privada de las aplicaciones controladas por modelos.  

## <a name="creating-an-empty-project"></a>Crear un proyecto vacío

Use la CLI de PowerApps para crear un nuevo proyecto vacío para el componente de código. Más información: [crear componentes mediante herramientas](create-custom-controls-using-pcf.md)

Una vez creado el proyecto, migre el origen del componente de código al nuevo proyecto:

1. Copie o reemplace el archivo de origen de componentes del archivo de origen anterior en **index. ts**.
2. Copie o reemplace el contenido de **ControlManifest. XML** en el archivo **ControlManifest. Input. XML** .
3. Copie todos los demás recursos de componentes periféricos, como CSS, RESX o IMG, en la subcarpeta correspondiente del proyecto anterior al nuevo proyecto.

## <a name="updating-manifest-file"></a>Actualizando el archivo de manifiesto

El archivo `ControlManifest.xml` que define las propiedades del componente de código se reemplaza por el archivo `ControlManifest.Input.xml`. En caso contrario, debería haber un pequeño cambio en el esquema entre los dos archivos.

Pero hay un par de cambios semánticos importantes:

1. La entrada de recurso `code` debe apuntar ahora al archivo de código fuente precompilado del componente de código. El nombre de archivo predeterminado es **index. ts**.

   Por ejemplo, si el origen del componente se implementa en un archivo denominado `MyControl.ts`, la entrada `code` de `ControlManifest.Input.xml` debe apuntar a ese archivo. El archivo `code` debe ser también un archivo TypeScript válido. Esto contrasta con los archivos de manifiesto heredados que especifican el archivo de salida de JS compilado en la entrada `code`.
2. El atributo `path` del elemento resource como `code` o `css` ahora hace referencia a la ruta de acceso local al archivo en el disco. Por ejemplo:

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

El atributo `path` anterior indica que el archivo de `YourControlName.css` se encuentra en la subcarpeta `css` relativa al directorio actual en el que reside el `ControlManifest.Input.xml` en el disco.

Actualice los archivos ControlManifest. Input. XML como se indica a continuación:

1. Edite la entrada `code` en `ControlManifest.Input.xml` en el archivo de código fuente precompilado del componente de código (normalmente index. TS).
2. Edite las rutas de acceso de los recursos para hacer referencia correctamente a las rutas de acceso relativas a los archivos del disco.

## <a name="updating-the-project-files"></a>Actualización de los archivos de proyecto

Si ha creado un componente con la versión anterior de las herramientas y desea aprovechar las ventajas de las funcionalidades más recientes, asegúrese de actualizar los archivos de proyecto como se muestra aquí:

1. Actualice los proyectos existentes para usar los módulos más recientes.
 
   - Actualice la etiqueta de versión en el `pcfproj` ubicado dentro de la carpeta de proyecto del marco de componentes de PowerApps de la siguiente manera:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Pcf" Version="1.*"/>
      ```
   - Actualice la etiqueta de versión en el `cdsproj` ubicado dentro de la carpeta de proyecto de la solución de la siguiente manera:

      ```XML
      <Packagereference Include="Microsoft.PowerApps.MSBuild.Solution" Version="1.*"/>
      ```

      > [!NOTE] 
      > Después de realizar los cambios anteriores, ejecute el comando `msbuild /t:restore` para actualizar el proyecto a la versión correcta.


   - Actualice la etiqueta de versión en el archivo de `package.json` que se encuentra dentro de la carpeta de proyecto del marco de componentes de PowerApps:

      ```JSON
      "devDependencies":{
       "pcf-scripts": "^1",
       "pcf-start": "^1"
          }
      ```
     > [!NOTE]
     > Después de realizar los cambios anteriores, ejecute el comando `npm update` para actualizar el proyecto a la versión correcta.

2. Si ya ha creado un perfil de autenticación, deberá volver a crearlo. Esto se debe a que se ha agregado una nueva propiedad al perfil para admitir la nube no pública. Puede hacerlo de la siguiente manera:
 
    - Ejecutar el `pac auth clear` de comandos.
    - Ejecutar el `pac auth create --url <your org url>` de comandos.

## <a name="updating-your-project-with-the-latest-node-modules"></a>Actualización del proyecto con los módulos de nodo más recientes

Los proyectos heredados requieren la recuperación de los últimos módulos NPM para aprovechar las funcionalidades más recientes de la CLI. Para actualizar los módulos de nodo que descargó anteriormente, vaya al directorio del proyecto en el símbolo del sistema para desarrolladores y ejecute el comando `npm update`. 

## <a name="using-es6-module-syntax"></a>Usar la sintaxis del módulo ES6

Las herramientas de compilación esperan que el origen del componente se exporte con el formato de módulo estándar de ES6. Los componentes heredados se suelen exportar como módulos internos (también conocidos como espacios de nombres). El archivo de código fuente del componente debe modificarse como se indica a continuación para alinearse con las nuevas herramientas de compilación.

1. Abra el archivo de código fuente que implementa el componente de código (por ejemplo, index. TS).
2. Use la sintaxis de exportación de ES6 estándar quitando la declaración del módulo.

     Nunca
     ```TypeScript
     module SampleNamespace
     {
    export class TSLinearInputControl implements ComponentFramework.StandardControl<InputsOutputs.IInputBag, InputsOutputs.IOutputBag> {
          <your class implementation>
           }
            }
     
      ```
    Continuación
    ```TypeScript
     export class YourControlName implements ComponentFramework.StandardControl<IInputs, IOutputs> { 
          <your class implementation>
          }
   ```

## <a name="using-generated-manifest-typing-file"></a>Usar archivo de escritura de manifiesto generado

Los proyectos heredados requieren la creación y edición manuales de un `inputsOutputs.d.ts` escribir el archivo, que normalmente se encuentra en la subcarpeta `private_typing`. Ahora, las herramientas de la CLI de PowerApps generan automáticamente este archivo en el momento de la compilación. 

Code-gen garantiza que las definiciones de `type` usadas en el código fuente del componente permanecen sincronizadas con `types` definidas en el archivo de manifiesto del componente.

Se cambia el nombre del archivo de escritura a `ManifestTypes.d.ts` y ahora se genera en una subcarpeta denominada `generated`. Además, se cambia el nombre de los tipos `InputsOutputs.IInputBag` y `InputsOutputs.IOutputBag` a `IInputs` y `IOutputs` respectivamente.

Para usar el nuevo archivo de escritura:

1. Importe el nuevo archivo de `ManifestTypes.d.ts` agregando la siguiente línea en la parte superior del archivo de origen del componente:

    importe {IInputs, IOutputs} desde `./generated/ManifestTypes`.
2. Cambie el nombre de todas las referencias de **InputsOutputs. IInputBag** a **IInputs**.
3. Cambie el nombre de todas las referencias de **InputsOutputs. IOutputBag** a **IOutputs**.
4. Compile el proyecto para generar un nuevo archivo **ManifestTypes. d. ts** mediante el comando `npm run build`.

## <a name="troubleshooting-and-workarounds"></a>Solución de problemas y soluciones alternativas

1. Si recibe una notificación de 1ES en la que se le pregunta cómo se usan los scripts de PCF, tenga en cuenta que estos scripts solo se usan para compilar los componentes de código, pero el componente resultante no los incluye o los utiliza.  
2. Si ha creado previamente un componente de código mediante la versión de herramientas 0.1.817.1 o anterior y desea asegurarse de que se usan los módulos de compilación y depuración más recientes, realice las actualizaciones en package. JSON como se muestra a continuación:
   
    ```JSON
     "dependencies": { "@types/node": "^10.12.18", "@types/powerapps-component-framework": "1.1.0"}, "devDependencies": { "pcf-scripts": "~0", "pcf-start": "~0" } 
    ```
3. El usuario obtiene el error `Failed to retrieve information about Microsoft.PowerApps.MSBuild.Pcf from remote source <Feed Url>` cuando se produce un error en la compilación para problemas de autorización. Esta es la solución alternativa para esto:

   - Abra el archivo NuGet. config desde **%AppData%\NuGet**. La fuente desde la que el usuario recibe el error debe estar presente en este archivo. 
   - Quite la fuente del archivo NuGet. config o genere un token PAT y agréguelo al archivo Nuget. config. Por ejemplo:

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

[Limitaciones de la plataforma de componentes de PowerApps](limitations.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)
