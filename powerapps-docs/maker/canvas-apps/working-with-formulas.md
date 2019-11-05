---
title: Introducción a las fórmulas en una aplicación de lienzo | Microsoft Docs
description: En PowerApps, use fórmulas para personalizar una aplicación de lienzo.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 715f82a1db2c8a4bb495e41b45a3911182024158
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73541605"
---
# <a name="get-started-with-canvas-app-formulas-in-powerapps"></a>Introducción a las fórmulas de aplicación de lienzo en PowerApps

Configure la aplicación de lienzo con fórmulas no solo para calcular valores y realizar otras tareas (como en Excel), sino también para responder a la entrada del usuario (como una aplicación requiere).

* En Excel, se crean fórmulas que, por ejemplo, rellenan celdas y crean tablas y gráficos.
* En PowerApps, va a crear fórmulas parecidas al configurar controles en lugar de celdas. Además, va a crear fórmulas que se aplican específicamente a aplicaciones en lugar de a hojas de cálculo.

Por ejemplo, puede crear una fórmula para determinar cómo responde la aplicación cuando los usuarios seleccionan un botón, ajustan un control deslizante o proporcionan otra entrada. Estas fórmulas podrían mostrar una pantalla diferente, actualizar un origen de datos externo a la aplicación o crear una tabla que contiene un subconjunto de los datos de una tabla existente.

Puede usar fórmulas para una amplia variedad de escenarios. Por ejemplo, puede usar el GPS de su dispositivo, un control de mapa y una fórmula que use **Location.Latitude** y **Location.Longitude** para mostrar su ubicación actual. A medida que se desplaza, el mapa sigue automáticamente su ubicación.

En este tema se proporciona únicamente información general sobre cómo trabajar con fórmulas. Examine la [referencia sobre fórmulas](formula-reference.md) para más información y la lista completa de funciones, operadores y otros bloques de creación que puede usar.

## <a name="prerequisites"></a>Requisitos previos

