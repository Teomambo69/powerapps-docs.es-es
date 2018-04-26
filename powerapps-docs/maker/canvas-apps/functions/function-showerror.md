---
title: Función ShowError | Microsoft Docs
description: Información de referencia de la función ShowError de PowerApps, con sintaxis y ejemplos
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 03/21/2018
ms.author: gregli
ms.openlocfilehash: 1191016f26192f997b8347cdbfecc7701c19cb8c
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
