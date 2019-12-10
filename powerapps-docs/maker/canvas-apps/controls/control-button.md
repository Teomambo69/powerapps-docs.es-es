---
title: 'Control Botón: referencia | Microsoft Docs'
description: Información sobre el control Botón, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 02d5f59f16b68ce7f140857591b86a5cd8e54cd5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74722958"
ms.PowerAppsDecimalTransform: true
---
# <a name="button-control-in-power-apps"></a>Control de botón en Power apps
Un control en el que el usuario puede hacer clic o pulsar para interactuar con la aplicación.

## <a name="description"></a>Descripción
Configure la propiedad **[AlSeleccionar](properties-core.md)**  de un control **Botón** para ejecutar una o más fórmulas cuando el usuario haga clic en el control o lo pulse.

## <a name="key-properties"></a>Propiedades principales
**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[Text](properties-core.md)** : texto que aparece en un control o que el usuario escribe en un control.

## <a name="additional-properties"></a>Propiedades adicionales
**[Align](properties-text.md)** : la ubicación del texto respecto al centro horizontal de su control.

**AutoDisableOnSelect** (DesahabilitarAutomáticamenteAlSeleccionar): deshabilita automáticamente el control mientras se está ejecutando el comportamiento **AlSeleccionar**.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[Color](properties-color-border.md)** : el color del texto en un control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)** : el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)** : el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)** : el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[Font](properties-text.md)** : el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)** : el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)** : el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)** : indica si el texto de un control está en cursiva.

**[RellenoInferior](properties-size-location.md)** : distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)** : distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)** : distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)** : distancia entre el texto de un control y el borde superior de ese control.

**Pressed**: *true* mientras se presiona un control, en caso contrario *false*.

**[PressedBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)** : el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[RadiusBottomLeft](properties-size-location.md)** : el grado al que se redondea la esquina inferior izquierda de un control.

**[RadiusBottomRight](properties-size-location.md)** : el grado al que se redondea la esquina inferior derecha de un control.

**[RadiusTopLeft](properties-size-location.md)** : el grado al que se redondea la esquina superior izquierda de un control.

**[RadiusTopRight](properties-size-location.md)** : el grado al que se redondea la esquina superior derecha de un control.

**[Size](properties-text.md)** : el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)** : indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)** : indica si aparece una línea debajo del texto de un control.

**[VerticalAlign](properties-text.md)** : la ubicación del texto en un control respecto al centro vertical de ese control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
**[Navegar( *NombrePantalla*; *ScreenTransitionValue* )](../functions/function-navigate.md)**

## <a name="examples"></a>Ejemplos
### <a name="add-a-basic-formula-to-a-button"></a>Agregar una fórmula básica a un botón
1. Agregue un control **[Entrada de texto](control-text-input.md)** y denomínelo **Origen**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **Botón**, establezca su propiedad **[Texto](properties-core.md)** en "Agregar" y su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>
   **UpdateContext({Total:Total + Value(Source.Text)})**
   
    ¿Desea más información sobre la función **[UpdateContext](../functions/function-updatecontext.md)** u [otras funciones](../formula-reference.md)?
3. Agregue un control **[Etiqueta](control-text-box.md)** , establezca su propiedad **[Texto](properties-core.md)** en **Total** y presione **F5**.
4. Borre el texto predeterminado de **Origen**, escriba un número en él y, a continuación, haga clic o pulse **Agregar**.
   
    El control **[Etiqueta](control-text-box.md)** muestra el número que ha escrito.
5. Borre el número de **Origen**, escriba otro número y, a continuación, haga clic o pulse **Agregar**.
   
    El control **[Etiqueta](control-text-box.md)** muestra la suma de los números que ha escrito.
6. (opcional) Repita el paso anterior una o varias veces.
7. Para volver al área de trabajo predeterminada, presione Esc (o haga clic o pulse el icono de cerrar en la esquina superior derecha).

### <a name="configure-a-button-with-multiple-formulas"></a>Configuración de un botón con varias fórmulas
Agregue una fórmula que borra el control **Entrada de texto** entre las entradas.

1. Establezca la propiedad **[TextoDeSugerencia](control-text-input.md)** de **Origen** en "Enter a number" (Escriba un número).
2. Establezca la propiedad **[AlSeleccionar](properties-core.md)** de **Agregar** en esta fórmula:
   
    **UpdateContext({Total:Total + Value(Source.Text)});;<br>UpdateContext({ClearInput: ""})**
   
    > [!NOTE]
   > Utilice el punto y coma " **;** " para separar varias fórmulas.
