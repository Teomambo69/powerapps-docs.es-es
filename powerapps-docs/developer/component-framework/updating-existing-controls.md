---
title: Actualizar componentes personalizados existentes mediante útiles de marco de componentes de PowerApps| Microsoft Docs
description: Actualizar componentes mediante útiles de marco de componentes de PowerApps
keywords: 'Marco de componentes de PowerApps, Componente personalizado, Marco de componentes'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---
# <a name="updating-existing-custom-components"></a>Actualizar componentes personalizados existentes 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Si usted es participante de Versión preliminar privada del marco de componentes de PowerApps y ha creado ya componentes personalizados, deberá realizar algunas actualizaciones de menor importancia para que sea compatible con las nuevas estructuras de proyecto centradas en ALM. Para usar las nuevas herramientas de creación del marco de componentes de PowerApps con su origen de componentes personalizados existentes del marco de componentes de PowerApps, algunos cambios son necesarios.

## <a name="creating-an-empty-project"></a>Crear un proyecto vacío

Utilice PowerApps CLI para crear un nuevo proyecto vacío para el componente personalizado. Más información [Crear componentes usando los útiles](create-custom-controls-using-pcf.md).
Una vez el proyecto se ha creado, migre el origen de componente personalizado al nuevo proyecto:

1. Copie o reemplace el origen del componente desde el antiguo archivo de origen en **index.ts**.
2. Copie o reemplace el contenido de **ControlManifest.xml** en el archivo **ControlManifest.Input.xml**.
3. Copie todos los demás recursos de componentes periféricos como css, resx, img en la subcarpeta correspondiente del antiguo proyecto en el nuevo proyecto.

## <a name="updating-manifest-file"></a>Actualizar el archivo de manifiesto

El archivo `ControlManifest.xml` que define las propiedades de componente personalizado es reemplazado por un archivo `ControlManifest.Input.xml`. Por lo demás debe haber pocos cambios en el esquema entre los dos archivos.
Hay un par de cambios semánticos importantes.

1. La entrada de recurso `code` ahora debe señalar al archivo de origen precompilado del componente personalizado. El nombre de archivo se ha establecido de forma predeterminada como **index.ts**.
Por ejemplo, si el origen del componente se implementa en un archivo llamado `MyControl.ts`, la entrada `code` en `ControlManifest.Input.xml` debe señalar a ese archivo. El archivo `code` también debe ser un archivo Typescript válido. Esto contrasta con los archivos de manifiesto antiguos que especificaban el archivo de salida JS compilado en la entrada `code`.
2. El atributo `path` del elemento de recurso como `code` o `css` ahora hace referencia a la ruta de acceso local al archivo en el disco. Por ejemplo:

    ```XML
   <resources>
    <css path="css/YourControlName" order="1"/>
    </resources>
    ```

El atributo `path` anterior indica que el archivo `YourControlName.css` se encuentra en la subcarpeta `css` en relación con el directorio actual donde `ControlManifest.Input.xml` se encuentra en el disco.
Actualice los archivos ControlManifest.Input.xml de este modo:

1. Edite la entrada `code` en `ControlManifest.Input.xml` al archivo de origen precompilado del componente personalizado (normalmente será index.ts).
2. Edite las rutas de los recursos para que hagan referencia correctamente a las rutas de acceso relativas a los archivos en el disco.

## <a name="using-es6-module-syntax"></a>Uso de la sintaxis de módulo ES6

Las herramientas de generación esperan que el origen de componente se exporte usando el formato de módulo ES6 estándar. Los controles antiguos se exportan normalmente como módulos internos (también llamados espacios de nombres). Para alinearse con las nuevas herramientas de generación el origen de componente se deben modificar de este modo.

1. Abra el archivo de origen que implementa el componente personalizado (por ejemplo index.ts).
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

Los proyectos antiguos requería la creación y edición manuales de un archivo de escritura `inputsOutputs.d.ts`. Este archivo se encuentra normalmente en la subcarpeta `private_typing`. Los nuevos útiles ahora generan automáticamente este archivo en la compilación. La generación de código garantiza que las definiciones de `type` usadas en el código de origen del componente permanezcan en sincronizadas con `types` definidos en el archivo de manifiesto del componente.  
El archivo de escritura cambia de nombre a `ManifestTypes.d.ts` y ahora se genera en una subcarpeta llamada `generated`. Además, los tipos `InputsOutputs.IInputBag` y `InputsOutputs.IOutputBag` cambian de nombre a `IInputs` y `IOutputs` respectivamente.
Para utilizar el nuevo archivo de escritura:

1. Importe el nuevo archivo `ManifestTypes.d.ts` agregando la siguiente línea en la parte superior del archivo de origen del componente: { IInputs, IOutputs } from `./generated/ManifestTypes`.
2. Cambie el nombre de todas las referencias de **InputsOutputs.IInputBag** a **IInputs**.
3. Cambie el nombre de todas las referencias de **InputsOutputs.IOutputBag** a IOutputs**.
4. Compile el proyecto para generar un nuevo archivo **ManifestTypes.d.ts** usando el comando `npm run build`.

### <a name="see-also"></a>Vea también

[Limitaciones del marco de componentes de PowerApps](limitations.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
