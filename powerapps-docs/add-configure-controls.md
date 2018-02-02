---
title: "Adición y configuración de un control | Microsoft Docs"
description: "Instrucciones paso a paso para agregar y configurar controles directamente, desde la barra de herramientas, en la pestaña Propiedades o en la barra de fórmulas."
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/10/2017
ms.author: sharik
ms.openlocfilehash: 0e7ed1dfa73c1d7f37ed0af9be797435a0790d7c
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="add-and-configure-a-control-in-powerapps"></a>Adición y configuración de un control en PowerApps
Añada diversos elementos de interfaz de usuario a su aplicación y configure aspectos de su apariencia y comportamiento directamente, desde la barra de herramientas, en la pestaña **Propiedades** o en la barra de fórmulas. Estos elementos de interfaz de usuario se denominan controles y los aspectos que configura se denominan propiedades.

## <a name="prerequisites"></a>Requisitos previos
1. [Suscríbase](signup-for-powerapps.md) a PowerApps, [instálelo](http://aka.ms/powerappsinstall), ábralo e inicie sesión con las mismas credenciales que usó para suscribirse.

2. En PowerApps Studio, pulse o haga clic en **Nuevo** en el menú **Archivo** (cerca del borde izquierdo).

    ![Opción Nuevo en el menú Archivo](./media/add-configure-controls/file-new.png)

3. En el icono **Blank app** (Aplicación vacía), pulse o haga clic en **Phone layout** (Diseño de teléfono).

    ![Crear una aplicación desde cero](./media/add-configure-controls/blank-app.png)

4. Si se le pide que realice un paseo introductorio, haga clic o pulse en **Siguiente** para familiarizarse con las áreas principales de la interfaz de PowerApps (o haga clic o pulse en **Omitir**).

    ![Pantalla inicial del paseo introductorio](./media/add-configure-controls/quick-tour.png)

    Siempre puede realizar el paseo más tarde haciendo clic o pulsando en el icono del signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, haciendo clic o pulsando en **Take the intro tour** (Realizar paseo introductorio).

## <a name="add-a-control"></a>Adición de un control
Puede agregar cualquier control en diversas categorías, para lo que debe hacer clic o pulsar en la pestaña **Insertar** de la barra de herramientas, a continuación, en una categoría y, finalmente, en el control que desea. En esta sección, revise los controles de cada categoría para familiarizarse con los tipos de controles que se pueden añadir y dónde puede encontrarse cada tipo.

En la pestaña **Insertar**, pulse o haga clic en cualquiera de estas categorías y luego pulse o haga clic en el control que desea agregar:

**Texto**: Etiqueta, Entrada de texto, Texto HTML, Entrada manuscrita<br>
**Controles**: Botón, Lista desplegable, Selector de fecha, Cuadro de lista, Casilla, Radio, Alternar, Control deslizante, Clasificación, Temporizador<br>
**Galería**: Vertical, Horizontal, Flexible height (Alto flexible), Blank vertical (Blanco vertical), Blank horizontal (Blanco horizontal), Blank flexible height (Blanco alto flexible)<br>
**Tabla de datos**<br>
**Formularios**: Editar, Mostrar, Entity form (Formulario de la entidad)<br>
**Elementos multimedia**: Imagen, Cámara, Código de barras, Vídeo, Audio, Micrófono, Agregar imagen<br>
**Gráficos**: Gráfico de columnas, Gráfico de líneas, Gráfico circular<br>
**Iconos**

> [!TIP]
> Si necesita más espacio para controles, [agregue otra pantalla](add-screen-context-variables.md).

## <a name="configure-a-control-directly"></a>Configuración directa de un control
En este procedimiento, agregará y configurará un control **Etiqueta**, pero puede aplicar muchos de los mismos principios a otros controles.

1. Pulse o haga clic en la pestaña **Insertar** y en **Etiqueta**.

    ![Pestaña Insertar](./media/add-configure-controls/insert-text-box.png)

    Al añadir un control, se selecciona de forma predeterminada. También puede seleccionar un control existente haciendo clic en él o pulsándolo. Cuando se selecciona un control, aparece un cuadro de selección alrededor de él y otras áreas de la interfaz de usuario cambian para que pueda configurar el control seleccionado. Por ejemplo, un control **Etiqueta** seleccionado se parece a este gráfico.

    ![Una etiqueta seleccionada](./media/add-configure-controls/selected-text-box.png)

    > [!IMPORTANT]
> Si ya hay un control seleccionado, al seleccionar otro o un área en blanco de la pantalla, el primer elemento dejará de estar seleccionado.
2. Reduzca la anchura del control **Etiqueta** arrastrando un controlador del borde derecho del cuadro de selección hacia la izquierda. El controlador central solo aparece al acercar la imagen.

    ![Una etiqueta cuyo tamaño ha cambiado](./media/add-configure-controls/shorter-text-box.png)

     También es posible cambiar el tamaño de un control si modifica sus propiedades **[Altura](controls/properties-size-location.md)**, **[Ancho](controls/properties-size-location.md)** o ambas, como se describe más adelante en este tema.

3. Mueva el control **Etiqueta** arrastrando el propio cuadro de selección (o modificando las propiedades **[X](controls/properties-size-location.md)**,  **[Y](controls/properties-size-location.md)** o ambas, como se describe más adelante en este tema).

4. Haga clic tres veces en el texto que aparece en el control **Etiqueta** y escriba **Hola, mundo**.

    ![Una etiqueta con texto personalizado](./media/add-configure-controls/change-text-directly.png)

     También puede definir la propiedad **[Texto](controls/properties-core.md)** de este control para modificar este texto, como se describe más adelante en este tema.

## <a name="configure-a-control-from-the-toolbar"></a>Configuración de un control desde la barra de herramientas
Al configurar un control desde la barra de herramientas, puede especificar una mayor variedad de opciones que si lo hace directamente.

1. Con el control **Etiqueta** seleccionado, pulse o haga clic en la pestaña **Inicio** de la barra de herramientas.

    ![Pestaña Inicio](./media/add-configure-controls/home-tab.png)

2. Pulse o haga clic en **Rellenar** y, a continuación, pulse o haga clic en un color como aguamarina.

    ![Opción de relleno](./media/add-configure-controls/fill-option.png)

    El control **Etiqueta** reflejará la selección.

    ![Etiqueta con relleno de color aguamarina](./media/add-configure-controls/change-fill.png)

3. Cambie la familia de fuentes y el tamaño del texto (por ejemplo, a 18 ptos. Georgia).

    ![Controles de fuente](./media/add-configure-controls/font-size.png)

    El control **Etiqueta** reflejará la selección.

    ![Georgia, 18 puntos](./media/add-configure-controls/change-font.png)

4. Pulse o haga clic en la pestaña **Etiqueta**, en **Alineación vertical** y, después, en **Superior**.

    ![Pestaña Cuadro de texto](./media/add-configure-controls/text-box-tab.png)

    El control **Etiqueta** reflejará la selección.

    ![Etiqueta con texto alineado en la parte superior del cuadro](./media/add-configure-controls/change-align.png)

## <a name="configure-a-control-from-the-properties-tab"></a>Configuración de un control mediante la pestaña Propiedades
Mediante la pestaña **Propiedades**, puede configurar un control sin necesidad de escribir una fórmula. En este procedimiento, agregará y configurará un control **Etiqueta**, pero puede aplicar muchos de los mismos principios a otros controles.

1. Agregue otro control **Etiqueta** como ya se describió anteriormente en este tema.

2. Con el nuevo control seleccionado, pulse o haga clic en la pestaña **Propiedades** del panel derecho.

    ![Panel Propiedades](./media/add-configure-controls/properties-panel.png)

3. En el cuadro **Texto**, escriba **pestaña Propiedades**.

    ![Panel Propiedades Etiqueta Texto](./media/add-configure-controls/properties-panel-text.png)

    El control **Etiqueta** muestra el texto escrito.

    ![Panel Propiedades lienzo Texto](./media/add-configure-controls/properties-panel-canvas-text.png)

4. Haga clic o pulse en el icono de **relleno** del panel **Propiedades** y, a continuación, haga clic o pulse en un color.

    ![Panel Propiedades color Texto](./media/add-configure-controls/properties-panel-color.png)

    El control **Etiqueta** reflejará la selección.

    ![Panel Propiedades lienzo color](./media/add-configure-controls/properties-panel-canvas-color.png)

5. Haga clic o pulse en la propiedad **Color** del panel de propiedades.

    ![Panel Propiedades propiedad](./media/add-configure-controls/properties-panel-property.png)

    El valor de la propiedad **Color** está resaltado en la barra de fórmulas.

    ![Panel Propiedades propiedad expresión](./media/add-configure-controls/properties-panel-property-expression.png)

6. Para eliminar el segundo control **Etiqueta**, pulse o haga clic en él y presione Suprimir.

## <a name="configure-a-control-in-the-formula-bar"></a>Configuración de un control en la barra de fórmulas
Mediante el uso de la barra de fórmulas, puede establecer propiedades que no se pueden definir directamente en la pestaña **Propiedades** ni con la barra de herramientas. Por ejemplo, puede definir que aparezca información sobre herramientas cuando un usuario señale el control, pero no haga clic en él ni lo pulse. También puede especificar fórmulas complejas que aumentan la capacidad de la aplicación.

Cada cambio que ha realizado anteriormente en este tema actualiza el valor de una [propiedad](reference-properties.md) para el control que ha configurado.

* Al cambiar el tamaño del control, ha cambiado su propiedad **[Width](controls/properties-size-location.md)**.
* Al mover el control, ha cambiado sus propiedades **[X](controls/properties-size-location.md)** e **[Y](controls/properties-size-location.md)**.
* Al cambiar el texto que muestra el control, ha cambiado su propiedad **[Texto](controls/properties-core.md)**.

En lugar de configurar un control directamente en la pestaña **Propiedades** o desde la barra de herramientas, también puede actualizar el valor de una propiedad seleccionándola en la lista de propiedades y, a continuación, especificando un valor en la barra de fórmulas. Con este enfoque, puede buscar una propiedad por orden alfabético y especificar otros tipos de valores.

1. Con el control **Etiqueta** restante seleccionado, pulse o haga clic en **[Texto](controls/properties-core.md)** en la lista de propiedades y escriba **"Nombre de mi empresa"** (comillas incluidas) en la barra de fórmulas.

    ![Cadena literal en una etiqueta](./media/add-configure-controls/text-literal.png)

    Al incluir una cadena de texto entre comillas, especifica que debe tratarse exactamente tal como la escribió. Como alternativa, puede definir una fórmula para el valor de una propiedad.

2. Con el control **Etiqueta** seleccionado, pulse o haga clic en **[Texto](controls/properties-core.md)** en la lista de propiedades y escriba **Today()** (sin comillas) en la barra de fórmulas.

    El control mostrará la fecha actual.

    ![Función Today](./media/add-configure-controls/today-function.png)

    > [!TIP]
> Hay varias formas de [dar formato a las fechas y horas](show-text-dates-times.md), además de realizar cálculos en ellas.

## <a name="configure-two-controls-to-interact-with-each-other"></a>Configuración de dos controles para interactuar entre sí
En este procedimiento, agregará una casilla y, a continuación, configurará la etiqueta que ya tiene para que aparezca solo cuando se activa la casilla.

1. Pulse o haga clic en la pestaña **Insertar**.

    ![Pestaña Insertar](./media/add-configure-controls/insert-tab.png)

2. Pulse o haga clic en **Controles** y, a continuación, pulse o haga clic en **Casilla**.

    ![Inserción de casilla](./media/add-configure-controls/insert-check-box.png)

3. Mueva el control **Casilla** de forma que aparezca debajo del control **Etiqueta** y establezca la propiedad **[Texto](controls/properties-core.md)** del control **Casilla** para que aparezca **Mostrar texto**.

    ![Configuración de casilla](./media/add-configure-controls/configure-check-box.png)

4. Con el control **Casilla** aún seleccionado, haga clic o pulse en su nombre justo encima de la pestaña **Propiedades** y, a continuación, escriba **MyCheckbox**

    ![Cambio de nombre de casilla](./media/add-configure-controls/properties-panel-rename.png)

5. Haga clic o pulse en el control **Etiqueta** para seleccionarlo.

6. En la pestaña **Propiedades**, haga clic o pulse en la propiedad **Visible**.

    ![Propiedad Visible](./media/add-configure-controls/properties-panel-visible-property.png)

7. En la barra de fórmulas, elimine **true** y, a continuación, escriba o pegue esta fórmula:

    **If(MyCheckbox.Value = true, true, false)**

    Esta **[función If](functions/function-if.md)** indica que la etiqueta debe aparecer solo cuando se activa la casilla. Al estar desactivada la casilla, el control **Etiqueta** desaparece (excepto el cuadro de selección).

    ![Fórmula Visible](./media/add-configure-controls/visible-formula.png)

8. Pulse o haga clic en el control **Casilla** para agregar el cuadro de selección y, a continuación, haga clic en él o púlselo de nuevo para agregar una marca de verificación.

    El control **Etiqueta** vuelve a aparecer:

    ![Etiqueta mostrada cuando la casilla está activada](./media/add-configure-controls/show-text.png)

9. Desactive el control **Casilla** para ocultar el control **Etiqueta**.

    ![La etiqueta desaparece cuando la casilla está desactivada](./media/add-configure-controls/hide-text.png)

Este ejemplo es básico, pero puede configurar el comportamiento y la apariencia de la aplicación mediante la creación de una o varias [fórmulas](formula-reference.md) que vayan aumentando su nivel de complejidad.

## <a name="rename-a-screen-or-a-control"></a>Cambio de nombre de una pantalla o un control
Al cambiar el nombre de una pantalla o un control, puede crear fórmulas que son más fáciles de leer y recordar.

1. Pulse o haga clic en la pantalla o el control cuyo nombre desea cambiar.

2. En el panel derecho, haga clic o pulse en el nombre del control (justo encima de la pestaña **Propiedades**) y, a continuación, escriba el nombre que desee.

    ![Cambio de nombre de casilla](./media/add-configure-controls/properties-panel-rename.png)

## <a name="find-and-select-a-screen-or-a-control"></a>Buscar y seleccionar una pantalla o un control
Puede buscar y seleccionar una pantalla o un control, incluso si está oculto o se solapa con otro; solo tiene que buscarlo en el panel izquierdo. Este panel muestra una miniatura de cada pantalla de la aplicación o una vista jerárquica de cada pantalla y de los controles que contiene.

* **Para cambiar entre las miniaturas y la vista jerárquica**, pulse o haga clic en un icono de la esquina superior derecha del panel.

    ![Alternancia de las vistas](./media/add-configure-controls/toggle-view.png)

* **Para buscar un control**, escriba uno o varios caracteres para resaltar los nombres de los controles que contienen el texto que escribe.

    Si pulsa o hace clic en un resultado de búsqueda, selecciona ese control en la aplicación.

    ![Buscar en la vista de árbol](./media/add-configure-controls/search.png)

* **Para mover una pantalla arriba o abajo, duplicarla, eliminarla o cambiar su nombre**, haga clic en ella con el botón derecho (o pulse y haga clic en el botón de puntos suspensivos situado al lado) y luego pulse o haga clic en la opción que desea.

    ![Menú contextual de vista de árbol](./media/add-configure-controls/context.png)

* **Para copiar y pegar un control, eliminarlo o cambiar su nombre**, haga clic en él con el botón secundario (o pulse y haga clic en el botón de puntos suspensivos situado al lado) y, a continuación, pulse o haga clic en la opción que desea.