3. Establezca la propiedad **[Predeterminad](properties-core.md)** de **Origen** en **ClearInput** (Borrar entrada).
4. Presione **F5**y, a continuación, pruebe la aplicación agregando varios números juntos.

### <a name="add-another-button-to-reset-the-total"></a>Integración de otro botón para restablecer el total
Agregue un segundo botón para borrar el total entre un cálculo y otro.

1. Agregue otro control **Botón**, establezca su propiedad **[Texto](properties-core.md)** en "Borrar" y su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:
   
    **UpdateContext ({Total:0})**
2. Presione **F5**, sume varios números y luego haga clic o pulse **Borrar** para restablecer el total.

### <a name="change-a-buttons-appearance"></a>Cambio de la apariencia de un botón
#### <a name="change-a-buttons-shape"></a>Cambio de la forma de un botón
De forma predeterminada, Power apps crea un control de **botón** rectangular con esquinas redondeadas. Puede realizar modificaciones básicas en la forma de un control **Botón** estableciendo sus propiedades **[Altura](properties-size-location.md)** , **[Ancho](properties-size-location.md)** , y **[Radius](properties-size-location.md)** (Radio).

> [!NOTE]
> [Icons and Shapes](control-shapes-icons.md) (Iconos y formas) proporcionan una gran variedad de diseños y pueden realizar algunas de las mismas funciones básicas que realizan los controles **Botón**. Pero, **[Icons and shapes](control-shapes-icons.md)** (Iconos y formas) no tiene una propiedad **[Texto](properties-core.md)** .

1. Agregue un control **Botón**, y establezca sus propiedades **[Altura](properties-size-location.md)** y **[Ancho](properties-size-location.md)** en **300** para hacer un botón cuadrado grande.
2. Modifique las propiedades **[RadiusTopLeft](properties-size-location.md)** (RadioSuperiorIzquierdo), **[RadiusTopRight](properties-size-location.md)** (RadioSuperiorDerecho), **[RadiusBottomLeft](properties-size-location.md)** (RadioInferiorIzquierdo), y **[RadiusBottomRight](properties-size-location.md)** (RadioInferiorDerecho) para ajustar la cantidad de curvatura en cada esquina. Estos son algunos ejemplos de formas diferentes, cada una comenzando a partir de un botón cuadrado de 300 x 300:
   
   * Establezca los cuatro valores de **[Radius](properties-size-location.md)** (Radio) en **150** para crear un círculo.
   * Establezca los valores de **[RadiusTopLeft](properties-size-location.md)** (RadioSuperiorIzquierdo) y **[RadiusBottomRight](properties-size-location.md)** (RadioInferiorDerecho) en **300** para crear un **Botón** en forma de hoja.
   * Establezca los valores de **[RadiusTopLeft](properties-size-location.md)** (RadioSuperiorIzquierdo) y **[RadiusTopRight](properties-size-location.md)** (RadioSuperiorDerecho)en **300** y los valores de **[RadiusBottomLeft](properties-size-location.md)** (RadioInferiorIzquierdo) y **[RadiusBottomRight](properties-size-location.md)** (RadioInferiorDerecho) en **100** para crear un botón en forma de pestaña.

#### <a name="change-a-buttons-color-when-you-hover-over-it"></a>Cambio del color de un botón cuando se mantiene el puntero sobre él
De forma predeterminada, el color de relleno de un control **Botón** se atenuará en un 20 % al mantener el mouse sobre él. Puede ajustar este comportamiento cambiando la propiedad **[RellenoAlMantener](properties-color-border.md)** , que usa la función **[ColorFade](../functions/function-colors.md)** . Si establece la fórmula **[ColorFade](../functions/function-colors.md)** en un porcentaje positivo, el color se vuelve más claro al mantener el mouse sobre el botón, mientras que un porcentaje negativo hace que el color sea más oscuro.

* Cambie el porcentaje de **[ColorFade](../functions/function-colors.md)** en la propiedad **[RellenoAlMantener](properties-color-border.md)** de uno de los botones que creó y observe los efectos.

También puede especificar el color de un control **Botón** estableciendo su propiedad **[RellenoAlMantener](properties-color-border.md)** en una fórmula que contenga la función **[ColorValue](../functions/function-colors.md)** función en lugar de la función **[ColorFade](../functions/function-colors.md)** , como en **ColorValue("Red")** .

> [!NOTE]
> El valor de color puede ser cualquier definición de color CSS, ya sea un nombre o un valor hexadecimal.

* Reemplace la función **[ColorFade](../functions/function-colors.md)** con una función **[ColorValue](../functions/function-colors.md)** en uno de los botones que creó y observe los efectos.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
* Se aplican [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[Text](properties-core.md)** debe existir.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
 
