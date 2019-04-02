---
title: Referencia para la plantilla de pantalla de calendario para las aplicaciones de lienzo | Microsoft Docs
description: Comprender los detalles del funcionamiento de la plantilla de pantalla de calendario para las aplicaciones de lienzo en PowerApps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e3d5f40a604d2cbfa074ed5973d599c40a6c5c05
ms.sourcegitcommit: 647e183c070c2159b790c7813a7be1d60b2551bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58765592"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>Información de referencia acerca de la plantilla de pantalla de calendario para las aplicaciones de lienzo

Para las aplicaciones de lienzo en PowerApps, comprender cómo contribuye cada control significativo en la plantilla de pantalla de calendario a la funcionalidad de la pantalla general predeterminada. Este análisis detallado de presentan las fórmulas de comportamiento y los valores de otras propiedades que determinan cómo responden los controles a la entrada del usuario. Para un análisis de alto nivel de funcionalidad de forma predeterminada de la pantalla, consulte el [información general de la pantalla de calendario](calendar-screen-overview.md).

En este tema se destacan algunos controles importantes y explica las expresiones o las fórmulas que varias propiedades (como **elementos** y **OnSelect**) de estos controles están establecidos:

- [Calendario desplegable (dropdownCalendarSelection)](#calendar-drop-down)
- [Icono del calendario (iconCalendar)](#calendar-icon)
- [Previous-month chevron (iconPrevMonth)](#previous-month-chevron)
- [Mes próximo contenido adicional (iconNextMonth)](#next-month-chevron)
- [Galería de calendario (MonthDayGallery) (+ controles secundarios)](#calendar-gallery)
- [Galería de eventos (CalendarEventsGallery)](#events-gallery)

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="calendar-drop-down"></a>Calendario desplegable

![control dropdownCalendarSelection](media/calendar-screen/calendar-dropdown.png)

- Propiedad: **elementos**<br>
    Valor: `Office365.CalendarGetTables().value`

    Este valor es una operación de conector que recupera calendarios de Outlook del usuario de la aplicación. Puede ver [el valor](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table]) que esta operación recupera.

- Propiedad: **OnChange**<br>Valor: `Select(dropdownCalendarSelection)`

    Cuando el usuario selecciona una opción en la lista, la función en el control **OnSelect** ejecuciones de la propiedad.

- Propiedad: **OnSelect**<br>
    Valor: Un **si** función, que aparece en el siguiente bloque de código y varias funciones adicionales que aparecen en el bloque de código después de eso.

   Esta parte de la se ejecuta la fórmula solo la primera vez que el usuario selecciona una opción en la lista desplegable después de abrir la aplicación:

    ```powerapps-dot
    If( IsBlank( _userDomain ),
        UpdateContext( {_showLoading: true} );
        Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
        Set( _dateSelected, Today() );
        Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );  
        Set( _firstDayInView, DateAdd( _firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 1), Days ) );
        Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )  
    );
    ```

    El código anterior define las siguientes variables:
    
  - **\_userDomain**: Dominio de empresa del usuario de la aplicación, tal como se refleja en la dirección de correo electrónico del usuario.
  - **\_dateSelected**: Fecha de hoy en día (de forma predeterminada). La Galería de calendario destaca esta fecha y la Galería de eventos muestra los eventos que están programados para esa fecha.
  - **\_firstDayOfMonth**: El primer día del mes actual. Dado que `(Today + (1 - Today)) = Today - Today + 1 = 1`, este **DateAdd** función siempre devuelve el primer día del mes.
  - **\_firstDayInView**: El primer día que se puede mostrar la Galería de calendario. Este valor no es igual que el primer día del mes, a menos que el mes comienza en domingo. Para impedir que se muestre toda una semana del mes anterior, el valor de  **\_firstDayInView** es `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`.
  - **\_lastDayOfMonth**: El último día del mes actual, que es el mismo que el primer día del mes siguiente, menos un día.

   Las funciones después de la **si** función ejecutar cada vez que el usuario selecciona una opción en la lista desplegable de calendario (no solo la primera vez que el usuario abre la aplicación):

    ```powerapps-dot
    Set( _calendarVisible, false );
    UpdateContext( {_showLoading: true} );
    Set( _myCalendar, dropdownCalendarSelection2.Selected );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set(_maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ), 
            40, 
            Days
        )
    );
    ClearCollect( MyCalendarEvents, 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC )
        ).value
    );
    UpdateContext( {_showLoading: false} );
    Set( _calendarVisible, true )
    ```

    El código anterior define estas variables y una colección:

    - **\_calendarVisible**: Establecido en **false** para que el calendario no aparece mientras se carga la nueva selección.
    - **\_showLoading**: Establecido en **true** para que se muestran los indicadores de carga mientras se carga la nueva selección.
    - **\_myCalendar**: Establezca el valor actual de la **calendario desplegable** controlar de manera que se recuperan los eventos del calendario correcto.
    - **\_minDate**: Establecer en el mismo valor que  **\_firstDayInView**. Esta variable determina qué eventos ya se han recuperado desde Outlook y almacenar en caché en la aplicación.
    - **\_maxDate**: Se establece en el último día pueden ver en el calendario. La fórmula es `_firstDayInView + 40`. El calendario muestra un máximo de 41 días, por lo que la  **\_maxDate** variable siempre refleja el último día visible y determina qué eventos ya se han recuperado desde Outlook y almacenar en caché en la aplicación.
    - **MyCalendarEvents**: Establecer en una colección de eventos del usuario en el calendario seleccionado, que abarcan desde  **\_minDate** a  **\_maxDate**.
    - **\_showLoading**: Establecido en **false**;  **\_calendarVisible** está establecido en **true** después de todo lo demás se ha cargado.

## <a name="calendar-icon"></a>Icono del calendario

![control iconCalendar](media/calendar-screen/calendar-today-icon.png)

- Propiedad: **OnSelect**<br>
    Valor: Cuatro **establecer** funciones que restablece la Galería de calendario en la fecha de hoy:

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    El código anterior restablece todas las variables de fecha que son necesarias para mostrar la vista de calendario adecuada:

    - **\_dateSelected** se restablece a hoy.
    - **\_firstDayOfMonth** se restablece en el primer día del mes de hoy.
    - **\_firstDayInView** se restablece en el primer día visible cuando se selecciona el mes de hoy.
    - **\_lastDayOfMonth** se restablece en el último día del mes de hoy.

    El [ **calendario desplegable** ](#calendar-drop-down) sección de este tema explican estas variables con más detalle.

## <a name="previous-month-chevron"></a>Contenido adicional del mes anterior

![control iconPrevMonth](media/calendar-screen/calendar-back.png)

- Propiedad: **OnSelect**<br>Valor: Cuatro **establecer** funciones y una **si** función que se muestra el mes anterior en la Galería de calendario:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, -1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set( _lastDayOfMonth, DateAdd(DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _minDate > _firstDayOfMonth,
        Collect( MyCalendarEvents,
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name,
                Text( _firstDayInView, UTC ), 
                Text( DateAdd( _minDate, -1, Days ), UTC )
            ).value
        );
        Set( _minDate, _firstDayInView )
    )
    ```

    > [!NOTE]
    > Las definiciones para  **\_firstDayOfMonth**,  **\_firstDayInView**, y  **\_lastDayOfMonth** son casi idénticas a las en el [calendario desplegable](#calendar-drop-down) sección de este tema.

    Las tres primeras líneas del código anterior se ejecutan cada vez que el usuario selecciona el botón de contenido adicional de mes anterior. El código establece las variables que son necesarias para mostrar la vista de calendario adecuado. El código restante se ejecuta sólo si el usuario no ha seleccionado anteriormente este mes para el calendario seleccionado.

    Si es así,  **\_minDate** es el primer día que aparece cuando se muestra el mes anterior. Antes de que el usuario selecciona el icono,  **\_minDate** tiene un valor mínimo posible de las 23 del mes actual. (Cuando es un sábado, 1 de marzo  **\_firstDayInView** para marzo es 23 de febrero.) Esto significa que si un usuario no ha seleccionado todavía, este mes  **\_minDate** es mayor que el nuevo  **\_firstDayOfMonth**y el **si** función devuelve **true**. El código se ejecuta y una colección y una variable se actualizan:

    - **MyCalendarEvents** recupera eventos del calendario seleccionado con el [Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) operación. Es el intervalo de fechas entre el  **\_firstDayInView** fecha y  **\_minDate** - 1. Dado que **MyCalendarEvents** ya contiene los eventos en el  **\_minDate** fecha, se resta 1 de esa fecha para el valor máximo de este nuevo intervalo de fechas.

    - **\_minDate** está establecida en actual  **\_firstDayInView** porque se trata de la primera fecha que se han recuperado los eventos. Si un usuario vuelva a esta fecha seleccionando el botón de contenido adicional de mes anterior, el **si** función devuelve **false**; no se ejecuta el código porque ya se almacenan en caché los eventos para esta vista en  **MyCalendarEvents**.

## <a name="next-month-chevron"></a>Contenido adicional del siguiente mes

![control iconNextMonth](media/calendar-screen/calendar-forward.png)

- Propiedad: **OnSelect**<br>
    Valor: Cuatro **establecer** funciones y una **si** función que se muestra el mes siguiente en la Galería de calendario:

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, 1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ) );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _maxDate < _lastDayOfMonth,
        Collect( MyCalendarEvents, 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
                Text( DateAdd( _maxDate, 1, Days ), UTC ), 
                DateAdd( _firstDayInView, 40, Days )
            ).value
        );
        Set( _maxDate, DateAdd( _firstDayInView, 40, Days) )    
    )
    ```

    > [!NOTE]
    > Las definiciones para  **\_firstDayOfMonth**,  **\_firstDayInView**, y  **\_lastDayOfMonth** son casi idénticas a las en el [calendario desplegable](#calendar-drop-down) sección de este tema.

    Las tres primeras líneas del código anterior, que se ejecutan cuando el usuario selecciona el botón de contenido adicional de mes próximo, establecen las variables que son necesarias para mostrar la vista de calendario adecuado. El código restante se ejecuta sólo si el usuario no ha seleccionado anteriormente este mes para el calendario seleccionado.

    En ese caso,  **\_maxDate** es el último día que aparece cuando se muestra el mes anterior. Antes de que el usuario selecciona el botón de contenido adicional de mes próximo,  **\_maxDate** tiene un valor máximo posible de los 13 del próximo mes. (Cuando el 1 de febrero cae en un año que no es bisiesto el domingo,  **\_maxDate** es 13 de marzo, que es  **\_firstDayInView** + 40 días.) Esto significa que si un usuario no ha seleccionado todavía, este mes  **\_maxDate** es mayor que el nuevo  **\_lastDayOfMonth**y el **si** (función) Devuelve **true**. El código se ejecuta y una colección y una variable se actualizan:

    - **MyCalendarEvents** recupera eventos del calendario seleccionado con el [Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-) operación. Es el intervalo de fechas entre  **\_maxDate** + 1 día y  **\_firstDayInView** + 40 días. Dado que **MyCalendarEvents** ya contiene los eventos en el  **\_minDate** fecha, se agrega 1 a esa fecha para el valor mínimo de este nuevo intervalo de fechas. **\_firstDayInView** + 40 es la fórmula para  **\_maxDate**, por lo que la segunda fecha en el intervalo es simplemente el nuevo  **\_maxDate**.

    - **\_maxDate** está establecido en  **\_firstDayInView** + 40 días porque se trata del último día para los eventos que se han recuperado. Si un usuario vuelva a esta fecha seleccionando el botón de contenido adicional de mes próximo, el **si** función devuelve **false**; no se ejecuta el código porque ya se almacenan en caché los eventos para esta vista en  **MyCalendarEvents**.

## <a name="calendar-gallery"></a>Galería de calendario

![Control MonthDayGallery](media/calendar-screen/calendar-month-gall.png)

- Propiedad: **elementos**<br>
    Valor: `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  El conjunto de 0 a 41 se usa para los elementos de la Galería de calendario porque, en el peor de los casos, la vista de calendario deberá mostrar 42 días completos. Esto se produce cuando se produce el primer mes de un sábado y el último día del mes se produce en domingo. En este caso, el calendario muestra seis días del mes anterior en la fila que contiene el primero del mes y seis días del mes en la fila que contiene el último día del mes siguiente. Se trata de 42 valores únicos, de los cuales 30 son para el mes seleccionado.

- Propiedad: **WrapCount**<br>
    Valor: `7`

  Este valor refleja una semana de siete días.

### <a name="title-control-in-the-calendar-gallery"></a>Control de título de la Galería de calendario

![Control MonthDayGallery título](media/calendar-screen/calendar-month-text.png)

- Propiedad: **Texto**<br>
    Valor: `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    Recuerde que  **\_firstDayInView** se define como (**\_firstDayOfMonth** -su valor de día de la semana) + 1. Esto indica que  **\_firstDayInView** es siempre un domingo y  **\_firstDayOfMonth** siempre está en la primera fila de **MonthDayGallery**. Debido a estos dos factores,  **\_firstDayInView** siempre está en la primera celda de **MonthDayGallery**. **ThisItem.Value** es el número de esa celda en la **MonthDayGallery** propiedad item. Por lo tanto, teniendo  **\_firstDayInView** como punto de partida, cada celda muestra el incremento de  **\_firstDayInView** + su valor de la celda correspondiente.

- Propiedad: **Fill**<br>
    Valor: Una **si** función:

    ```powerapps-dot
    If( DateAdd( _firstDayInView, ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected, 
            RGBA( 0, 0, 0, 0 ),
        DateAdd( _firstDayInView, ThisItem.Value) = Today(), 
            ColorFade( Subcircle.Fill, 0.67 ),
        Abs( Title.Text - ThisItem.Value) > 10,
            RGBA( 200, 200, 200, 0.3 ),
        RGBA( 0, 0, 0, 0 )
    )
    ```

  Como se describe en la descripción de la **texto** propiedad `DateAdd(_firstDayInView, ThisItem.Value)` representa el día en la celda visible. Teniendo esto en cuenta, el código anterior realiza estas comparaciones:
  1. Si el valor de celda es la fecha de hoy y es equivalente a esta celda  **\_dateSelected**, no proporciona un valor de relleno.
  1. Si el valor de celda es la fecha de hoy, pero no es equivalente a  **\_dateSelected**, proporcione el **ColorFade** relleno.
  1. La última comparación no es lo más clara. Es una comparación entre el valor de texto real de la celda y el valor del elemento de celda (número en pantalla) y el número de elemento.<br>

      Para comprender esto mejor, considere la posibilidad de septiembre de 2018, un mes que se inicia un sábado y termina el domingo. En este caso, el calendario muestra el 26 31 de agosto y el 1 de septiembre en la primera fila, y `Abs(Title.Text - ThisItem.Value) = 26` hasta el 1 de septiembre. A continuación, `Abs(Title.Text - ThisItem.Value) = 5`. Permanecerá en 5 hasta que la última fila en el calendario, que muestra el 30 de septiembre y del 1 de octubre a través de 6. En el sentido `Abs(Title.Text - ThisItem.Value)` seguirá siendo 5 para el 30 de septiembre, pero será 35 para las fechas de octubre.<br>

      Este es el patrón: Para los días que se muestran en el mes anterior, `Abs(Title.Text - ThisItem.Value)` siempre será igual a la `Title.Text` valor del primer día en pantalla. Durante los días que se muestran en el próximo mes, `Abs(Title.Text - ThisItem.Value)` siempre será igual a la **MonthDayGallery** elemento el valor de la primera celda de ese mes (en este caso, 1 de octubre) menos 1. Y, lo más importante, para los días que se muestran en el mes seleccionado actualmente, `Abs(Title.Text - ThisItem.Value)` será también siempre igual que el valor del primer elemento de ese mes menos 1 y nunca será superior a 5, como se muestra en el ejemplo anterior. Por lo que es perfectamente válido para escribir la fórmula como `Abs(Title.Text - ThisItem.Value) > 5`.

      Esta instrucción comprueba si el valor de fecha está fuera del mes seleccionado actualmente. Si es así, **rellenar** es un gris parcialmente opaco.

    > [!NOTE]
    > Puede comprobar la validez de esta última comparación usted mismo mediante la inserción de un **etiqueta** control en la galería y la configuración de su **texto** este valor para propiedad:<br>`Abs(Title.Text - ThisItem.Value)`.

- Propiedad: **Visible**<br>
    Valor:

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    La instrucción anterior comprueba si la celda está en una fila que se producen sin días del mes seleccionado actualmente. Recuerde que si se resta el valor de día de la semana de un día desde su valor de fecha y agregando 1 siempre devuelve el primer elemento de la fila de ese día se encuentra en. Por lo que esta instrucción comprueba si el primer día de la fila está después del último día del mes visible. Si es así, no aparecerá porque toda la fila contiene los días del mes siguiente.

- Propiedad: **OnSelect**<br>
    Valor: Un **establecer** función que establece la  **\_dateSelected** variable a la fecha de la celda seleccionada:

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>Control de círculo en la Galería de calendario

![Control de círculo MonthDayGallery](media/calendar-screen/calendar-month-event.png)

- Propiedad: **Visible**<br>
    Valor: Una fórmula que determina si los eventos están programados para la fecha seleccionada y si la **Subcircle** y **título** controles están visibles:

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    El **círculo** control es visible si la **iniciar** campo para cualquier evento es equivalente a la fecha de la celda, si el **título** control está visible y si el  **Subcircle** control no está visible. En otras palabras, este control está visible cuando se produce al menos un evento en este día, y este día no está seleccionado. Si está seleccionada, los eventos de ese día se muestran en el **CalendarEventsGallery** control.

### <a name="subcircle-control-in-the-calendar-gallery"></a>Control subcircle en la Galería de calendario

![Control MonthDayGallery Subcircle](media/calendar-screen/calendar-month-selected.png)

- Propiedad: **Visible**<br>
    Valor:

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  El **Subcircle** control es visible cuando  **\_dateSelected** es equivalente a la fecha de la celda y el **título** control está visible. En otras palabras, este control aparece cuando la celda es la fecha seleccionada actualmente.

## <a name="events-gallery"></a>Galería de eventos

![Control CalendarEventsGallery](media/calendar-screen/calendar-events-gall.png)

- Propiedad: **elementos**<br>
    Valor: Una fórmula que se ordena y filtra la Galería de eventos:

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   El **MyCalendarEvents** colección contiene todos los eventos entre  **\_minDate** y  **\_maxDate**. Con el fin de mostrar los eventos para solo la fecha seleccionada, se aplica un filtro en **MyCalendarEvents** para mostrar los eventos que tienen una fecha de inicio equivalente a **\ _dateSelected**. Los elementos se ordenan por sus fechas de comienzo para ponerlos en orden secuencial.

## <a name="next-steps"></a>Pasos siguientes

- [Más información sobre esta pantalla](./calendar-screen-overview.md)
- [Más información sobre el conector de Office 365 Outlook en PowerApps](../connections/connection-office365-outlook.md)
- [Más información sobre el conector de usuarios de Office 365 en PowerApps](../connections/connection-office365-users.md)
