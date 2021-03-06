---
title: Crear y generar un componente de código| Microsoft Docs
description: Empiece a crear un componente mediante útiles de Power Apps component framework
keywords: Power Apps component framework, componentes de código, component framework
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/20/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2cbf58a-9112-45c2-b823-2c07a310714c
ms.openlocfilehash: ccdb91def96f485d4641a71a6d12199117063e78
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162165"
---
# <a name="create-and-build-a-code-component"></a>Crear y generar un componente de código

Este artículo muestra cómo crear e implementar componentes de código utilizando Power Apps CLI. Asegúrese de que tiene instalado [Microsoft Power Apps CLI](https://aka.ms/PowerAppsCLI).

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

Para generar el proyecto de componentes abra la carpeta de proyecto que contiene `package.json` en Código de Visual Studio y use el comando (Ctrl-Mayús-B), y luego seleccione las opciones de compilación. 

Como alternativa, puede compilar el componente rápidamente mediante el comando `npm run build` en la ventana de Developer Command Prompt for VS 2017.

> [!TIP]
> Para depurar el componente durante o después de operaciones de compilación, consulte [Depurar un componente de código](debugging-custom-controls.md).

Finalmente, cuando haya terminado de implementar la lógica del componente en TypeScript, debe agrupar todos los elementos del componente de código en un archivo de solución para poder importar la solución en Common Data Service. Más información: [Empaquetar un componente de código](import-custom-controls.md)

### <a name="see-also"></a>Vea también

[Depurar componentes de código](debugging-custom-controls.md)<br/>
[Empaquete un componente de código](import-custom-controls.md)<br/>
[Agregar componentes de código a un campo o una entidad](add-custom-controls-to-a-field-or-entity.md)<br/>
[Actualizar componentes de código existentes](updating-existing-controls.md)<br/>
[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
