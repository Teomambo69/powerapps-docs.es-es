---
title: Función ShowError | Microsoft Docs
description: Información de referencia de la función ShowError de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/05/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1a02a83e00b9f377f3882cb32c1e6b6606b5cc2a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678244"
ms.PowerAppsDecimalTransform: true
---
# <a name="notify-function-in-powerapps"></a>Función Notify en PowerApps
Muestra un mensaje de pancarta al usuario.

## <a name="description"></a>Descripción
La función **Notify** muestra un mensaje de pancarta al usuario en la parte superior de la pantalla, superpuesto sobre lo que se muestre actualmente.  

Se usa el color y el icono adecuados según el tipo del mensaje.   El tipo se especifica mediante el segundo argumento de la función:

| Argumento NotificationType | Descripción |
| --- | --- |
| **NotificationType.Error** | Muestra el mensaje como un error. |
| **NotificationType.Information** (valor predeterminado) | Muestra el mensaje como información.  |
| **NotificationType.Success** | Muestra el mensaje como correcto. |
| **NotificationType.Warning** | Muestra el mensaje como una advertencia. |

Los mensajes se muestran cuando se crea la aplicación y cuando los usuarios finales la usan.

**Notify** solo se puede usar en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

**Notify** se puede emparejar con la función [**IfError**](function-iferror.md) para detectar y notificar errores con un mensaje de error personalizado.

Power apps también puede enviar notificaciones de envío mediante un mecanismo totalmente diferente a la **notificación**.  Para obtener más información, vea [Envío de una notificación push en PowerApps](../add-notifications.md).

**Notify** siempre devuelve *true*.

Nota: Esta función se denominaba anteriormente **ShowError** cuando solo podía mostrar mensajes de error.

## <a name="syntax"></a>Sintaxis
**Notify**( *Message*; [ *NotificationType* ] )

* *Mensaje*: es necesario.  Mensaje que se va a mostrar al usuario.
* *NotificationType*: opcional.  El tipo de mensaje que se va a mostrar de la tabla anterior.  El valor predeterminado es **NotificationType.Information**.  

## <a name="examples"></a>Ejemplos

### <a name="step-by-step"></a>Paso a paso

1. Agregue un control **Botón** a la pantalla.

2. Establezca la propiedad **OnSelect** del control **Botón** en:

    **Notify( "Hello, World" )**

3. Haga clic o presione el botón.  

    Cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como una información.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color azul](media/function-showerror/hello-world.png)

4. Cambie el tipo de mensaje para indicar un error.  Agregue un segundo argumento a la fórmula:

    **Notify( "Hello, World"; NotificationType.Error )**

5. Haga clic o presione el botón.

    Ahora, cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como un error.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color rojo](media/function-showerror/hello-world-error.png)

4. Cambie el tipo de mensaje para indicar una advertencia.  Cambie el segundo argumento de la fórmula:

    **Notify( "Hello, World"; NotificationType.Warning )**

5. Haga clic o presione el botón.

    Ahora, cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como una advertencia.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color naranja](media/function-showerror/hello-world-warning.png)

4. Cambie el tipo de mensaje para indicar que es correcto.  Cambie el segundo argumento de la fórmula:

    **Notify( "Hello, World"; NotificationType.Success )**

5. Haga clic o presione el botón.

    Ahora, cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como una operación correcta.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color verde](media/function-showerror/hello-world-success.png)
