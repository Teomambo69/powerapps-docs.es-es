---
title: Mostrar texto, fechas y horas en una aplicación de lienzo | Microsoft Docs
description: En Power Apps, mostrar texto, fechas y horas en una aplicación de lienzo
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/16/2016
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0fbbb330a8594ce953530ece623472826be14891
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732999"
ms.PowerAppsDecimalTransform: true
---
# <a name="show-text-dates-and-times-in-power-apps"></a>Mostrar texto, fechas y horas en Power apps
En Power Apps, agregue fechas y horas a una aplicación de lienzo y asígneles formato para mostrar el nivel de detalle correcto o para reflejar la configuración regional. Calcule el tiempo entre dos fechas o calcule una fecha que esté cierto tiempo antes o después de una fecha que especifique. Convierta fechas en y desde valores independientes para días, meses y años, y convierta horas en y desde valores independientes para horas, minutos y segundos.

Por ejemplo, agregue datos de usuarios sobre acciones o reuniones de cliente, datos de un origen externo o datos de otra aplicación creada en Power apps. Si esos datos incluyen horas detalladas hasta el milisegundo, redondéelas al minuto más cercano para simplificarlas. Calcule cuántos días quedan hasta un hito importante. Si desea programar reuniones con los clientes cada cinco días, calcule esas fechas automáticamente. Si el 10 de mayo de 1985 está almacenado en campos independientes para el día, el mes y el año, consolide esos campos en un solo valor. También puede dividir cada fecha en valores independientes si su aplicación los administra por separado.

## <a name="prerequisites"></a>Requisitos previos

