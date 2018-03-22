---
title: 'Controles Forma e Icono: referencia | Microsoft Docs'
description: Información sobre los controles Forma e Icon, con propiedades y ejemplos
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
ms.openlocfilehash: 7a71695460453816dd5c63dad8477cb7ccc703d7
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Controles Forma e Icon de PowerApps
Gráficos para los que puede configurar las propiedades de aspecto y comportamiento.

## <a name="description"></a>Descripción
Estos controles incluyen flechas, formas geométricas, iconos de acción y símbolos para los que puede configurar propiedades como el relleno, el tamaño y la ubicación. También puede configurar su propiedad **[AlSeleccionar](properties-core.md)** para que la aplicación responda si el usuario hace clic en el control o lo pulsa.

## <a name="key-properties"></a>Propiedades principales
**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

## <a name="additional-properties"></a>Propiedades adicionales
**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[HoverFill](properties-color-border.md)**: el color de fondo de un control cuando el usuario mantiene el puntero del mouse sobre él.

**[PressedBorderColor](properties-color-border.md)**: el color de un borde del control cuando el usuario toca o hace clic en ese control.

**[FocusedBorderThickness](properties-color-border.md)**: grosor del borde del control cuando se resalta el teclado.

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
3. En **Source**, agregue un control **Forma** y establezca su propiedad **[AlSeleccionar](properties-core.md)** en esta fórmula:
   <br>**Navigate(Target, ScreenTransition.Fade)**
4. Presione F5 y pulse o haga clic en el control **Forma**.
   
    Aparecerá la pantalla **Target**.
5. (opcional) Presione Esc para volver al área de trabajo predeterminada, agregue un control **Forma** a **Target** y establezca la propiedad **[AlSeleccionar](properties-core.md)** del control **Forma** en la siguiente fórmula:
   <br>**Navigate(Source, ScreenTransition.Fade)**

