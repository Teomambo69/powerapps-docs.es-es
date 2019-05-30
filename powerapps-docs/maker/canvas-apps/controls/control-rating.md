---
title: 'Control Clasificación: referencia | Microsoft Docs'
description: Información sobre el control Clasificación, con propiedades y ejemplos
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
ms.openlocfilehash: 1979ad63ce9cd5fbe3f3a9a3fa5a56df5e80966e
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61526065"
---
# <a name="rating-control-in-powerapps"></a>Control Clasificación en PowerApps
Un control con el que los usuarios pueden indicar un valor comprendido entre 1 y el número máximo que especifique.

## <a name="description"></a>Descripción
En este control el usuario puede indicar, por ejemplo, cuánto le ha gustado algo seleccionando un cierto número de estrellas.

## <a name="key-properties"></a>Propiedades principales
**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

**Max**: el valor máximo para el que el usuario puede establecer un control deslizante o una clasificación.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**RellenoDeClasificación**: el color de las estrellas de un control de clasificación.

**ReadOnly**: indica si un usuario puede cambiar el valor de un control deslizante o el control de clasificación.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**MostrarValor**: indica si el valor de un control deslizante o una clasificación aparece cuando el usuario cambia ese valor o mantiene el puntero sobre el control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Average**( *Value1*, *Value2,* ... )](../functions/function-aggregates.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **Clasificación** y llámelo **Cuantitativo**.
   
    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?
2. Agregue un control **[Entrada de texto](control-text-input.md)**, denomínelo **Cualitativo**, y muévalo debajo del control **Clasificación**.
3. Establezca la propiedad **[Default](properties-core.md)** del control **[Entrada de texto](control-text-input.md)** en **""** y establezca su **TextoDeSugerencia** en esta fórmula:
   <br>**If(Quantitative.Value > 3, "¿qué le gustó especialmente?", "¿cómo podemos mejorar?")**
   
    ¿Desea más información sobre la función **[If](../functions/function-if.md)** u [otras funciones](../formula-reference.md)?
4. Presione F5 y, a continuación, pulse o haga clic en cuatro o cinco estrellas en el control **Clasificación**.
   
    La sugerencia del control **[Entrada de texto](control-text-input.md)** cambia para reflejar la alta clasificación.
5. Pulse o haga clic en menos de cuatro estrellas en **Cuantitativo**.
   
    La sugerencia del control **[Entrada de texto](control-text-input.md)** cambia para reflejar la baja clasificación.
6. Presione Esc para volver al área de trabajo predeterminada.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **RatingFill** y **[Fill](properties-color-border.md)**

Y esto, además de los [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

    > [!NOTE]
  > Los lectores de pantalla tratan el control **Clasificación** como botones de radio.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
* Considere la posibilidad de usar otro control si hay demasiadas estrellas. Puede resultar agotador navegar con un teclado y difícil seleccionar con precisión con una pantalla táctil.

    > [!NOTE]
  > Las mismas interacciones de teclado para los botones de radio se pueden emplear en **Clasificación**.
