---
title: Depurar componentes personalizados | MicrosoftDocs
description: Cómo depurar un componente personalizado mediante la depuración de Fiddler y nativa
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
---
# <a name="debug-custom-components"></a>Depurar componentes personalizados

Una vez que termine de implementar la lógica del componente personalizado, empiece a probar y depurar el componente personalizado mediante el comando `npm start`. De este modo se compila el componente personalizado y se abre en el agente de prueba local.

> [!div class="mx-imgBorder"]
> ![agente de prueba 1](media/test-harness-1.png "agente de prueba 1")

Como se muestra en la imagen de arriba, la ventana del explorador se abre con 4 secciones. El componente personalizado se genera en el panel izquierdo mientras que el panel derecho se compone de las secciones **Entradas de contexto**, **Entradas de datos** y **Salidas**.

- La sección**Entradas de contexto** proporciona una forma de especificar el factor de forma y de probar el componente personalizado con cada factor de forma (web, tableta, teléfono). Esto es especialmente útil cuando el componente personalizado depende de una capacidad específica de factor de forma. En la nueva versión, puede tener la capacidad de especificar la altura y el ancho.
- La sección**Entradas de datos** es una interfaz de usuario interactiva que muestra todas las propiedades y sus tipos o grupos de tipos definidos en el archivo de manifiesto. Permitir escribir datos ficticios para cada propiedad. 
- La sección**Salidas** genera la salida cada vez que se llama al método `getOutputs` de un componente.  

     > [!div class="mx-imgBorder"]
     > ![agente de prueba 2](media/test-harness-2.png "agente de prueba 2")

> [!NOTE]
> Si desea modificar el archivo `manifest.xml` o crear propiedades adicionales, deberá reiniciar el proceso de depuración antes de que aparezcan en la sección de entradas.

## <a name="test-custom-components-with-mock-data"></a>Probar componentes personalizados con datos ficticios

- En el caso de componentes de campo, puede introducir el valor y el tipo de entrada para cada propiedad definida en su **ControlManifest.Input.xml** como se muestra a continuación

   > [!div class="mx-imgBorder"]
   > ![agente de prueba 2.5](media/test-harness-2.5.png "agente de prueba 2.5")

- Para conjuntos de datos, puede cargar un archivo CSV con datos de prueba. Se puede crear o exportar manualmente en formato .csv directamente desde su entorno. Una vez que un archivo CSV válido está disponible, se puede cargar como se indica a continuación:

   > [!div class="mx-imgBorder"]
   > ![agente de prueba 3](media/test-harness-3.png "agente de prueba 3")

- Después de cargar un archivo CSV, vincule cada propiedad definida en su **ControlManifest.Input.xml** a una columna del CSV. Esto hace seleccionando la columna para cada propiedad como se indica a continuación:

    > [!div class="mx-imgBorder"]
    > ![agente de prueba 4](media/test-harness-4.png "agente de prueba 4")

- Si no tiene ninguna propiedad definida en el **ControlManifest.Input.xml**, todas las columnas se cargan automáticamente en el agente.

   > [!div class="mx-imgBorder"]
   > ![agente de prueba 5](media/test-harness-5.png "agente de prueba 5")

## <a name="debug-custom-components-using-native-browsers"></a>Depurar componentes personalizados mediante exploradores nativos

Puede usar las funcionalidades de depuración del explorador para observar el comportamiento del componente. Cada explorador proporciona una herramienta de depuración para ayudarle a depurar el código nativo en el explorador. Normalmente, puede activar la depuración en el explorador presionando la tecla **F12** para mostrar la herramienta de desarrollo nativa usada para depuración.

Por ejemplo, en **Microsoft Edge**,

- Presione **F12** para abrir el inspector.
- Haga clic en el componente
- En la barra superior, vaya a **Depurador** y luego empiece a buscar el nombre del componente descrito en el archivo de manifiesto en la barra de búsqueda. Por ejemplo, escriba el nombre del componente como `Hello World component`.

     > [!div class="mx-imgBorder"]
     > ![componente-depuración](media/debug-control.png "Componente de depuración")

> [!NOTE]
> Siempre es conveniente establecer puntos de interrupción en los métodos de ciclo de vida del componente como `init` y `updateView`.

También puede interactuar con el componente localmente en tiempo real y observar elementos en DOM estableciendo un punto de interrupción en la pestaña Buzón del origen de la siguiente manera:

> [!div class="mx-imgBorder"]
> ![componente-depuración](media/debug-control-1.png "Componente de depuración 1")

## <a name="fiddler-autoresponder"></a>Fiddler AutoResponder

Use Fiddler AutoResponder para depurar rápidamente sus componentes personalizados. Instale [Fiddler](https://www.telerik.com/download/fiddler) y siga los pasos para configurar [AutoResponder](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)
