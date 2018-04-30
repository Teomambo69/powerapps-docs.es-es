---
title: 'Control Entrada de texto: referencia | Microsoft Docs'
description: Información sobre el control Entrada de texto, con propiedades y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: fca84b687f6e86905c6eeea18a7cd302f0c58b44
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="text-input-control-in-powerapps"></a>Control Entrada de texto en PowerApps
Un cuadro en el que el usuario puede escribir texto, números y otros datos.

## <a name="description"></a>Descripción
El usuario puede especificar datos escribiendo en un control Entrada de texto. Dependiendo de cómo configure la aplicación, puede que esos datos se agreguen a un origen de datos, usado para calcular un valor temporal, o que se incorporen de alguna otra manera.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**[Text](properties-core.md)**: texto que aparece en un control o que el usuario escribe en un control.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[Align](properties-text.md)**: la ubicación del texto respecto al centro horizontal de su control.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**Clear**: indica si un control Entrada de texto muestra una "X" sobre la que el usuario puede pulsar o hacer clic para borrar el contenido de ese control.

**[Color](properties-color-border.md)**: el color del texto en un control.

**DelayOutput**: cuando se establece en true, la entrada del usuario se registra después de un retraso de medio segundo.  Resulta útil para retrasar operaciones costosas hasta que el usuario completa la entrada de texto (es decir, para el filtrado cuando la entrada se utiliza en otras fórmulas).

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**: el peso del texto en un control: **Bold**, **Semibold**, **Normal** o **Lighter**.

**Formato**: indica si se han restringido las entradas de usuario a solo números o a cualquier tipo de texto.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**TextoDeSugerencia**: texto de color gris claro que aparece en un control Entrada de texto si está vacío.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[AlturaDeLínea](properties-text.md)**: distancia entre, por ejemplo, líneas de texto o elementos de una lista.

**MaxLength**: el número de caracteres que el usuario puede escribir en un control Entrada de texto.

**Mode**: el control se encuentra en modo **SingleLine**, **MultiLine** o **Password**.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[RadiusBottomLeft](properties-size-location.md)**: el grado al que se redondea la esquina inferior izquierda de un control.

**[RadiusBottomRight](properties-size-location.md)**: el grado al que se redondea la esquina inferior derecha de un control.

**[RadiusTopLeft](properties-size-location.md)**: el grado al que se redondea la esquina superior izquierda de un control.

**[RadiusTopRight](properties-size-location.md)**: el grado al que se redondea la esquina superior derecha de un control.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**DateTimeValue**( *String* )](../functions/function-datevalue-timevalue.md)

## <a name="examples"></a>Ejemplos
### <a name="collect-data"></a>Recopilación de datos
1. Agregue dos controles Entrada de texto y llámelos **inputFirst** y **inputLast**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un botón, establezca su propiedad **[Texto](properties-core.md)** en **Agregar** y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>
   **Collect(Names, {FirstName:inputFirst.Text, LastName:inputLast.Text})**
   
    ¿Desea más información sobre la función **[Recopilar](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
3. Agregue una galería de texto en orientación vertical, establezca su propiedad **[Elementos](properties-core.md)** en **Names** y establezca la propiedad **[Texto](properties-core.md)** de **Subtitle1** en **ThisItem.FirstName**.
4. (Opcional) En la galería de plantillas, elimine la etiqueta inferior, llamada **Body1** y establezca la propiedad **[TamañoDePlantilla](control-gallery.md)** de la galería en **80**.
5. Presione F5, escriba una cadena de texto en **inputFirst** y en **inputLast**y, a continuación, pulse o haga clic en el botón **Agregar**.
6. (opcional) Agregue más nombres a la colección y, a continuación, presione Esc para volver al área de trabajo predeterminada.

### <a name="prompt-for-a-password"></a>Solicitud de una contraseña
1. Agregue un control Entrada de texto, llámelo **inputPassword**y establezca su propiedad **Mode** en **Password**.
2. Agregue una etiqueta y establezca su propiedad **[Text](properties-core.md)** en esta fórmula:<br>
   **If(inputPassword.Text = "P@ssw0rd", "Access granted", "Access denied")**
   
    ¿Desea más información sobre la función **[If](../functions/function-if.md)** u [otras funciones](../formula-reference.md)?
3. Presione F5 y, a continuación, escriba **P@ssw0rd** en **inputPassword**.
   
    Cuando acabe de escribir la contraseña, la etiqueta dejará de mostrar**Acceso denegado** y empezará a mostrar **Acceso concedido**.
4. Presione Esc para volver al área de trabajo predeterminada.
5. (opcional) Agregue un control como una flecha, configúrelo para desplazarse a otra pantalla y que solo aparezca después de que el usuario escriba la contraseña.
6. (opcional) Agregue un botón, configure su propiedad **[Texto](properties-core.md)** para que muestre **Iniciar sesión**, agregue un temporizador y deshabilite el control Entrada de texto durante un determinado período de tiempo si el usuario escribe una contraseña incorrecta y, a continuación, pulse o haga clic en el botón **Iniciar sesión**.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
* Se aplican requisitos estándar de contraste de color.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
 