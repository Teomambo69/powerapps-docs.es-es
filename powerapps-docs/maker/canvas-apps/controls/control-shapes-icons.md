---
title: 'Controles Forma e Icono: referencia | Microsoft Docs'
description: Información sobre los controles Forma e Icon, con propiedades y ejemplos
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
ms.openlocfilehash: 88e0a74d2c25d1d2f5f571f4d1850417d1aab9ca
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63318429"
ms.PowerAppsDecimalTransform: true
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Controles Forma e Icon de PowerApps
Gráficos para los que puede configurar las propiedades de aspecto y comportamiento.

## <a name="description"></a>Descripción
Estos controles incluyen flechas, formas geométricas, iconos de acción y símbolos para los que puede configurar propiedades como el relleno, el tamaño y la ubicación. También puede configurar sus **[Alseleccionar](properties-core.md)** propiedad para que la aplicación responde si el usuario selecciona el control.

## <a name="key-properties-icons-and-shapes"></a>Propiedades de clave (iconos y formas)
**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[OnSelect](properties-core.md)**  : cómo responde la aplicación cuando el usuario selecciona un control.

## <a name="key-properties-icons-only"></a>Propiedades de clave (sólo para iconos)

**Icono** -el tipo de icono que se va a mostrar (por ejemplo, **ArrowDown** o **ShoppingCart**). 

**Rotación** -el número de grados para girar el icono. 

**Color** : el color del icono por nombre o los valores RGBA.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[PressedBorderColor](properties-color-border.md)**  : el color del borde de un control cuando el usuario selecciona ese control.

**[PressedFill](properties-color-border.md)**  : el color de fondo de un control cuando el usuario selecciona ese control.

**[TabIndex](properties-accessibility.md)** : orden de navegación del teclado en relación con otros controles.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas

[**Navegar**( *NombrePantalla*; *TransiciónDePantalla* )](../functions/function-navigate.md)

## <a name="example"></a>Ejemplo

1. Asigne al control **[Pantalla](control-screen.md)** predeterminado el nombre **Target**, agregue un control **[Etiqueta](control-text-box.md)** y establezca su propiedad **[Texto](properties-core.md)** para que muestre **Target**.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

1. Agregue un control **[Pantalla](control-screen.md)** y denomínelo **Source**.

1. En **Source**, agregue un control **Forma** y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:

  `Navigate(Target; ScreenTransition.Fade)`
  
1. Presione F5 y, a continuación, seleccione el **forma** control.

    Aparecerá la pantalla **Target**.

1. (opcional) Presione Esc para volver al área de trabajo predeterminada, agregue un control **Forma** a **Target** y establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **Forma** en la siguiente fórmula:

  `Navigate(Source; ScreenTransition.Fade)`

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="color-contrast"></a>Contraste de color

Lo siguiente se aplica solo a gráficos que se usan como botones o no solo como decoración.

Para los iconos:
- **[Color](properties-color-border.md)** y **[Fill](properties-color-border.md)**
- Se aplican otros [requisitos de contraste de color estándar](../accessible-apps-color.md) (si se usan como botón)

Para las formas con bordes:
- **[BorderColor](properties-color-border.md)** y el color fuera del control
- **[FocusedBorderColor](properties-color-border.md)** y el color fuera del control (si se usa como botón)

Para las formas sin bordes:
- **[Fill](properties-color-border.md)** y el color fuera del control
- **[PressedFill](properties-color-border.md)** y el color fuera del control (si se usa como botón)
- **[HoverFill](properties-color-border.md)** y el color fuera del control (si se usa como botón)

### <a name="screen-reader-support"></a>Compatibilidad con el lector de pantalla
- **[AccessibleLabel](properties-accessibility.md)**  debe establecerse en una cadena vacía si el gráfico se usa como un botón o en caso contrario, no solo como decoración.

- **[AccessibleLabel](properties-accessibility.md)**  debe estar vacía o una cadena vacía **""** si el gráfico proporciona información redundante o es exclusivamente decorativo. Este valor hace que los lectores de pantalla omiten el gráfico.

Por ejemplo, puede establecer el **[AccessibleLabel](properties-accessibility.md)** propiedad de un **configuración** icono para **configuración**. Este icono no se usa como un botón. Se encuentra junto a un **[etiqueta](control-text-box.md)** que también dice **configuración**. Los lectores de pantalla leerán el icono y la etiqueta como **configuración**, que es innecesariamente detallado. En este caso, no necesita el icono de un  **[AccessibleLabel](properties-accessibility.md)** .

> [!IMPORTANT]
> Los lectores de pantalla leerán leer un icono o forma como **botón** si su **[AccessibleLabel](properties-accessibility.md)** está establecida en una cadena vacía y su **[TabIndex ](properties-accessibility.md)** se establece en cero o mayor. Estos iconos o formas se representan como botones. 

### <a name="keyboard-support"></a>Compatibilidad con el teclado
- **[TabIndex](properties-accessibility.md)**  debe ser cero o mayor si el gráfico se utiliza como un botón. Si establece este valor para un icono o forma, los usuarios de teclado pueden navegar a él.

- Los indicadores de foco deben ser claramente visibles si el gráfico se utiliza como un botón. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para lograr este resultado.

    > [!NOTE]
    > Cuando **[TabIndex](properties-accessibility.md)** es cero o mayor, el icono o forma se representa como un botón. No cambia su aspecto, pero los lectores de pantalla identifican correctamente la imagen como un botón. Cuando **[TabIndex](properties-accessibility.md)** es menor que cero, el icono o forma se identifica como una imagen.
