---
title: 'Control deslizante: referencia | Microsoft Docs'
description: Información sobre el control deslizante, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 198275ef72129b17cbf73a5f4eb47fd342de3b24
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42830745"
---
# <a name="slider-control-in-powerapps"></a>Control deslizante en PowerApps
Un control con el que el usuario puede especificar un valor arrastrando un controlador.

## <a name="description"></a>Descripción
El usuario puede indicar un valor comprendido entre un valor mínimo y un máximo que puede especificar arrastrando el controlador de un control deslizante de derecha a izquierda o de arriba a abajo, dependiendo de la dirección que desee.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**Max**: el valor máximo para el que el usuario puede establecer un control deslizante o una clasificación.

**Max**: el valor mínimo para el que el usuario puede establecer un control deslizante.

**[Valor](properties-core.md)**: el valor de un control de entrada.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**RellenoDeControladorActivo**: el color del controlador de un control deslizante cuando el usuario cambia el valor.

**RellenoDeControlador**: el color del controlador (el elemento que cambia de posición) en un control de alternancia o control deslizante.

**RellenoDeControladorAlMantener**: el color del texto del controlador cuando el usuario mantiene el puntero sobre él.

**HandleSize**: el diámetro del controlador.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**Layout**: indica si el usuario se desplaza por la galería o ajusta un control deslizante de arriba a abajo (**Vertical**) o de izquierda a derecha (**Horizontal**).

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**RellenoDeRaíl**: color de fondo del rectángulo en un control Alternar cuando su valor es **false** o color de la línea a la derecha del identificador en un control deslizante.

**RellenoRaílAlMantenerPuntero**: al mantener el puntero sobre un control Alternar o deslizante, color de fondo del rectángulo del primero cuando su valor es **false** o color de la línea a la derecha del identificador del segundo.

**ReadOnly**: indica si un usuario puede cambiar el valor de un control deslizante o el control de clasificación.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**MostrarValor**: indica si el valor de un control deslizante o una clasificación aparece cuando el usuario cambia ese valor o mantiene el puntero sobre el control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**RellenoDeValor**: color de fondo del rectángulo en un control Alternar cuando su valor es **true** o color de la línea a la izquierda del identificador en un control deslizante.

**RellenoValorAlMantenerPuntero**: al mantener el puntero del mouse sobre un control Alternar o Control deslizante, color de fondo del rectángulo del primero cuando su valor es **true** o color de la línea a la izquierda del identificador del segundo.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Sum**( *Value1*, *Value2* )](../functions/function-aggregates.md)

## <a name="example"></a>Ejemplo
1. Agregue un botón y establezca su propiedad **[OnSelect](properties-core.md)** en esta fórmula:
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
   
    ¿Desea más información sobre la función **[ClearCollect](../functions/function-clear-collect-clearcollect.md)** u [otras funciones](../formula-reference.md)?
2. Presione F5, seleccione el botón y presione Esc.
3. Agregue un control deslizante, muévalo debajo del botón y llámelo **MinPopulation**.
4. Establezca la propiedad **Max** del control deslizante en **5000000** y la propiedad **Min** en **1000000**.
5. Agregue una galería de texto en orientación vertical, muévala debajo del control deslizante y establezca la propiedad **[Elementos](properties-core.md)** de la galería en esta fórmula:<br>
   **Filter(CityPopulations, Population > MinPopulation)**
6. En el primer elemento de la galería, establezca la propiedad **[Texto](properties-core.md)** de la etiqueta superior en **ThisItem.City** y establezca la propiedad **[Texto](properties-core.md)** de la etiqueta inferior en esta fórmula:<br> **Text(ThisItem.Population, "##,###")**
7. Presione F5 y, a continuación, ajuste **MinPopulation** para que se muestren solo aquellas ciudades que tengan una población mayor que el valor especificado.
8. Presione Esc para volver al área de trabajo predeterminada.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **ValueFill** y **RailFill**
* **ValueHoverFill** y **RailHoverFill**
* **[FocusedBorderColor](properties-color-border.md)** y el color situado fuera del control
* **ValueFill** y el color de fondo
* **RailFill** y el color de fondo
* **ValueHoverFill** y el color de fondo
* **RailHoverFill** y el color de fondo

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
* El valor del control deslizante se debe mostrar al interactuar con el teclado. Esto puede lograrse mediante cualquiera de estos métodos:
    * Establezca **ShowValue** en **true**.
    * Agregue un control **[Etiqueta](control-text-box.md)** adyacente al control deslizante. Establezca la propiedad **[Text](properties-core.md)** de la etiqueta en la propiedad **[Value](properties-core.md)** del control deslizante.
