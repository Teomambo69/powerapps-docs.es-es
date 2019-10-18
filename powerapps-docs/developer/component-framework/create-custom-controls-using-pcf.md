---
title: Crear y compilar un componente de código | Microsoft Docs
description: Empezar a crear un componente con las herramientas del marco de componentes de PowerApps
keywords: Marco de componentes de PowerApps, componentes de código, marco de componentes
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 286458da2ed7b7b94f92b86355bf8785161ef778
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347024"
---
# <a name="create-and-build-a-code-component"></a>Crear y compilar un componente de código

En este tema se explica cómo crear e implementar componentes de código mediante la CLI de PowerApps. Asegúrese de que ha instalado [Microsoft POWERAPPS CLI](https://aka.ms/PowerAppsCLI).

## <a name="create-a-new-component"></a>Crear un nuevo componente

Para empezar, Abra **símbolo del sistema para desarrolladores para VS 2017 después de** instalar la CLI de PowerApps.

1. En el Símbolo del sistema para desarrolladores de VS 2017, cree una nueva carpeta en el equipo local, por ejemplo, *C:\Users\your name\Documents\My_PCF_Component* con el comando `mkdir <Specify the folder name>`.
2. Vaya a la carpeta recién creada con la `cd <specify your new folder path>` de comandos.
3. Ejecute el siguiente comando para crear un nuevo proyecto de componente pasando algunos parámetros básicos:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Actualmente, la CLI de PowerApps admite dos tipos de componentes: **Field** y **DataSet**.  En el caso de las aplicaciones de Canvas, solo se admite el tipo de **campo** para esta vista previa experimental.

4. Para recuperar todas las dependencias necesarias del proyecto, ejecute el comando `npm install`.
5. Abra la carpeta del proyecto `C:\Users\<your name>\Documents\<My_PCF_Component>` en el entorno de desarrollador que prefiera y empiece a trabajar con el desarrollo de componentes de código. La forma más rápida de empezar es mediante la ejecución de `code .` desde el símbolo del sistema una vez que se encuentra en el directorio `C:\Users\<your name>\Documents\<My_PCF_Component>`. Este comando abre el proyecto de componente en Visual Studio Code.

## <a name="build-your-component"></a>Compilar el componente

Para compilar el proyecto de componente, abra la carpeta de proyecto que contiene `package.json` en Visual Studio Code y use el comando (Ctrl-Shift-B) y, a continuación, seleccione las opciones de compilación. Como alternativa, puede compilar el componente rápidamente con el comando `npm run build` en la ventana Símbolo del sistema para desarrolladores para VS 2017.

> [!TIP]
> Para depurar el componente durante o después de la operación de compilación, vea [depurar un componente de código](debugging-custom-controls.md).

Una vez que haya terminado de implementar la lógica del componente en TypeScript, debe agrupar todos los elementos de componente de código en un archivo de solución para poder importar la solución en Common Data Service. Más información: [empaquetar un componente de código](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>Problemas y soluciones de configuración conocidos

**Error de MSBuild MSB4036:**

1. El nombre de la tarea en el archivo de proyecto es el mismo que el nombre de la clase de tarea.
2. La clase de tarea es pública e implementa la interfaz Microsoft. Build. Framework. ITask.
3. La tarea se ha declarado correctamente con *\<UsingTask >* en el archivo de proyecto o en los archivos *. Tasks ubicados en el directorio path.

**Traducción**

1. Abra Instalador de Visual Studio. 
1. Para Visual Studio 2017, seleccione **modificar**. 
1. Seleccione **componentes individuales**.
1. En herramientas de código, compruebe los **destinos de NuGet & las tareas de compilación**.

**Prefijo del publicador**

Si un componente se crea con una versión de herramientas de la CLI de PowerApps inferior a 0.4.3, se producirá un error al intentar volver a importar el archivo de solución en Common Data Service. El error se produce porque el nombre del componente recién importado se anexa ahora con el prefijo del publicador para garantizar su exclusividad y evitar colisiones.

**Solución alternativa**:

- Elimine la solución que contiene el componente correspondiente de Common Data Service. Si el componente ya está configurado en un formulario o una cuadrícula, debe quitarlo primero porque la solución de componentes tenía una dependencia en la configuración.  
- Importe la nueva solución con actualizaciones al componente creado con la versión más reciente de la CLI.
- Los componentes recién importados se pueden configurar ahora en formularios o cuadrículas.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>Vea también

[Componentes de código de depuración](debugging-custom-controls.md)<br/>
[Empaquetar un componente de código](import-custom-controls.md)<br/>
[Agregar componentes de código a un campo o una entidad](add-custom-controls-to-a-field-or-entity.md)<br/>
[Actualizar componentes de código existentes](updating-existing-controls.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)