* [Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.
* Aprenda a [configurar un control](add-configure-controls.md) en PowerApps.

## <a name="show-a-simple-value"></a>Mostrar un valor simple

En Excel, puede indicar un dato específico, como el número **42** o la frase **Hello World**, escribiéndolo en una celda. Esa celda siempre mostrará el dato exactamente como lo escribió. En PowerApps, de forma similar, puede especificar un dato que no cambia si establece la propiedad **[Text](controls/properties-core.md)** de una etiqueta en la secuencia exacta de caracteres que desee, entre comillas dobles.

1. Seleccione **Nuevo** en el menú **Archivo** (cerca del borde izquierdo de la pantalla).
2. En **Create an app** (Crear aplicación), seleccione **Diseño de teléfono** en el icono **Aplicación vacía**.

    La barra de fórmulas se encuentra en la parte superior de la pantalla.

    ![Barra de fórmulas](./media/working-with-formulas/formula-bar.png)

    Esta barra tiene dos partes:

   * *Lista de propiedades*: cada pantalla y control tienen un [conjunto de propiedades](reference-properties.md).  Use esta lista para seleccionar una propiedad específica.  
   * *Fórmula*: la fórmula que se calculará para esta propiedad, compuesta por [valores, operadores y funciones](formula-reference.md).

     En la barra de fórmulas, puede ver y editar las propiedades del control seleccionado o de la pantalla si no hay controles seleccionados.  Se ve el nombre del control seleccionado en la pestaña **Contenido**:

     ![Barra de contenido que muestra el control seleccionado actualmente](./media/working-with-formulas/content-tab-selection.png)

     Puede cambiar el nombre del control seleccionado en la pestaña **Contenido** si hace clic en el nombre.
3. Agregue un control **[Etiqueta](controls/control-text-box.md)**  a la pantalla.

    ![Control TextBox agregado](./media/working-with-formulas/add-a-label.png)

    Cuando se agrega una etiqueta, la lista de propiedades muestra automáticamente la propiedad **[Texto](controls/properties-core.md)** , que determina lo que se muestra en el control. De forma predeterminada, el valor de esta propiedad es **"Texto"** .  
4. Establezca el valor de la propiedad **[Text](controls/properties-core.md)** en **"Hello World"** escribiendo esa cadena, encerrada entre comillas dobles, en la barra de fórmulas:

    ![Usar la etiqueta "Hello World"](./media/working-with-formulas/label-hello-world.png)

    La etiqueta refleja este nuevo valor a medida que lo escribe.  Es posible que aparezcan en pantalla iconos de signos de exclamación amarillos mientras escriba. Estos iconos indican errores, pero desaparecerán cuando termine de escribir un valor válido. Por ejemplo, una cadena no encerrada entre comillas dobles no es válida.

    En Excel, puede mostrar un número, como **42**, escribiéndolo en una celda o escribiendo una fórmula que se resuelve en ese número, como **=SUMA(30,12)** . En PowerApps, puede lograr el mismo efecto si establece la propiedad **Texto** de un control, como una etiqueta, en **42** o **Sum(30,12)** . La celda y la etiqueta mostrarán siempre dicho número, independientemente de los cambios que se produzcan en la hoja de cálculo o en la aplicación.

    > [!NOTE]
   > En PowerApps, no anteponga un signo igual o más a la fórmula como se hace en Excel. La barra de fórmulas trata todo lo que escribe en ella como fórmula de forma predeterminada. Tampoco debe encerrar una fórmula entre comillas dobles ("), como hizo antes para especificar una cadena de texto.
5. En la propiedad **[Texto](controls/properties-core.md)** de la etiqueta, reemplace **"Hola mundo"** por **Sum(1,2,3)** .

    ![Si escribe la función parcial Sum(1,2,3 sin paréntesis de cierre, aparecen errores](./media/working-with-formulas/label-sum-partial.png)

    Mientras escribe, la barra de fórmulas lo ayuda mostrando la descripción y los argumentos esperados para esta función.  Al igual que con la comilla doble final en **"Hello World"** , la pantalla muestra los signos de exclamación amarillos para indicar un error hasta que escriba el paréntesis final de esta fórmula:

    ![Usar la fórmula Sum(1,2,3) completa](./media/working-with-formulas/label-sum.png)

## <a name="change-a-value-based-on-input"></a>Cambiar un valor en función de la entrada

En Excel, escriba **= a1 + a2** en una celda para mostrar la suma de los valores que contienen las celdas **a1** y **a2** . Si uno o ambos de esos valores cambian, la celda que contiene la fórmula muestra automáticamente el resultado actualizado.

![Animación de Excel que vuelve a calcular la suma de dos números](./media/working-with-formulas/excel-recalc.gif)

En PowerApps, puede lograr un resultado similar agregando controles a una pantalla y estableciendo sus propiedades. En este ejemplo se muestra un control de etiqueta denominado **Label1** y dos controles de **[entrada de texto](controls/control-text-input.md)** , denominados **TextInput1** y **TextInput2**.

![Ilustrar el recálculo de la suma de dos números en PowerApps](./media/working-with-formulas/recalc1.png)

Con independencia de los números que escriba en los controles de entrada de texto, la etiqueta siempre muestra la suma de esos números porque su propiedad **[Texto](controls/properties-core.md)** está establecida en esta fórmula:

`TextInput1 + TextInput2`

![Animación de PowerApps que vuelve a calcular la suma de dos números](./media/working-with-formulas/recalc2.gif)

En Excel, puede usar fórmulas de formato condicional para mostrar, por ejemplo, valores negativos en rojo. En PowerApps, puede usar fórmulas para determinar no solo el valor principal de un control, sino propiedades como el formato. En el ejemplo siguiente, una fórmula para la propiedad **[color](controls/properties-color-border.md)** de la etiqueta muestra automáticamente los valores negativos en rojo. El aspecto de la función **[If](functions/function-if.md)** debería resultarle familiar de Excel:

`If( Value(Label1.Text) < 0, Red, Black )`

![Animación de formato condicional](media/working-with-variables/recalc-color.gif)

## <a name="change-a-color-based-on-user-input"></a>Cambiar un color en función de la entrada de usuario

Puede configurar la aplicación con fórmulas para que los usuarios puedan cambiar su apariencia o comportamiento. Por ejemplo, puede crear un filtro para mostrar solo los datos que contengan una cadena de texto especificada por el usuario o puede permitir que los usuarios ordenen un conjunto de datos por una columna determinada del conjunto de datos. En este procedimiento, permitirá que los usuarios cambien el color de la pantalla mediante uno o varios controles deslizantes.

1. Quite los controles de los procedimientos anteriores o cree una aplicación vacía como hizo antes y agréguele tres controles deslizantes:

    ![Insertar un control deslizante](./media/working-with-formulas/insert-slider.png)
2. Organice los controles deslizantes de forma que no se superpongan, agregue tres etiquetas y configúrelas para que muestren **Rojo**, **Verde** y **Azul**:

    ![Organizar los controles deslizantes y agregar etiquetas para cada componente de color](./media/working-with-formulas/three-sliders.png)
3. Establezca la propiedad **Max** de cada control deslizante en 255, que es el valor máximo de un componente de color para la función **[RGBA](functions/function-colors.md)** .

    Puede especificar la propiedad **Max** si la selecciona en la pestaña **Contenido** o en la lista de propiedades:

    ![Cambiar el valor máximo de cada control deslizante](./media/working-with-formulas/three-sliders-max.png)
4. Haga clic fuera de cualquier control para seleccionar la pantalla y establezca la propiedad **[Fill](controls/properties-color-border.md)** de esta en esta fórmula:<br>**RGBA( Slider1.Value, Slider2.Value, Slider3.Value, 1 )**

    Como ya se ha descrito, para acceder a las propiedades de un control, use el operador " **.** " .  **Slider1.Value** se refiere a la propiedad **[Value](controls/properties-core.md)** del control deslizante, que refleja el lugar donde el usuario ha colocado el control deslizante entre los valores **Min** y **Max**. A medida que escribe esta fórmula, cada control que la contenga se marca con un color entre la pantalla y la barra de fórmulas:

    ![Cambiar la fórmula para el color de relleno de fondo de la pantalla, pero aún sin concluir](./media/working-with-formulas/three-sliders-partial-rgba.png)

    Al escribir el paréntesis de cierre, el fondo de la pantalla cambiará a gris oscuro basándose en el valor predeterminado de cada control deslizante, que es **50**. En cuanto termine de escribir la fórmula, se calcula y se usa como valor del color de relleno de fondo. Puede interactuar con la aplicación en el área de trabajo predeterminada sin necesidad de abrir Vista previa:

    ![Cambiar el valor máximo de cada control deslizante](./media/working-with-formulas/three-sliders-complete-rgba.png)
5. Ajuste los controles deslizantes y vea cómo los cambios afectan al color de fondo.

    A medida que cambia cada control deslizante, la fórmula que contiene la función **[RGBA](functions/function-colors.md)** se vuelve a calcular, lo que cambia inmediatamente la apariencia de la pantalla.

    ![Cambiar la fórmula para el color de relleno de fondo de la pantalla, ahora completo](./media/working-with-formulas/color-sliders.gif)

## <a name="manage-app-behavior"></a>Administrar el comportamiento de la aplicación

Puede usar fórmulas no solo para realizar cálculos y cambiar la apariencia, sino también para llevar a cabo acciones. Por ejemplo, puede establecer la propiedad **[OnSelect](controls/properties-core.md)** de un botón en una fórmula que incluya la función **[Navigate](functions/function-navigate.md)** . Cuando un usuario selecciona ese botón, aparece la pantalla que especifique en la fórmula.

Puede usar algunas funciones, como **[Navigate](functions/function-navigate.md)** y **[Collect](functions/function-clear-collect-clearcollect.md)** , solo en fórmulas de comportamiento.  En la referencia sobre fórmulas, se indica si una función se puede usar solo en este contexto.  

Puede usar más de una acción en una fórmula de comportamiento si separa las funciones con un punto y coma (;). Por ejemplo, podría actualizar una variable de contexto, insertar datos en un origen de datos y finalmente ir a otra pantalla.

## <a name="view-a-list-of-properties-by-category"></a>Ver una lista de propiedades por categoría

En la lista de propiedades, estas se muestran por orden alfabético, aunque también puede ver todas las propiedades de un control, organizadas por categorías, si selecciona la opción **Avanzada** en la pestaña **Vista**:

![Vista avanzada](./media/working-with-formulas/advanced-open.png)

Puede editar las fórmulas directamente en esta vista.  Con el selector del control en la parte superior del panel, puede buscar rápidamente un control con el que trabajar.  Además, con la búsqueda de propiedades, puede buscar rápidamente una propiedad de ese control.

En un principio, esta vista muestra las propiedades más importantes.  Para mostrar todas, haga clic en la flecha abajo de la parte inferior del panel.  Cada control posee una larga lista de propiedades que controlan todos los aspectos de su comportamiento y apariencia. Para buscar una propiedad, puede desplazarse por la lista o escribir en el cuadro de la parte superior del panel.

## <a name="formula-syntax"></a>Sintaxis de las fórmulas

A medida que escribe una fórmula en la barra de fórmulas, los elementos de sintaxis diferente aparecerán en distintos colores para mejorar la legibilidad y ayudarle a comprender las fórmulas largas. Esta es la lista de códigos de color de PowerApps.

![sintaxis resaltada](./media/working-with-formulas/syntax-highlighting.png)