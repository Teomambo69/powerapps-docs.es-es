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
ms.openlocfilehash: 34e76821a10ef5803028bc7fd31bbd70c2845b36
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42849211"
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Controles Forma e Icon de PowerApps
Gráficos para los que puede configurar las propiedades de aspecto y comportamiento.

## <a name="description"></a>Descripción
Estos controles incluyen flechas, formas geométricas, iconos de acción y símbolos para los que puede configurar propiedades como el relleno, el tamaño y la ubicación. También puede configurar su propiedad **[AlSeleccionar](properties-core.md)** para que la aplicación responda si el usuario hace clic en el control o lo pulsa.

## <a name="key-properties"></a>Propiedades principales
**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[PressedFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario toca o hace clic en ese control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas

[**Navegar**( *NombrePantalla*, *TransiciónDePantalla* )](../functions/function-navigate.md)

## <a name="example"></a>Ejemplo

1. Asigne al control **[Pantalla](control-screen.md)** predeterminado el nombre **Target**, agregue un control **[Etiqueta](control-text-box.md)** y establezca su propiedad **[Texto](properties-core.md)** para que muestre **Target**.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?

2. Agregue un control **[Pantalla](control-screen.md)** y denomínelo **Source**.
3. En **Source**, agregue un control **Forma** y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:<br>**Navigate(Target, ScreenTransition.Fade)**
4. Presione F5 y pulse o haga clic en el control **Forma**.

    Aparecerá la pantalla **Target**.

5. (opcional) Presione Esc para volver al área de trabajo predeterminada, agregue un control **Forma** a **Target** y establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **Forma** en la siguiente fórmula:
   <br>**Navigate(Origen, ScreenTransition.Fade)**


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="color-contrast"></a>Contraste de color

Lo siguiente se aplica solo a gráficos que se usan como botones o no solo como decoración.

Para los iconos:
* **[Color](properties-color-border.md)** y **[Fill](properties-color-border.md)**
* Se aplican otros [requisitos de contraste de color estándar](../accessible-apps-color.md) (si se usan como botón)

Para las formas con bordes:
* **[BorderColor](properties-color-border.md)** y el color fuera del control
* **[FocusedBorderColor](properties-color-border.md)** y el color fuera del control (si se usa como botón)

Para las formas sin bordes:
* **[Fill](properties-color-border.md)** y el color fuera del control
* **[PressedFill](properties-color-border.md)** y el color fuera del control (si se usa como botón)
* **[HoverFill](properties-color-border.md)** y el color fuera del control (si se usa como botón)

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente si el gráfico se usa como botón o no solo como decoración.
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar vacía o la cadena **""** vacía si el gráfico es exclusivamente decorativo. De esta forma, los lectores de pantalla omiten el gráfico.
* La propiedad **[AccessibleLabel](properties-accessibility.md)** puede estar vacía o la cadena **""** vacía si el gráfico proporciona información redundante.

    Por ejemplo, un icono **Configuración** con su propiedad **[AccessibleLabel](properties-accessibility.md)** establecida en **Configuración**. Este icono no se utiliza como botón. Se encuentra junto a una **[etiqueta](control-text-box.md)** que también dice **Configuración**. Los lectores de pantalla leerán el icono como **Configuración** y, nuevamente, la etiqueta como **Configuración**. No es necesario tanto detalle. En este caso, el icono no necesita una propiedad **[AccessibleLabel](properties-accessibility.md)**.

    > [!IMPORTANT]
    > Los lectores de pantalla siempre leerán los iconos o formas que tienen **[TabIndex](properties-accessibility.md)** de cero o mayor, incluso si **[AccessibleLabel](properties-accessibility.md)** está vacía. El motivo es que se representan como botones. Si no se proporciona ninguna propiedad **[AccessibleLabel](properties-accessibility.md)**, los lectores de pantalla simplemente leerán el gráfico como un **botón**.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* **[TabIndex](properties-accessibility.md)** debe ser cero o mayor si el gráfico se utiliza como botón. De esta forma, los usuarios de teclado pueden navegar hasta él.
* Los indicadores de foco deben ser claramente visibles si el gráfico se usa como botón. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.

    > [!NOTE]
  > Cuando **[TabIndex](properties-accessibility.md)** es cero o mayor, el icono o forma se representa como un botón. No hay ningún cambio en la apariencia visual, pero los lectores de pantalla identifican correctamente la imagen como un botón. Cuando **[TabIndex](properties-accessibility.md)** es menor que cero, el icono o forma se identifica como una imagen.
