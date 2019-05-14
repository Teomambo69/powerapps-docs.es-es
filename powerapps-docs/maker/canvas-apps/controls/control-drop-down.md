---
title: 'Control Lista desplegable: referencia | Microsoft Docs'
description: Información sobre el control Lista desplegable, con propiedades y ejemplos
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
ms.openlocfilehash: 02e8477873adad476c65e513a470e027aee5cd5c
ms.sourcegitcommit: 8d0ba2ec0c97be91d1350180dd6881c14dec8f2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65517383"
ms.PowerAppsDecimalTransform: true
---
# <a name="drop-down-control-in-powerapps"></a>Control Lista desplegable en PowerApps
Una lista que muestra solo el primer elemento a menos que el usuario la abra.

## <a name="description"></a>Descripción
Un control **Lista desplegable** conserva el estado real de la pantalla, en especial cuando la lista contiene un gran número de opciones. El control toma una sola línea a menos que el usuario seleccione las comillas angulares para revelar más opciones.  El control muestra un máximo de 500 elementos.

## <a name="key-properties"></a>Propiedades principales
**[Valor predeterminado](properties-core.md)**: valor inicial de un control antes de que el usuario especifique otro.

**[Elementos](properties-core.md)**: origen de datos que contiene los elementos que aparecen en el control. Si el origen tiene varias columnas, establezca la propiedad **Valor** del control en la columna de datos que quiere mostrar.
  
**Valor**: columna de datos que quiere mostrar en el control (por ejemplo, si un origen de datos tiene varias columnas).

**Seleccionado** : el registro de datos que representa el elemento seleccionado.

**AllowEmptySelection** : indica si el control muestra una selección vacía si no se ha seleccionado ningún elemento. Usuarios de la aplicación también pueden borrar sus opciones al seleccionar el elemento en blanco.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**ChevronBackground**: el color detrás de la flecha hacia abajo en una lista desplegable.

**ChevronFill**: el color de la flecha hacia abajo en una lista desplegable.

**[Color](properties-color-border.md)**: el color del texto en un control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledColor](properties-color-border.md)**: el color del texto en un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**[FontWeight](properties-text.md)**  : el peso del texto en un control: **Negrita**, **seminegrita**, **Normal**, o **más claro**.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[HoverColor](properties-color-border.md)**: el color del texto de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[Italic](properties-text.md)**: indica si el texto de un control está en cursiva.

**[AlCambiar](properties-core.md)**: indica cómo responde la aplicación cuando el usuario cambia el valor de un control (por ejemplo, mediante el ajuste de un control deslizante).

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedColor](properties-color-border.md)**: el color de texto de un control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[Reset](properties-core.md)**: indica si un control vuelve a su valor predeterminado.

**(En desuso) SelectedText** : un valor de cadena que representa el elemento seleccionado.

**[ColorDeSelección](properties-color-border.md)**: color del texto de los elementos seleccionados en una lista o de la herramienta de selección de un control de entrada manuscrita.

**[RellenoDeSelección](properties-color-border.md)**: el color de fondo de uno o varios elementos seleccionados en una lista o un área seleccionada de un control de entrada manuscrita.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Strikethrough](properties-text.md)**: indica si aparece una línea sobre el texto de un control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Underline](properties-text.md)**: indica si aparece una línea debajo del texto de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo

### <a name="simple-list"></a>Lista sencilla

1. Agregue un control **Lista desplegable** y establezca su propiedad **[Items](properties-core.md)** en esta expresión:

    `["Seattle"; "Tokyo"; "London"; "Johannesburg"; "Rio de Janeiro"]`

    ¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

1. Para mostrar los elementos de la lista, seleccione la flecha hacia abajo del control mientras presiona la tecla Alt.

### <a name="list-from-a-data-source"></a>Lista de un origen de datos
Los principios de este procedimiento se aplican a ninguna [origen de datos que se proporciona tablas](../connections-list.md#tables) pero, para seguir estos pasos exactamente, debe abrir un entorno para el que una base de datos de Common Data Service ha sido creados y ver datos agregados.

1. [Abra una aplicación en blanco](../data-platform-create-app-scratch.md#open-a-blank-app) y [especifique la entidad **Cuentas**](../data-platform-create-app-scratch.md#specify-an-entity).

1. Agregue un control **Lista desplegable** y establezca su propiedad **[Elementos](properties-core.md)** en esta fórmula:

    `Distinct(Accounts; address1_city)`

    Esta fórmula muestra todas las ciudades de la entidad **Cuentas**. Si hay más de un registro con la misma ciudad, la función **[Distinct](../functions/function-distinct.md)** oculta la duplicación en el control de lista desplegable.

1. (opcional) Cambie el nombre del control **Lista desplegable** a **Ciudades**, agregue un control vertical **Galería** y establezca la propiedad **[Elementos](properties-core.md)** de la galería en esta fórmula:

    `Filter(Accounts; address1_city = Cities.Selected.Value)`

    Esta función **[Filtro](../functions/function-filter-lookup.md)** muestra únicamente aquellos registros de la entidad **Cuentas** en los que la ciudad coincida con el valor seleccionado en el control **Ciudades**.

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **ChevronFill** y **ChevronBackground**
* **ChevronHoverFill** y **ChevronHoverBackground**
* **SelectionColor** y **SelectionFill**
* **SelectionFill** y **[Fill](properties-color-border.md)**

Y esto, además de los [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.
