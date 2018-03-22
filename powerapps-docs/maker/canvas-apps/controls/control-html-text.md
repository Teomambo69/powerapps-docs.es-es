---
title: 'Control Texto HTML: referencia | Microsoft Docs'
description: "Información sobre el control Texto HTML, con propiedades y ejemplos"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: bb652f3ba6decad7cb6f93007eaec6340f230ca1
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="html-text-control-in-powerapps"></a>Control Texto HTML en PowerApps
Un cuadro que muestra el texto y convierte las etiquetas HTML al formato.

## <a name="description"></a>Descripción
Un control **Texto HTML** no solo muestra texto sin formato y números, también convierte las etiquetas HTML, como los espacios de no separación.

## <a name="key-properties"></a>Propiedades principales
**[Color](properties-color-border.md)**: el color del texto en un control.

**[Font](properties-text.md)**: el nombre de la familia de fuentes en la que aparece el texto.

**Texto HTML**: texto que aparece en un control de texto HTML y que puede contener etiquetas HTML.

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[DisabledBorderColor](properties-color-border.md)**: el color de un borde del control si la propiedad **[DisplayMode](properties-core.md)** del control está establecida en **Disabled**.

**[DisabledFill](properties-color-border.md)**: el color de fondo de un control si su propiedad **[DisplayMode](properties-core.md)** está establecida en **Disabled**.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario mantiene el puntero del mouse sobre ese control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[RellenoInferior](properties-size-location.md)**: distancia entre el texto de un control y el borde inferior de ese control.

**[RellenoIzquierdo](properties-size-location.md)**: distancia entre el texto de un control y el borde izquierdo de ese control.

**[RellenoDerecho](properties-size-location.md)**: distancia entre el texto de un control y el borde derecho de ese control.

**[RellenoSuperior](properties-size-location.md)**: distancia entre el texto de un control y el borde superior de ese control.

**[Size](properties-text.md)**: el tamaño de la fuente del texto que aparece en un control.

**[Información sobre herramientas](properties-core.md)**: texto explicativo que aparece cuando el usuario mantiene el puntero sobre un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas
[**Buscar**( *FindString*, *WithinString* )](../functions/function-find.md)

## <a name="example"></a>Ejemplo
1. Agregue un control **[Etiqueta](control-text-box.md)**, llámelo **Source** y establezca su propiedad **[Texto](properties-core.md)** en esta cadena:

\<p > Hemos realizado una tarea de globalización y localización particularmente \&nbsp; \&quot; intensiva \&quot; \<p >

¿No sabe cómo [agregar, nombrar y configurar un control](../add-configure-controls.md)?

1. Agregue un Control **Texto HTML** y establezca su propiedad **TextoHTML** con este valor:<br>
   **Source.Text**
   
     El control **Texto HTML** muestra el mismo texto que el **[Etiqueta](control-text-box.md)** pero convierte las etiquetas en los caracteres correspondientes.

