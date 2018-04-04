---
title: Función ShowError | Microsoft Docs
description: Información de referencia de la función ShowError de PowerApps, con sintaxis y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: gregli
ms.openlocfilehash: 7c1d5a8c7b35d316a2720d564977170029e28359
ms.sourcegitcommit: a9d33322228c398d29964429602dc3fe19fa67d2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="showerror-function-in-powerapps"></a>Función ShowError en PowerApps
Muestra un error al usuario.

## <a name="description"></a>Descripción
La función **ShowError** muestra un error al usuario.  Los mensajes se muestran cuando se crea la aplicación y cuando los usuarios finales la usan.

**ShowError** solo se puede usar en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

**ShowError** siempre devuelve *true*.

**ShowError** se puede emparejar con la función [**IfError**](function-iferror.md) para detectar y notificar errores con un mensaje de error personalizado.

## <a name="syntax"></a>Sintaxis
**ShowError**( *Mensaje* )

* *Mensaje*: obligatorio.  Mensaje que se va a mostrar al usuario. 

## <a name="examples"></a>Ejemplos

### <a name="step-by-step"></a>Paso a paso

1. Agregue un control **Botón** a la pantalla.

2. Establezca la propiedad **OnSelect** del control **Botón** en:

    **ShowError( "Hello, World" )**

3. Haga clic o presione el botón.  

    Cada vez que se hace clic en el botón se muestra al usuario el mensaje **Hello, World**.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a ShowError y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color rojo](media/function-showerror/hello-world.png)
