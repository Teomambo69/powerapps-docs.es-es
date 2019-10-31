---
title: Crear y generar un componente de código| Microsoft Docs
description: Empiece a crear un componente mediante útiles de PowerApps component framework
keywords: 'PowerApps component framework, componentes de código, Component Framework'
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
---

# <a name="create-and-build-a-code-component"></a>Crear y generar un componente de código

En este tema se demuestra cómo crear e implementar componentes de código mediante PowerApps CLI. Asegúrese de que tiene instalado [Microsoft PowerApps CLI](https://aka.ms/PowerAppsCLI).

## <a name="create-a-new-component"></a>Crear un componente

Para empezar, abra un nuevo **Developer Command Prompt for VS 2017** después de instalar PowerApps CLI.

1. En el Developer Command Prompt for VS 2017, cree una nueva carpeta en el equipo local, por ejemplo, *C:\Users\your name\Documents\My_PCF_Component* utilizando el comando `mkdir <Specify the folder name>`.
2. Vaya a la carpeta recién creada usando el comando `cd <specify your new folder path>`.
3. Ejecute el comando siguiente para crear un nuevo proyecto de componente pasando algunos parámetros básicos:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Actualmente PowerApps CLI admite dos tipos de componentes: **campo** y **conjunto de datos**.  Para aplicaciones de lienzo, solo se admite el tipo **campo** para esta vista previa piloto.

4. Para recuperar todas las dependencias necesarias de proyecto, ejecute el comando `npm install`.
5. Abra la carpeta de proyecto `C:\Users\<your name>\Documents\<My_PCF_Component>` en cualquier entorno de desarrollo de su elección y empiece con el desarrollo del componente de código. La forma más rápida de empezar es ejecutando `code .` desde el símbolo del sistema una vez que está en el directorio `C:\Users\<your name>\Documents\<My_PCF_Component>`. Este comando abre el proyecto de componente en Código de Visual Studio.

## <a name="build-your-component"></a>Crear su componente

Para generar el proyecto de componentes abra la carpeta de proyecto que contiene `package.json` en Código de Visual Studio y use el comando (Ctrl-Mayús-B), y luego seleccione las opciones de compilación. Como alternativa, puede compilar el componente rápidamente mediante el comando `npm run build` en la ventana de Developer Command Prompt for VS 2017

> [!TIP]
> Para depurar el componente durante o después de operaciones de compilación, consulte [Depurar un componente de código](debugging-custom-controls.md).

Una vez que haya finalizado de implementar la lógica de componente en TypeScript, necesita agrupar todos los elementos de componente de código en un archivo de solución para que pueda importar la solución en Common Data Service. Más información: [Empaquetar un componente de código](import-custom-controls.md)

## <a name="known-configuration-issues-and-workarounds"></a>Problemas conocidos de configuración y soluciones alternativas

**Msbuild error MSB4036:**

1. El nombre de la tarea en el archivo del proyecto es igual que el nombre de la clase de tarea.
2. La clase de tarea es pública e implementa la interfaz de Microsoft.Build.Framework.ITask.
3. La tarea se declara correctamente con *\<UsingTask>* en el archivo de proyecto o en los archivos *.tasks situados en el directorio de la ruta.

**Resolución**

1. Abra Instalador de Visual Studio. 
1. Para VS 2017, seleccione **Modificar**. 
1. Haga clic en Componentes individuales.
1. En Herramientas de código, active **Destinos de NuGet y tareas de compilación**.

**Prefijo de publicador**

Si se crea un componente con una versión de útiles de PowerApps CLI menor que 0.4.3, se producirá un error al intentar reimportar el archivo de solución en Common Data Service. Se produce el error porque el nombre del componente recién importado se anexa ahora con el prefijo del editor para garantizar su singularidad y evitar colisiones.

**Solución alternativa**:

- Elimine la solución que contiene el componente relevante de Common Data Service. Si el componente ya está configurado en un formulario o una cuadrícula, debe quitarlo primero de ahí ya que la solución de componente tenía dependencia de la configuración.  
- Importe la nueva solución con actualizaciones en el componente compilado por la última versión de CLI.
- Los componentes recién importados ahora pueden configurarse en formularios o cuadrículas.  


<!--2. When the components are created with the publisher prefix in mixed or upper case using the new CLI tooling version, it throws an error while importing the solution. This happens because the updated tooling version (0.4.3 and newer) now enforces the platform standard for lower case publisher prefix.

   **Workaround**:

    Update the solution and customizations to ensure that the associated prefix is modified to lower case and import the new solution into Common Data Service.-->


### <a name="see-also"></a>Vea también

[Depurar componentes de código](debugging-custom-controls.md)<br/>
[Empaquete un componente de código](import-custom-controls.md)<br/>
[Agregar componentes de código a un campo o una entidad](add-custom-controls-to-a-field-or-entity.md)<br/>
[Actualizar componentes de código existentes](updating-existing-controls.md)<br/>
[Referencia de la API de PowerApps component framework](reference/index.md)<br/>
[Información general sobre PowerApps component framework](overview.md)
