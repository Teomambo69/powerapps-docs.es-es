---
title: Depurar componentes de código | MicrosoftDocs
description: Cómo depurar un componente de código mediante la depuración de Fiddler y nativa
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: cc4e4dd513cc627c7c9622854151f6a3f85c3e77
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162169"
---
# <a name="debug-code-components"></a>Depurar componentes de código

Después de implementar la lógica del componente de código, puede empezar a probar y depurar el componente de código utilizando el comando `npm start`. Este comando compila el componente de código y lo abre en el agente de prueba local.

> [!div class="mx-imgBorder"]
> ![Agente de prueba 1](media/test-harness-1.png "Agente de prueba 1")

Como se muestra en la imagen de arriba, la ventana del explorador se abre con cuatro secciones. El componente de código se genera en el panel izquierdo mientras que el panel derecho se compone de las secciones **Entradas de contexto**, **Entradas de datos** y **Salidas**.

- **Entradas de contexto** proporciona una forma de especificar el factor de forma y de probar el componente de código con cada factor de forma (web, tableta, teléfono). Esto es útil cuando el componente de código depende de una capacidad específica de factor de forma.
- **Entradas de datos** es una interfaz de usuario interactiva que muestra todas las propiedades y sus [tipos](manifest-schema-reference/types.md) o [grupos](manifest-schema-reference/type-group.md) de tipos definidos en el archivo de [manifiesto](manifest-schema-reference/manifest.md). Permitir escribir datos ficticios para cada propiedad. 
- **Salidas** representa la salida cada vez que se llama al método [getOutputs](reference/control/getoutputs.md) de un componente.  

     > [!div class="mx-imgBorder"]
     > ![Agente de prueba 2](media/test-harness-2.png "Agente de prueba 2")

> [!NOTE]
> Si desea modificar el archivo `ControlManifest.Input.xml` o crear propiedades adicionales, deberá reiniciar el proceso de depuración antes de que aparezcan en la sección de entradas.

## <a name="test-code-components-with-mock-data"></a>Probar componentes de código con datos ficticios

- En el caso de componentes de tipo *campo*, puede introducir el valor y el tipo de entrada para cada propiedad definida en su **ControlManifest.Input.xml** como se muestra aquí:

   > [!div class="mx-imgBorder"]
   > ![Agente de prueba 2.5](media/test-harness-2.5.png "Agente de prueba 2.5")

- Para componentes de tipo *conjuntos de datos*, puede cargar un archivo CSV con datos de prueba. Se puede crear o exportar manualmente en formato .csv directamente desde su entorno. Una vez que un archivo CSV válido está disponible, se puede cargar como se indica aquí:

   > [!div class="mx-imgBorder"]
   > ![agente de prueba 3](media/test-harness-3.png "agente de prueba 3")

- Después de cargar un archivo CSV, vincule cada propiedad definida en el **ControlManifest.Input.xml** a una columna del archivo CSV. Esto hace seleccionando la columna para cada propiedad como se indica aquí:

    > [!div class="mx-imgBorder"]
    > ![Agente de prueba 4](media/test-harness-4.png "Agente de prueba 4")

- Si no tiene ninguna propiedad definida en el archivo **ControlManifest.Input.xml**, todas las columnas se cargan automáticamente en el agente de prueba.

   > [!div class="mx-imgBorder"]
   > ![Agente de prueba 5](media/test-harness-5.png "Agente de prueba 5")


## <a name="watch-mode-in-test-harness"></a>Modo watch en agente de prueba

El agente de prueba admite el modo `watch` del que se puede aprovechar para proyectos de Power Apps component framework. Para habilitar el modo `watch`, inicie el agente de prueba usando el comando `npm start watch`. En modo `watch`, los cambios realizados en cualquiera de los activos de componente se reflejan automáticamente en el agente de prueba sin tener que reiniciarlo:

1.    `index.ts`.
2.    `ControlManifest.Input.xml`.
3.    Bibliotecas importadas en `index.ts`.
4.    Todos los recursos incluidos en el archivo de manifiesto.

## <a name="debug-code-components-using-native-browsers"></a>Depurar componentes de código mediante exploradores nativos

Puede usar las funcionalidades de depuración del explorador para observar el comportamiento del componente. Cada explorador proporciona una herramienta de depuración para ayudarle a depurar el código nativo en el explorador. 

Normalmente, puede activar la depuración en el explorador presionando la tecla **F12** para mostrar la herramienta de desarrollo nativa usada para depuración.

Por ejemplo, en **Microsoft Edge**:

- Presione **F12** para abrir el inspector.
- Seleccione un componente.
- En la barra superior, vaya a **Depurador** y luego busque el nombre del componente descrito en el archivo de manifiesto en la barra de búsqueda. Por ejemplo, escriba el nombre del componente como `Hello World component`.

     > [!div class="mx-imgBorder"]
     > ![Componente de depuración](media/debug-control.png "Componente de depuración")

> [!NOTE]
> Siempre es conveniente establecer puntos de interrupción en los métodos de ciclo de vida del componente como [init](reference/control/init.md) y [updateView](reference/control/updateview.md).

También puede interactuar con el componente localmente en tiempo real y observar elementos en DOM estableciendo un punto de interrupción en la pestaña *Orígenes* como se muestra aquí:

> [!div class="mx-imgBorder"]
> ![Componente de depuración](media/debug-control-1.png "Componente de depuración 1")

## <a name="fiddler-autoresponder"></a>Fiddler AutoResponder

Use Fiddler AutoResponder para depurar rápidamente sus componentes de código. Instale [Fiddler](https://www.telerik.com/download/fiddler) y siga los pasos para configurar [AutoResponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder).

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de Power Apps component framework](reference/index.md)<br/>
[Información general sobre Power Apps component framework](overview.md)
