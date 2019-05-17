---
title: Depurar componentes personalizados | MicrosoftDocs
description: Cómo depurar un control personalizado mediante la depuración de Fiddler y nativa
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: index-page
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
---
# <a name="debugging-csutom-components"></a>Depurar componentes personalizados

Una vez que termine de implementar la lógica del control personalizado, ejecute el siguiente comando de iniciar el proceso de depuración `npm start`

> [!NOTE]
> Hoy solo puede visualizar el control de campo, pero se proporcionará próximamente compatibilidad para el conjunto de datos.

> [!div class="mx-imgBorder"]
> ![host-local](media/local-host.png "host local")

Como se muestra en la imagen de arriba, la ventana de exploración se abrirán con 3 secciones. El control se generará en el panel izquierdo mientras que el panel derecho se compone de las secciones **Entradas** y **Salidas**

  - La sección**Entradas** es una interfaz de usuario interactiva que muestra todas las propiedades y sus tipos y grupos de tipos definidos en manifest.xml. Permitir escribir datos ficticios para cada propiedad. 
  - La sección**Salidas** genera la salida cada vez que se llama al método `getOutputs` de un control.  
 
> [!NOTE]
> Si desea modificar `manifest.xml` o crear propiedades adicionales, deberá reiniciar el proceso de depuración antes de que aparezcan en la sección de entradas.

Cuando introduce datos ficticios, puede usar las funcionalidades de depuración del explorador para observar el comportamiento del control. Cada explorador proporciona una herramienta de depuración para ayudarle a depurar el código nativo en el explorador. Normalmente, puede activar la depuración en el explorador presionando la tecla **F12** para mostrar la herramienta de desarrollo nativa usada para depuración.

Por ejemplo, en **Microsoft Edge**,

- Presione **F12** para abrir inspector.
- Haga clic en el control
- En la barra superior, vaya a **Depurador** y luego empiece a buscar el nombre del control descrito en el archivo Manifest en la barra de búsqueda. Por ejemplo, escriba el nombre del control como `Hello World Control`.

     > [!div class="mx-imgBorder"]
     > ![debug-control](media/debug-control.png "Depurar control")

> [!NOTE]
> Siempre es conveniente establecer puntos de interrupción en los métodos de ciclo de vida del control como `init` y `updateView`

También puede interactuar con el control localmente en tiempo real y observar elementos en DOM estableciendo un punto de interrupción en la pestaña Buzón del origen de la siguiente manera:

> [!div class="mx-imgBorder"]
> ![host-local](media/local-host.png "host local")

> [!div class="mx-imgBorder"]
> ![debug-control](media/debug-control-1.png "Depurar control 1")

## <a name="fiddler-autoresponder"></a>Fiddler AutoResponder

Use Fiddler AutoResponder para depurar rápidamente sus componentes personalizados. Instale [Fiddler](https://www.telerik.com/download/fiddler) y siga los pasos para configurar [AutoResponder](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder)

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](overview.md)