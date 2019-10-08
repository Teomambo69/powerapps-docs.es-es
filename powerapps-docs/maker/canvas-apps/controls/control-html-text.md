---
title: 'Control Texto HTML: referencia | Microsoft Docs'
description: Información sobre el control Texto HTML, con propiedades y ejemplos
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
ms.openlocfilehash: 5706b2c1b21c0135cc60678b6cf3f882df6fa56c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986625"
ms.PowerAppsDecimalTransform: true
---
# <a name="html-text-control-in-powerapps"></a>Control Texto HTML en PowerApps
Un cuadro que muestra el texto y convierte las etiquetas HTML al formato.

## <a name="description"></a>Descripción
Un control **Texto HTML** no solo muestra texto sin formato y números, también convierte las etiquetas HTML, como los espacios de no separación.

## <a name="key-properties"></a>Propiedades principales
**[Color](properties-color-border.md)** : el color del texto en un control.

**[Font](properties-text.md)** : el nombre de la familia de fuentes en la que aparece el texto.

**HtmlText**: texto que aparece en un control de texto HTML y que puede contener etiquetas HTML.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[DisplayMode](properties-core.md)** : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)** : el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)** : el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)** : el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[OnSelect](properties-core.md)** : indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)** : distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)** : distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)** : distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)** : distancia entre el texto de un control y el borde superior de ese control.

**[Size](properties-text.md)** : el tamaño de la fuente del texto que aparece en un control.

**[Información sobre herramientas](properties-core.md)** : texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Buscar**( *FindString*; *WithinString* )](../functions/function-find.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **[Etiqueta](control-text-box.md)** , llámelo **Source** y establezca su propiedad **[Texto](properties-core.md)** en esta cadena:

"\<p>Hemos\&nbsp;realizado una tarea de globalización y localización particularmente \&quot;intensiva\&quot;.\<p>"

¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

1. Agregue un control **Texto HTML** y establezca su propiedad **HtmlText** en este valor:<br>
   **Source.Text**
   
     El control **Texto HTML** muestra el mismo texto que el **[Etiqueta](control-text-box.md)** pero convierte las etiquetas en los caracteres correspondientes.


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
La finalidad del **texto HTML** no es ser interactivo. Solo debe usarse para la visualización de texto.

### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **[Color](properties-color-border.md)** y **[Fill](properties-color-border.md)**
* Texto con colores personalizados y su fondo

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **HtmlText** debe existir.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **HtmlText** no debe contener elementos interactivos, como `<button>`, `<a>` o `<input>`. El sistema de **[TabIndex](properties-accessibility.md)** en PowerApps no tiene en cuenta los elementos dentro de **HtmlText**.
