---
title: Componentes de código de depuración | MicrosoftDocs
description: Cómo depurar un componente de código mediante Fiddler y la depuración nativa
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 18e88d702-3349-4022-a7d8-a9adf52cd34f
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 088792a32f401ddaf7d3a3cd4fd4d5aa9fa472ff
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346932"
---
# <a name="debug-code-components"></a>Componentes de código de depuración

Una vez que haya terminado de implementar la lógica del componente de código, puede empezar a probar y depurar el componente de código mediante el comando `npm start`. Esto genera el componente de código y lo abre en el instrumento de prueba local.

> [!div class="mx-imgBorder"]
> Agente de prueba del ![agente]de(media/test-harness-1.png "pruebas 1 1")

Como se muestra en la imagen anterior, la ventana del explorador se abre con cuatro secciones. El componente de código se representa en el panel izquierdo, mientras que el panel derecho tiene las secciones **entradas de contexto**, **entradas de datos**y **salidas** .

- Las **entradas de contexto** proporcionan una manera de especificar el factor de forma y probar el componente de código con cada factor de forma (Web, tableta, teléfono). Esto resulta útil cuando el componente de código depende de una funcionalidad de factor de forma determinada.
- **Entradas de datos** es una interfaz de usuario interactiva que muestra todas las propiedades y sus [tipos](manifest-schema-reference/types.md) o [grupos](manifest-schema-reference/type-group.md) de tipos definidos en el archivo de [manifiesto](manifest-schema-reference/manifest.md) . Permite clave en los datos ficticios para cada propiedad. 
- Las **salidas** representan el resultado cada vez que se llama al método [getOutputs](reference/control/getoutputs.md) de un componente.  

     > [!div class="mx-imgBorder"]
     > ![](media/test-harness-2.png "Agente de") prueba 2 del instrumento de prueba 2

> [!NOTE]
> Si desea modificar el archivo de `ControlManifest.Input.xml` o crear propiedades adicionales, deberá reiniciar el proceso de depuración antes de que aparezcan en la sección entradas.

## <a name="test-code-components-with-mock-data"></a>Probar componentes de código con datos ficticios

- En el caso de los componentes de tipo de *campo* , puede especificar el valor y el tipo de cada propiedad definida en el **archivo ControlManifest. Input. XML** como se muestra aquí:

   > [!div class="mx-imgBorder"]
   > Agente de ![prueba 2,5](media/test-harness-2.5.png "instrumento de prueba 2,5")

- En el caso de los componentes de tipo *DataSet* , puede cargar un archivo CSV con datos de prueba. Puede crear o exportar manualmente en formato. csv directamente desde su entorno. Una vez que haya disponible un archivo CSV válido, se puede cargar como se muestra aquí:

   > [!div class="mx-imgBorder"]
   > agente de prueba ![3](media/test-harness-3.png "instrumento de prueba 3")

- Después de cargar un archivo CSV, enlace cada propiedad definida en **ControlManifest. Input. XML** a una columna del archivo CSV. Para ello, se selecciona la columna de cada propiedad, como se muestra aquí:

    > [!div class="mx-imgBorder"]
    > Agente de prueba ![4](media/test-harness-4.png "mazo de pruebas") 4

- Si no tiene ninguna propiedad definida en el archivo **ControlManifest. Input. XML** , todas las columnas se cargan automáticamente en el instrumento de prueba.

   > [!div class="mx-imgBorder"]
   > Agente de prueba ![5](media/test-harness-5.png "instrumento de prueba 5")


## <a name="watch-mode-in-test-harness"></a>Modo de inspección en instrumento de prueba

El instrumento de prueba es compatible con el modo de `watch`, que puede aprovecharse de los proyectos de marco de componentes de PowerApps. Para habilitar el modo de `watch`, inicie el instrumento de prueba mediante el `npm start watch` de comandos. En el modo `watch`, los cambios realizados en cualquiera de los siguientes recursos del componente se reflejan automáticamente en el instrumento de prueba sin tener que reiniciarlo:

1.  `index.ts` archivo.
2.  `ControlManifest.Input.xml` archivo.
3.  Bibliotecas importadas en `index.ts`.
4.  Todos los recursos enumerados en el archivo de manifiesto.

## <a name="debug-code-components-using-native-browsers"></a>Depurar componentes de código mediante exploradores nativos

Puede usar las funciones de depuración del explorador para observar el comportamiento del componente. Cada explorador proporciona una herramienta de depuración que le ayudará a depurar el código de forma nativa en el explorador. Normalmente, puede activar la depuración en el explorador presionando la tecla **F12** para mostrar la herramienta de desarrollo nativo que se usa para la depuración.

Por ejemplo, en **Microsoft Edge**:

- Presione **F12** para abrir el inspector.
- Seleccione el componente.
- En la barra superior, vaya a **depurador** y busque el nombre del componente descrito en el archivo de manifiesto en la barra de búsqueda. Por ejemplo, escriba el nombre del componente como `Hello World component`.

     > [!div class="mx-imgBorder"]
     > ![Depurar]componente de(media/debug-control.png "depuración")

> [!NOTE]
> Siempre es recomendable establecer puntos de interrupción en los métodos de ciclo de vida del componente como [init](reference/control/init.md) y [updateView](reference/control/updateview.md).

También puede interactuar con el componente localmente en tiempo real y observar los elementos del DOM estableciendo un punto de interrupción en la pestaña *orígenes* , como se muestra aquí:

> [!div class="mx-imgBorder"]
> Componente de depuración ![componente](media/debug-control-1.png "1")

## <a name="fiddler-autoresponder"></a>Respondedor de Fiddler

Use el autorespondedor de Fiddler para depurar rápidamente los componentes de código. Instale [Fiddler](https://www.telerik.com/download/fiddler) y siga los pasos para configurar el [respondedor](https://docs.microsoft.com/dynamics365/customer-engagement/developer/streamline-javascript-development-fiddler-autoresponder).

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](overview.md)
