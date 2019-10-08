---
title: 'Controles Forma e Icono: referencia | Microsoft Docs'
description: Información sobre los controles Forma e Icon, con propiedades y ejemplos
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
ms.openlocfilehash: 46f1974b5ff32cf21d1e9f24c15362c24b44fbe3
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986331"
ms.PowerAppsDecimalTransform: true
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Controles Forma e Icon de PowerApps
Gráficos para los que puede configurar las propiedades de aspecto y comportamiento.

## <a name="description"></a>Descripción
Estos controles incluyen flechas, formas geométricas, iconos de acción y símbolos para los que puede configurar propiedades como el relleno, el tamaño y la ubicación. También puede configurar su propiedad **[alseleccionar](properties-core.md)** para que la aplicación responda si el usuario selecciona el control.

## <a name="key-properties-icons-and-shapes"></a>Propiedades de clave (iconos y formas)
**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[Alseleccionar](properties-core.md)** : cómo responde la aplicación cuando el usuario selecciona un control.

## <a name="key-properties-icons-only"></a>Propiedades de clave (solo iconos)

**Icono** : el tipo de icono que se va a mostrar (por ejemplo, **ArrowDown** o **ShoppingCart**). 

**Rotation** : el número de grados que se va a girar el icono. 

**Color** : el color del icono por nombre o valores RGBA.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)** : etiqueta para lectores de pantalla.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)** : el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[PressedBorderColor](properties-color-border.md)** : el color del borde de un control cuando el usuario selecciona ese control.

**[PressedFill](properties-color-border.md)** : el color de fondo de un control cuando el usuario selecciona ese control.

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
  
1. Presione F5 y, a continuación, seleccione el control **forma** .

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
- **[Propiedad accessiblelabel](properties-accessibility.md)** debe establecerse en una cadena que no esté vacía si el gráfico se utiliza como botón o no solo para la decoración.

- **[Propiedad accessiblelabel](properties-accessibility.md)** debe estar vacío o la cadena vacía **""** si el gráfico proporciona información redundante o es meramente para la decoración. Este valor hace que los lectores de pantalla omitan el gráfico.

Por ejemplo, puede establecer la propiedad **[propiedad accessiblelabel](properties-accessibility.md)** de un icono de **configuración** en **configuración**. Este icono no se utiliza como botón. Está junto a una **[etiqueta](control-text-box.md)** que también indica la **configuración**. Los lectores de pantalla leerán el icono y la etiqueta como **configuración**, que es innecesariamente detallado. En este caso, el icono no necesita un **[propiedad accessiblelabel](properties-accessibility.md)** .

> [!IMPORTANT]
> Los lectores de pantalla leerán un icono o forma como **botón** si su **[propiedad accessiblelabel](properties-accessibility.md)** se establece en una cadena vacía y su **[TabIndex](properties-accessibility.md)** se establece en cero o más. Estos iconos o formas se representan como botones. 

### <a name="keyboard-support"></a>Compatibilidad con el teclado
- **[TabIndex](properties-accessibility.md)** debe ser cero o superior si el gráfico se utiliza como botón. Si establece este valor para un icono o una forma, los usuarios del teclado pueden desplazarse hasta él.

- Los indicadores de foco deben ser claramente visibles si el gráfico se utiliza como botón. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para lograr este resultado.

    > [!NOTE]
    > Cuando **[TabIndex](properties-accessibility.md)** es cero o mayor, el icono o forma se representa como un botón. Su apariencia no cambia, pero los lectores de pantalla identificarán correctamente la imagen como un botón. Cuando **[TabIndex](properties-accessibility.md)** es menor que cero, el icono o forma se identifica como una imagen.
