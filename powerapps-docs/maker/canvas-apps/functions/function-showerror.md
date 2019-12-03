---
title: Función ShowError | Microsoft Docs
description: Información de referencia para la función ShowError en Power Apps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: 02881fdf284a174f5118e7ee0ae185cca61578f8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730182"
---
# <a name="notify-function-in-power-apps"></a>Función Notify en Power apps
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

Power apps también puede enviar notificaciones de envío mediante un mecanismo totalmente diferente a la **notificación**.  Para obtener más información, consulte [enviar una notificación en Power apps](../add-notifications.md).

**Notify** siempre devuelve *true*.

Nota: Esta función se denominaba anteriormente **ShowError** cuando solo podía mostrar mensajes de error.

## <a name="syntax"></a>Sintaxis
**Notify**( *Message*, [ *NotificationType* ] )

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

    **Notify( "Hello, World", NotificationType.Error )**

5. Haga clic o presione el botón.

    Ahora, cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como un error.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color rojo](media/function-showerror/hello-world-error.png)

4. Cambie el tipo de mensaje para indicar una advertencia.  Cambie el segundo argumento de la fórmula:

    **Notify( "Hello, World", NotificationType.Warning )**

5. Haga clic o presione el botón.

    Ahora, cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como una advertencia.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color naranja](media/function-showerror/hello-world-warning.png)

4. Cambie el tipo de mensaje para indicar que es correcto.  Cambie el segundo argumento de la fórmula:

    **Notify( "Hello, World", NotificationType.Success )**

5. Haga clic o presione el botón.

    Ahora, cada vez que se hace clic en el botón, se muestra el mensaje **Hello, World** al usuario como una operación correcta.

    ![En el entorno de creación se muestra Button.OnSelect, se llama a Notify y se muestra al usuario el mensaje resultante "Hello, World" en forma de mensaje de color verde](media/function-showerror/hello-world-success.png)
