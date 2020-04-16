---
title: Depuración del código JavaScript para aplicaciones basadas en modelos | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: conceptual
applies_to:
- Dynamics 365 (online)
ms.assetid: 3edad039-4397-4984-a29b-9307a7a2aaee
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f0441d5a96a3e35eb28f77c726591a6634be9704
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115672"
---
# <a name="debug-your-javascript-code-for-model-driven-apps"></a>Depuración del código JavaScript para aplicaciones basadas en modelos



Cada explorador proporciona algún tipo de extensión de depuración. Microsoft Edge e Internet Explorer proporcionan herramientas del desarrollador F12 que puede usar para depurar scripts en aplicaciones basadas en modelos. Las herramientas del desarrollador F12 se pueden abrir presionando F12 al ver una página con Microsoft Edge o Internet Explorer. Para obtener más información, consulte [Guía de las herramientas del desarrollador F12](https://docs.microsoft.com/microsoft-edge/f12-devtools-guide).

En Google Chrome, presione F12 para abrir las herramientas del desarrollador. Firebug es una popular extensión de explorador para desarrollo web con Mozilla Firefox. En Apple Safari, primero debe seleccionar el menú **Mostrar desarrollo** en la barra del menú de **Preferencias avanzadas**. A continuación puede elegir **Mostrar inspector web** en el menú **Desarrollo**.

Si usa bibliotecas JavaScript en aplicaciones basadas en modelos, las bibliotecas se cargan con la página web. En ocasiones puede resultar difícil aislar la biblioteca específica en el entorno de depuración. Al usar las herramientas de depuración en Microsoft Edge, en la pestaña **Depurador**, haga clic en el icono de carpeta en la esquina superior izquierda y expanda los scripts disponibles y busque el que tiene el nombre que corresponde al nombre del recurso web de JavaScript, como el recurso web **new_myCustomJavaScript.js** que se muestra a continuación. También puede buscar la biblioteca JavaScript escribiendo el nombre de archivo en el cuadro de búsqueda.

![Depurar JavaScript](../media/form-script-debugging.png)

Herramientas de depuración para distintos exploradores con capacidades similares. Una vez que ha encontrado la biblioteca, puede establecer un punto de interrupción y volver a crear el evento que debe hacer que el código se ejecute.

Mire también la siguiente entrada de blog en el sitio de blog de nuestro equipo para obtener más ideas sobre cómo depurar el código JavaScript: [Blog: Depurar código JavaScript personalizado en CRM con herramientas de desarrollo de explorador](https://blogs.msdn.microsoft.com/crm/2015/11/29/debugging-custom-javascript-code-in-crm-using-browser-developer-tools/).

## <a name="select-appropriate-frame-to-debug-your-code"></a>Seleccionar el marco adecuado para depurar el código

los formularios basados en modelos están compuestos por varios marcos. Para que el código funcione en la **Consola** de las herramientas de desarrollador del explorador, debe seleccionar el marco correspondiente. 
- Para los formularios de cliente web, seleccione el marco llamado **ClientApiWrapper**. 
- Para los formularios de interfaz unificada nuevos, seleccione el marco denominado **ClientApiFrame_[n]** donde n es el identificador de la página interna. Debe seleccionar el marco con el valor más alto para [n].

## <a name="write-messages-to-the-console"></a>Escribir mensajes en la consola

El uso del método [window.alert](https://msdn.microsoft.com/library/ms535933(v=vs.85).aspx) al depurar JavaScript sigue siendo una forma común de solucionar problemas de código en la aplicación. Sin embargo, ahora que todos los exploradores modernos proporcionan acceso sencillo a las herramientas de depuración, no se recomienda, especialmente cuando otras personas pueden estar usando la aplicación que está depurando.

Piense en escribir sus mensaje en la consola en su lugar. Lo siguiente es una pequeña función que puede agregar a sus bibliotecas y que puede usar para enviar los mensajes que desea ver en la consola cuando se abre.

```JavaScript
function writeToConsole(message)
{
 if (typeof console != 'undefined') {
  console.log(message);
 }
}
```

A diferencia del uso del método de alerta, si se olvida de quitar código que use esta función, las personas que usen la aplicación no verán los mensajes.
