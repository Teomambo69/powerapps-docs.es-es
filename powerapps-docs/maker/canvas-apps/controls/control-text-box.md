---
title: 'Control Etiqueta: referencia | Microsoft Docs'
description: Información sobre el control Etiqueta, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f62aa84867a3aa4eae582b3fde320e84becdeeff
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986299"
---
# <a name="label-control-in-canvas-apps"></a>Control de etiqueta en aplicaciones de lienzo

Cuadro que muestra los datos como texto, números, fechas o moneda.

## <a name="description"></a>Descripción

En una etiqueta se muestran datos que se especifican como una cadena literal de texto, que aparece exactamente igual que se escribe o como una fórmula que se analiza como cadena de texto. Las etiquetas suelen aparecer fuera de cualquier otro control (por ejemplo, como encabezado que identifica una pantalla), como una etiqueta que identifica otro control (por ejemplo, un control de clasificación o de audio) o en una galería para mostrar un tipo específico de información sobre un elemento.

## <a name="key-properties"></a>Propiedades principales

**[Autoheight](properties-core.md)** : establézcalo en true para permitir que la etiqueta crezca automáticamente su alto para mostrar todo el texto. Establézcalo en false para truncar el texto con el alto asignado.

**[Color](properties-color-border.md)** : el color del texto en un control.

**[Font](properties-text.md)** : el nombre de la familia de fuentes en la que aparece el texto.

**[Text](properties-core.md)** : texto que aparece en un control o que el usuario escribe en un control.

**[DelayOutput](properties-core.md)** : establézcalo en true para retrasar la acción durante la entrada de texto.

## <a name="additional-properties"></a>Propiedades adicionales

**[Align](properties-text.md)** : la ubicación del texto respecto al centro horizontal de su control.

**AutoHeight**: indica si una etiqueta aumenta automáticamente su propiedad **[Altura](properties-size-location.md)** si su propiedad **[Texto](properties-core.md)** contiene más caracteres de los que el control permite mostrar a la vez.

**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)** : el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)** : el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)** : el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[FontWeight](properties-text.md)** : el peso del texto en un control: **Bold**, **Semibold**, **normal**o **Lighter**.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)** : el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)** : indica si el texto de un control está en cursiva.

**[AlturaDeLínea](properties-text.md)** : distancia entre, por ejemplo, líneas de texto o elementos de una lista.

**[Live](properties-accessibility.md)** : Cómo anuncia un lector de pantalla los cambios en el valor de la propiedad **Text** de la etiqueta.

* Cuando se establece en **OFF**, el lector de pantalla no anuncia cambios.
* Cuando se establece en **educado**, el lector de pantalla termina de hablar antes de anunciar los cambios que se produjeron mientras estaba hablando el lector de pantalla.
* Cuando se establece en **assertive**, el lector de pantalla se interrumpe para anunciar los cambios que se produjeron mientras estaba hablando el lector de pantalla.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**Desbordamiento**: indica si aparece una barra de desplazamiento en una etiqueta si su propiedad **Ajustar** está establecida en **true** y el valor de la propiedad **[Texto](properties-core.md)** del control contiene más caracteres de los que el control permite mostrar a la vez.

**[RellenoInferior](properties-size-location.md)** : distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)** : distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)** : distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)** : distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)** : el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**Role** : el rol semántico del texto de la etiqueta, como encabezado 1. No cambia el estilo de la etiqueta, pero hace que la salida sea semánticamente correcta para que la interpreten los lectores de pantalla.

**[Size](properties-text.md)** : el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)** : indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)** : indica si aparece una línea debajo del texto de un control.

**[VerticalAlign](properties-text.md)** : la ubicación del texto en un control respecto al centro vertical de ese control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**Ajustar**: indica si el texto que es demasiado largo para caber en una etiqueta se ajusta a la línea siguiente.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas

[**Text**( *Number*, "*FormatCodes*" )](../functions/function-text.md)

## <a name="examples"></a>Ejemplos

### <a name="show-a-literal-string"></a>Mostrar una cadena literal

* Agregue una etiqueta y establezca su propiedad **[Texto](properties-core.md)** en **"Hola, mundo"** (dobles comillas incluidas).
  
    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

### <a name="show-the-result-of-a-formula"></a>Mostrar el resultado de una fórmula

* Agregue una etiqueta y establezca su propiedad **[Texto](properties-core.md)** en una fórmula como esta:<br>
  **Today()**
  
    > [!NOTE]
  > Al especificar una fórmula, no use comillas, a menos que un argumento de la misma sea una cadena literal. En ese caso, incluya el argumento, no la fórmula, con comillas inglesas.
  
    ¿Desea más información sobre la función **[Today](../functions/function-now-today-istoday.md)** u [otras funciones](../formula-reference.md)?

### <a name="show-data-in-a-gallery"></a>Mostrar datos en una galería

En este procedimiento, creará una colección, denominada **CityPopulations**, que contiene datos sobre la población de varias ciudades de Europa. A continuación, mostrará los datos de una galería que contengan tres etiquetas y especificará el tipo de datos que se mostrará en cada etiqueta.

1. Agregue un botón y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:<br>
   **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
2. Presione F5, seleccione el botón y presione Esc.
3. Agregue una galería de texto y establezca su propiedad **[Elementos](properties-core.md)** en **CityPopulations**.

    Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
4. En el panel **Gallery1**, establezca la lista superior en **Population**, la del medio en **City** y la inferior en **Country**.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

A pesar de su nombre, un control **Etiqueta** no tiene que usarse como etiqueta con otro control. Se puede utilizar para mostrar cualquier fragmento de texto.

Un control **Etiqueta** se puede usar como botón o vínculo mediante la especificación del comportamiento **[OnSelect](properties-core.md)** . Cuando se utiliza de este modo, hay algunas consideraciones sobre accesibilidad parecidas a las que se tienen con los botones.

### <a name="color-contrast"></a>Contraste de color

Debe haber un contraste de color adecuado entre:

* **[Color](properties-color-border.md)** y **[Fill](properties-color-border.md)**
* Se aplican otros [requisitos estándar de contraste de color](../accessible-apps-color.md) (si se usa como botón o vínculo)

### <a name="screen-reader-support"></a>Compatibilidad con el lector de pantalla

* La propiedad **[Text](properties-core.md)** debe existir.
* **[Live](properties-accessibility.md)** debe establecerse en **educated** o **assertive** si un lector de pantalla debe anunciar cambios en el valor de la propiedad **Text** .

  > [!NOTE]
  > Los lectores de pantalla tratan los controles **Etiqueta** como botones cuando **[TabIndex](properties-accessibility.md)** es cero o superior.

### <a name="low-vision-support"></a>Apoyo para deficiencia visual

* El control **Etiqueta** debe parecerse a un vínculo, si se utiliza como vínculo.
  * Establezca la propiedad **[Underline](properties-text.md)** en **true**.
  * **[HoverColor](properties-color-border.md)** debe ser diferente de **[Color](properties-color-border.md)**

### <a name="keyboard-support"></a>Compatibilidad con el teclado

* **[TabIndex](properties-accessibility.md)** debe ser cero o mayor si el texto se utiliza como botón o vínculo. De esta forma, los usuarios de teclado pueden navegar hasta él.
* Los indicadores de foco deben ser claramente visibles si el texto se usa como botón o vínculo. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
