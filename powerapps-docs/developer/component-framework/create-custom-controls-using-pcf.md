---
title: Crear y generar un componente de código| Microsoft Docs
description: Empiece a crear un componente mediante útiles de Power Apps component framework
keywords: Power Apps component framework, componentes de código, Component Framework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: 8235c8ed0400223a36324a301fdf172a0610efec
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "2894998"
---
# <a name="create-and-build-a-code-component"></a>Crear y generar un componente de código

En este tema se demuestra cómo crear e implementar componentes de código mediante Power Apps CLI. Asegúrese de que tiene instalado [Microsoft Power Apps CLI](https://aka.ms/PowerAppsCLI).

## <a name="create-a-new-component"></a>Crear un componente

Para comenzar, abra **Developer Command Prompt for VS 2017** después de instalar Power Apps CLI.

1. En el Developer Command Prompt for VS 2017, cree una nueva carpeta en el equipo local, por ejemplo, *C:\Users\your name\Documents\My_code_Component* utilizando el comando `mkdir <Specify the folder name>`.
2. Vaya a la carpeta recién creada usando el comando `cd <specify your new folder path>`.
3. Cree un nuevo proyecto de componente pasando algunos parámetros básicos utilizando el comando:

    ```CLI
    pac pcf init --namespace <specify your namespace here> --name <Name of the code component> --template <component type>
    ```
 
   > [!NOTE]
   > Actualmente, Power Apps CLI admite dos tipos de componentes: **campo** y **conjunto de datos** para las aplicaciones basadas en modelo.  Para aplicaciones de lienzo, solo se admite el tipo **campo** para esta vista previa piloto.

4. Para recuperar todas las dependencias necesarias de proyecto, ejecute el comando `npm install`.
5. Abra la carpeta de proyecto `C:\Users\<your name>\Documents\<My_code_Component>` en cualquier entorno de desarrollo de su elección y empiece con el desarrollo del componente de código. La forma más rápida de empezar es ejecutando `code .` desde el símbolo del sistema una vez que está en el directorio `C:\Users\<your name>\Documents\<My_code_Component>`. Este comando abre el proyecto de componente en Código de Visual Studio.
6. Implemente los artefactos necesarios para el componente como manifiesto, lógica de componente y estilo y después compile el proyecto de componente. Más información: [Crear el primer componente de código](implementing-controls-using-typescript.md)

## <a name="build-your-component"></a>Crear su componente

Para generar el proyecto de componentes abra la carpeta de proyecto que contiene `package.json` en Código de Visual Studio y use el comando (Ctrl-Mayús-B), y luego seleccione las opciones de compilación. Como alternativa, puede compilar el componente rápidamente mediante el comando `npm run build` en la ventana de Developer Command Prompt for VS 2017.

> [!TIP]
> Para depurar el componente durante o después de operaciones de compilación, consulte [Depurar un componente de código](debugging-custom-controls.md).

Cuando finalice la implementación de lógica de componente en TypeScript, deberá agrupar todos los elementos de componente de código en un archivo de solución para que pueda importar la solución en Common Data Service. Más información: [Empaquetar un componente de código](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>Problemas conocidos de configuración y soluciones alternativas

**Msbuild error MSB4036:**

1. El nombre de la tarea en el archivo del proyecto es igual que el nombre de la clase de tarea.
2. La clase de tarea es pública e implementa la interfaz de Microsoft.Build.Framework.ITask.
3. La tarea se declara correctamente con *\<UsingTask>* en el archivo de proyecto o en los archivos *.tasks situados en el directorio de la ruta.

**Resolución**

1. Abra Instalador de Visual Studio. 
1. Para Visual Studio 2017, seleccione **Modificar**. 
1. Seleccione **Componentes individuales**.
1. En Herramientas de código, active **Destinos de NuGet y tareas de compilación**.

**Prefijo de publicador**

Si se crea un componente usando útiles Power Apps CLI de una versión menor que 0.4.3, se producirá un error al intentar reimportar el archivo de solución en Common Data Service. Se produce el error porque el nombre del componente recién importado se anexa ahora con el prefijo del editor para garantizar su singularidad y evitar colisiones.

**Solución alternativa**:

- Elimine la solución que contiene el componente relevante de Common Data Service. Si ta está configurado el componente en un formulario o una cuadrícula, deberá quitarse de ahí porque la solución de componente tenía una dependencia en la configuración.  
- Importe la nueva solución con actualizaciones del componente compilado por la última versión de CLI.
- Los componentes recién importados ahora pueden configurarse en formularios o cuadrículas.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>Vea también

[Depurar componentes de código](debugging-custom-controls.md)<br/>
[Empaquete un componente de código](import-custom-controls.md)<br/>
[Agregar componentes de código a un campo o una entidad](add-custom-controls-to-a-field-or-entity.md)<br/>
[Actualizar componentes de código existentes](updating-existing-controls.md)<br/>
[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
