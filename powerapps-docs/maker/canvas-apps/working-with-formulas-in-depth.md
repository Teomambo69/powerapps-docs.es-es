---
title: Comprender las fórmulas de comportamiento de una aplicación de lienzo | Microsoft Docs
description: Ofrece información de referencia sobre cómo trabajar con fórmulas de comportamiento, que cambian el estado de una aplicación de lienzo en PowerApps.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/10/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d48559ee3a54cbb723621a0e36f09cb4a1d0fe3b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61556767"
---
# <a name="understand-behavior-formulas-for-canvas-apps-in-powerapps"></a>Comprender las fórmulas de comportamiento de aplicaciones de lienzo en PowerApps

La mayoría de las fórmulas calcula un valor.  Al igual que una hoja de cálculo de Excel, el cálculo nuevo se realiza automáticamente cuando cambian los valores.  Por ejemplo, es posible que desee mostrar el valor de un control **[Etiqueta](controls/control-text-box.md)** en rojo si el valor es menor que cero o en blanco, si no es el caso. De este modo, puede establecer la propiedad **[Color](controls/properties-color-border.md)** de ese control en esta fórmula:

**If( Value(TextBox1.Text) >= 0, Color.Black, Color.Red )**

En este contexto, ¿qué significa que el usuario seleccione un control **[Botón](controls/control-button.md)** ?  No ha cambiado ningún valor, por lo que no es necesario hacer un cálculo nuevo. Excel no tiene un equivalente a un control **[Botón](controls/control-button.md)** .  

Al seleccionar un control **[Botón](controls/control-button.md)** , el usuario inicia una secuencia de acciones, o comportamientos, que cambiará el estado de la aplicación:

* Cambio de la pantalla que se muestra: **[Atrás](functions/function-navigate.md)**  y **[Navigate](functions/function-navigate.md)** funciones.
* Control un [señal](functions/signals.md): **[Habilitar](functions/function-enable-disable.md)**  y **[deshabilitar](functions/function-enable-disable.md)** funciones.
* Actualizar, actualizar o quitar elementos de un [origen de datos](working-with-data-sources.md): **[Actualizar](functions/function-refresh.md)** ,  **[actualización](functions/function-update-updateif.md)** ,  **[UpdateIf](functions/function-update-updateif.md)** , **[revisión](functions/function-patch.md)** ,  **[Quitar](functions/function-remove-removeif.md)** , **[RemoveIf](functions/function-remove-removeif.md)** funciones.
* Actualización de un [variable de contexto](working-with-variables.md#use-a-context-variable):  **[UpdateContext](functions/function-updatecontext.md)**  función.
* Crear, actualizar o quitar elementos de un [colección](working-with-data-sources.md#collections):  **[Recopilar](functions/function-clear-collect-clearcollect.md)** ,  **[clara](functions/function-clear-collect-clearcollect.md)** , **[ClearCollect](functions/function-clear-collect-clearcollect.md)** funciones.

Como estas funciones cambian el estado de la aplicación, no se pueden volver a calcular automáticamente. Puede usarlas en las fórmulas para las propiedades **[OnSelect](controls/properties-core.md)** , **[OnVisible](controls/control-screen.md)** , **[OnHidden](controls/control-screen.md)** , además de otras propiedades del tipo **On...** , que se llaman fórmulas de comportamiento.

### <a name="more-than-one-action"></a>Más de una acción
Use puntos y comas para crear una lista de acciones a realizar. Por ejemplo, es posible que desee actualizar una variable de contexto y, luego, volver a la pantalla anterior:

* **UpdateContext( { x: 1}); Atrás()**

Las acciones se realizan en el orden en que aparecen en la fórmula.  La función siguiente no se iniciará hasta que se complete la función actual. Si se produce un error, no se iniciarán las funciones subsiguientes.