* [Regístrese](../signup-for-powerapps.md) en Power apps y, a continuación, [inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para suscribirse.
* Cree una aplicación o abra una aplicación existente en Power apps.
* Aprenda a [configurar un control](add-configure-controls.md) en Power apps.

## <a name="show-text-in-a-label-control"></a>Mostrar texto en un control Etiqueta
Muestre texto en un control **[Etiqueta](controls/control-text-box.md)** estableciendo el valor de su propiedad **[Texto](controls/properties-core.md)** . Establezca esta propiedad escribiendo directamente en el control o escribiendo una expresión en la barra de fórmulas.

* Si escribe directamente en el control, este muestra exactamente lo que escribe.
* Si escribe una expresión en la barra de fórmulas, el control muestra el resultado de la expresión.

A continuación, se ofrecen algunos ejemplos.

1. Agregue un control **[Etiqueta](controls/control-text-box.md)** denominado **ShowText** y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:
   <br>**Now()**
   
    Si su equipo tiene establecida la configuración regional "en-us", la fecha y hora actuales aparecen en este formato:  <br>*mm/dd/aaaa hh:mm AM/PM*
   
    Si su equipo tiene establecida la configuración regional "fr-fr", la fecha y hora actuales aparecen en este formato:  <br>*dd/mm/aaaa hh:mm AM/PM*
2. Establezca la propiedad **[Text](controls/properties-core.md)** de **ShowText** en esta fórmula:
   <br>**DateDiff(Today(); DateValue("01/01/2020"))**
   
    ![Número de días entre hoy y el 1 de enero de 2020](./media/show-text-dates-times/date-diff-text.png)
   
    El control muestra el número de días entre hoy y el 1 de enero de 2020. Para ello, usa estas funciones:
   
   * **DateDiff**, que calcula el número de días, trimestres o años entre dos fechas.
   * **Today**, que calcula el día actual como un valor.
   * **DateValue**, que convierte una cadena literal, como la que se muestra entre comillas dobles, en un valor en el que se pueden realizar cálculos.
3. Agregue un control **[Text input](controls/control-text-input.md)** denominado **BirthDate** y colóquelo bajo **ShowText**.

4. En **BirthDate**, escriba el mes y el día de su nacimiento (por ejemplo, **05/18**).

5. Establezca la propiedad **[Text](controls/properties-core.md)** de **ShowText** en esta fórmula:
   <br>**DateDiff(Today(); DateValue(BirthDate.Text))**
   
    ![Número de días entre hoy y su cumpleaños](./media/show-text-dates-times/birth-diff.png)
   
    **ShowText** muestra el número de días entre hoy y la fecha que haya escrito en **BirthDate**. Si la fecha de su cumpleaños ya ha pasado este año, **ShowText** muestra un valor negativo.

## <a name="format-dates-and-times-by-using-datetimevalue"></a>Aplicar formato a fechas y horas mediante DateTimeValue
Convierta fechas y horas de cadenas de texto a valores, a los que puede dar formato de diversas maneras y usarlos en los cálculos. Especifique el formato con las opciones integradas y personalizadas.

> [!NOTE]
> Las funciones **[DateTimeValue](functions/function-datevalue-timevalue.md)** y **[DateValue](functions/function-datevalue-timevalue.md)** pueden convertir en valores fechas que estén en cualquiera de estos formatos:  
> 
> * MM/DD/AAAA  
> * DD/MM/AAAA  
> * DD Mes AAAA  
> * Mes DD, AAAA  
> 
> 

1. Agregue un control **[Text input](controls/control-text-input.md)** denominado **ArrivalDateTime** y escriba una fecha y una hora en este formato:
   <br>**5/10/85 6:15 AM**
2. Agregue un control **[Etiqueta](controls/control-text-box.md)** denominado **ShowDate** y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:
   <br>**DateTimeValue(ArrivalDateTime.Text)**
   
    ![Convertir una fecha y hora de texto a un valor](./media/show-text-dates-times/date-value.png)
   
    **ShowDate** muestra la misma información que ha escrito, pero se ha convertido de texto a un valor y se le ha aplicado un formato distinto. Por ejemplo, el año aparece como cuatro dígitos en lugar de simplemente dos.
3. Cambie la propiedad **[Text](controls/properties-core.md)** de **ShowDate** a esta fórmula:
   <br>**DateTimeValue(ArrivalDateTime.Text; "fr")**
   
    ![Mostrar un valor de fecha y hora en formato francés](./media/show-text-dates-times/date-value-fr.png)
   
    **ShowDate** muestra el día antes del mes, tal y como esperaría un usuario francés.
   
   > [!TIP]
   > Para mostrar una lista de otras configuraciones regionales en Intellisense, quite las comillas de cierre y **fr** de la fórmula, pero conserve las comillas de apertura:
   > 
   > ![Mostrar una lista de configuraciones regionales](./media/show-text-dates-times/locale-list.png)
   > 
   > 
4. Para utilizar uno de los varios formatos integrados, cambie la propiedad **[Text](controls/properties-core.md)** de **ShowDate** a esta fórmula:
   <br>**Text(DateTimeValue(ArrivalDateTime.Text); DateTimeFormat.LongDateTime)**
   
    ![Mostrar un valor de fecha y hora en formato francés](./media/show-text-dates-times/long-date-time.png)
   
    **ShowDate** muestra el día de la semana, la fecha y la hora.
   
   > [!TIP]
   > El parámetro **DateTimeFormat** admite otros formatos integrados. Para mostrar esa lista, quite **LongDateTime** de la fórmula.
   > 
   > 
5. Para usar un formato personalizado, cambie la propiedad **[Text](controls/properties-core.md)** de **ShowDate** a esta fórmula:
   <br>**Text(DateTimeValue(ArrivalDateTime.Text); "mm/dd/yyyy hh:mm:ss.fff AM/PM")**
   
    ![Mostrar un valor de fecha y hora en formato francés](./media/show-text-dates-times/format-milliseconds.png)
   
    **ShowDate** muestra el valor de fecha y hora en el formato que ha especificado, incluidos los milisegundos.
   
   > [!TIP]
   > Para redondear la hora a la décima o centésima de segundo más cercana, especifique **hh:mm:ss.f** o **hh:mm:ss.ff** en la fórmula.
   > 
   > 

## <a name="format-a-date-by-using-datevalue"></a>Aplicar formato a una fecha mediante DateValue

1. Agregue un control **[Text input](controls/control-text-input.md)** denominado **ArrivalDate** y, luego, escriba una fecha en él (por ejemplo, **5/10/85**).

2. Agregue un control **[Etiqueta](controls/control-text-box.md)** denominado **FormatDate** y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:
   <br>**DateValue(ArrivalDate.Text)**
   
    **FormatDate** muestra la fecha que ha escrito, pero el año aparece con cuatro dígitos.
3. Establezca la propiedad **[Text](controls/properties-core.md)** de **FormatDate** en esta fórmula:
   <br>**DateValue(ArrivalDate.Text; "fr")**
   
    **FormatDate** muestra el día antes del mes, tal y como esperaría un usuario francés.
4. Para usar uno de los varios formatos integrados, establezca la propiedad **[Text](controls/properties-core.md)** de **FormatDate** en esta fórmula:
   <br>**Text(DateValue(ArrivalDate.Text); DateTimeFormat.LongDate)**
   
    **FormatDate** muestra el día de la semana, el mes, el día y el año.
5. Para usar un formato personalizado, establezca la propiedad **[Text](controls/properties-core.md)** de **FormatDate** en esta fórmula:
   <br>**Text(DateValue(ArrivalDate.Text); "yy/mm/dd")**
   
    **FormatDate** muestra la fecha en el formato especificado.

## <a name="format-a-time-using-datetimevalue"></a>Dar formato a una hora mediante DateTimeValue

1. Agregue un control **[Text input](controls/control-text-input.md)** denominado **ArrivalTime** y, luego, escriba **6:15 AM** en él.

2. Agregue un control **[Etiqueta](controls/control-text-box.md)** denominado **ShowTime**.

3. Para usar uno de los varios formatos integrados, establezca la propiedad **[Text](controls/properties-core.md)** de **ShowTime** en esta fórmula:
   <br>**Text(DateTimeValue(ArrivalTime.Text); DateTimeFormat.LongTime)**
   
    **ShowTime** muestra la hora que ha especificado, incluidos los segundos.
4. Para usar un formato personalizado, establezca la propiedad **[Text](controls/properties-core.md)** de **ShowTime** en esta fórmula:
   <br>**Text(DateTimeValue(ArrivalTime.Text); "hh:mm:ss.fff AM/PM")**
   
    **ShowTime** muestra la hora que ha especificado, incluidos los segundos y los milisegundos.
   
   > [!TIP]
   > Para redondear la hora a la décima o centésima de segundo más cercana, escriba **hh:mm:ss.f** o **hh:mm:ss.ff** en la fórmula.
   > 
   > 

## <a name="show-the-time-between-dates"></a>Mostrar el tiempo entre fechas

1. Agregue dos controles **[Text input](controls/control-text-input.md)** denominados **Start** y **End**.

2. Escriba **4/1/2015** en **Start** y **1/1/2016** en **End**.

3. Agregue un control **[Cuadro de texto](controls/control-text-box.md)** denominado **DateDiff** y establezca su propiedad **[Text](controls/properties-core.md)** en esta fórmula:
   <br>**DateDiff(DateValue(Start.Text); DateValue(End.Text))**
   
    ![Comparar dos fechas](./media/show-text-dates-times/date-diff.png)
   
    **DateDiff** muestra **275**, que es el número de días entre el 1 de abril de 2015 y el 1 de enero de 2016.
4. Establezca la propiedad **[Text](controls/properties-core.md)** de **DateDiff** en esta fórmula:  <br>**DateDiff(DateValue(Start.Text); DateValue(End.Text); Months)**
   
    **DateDiff** muestra **9**, que es el número de meses entre el 1 de abril de 2015 y el 1 de enero de 2016. Reemplace **Months** con **Quarters** o **Years** para mostrar el tiempo en trimestres o años.

## <a name="identify-a-date-before-or-after-another-date"></a>Identificar una fecha antes o después de otra fecha

1. Agregue un control **[Text input](controls/control-text-input.md)** denominado **Start** y escriba **5/10/1985** en él.

2. Agregue un control **[Etiqueta](controls/control-text-box.md)** denominado **DateAdd** y establezca su propiedad **[Texto](controls/properties-core.md)** en esta fórmula:
   <br>**DateAdd(DateValue(Start.Text); 3)**
   
    ![Agregar tres días](./media/show-text-dates-times/date-add.png)
   
    **DateAdd** muestra **5/13/1985**, que es tres días después de la fecha establecida en **Start**.
3. Establezca la propiedad **[Text](controls/properties-core.md)** de **DateAdd** en esta fórmula:
   <br>**DateAdd(DateValue(Start.Text); -3)**
   
    ![Restar tres días](./media/show-text-dates-times/date-subtract.png)
   
    **DateAdd** muestra **5/7/1985**, que es tres días antes de la fecha establecida en **Start**.
4. Cambie la propiedad **[Text](controls/properties-core.md)** de **DateAdd** a esta fórmula:
   <br>**DateAdd(DateValue(Start.Text); 3; Months)**
   
    ![Agregar tres meses](./media/show-text-dates-times/date-add-months.png)
   
    La etiqueta muestra **8/10/1985**, que es tres meses después de la fecha establecida en **Start**. Reemplace **Months** con **Quarters** o **Years** para identificar una fecha que tenga lugar el número especificado de trimestres o años antes o después de la fecha establecida en **Start**.

## <a name="calculate-dates-based-on-years-months-and-days"></a>Calcular fechas basándose en años, meses y días

1. Agregue tres controles **[Drop down](controls/control-drop-down.md)** denominados **Year**, **Month** y **Day**.

2. Establezca la propiedad **[Items](controls/properties-core.md)** de **Year** en esta fórmula:
   <br>**Table({Year:"2014"}; {Year:"2015"}; {Year:"2016"})**

3. Establezca la propiedad **[Items](controls/properties-core.md)** de **Month** en esta fórmula:
   <br>**Table({Month:"1"}; {Month:"2"}; {Month:"3"}; {Month:"4"}; {Month:"5"}; {Month:"6"}; {Month:"7"}; {Month:"8"}; {Month:"9"}; {Month:"10"}; {Month:"11"}; {Month:"12"})**

4. Establezca la propiedad **[Items](controls/properties-core.md)** de **Day** en esta fórmula:
   <br>**Table({Day:"1"}; {Day:"2"}; {Day:"3"}; {Day:"4"}; {Day:"5"}; {Day:"6"}; {Day:"7"}; {Day:"8"}; {Day:"9"}; {Day:"10"}; {Day:"11"}; {Day:"12"}; {Day:"13"}; {Day:"14"}; {Day:"15"}; {Day:"16"}; {Day:"17"}; {Day:"18"}; {Day:"19"}; {Day:"20"}; {Day:"21"}; {Day:"22"}; {Day:"23"}; {Day:"24"}; {Day:"25"}; {Day:"26"}; {Day:"27"}; {Day:"28"}; {Day:"29"}; {Day:"30"}; {Day:"31"})**

5. Agregue un control **[Label](controls/control-text-box.md)** y establezca su propiedad **[Text](controls/properties-core.md)** en esta fórmula:
   <br>**Text(Date(Value(Year.Selected.Value); Value(Month.Selected.Value); Value(Day.Selected.Value)); DateTimeFormat.LongDate)**
   
    La fecha **miércoles, 1 de enero de 2014** aparece de forma predeterminada. Seleccione valores diferentes en los controles **[Lista desplegable](controls/control-drop-down.md)** para cambiar la fecha en el control **[Etiqueta](controls/control-text-box.md)** .

Es posible que deba convertir datos que no esperaba. Si agrega controles **[Text input](controls/control-text-input.md)** en lugar de controles **[Drop down](controls/control-drop-down.md)** , puede que un usuario escriba una fecha incorrecta, como 45 de mayo. La función **[Date](functions/function-date-time.md)** se encarga de los datos inusuales de las siguientes formas:

* Si un valor de año está comprendido entre 0 y 1899 (ambos incluidos), la función agrega ese valor a 1900 para calcular el año.
* Si un valor de año está comprendido entre 1900 y 9999 (ambos incluidos), la función usa ese valor como el año.
* Si un valor de año es menor que 0, o mayor o igual que 10000, la función devuelve un valor de error.
* Si un valor de mes es mayor que 12, la función suma ese número de meses al primer mes del año especificado.
* Si un valor de mes es menor que 1, la función resta ese número de meses, más 1, del primer mes del año especificado.
* Si un valor de día es mayor que el número de días del mes especificado, la función sumará esos días al primer día del mes y devolverá la fecha correspondiente de un mes posterior.
* Si un valor de día es menor que 1, la función resta esa cantidad de días, más 1, del primer día del mes especificado.

## <a name="calculate-times-based-on-hours-minutes-and-seconds"></a>Calcular tiempos basándose en horas, minutos y segundos

1. Agregue dos listas **Drop-down** denominadas **Hour** y **Minute**.

2. Establezca la propiedad **[Items](controls/properties-core.md)** de **Hour** en esta fórmula:
   <br>**Table({Hour:"9"}; {Hour:"10"}; {Hour:"11"}; {Hour:"12"}; {Hour:"13"}; {Hour:"14"}; {Hour:"15"}; {Hour:"16"}; {Hour:"17"})**

3. Establezca la propiedad **[Items](controls/properties-core.md)** de **Minute** en esta fórmula:
   <br>**Table({Minute:"0"}; {Minute:"15"}; {Minute:"30"}; {Minute:"45"})**

4. Agregue un control **[Label](controls/control-text-box.md)** y establezca su propiedad **[Text](controls/properties-core.md)** en esta fórmula:  
   <br>**Text(Time(Value(Hour.Selected.Value); Value(Minute.Selected.Value); 0); DateTimeFormat.ShortTime)**

5. Seleccione **15** en **Hour** y **45** en **Minute**.
   
    El control **[Etiqueta](controls/control-text-box.md)** muestra **3:45 PM**.
   
    Puede agregar entradas a **Hour** y **Minute** para que los usuarios puedan seleccionar entre un intervalo más amplio de horas y un número más preciso de minutos. También puede agregar un tercer control **[Drop down](controls/control-drop-down.md)** para que los usuarios puedan especificar segundos. Si agrega una tercera lista, establezca la propiedad **[Texto](controls/properties-core.md)** del control **[Etiqueta](controls/control-text-box.md)** en la siguiente expresión:<br>**Text(Time(Value(Hour.Selected.Value); Value(Minute.Selected.Value); Value(Second.Selected.Value)); DateTimeFormat.LongTime)**

