---
title: Crear y generar un componente personalizado| Microsoft Docs
description: Empiece a crear un componente mediante útiles de marco de componentes de PowerApps
keywords: 'Marco de componentes de PowerApps, Componentes personalizados, Marco de componentes'
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

# <a name="create-and-build-a-custom-component"></a>Crear y generar un componente personalizado

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

En este tema se proporciona información sobre cómo crear e implementar un componente personalizado mediante PowerApps Component Framework.

Asegúrese de que tiene instalado Microsoft PowerApps CLI

## <a name="create-a-new-component"></a>Crear un componente

Para empezar, abra un nuevo Developer Command Prompt for VS 2017 después de instalar PowerApps CLI.

1. En el Developer Command Prompt for VS 2017, cree una nueva carpeta en el disco duro local, por ejemplo, *C:\Users\<your name>\Documents\My_PCF_Control*
2. Vaya a la carpeta recién creada usando el comando `cd <specify your new folder path>`
3. Ejecute el comando siguiente para crear un nuevo proyecto de componente pasando algunos parámetros básicos:

    `pac pcf init --namespace <specify your namespace here> --name <put component name here> --template <component type>`
 
   > [!NOTE]
   > Actualmente ofrecemos dos tipos de componentes: **campo** y **conjunto de datos**.

4. Para recuperar todas las dependencias necesarias de proyecto, ejecute el comando `npm install`.
5. Abra la carpeta de proyecto (`C:\Users\<your name>\Documents\My_PCF_Control\<component name>`) en cualquier entorno de desarrollo de su elección y empiece con el desarrollo del componente personalizado.

## <a name="build-your-component"></a>Crear su componente

Para generar el componente puede abrir la carpeta en Visual Studio Code y usar el comando (Ctrl-Mayús-B), luego seleccione las opciones de compilación. Como alternativa, puede compilar el componente rápidamente mediante el comando `npm run build` en la ventana de Developer Command Prompt for VS 2017.

> [!TIP]
> Para depurar el componente durante o después de operaciones de compilación, consulte [Depurar un componente personalizado](debugging-custom-controls.md).

## <a name="known-configuration-issues-and-workarounds"></a>Problemas conocidos de configuración y soluciones alternativas

**Msbuild error MSB4036:**

1. El nombre de la tarea en el archivo del proyecto es igual que el nombre de la clase de tarea.
2. La clase de tarea es pública e implementa la interfaz de Microsoft.Build.Framework.ITask.
3. La tarea se declara correctamente con \<UsingTask> en el archivo de proyecto o en los archivos *.tasks situados en el directorio <path>.

**Resolución**

1. Abra Instalador de Visual Studio. 
1. Para VS 2017, seleccione **Modificar**. 
1. Haga clic en Componentes individuales.
1. En Herramientas de código, active **Destinos de NuGet y tareas de compilación**.

### <a name="see-also"></a>Vea también

[Depurar componentes personalizados](debugging-custom-controls.md)<br/>
[Empaquete un componente personalizado](import-custom-controls.md)<br/>
[Agregar componentes personalizados a un campo o una entidad](add-custom-controls-to-a-field-or-entity.md)<br/>
[Actualizar componentes personalizados existentes](updating-existing-controls.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
