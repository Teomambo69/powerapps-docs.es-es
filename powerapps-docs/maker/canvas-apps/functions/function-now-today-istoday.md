---
title: Funciones Now, Today e IsToday | Microsoft Docs
description: Información de referencia de las funciones Now, Today e IsToday de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bc3f882a25c5a0588e2be1eac4668c53ebc91e64
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992584"
ms.PowerAppsDecimalTransform: true
---
# <a name="now-today-and-istoday-functions-in-powerapps"></a>Funciones Now, Today e IsToday en PowerApps
Devuelve la fecha y hora actuales y comprueba si un valor de fecha y hora es el día de hoy.

## <a name="description"></a>Descripción
La función **Now** devuelve la fecha y hora actuales como un valor de fecha y hora.

La función **Today** devuelve la fecha actual como un valor de fecha y hora. La parte de la hora es la medianoche. **Today** tiene el mismo valor a lo largo del día, desde hoy a medianoche hasta mañana a medianoche.

La función **IsToday** comprueba si un valor de fecha y hora está comprendido entre hoy a medianoche y mañana a medianoche. Con esta función, se devuelve un valor booleano **true** o **false**.

Todas estas funciones funcionan con la hora local del usuario actual.

Consulte [cómo trabajar con fechas y horas](../show-text-dates-times.md) para más información.

## <a name="volatile-functions"></a>Funciones volátiles
**Now** y **Today** son funciones volátiles.  Cada vez que se evalúa una de estas funciones, se devuelve un valor diferente.  

Cuando se usa en una fórmula de flujo de datos, una función volátil solo devuelve un valor diferente si se vuelve a evaluar la fórmula en la que aparece.  Si no hay ningún otro cambio en la fórmula, presenta el mismo valor durante la ejecución de la aplicación.

Por ejemplo, un control de etiqueta con **Label1.Text = Now()** no cambiará mientras la aplicación esté activa.  Solo se generará un nuevo valor si se cierra y se vuelve a abrir la aplicación.

Si la función forma parte de una fórmula en la que haya cambiado algún elemento más, se volverá a evaluar.  Por ejemplo, si modificamos el ejemplo para incluir un control deslizante con **Label1.Text = DateAdd( Now(); Slider1.Value; Minutes )** , se recuperará la hora actual cada vez que cambie el valor del control deslizante. Asimismo, se volverá a evaluar la propiedad de texto de la etiqueta.

Cuando se usa en una [fórmula de comportamiento](../working-with-formulas-in-depth.md), las funciones volátiles se evalúan cada vez que se evalúa la fórmula de comportamiento.  Encontrará un ejemplo a continuación.

## <a name="syntax"></a>Sintaxis
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DateTime*: requerido.  El valor de fecha y hora para comprobar.

## <a name="examples"></a>Ejemplos
En los ejemplos de esta sección, la hora actual es **3:59 AM** el **12 de febrero de 2015** y el idioma es **en-us**.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Text( Now(); "mm/dd/yyyy hh:mm:ss" )** |Recupera la fecha y hora actuales y las muestra como una cadena. |"02/12/2015 03:59:00" |
| **Text( Today(); "mm/dd/yyyy hh:mm:ss" )** |Recupera solo la fecha actual, dejando la parte de hora como medianoche, y la muestra como una cadena. |"02/12/2015 00:00:00" |
| **IsToday( Now() )** |Comprueba si la fecha y hora actuales se encuentran entre hoy a medianoche y mañana a medianoche. |**true** |
| **IsToday( Today() )** |Comprueba si la fecha actual se encuentra entre hoy a medianoche y mañana a medianoche. |**true** |
| **Text( DateAdd( Now(); 12 ); "mm/dd/yyyy hh:mm:ss" )** |Recupera la fecha y hora actuales, agrega 12 días al resultado y lo muestra como una cadena. |"02/24/2015 03:59:00" |
| **Text( DateAdd( Today(); 12 ); "mm/dd/yyyy hh:mm:ss" )** |Recupera la fecha actual, agrega 12 días al resultado y lo muestra como una cadena. |"02/24/2015 00:00:00" |
| **IsToday( DateAdd( Now(); 12 ) )** |Comprueba si la fecha y hora actuales, más 12 días, se encuentran entre hoy a medianoche y mañana a medianoche. |**false** |
| **IsToday( DateAdd( Today(); 12 ) )** |Comprueba si la fecha actual, más 12 días, se encuentra entre hoy a medianoche y mañana a medianoche. |**false** |

#### <a name="display-a-clock-that-updates-in-real-time"></a>Mostrar un reloj actualizado en tiempo real

1. Agregue un control **[Timer](../controls/control-timer.md)** , establezca su propiedad **Duration** en **1000** y establezca su propiedad **Repeat** en **true**.

    El temporizador se ejecutará durante un segundo y volverá a empezar automáticamente, y así sucesivamente. 

1. Establezca la propiedad **OnTimerEnd** del control en esta fórmula:

    **Set( CurrentTime; Now() )**

    Cada vez que el temporizador vuelve a empezar, es decir, cada segundo, esta fórmula establece la variable global **CurrentTime** en el valor actual de la función **Now**.

    ![Pantalla con un control de temporizador con la fórmula OnTimerEnd = Set(CurrentTime, Now()).](media/function-now-today-istoday/now-set-currenttime.png)

1. Agregue un control **[Label](../controls/control-text-box.md)** y establezca su propiedad **Text** en esta fórmula:

    **Text( CurrentTime; LongTime24 )**

    Use la función **[Text](function-text.md)** para aplicar el formato que quiera a la fecha y la hora o establezca esta propiedad en **CurrentTime** para que se muestren las horas y los minutos, sin los segundos.

    ![Pantalla con un control de etiqueta con la propiedad Text establecida en Text( CurrentTime, LongTime24).](media/function-now-today-istoday/now-use-currenttime.png)

1. Pulse F5 para obtener una versión preliminar de la aplicación y, a continuación, inicie el temporizador. Para ello, haga clic en él o púlselo.

    La etiqueta muestra la hora local de forma continua, segundo a segundo.

    ![Cuatro pantallas en las que se muestran cuatro valores de hora: 13:50:22, 13:50:45, 13:51:03 y 13:51:25.](media/function-now-today-istoday/now-four-times.png)

1. Establezca la propiedad **AutoStart** del temporizador en **true** y la propiedad **Visible** en **false**.

    El temporizador es invisible y se inicia automáticamente.

1. Establezca la propiedad **[OnStart](../controls/control-screen.md)** de la pantalla de modo que la variable **CurrentTime** tenga un valor válido, como en este ejemplo:

    **Set(CurrentTime; Now())**

    La etiqueta aparece en cuanto se inicia la aplicación, antes de que el temporizador se ejecute durante un segundo completo.
