---
title: Plantilla de pantalla calendario | Microsoft Docs
description: Descripción de cómo funciona la plantilla de pantalla calendario para las aplicaciones de Canvas, cómo modificar la pantalla y cómo ampliarla como parte de una aplicación
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4c466a2a090836ff880301f0960302413a3e25e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732632"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla calendario para aplicaciones de Canvas

En una aplicación de lienzo, agregue una pantalla de calendario que muestre los eventos próximos a los usuarios de sus cuentas de Office 365 Outlook. Los usuarios pueden seleccionar una fecha de un calendario y desplazarse por una lista de eventos de ese día. Puede cambiar los detalles que aparecen en la lista, agregar una segunda pantalla que muestre más detalles sobre cada evento, mostrar una lista de asistentes para cada evento y hacer otras personalizaciones.

También puede agregar otras pantallas basadas en plantillas que muestren datos diferentes de Office 365, como el [correo electrónico](email-screen-overview.md), las [personas](people-screen-overview.md) de una organización y la [disponibilidad](meeting-screen-overview.md) de personas que los usuarios quieran invitar a una reunión.

Esta información general le enseña:
> [!div class="checklist"]
> * Cómo usar la pantalla calendario predeterminada.
> * Cómo modificarlo.
> * Cómo integrarlo en una aplicación.

Para profundizar más en la funcionalidad predeterminada de esta pantalla, consulte la [referencia de la pantalla calendario](calendar-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Está familiarizado con cómo agregar y configurar pantallas y otros controles a medida que [crea una aplicación en Power apps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de calendario desde la plantilla:

1. [Inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) en Power apps y, después, cree una aplicación o abra una aplicación existente en Power apps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de Tablet PC.

1. En la pestaña **Inicio** de la cinta de opciones, seleccione **nueva pantalla** > **calendario**.

    De forma predeterminada, la pantalla tiene un aspecto similar al siguiente:

    ![Pantalla calendario](media/calendar-screen/calendar-initial.png)

1. Para Mostrar datos, seleccione una opción en la lista desplegable situada cerca de la parte superior de la pantalla.

    ![Pantalla del calendario una vez completada la carga](./media/calendar-screen/calendar-screen.png)

Algunas notas útiles:

* La fecha de hoy está seleccionada de forma predeterminada y puede volver a ella fácilmente seleccionando el icono de calendario en la esquina superior derecha.
* Si selecciona una fecha diferente, un círculo lo rodea y un rectángulo de color claro (azul si se aplica el tema predeterminado) rodea a la fecha de hoy.
* Si se programa al menos un evento para una fecha determinada, aparecerá un pequeño círculo coloreado debajo de esa fecha en el calendario.
* Si selecciona una fecha para la que se programan uno o más eventos, los eventos aparecen en una lista bajo el calendario.

## <a name="modify-the-screen"></a>Modificar la pantalla

Puede modificar la funcionalidad predeterminada de esta pantalla de varias maneras comunes:

* [Especifique el calendario](calendar-screen-overview.md#specify-the-calendar).
* [Mostrar detalles diferentes sobre un evento](calendar-screen-overview.md#show-different-details-about-an-event).
* [Ocultar eventos](calendar-screen-overview.md#hide-nonblocking-events)de no bloqueo.

Si desea modificar la pantalla con más detalle, use la [referencia de la pantalla calendario](./calendar-screen-reference.md) como guía.

### <a name="specify-the-calendar"></a>Especificar el calendario

Si ya sabe qué calendario deben ver los usuarios, puede simplificar la pantalla especificando ese calendario antes de publicar la aplicación. Este cambio elimina la necesidad de la lista desplegable de calendarios, por lo que puede quitarlo.

1. Establezca la propiedad **[OnStart](../controls/control-screen.md)** de la pantalla predeterminada de la aplicación en esta fórmula:

    ```powerapps-dot
    Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -( Weekday( _firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    Set( _calendarVisible, false );
    Set( _myCalendar, 
        LookUp( Office365.CalendarGetTables().value, DisplayName = "{YourCalendarNameHere}" )
    );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days ),
            40, 
            Days 
        )
    );
    ClearCollect( MyCalendarEvents, 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC ) 
        ).value
    );
    Set( _calendarVisible, true )
    ```

    > [!NOTE]
    > Esta fórmula se edita ligeramente desde el valor predeterminado de la propiedad **alseleccionar** de la lista desplegable para seleccionar un calendario. Para obtener más información sobre ese control, vea su sección en la referencia de la [pantalla calendario](./calendar-screen-reference.md#calendar-drop-down).

1. Reemplace `{YourCalendarNameHere}`, incluidas las llaves, por el nombre del calendario que desea mostrar (por ejemplo, **calendario**).

    > [!IMPORTANT]
    > En los pasos siguientes se supone que ha agregado solo una pantalla de calendario a la aplicación. Si ha agregado más de uno, los nombres de control (por ejemplo, **iconCalendar1**) terminarán con un número diferente y tendrá que ajustar las fórmulas según corresponda.

1. Establezca la propiedad **Y** del control **iconCalendar1** en esta expresión:

    `RectQuickActionBar1.Height + 20`

1. Establezca la propiedad **Y** del control **LblMonthSelected1** en esta expresión:

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. Establezca la propiedad **Text** del control **LblNoEvents1** en este valor:

    `"No events scheduled"`

1. Establezca la propiedad **visible** de **LblNoEvents1** en esta fórmula:

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. Elimine estos controles:

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. Si la pantalla de calendario no es la predeterminada, agregue un botón que navegue desde la pantalla predeterminada hasta la pantalla de calendario para que pueda probar la aplicación.

    Por ejemplo, agregue un botón en **Screen1** que navegue a **Screen2** si agregó una pantalla de calendario a una aplicación que creó desde cero.

1. Guarde la aplicación y, a continuación, probarla en un explorador o en un dispositivo móvil.

### <a name="show-different-details-about-an-event"></a>Mostrar detalles diferentes sobre un evento

De forma predeterminada, la galería de en el calendario, denominada **CalendarEventsGallery**, muestra la hora de inicio, la duración, el asunto y la ubicación de cada evento. Puede configurar la galería para mostrar cualquier campo (como el organizador) que admita el [conector de Office 365](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) .

1. En **CalendarEventsGallery**, establezca la propiedad **texto** de una etiqueta nueva o existente en `ThisItem` seguido de un punto.

    IntelliSense muestra los campos que puede seleccionar.

1. Seleccione el campo que desee.

    La etiqueta muestra el tipo de información que ha especificado.

### <a name="hide-nonblocking-events"></a>Ocultar eventos de no bloqueo

En muchas oficinas, los miembros del equipo envían convocatorias de reunión para que se notifiquen entre sí cuando se encuentren fuera de la oficina. Para evitar el bloqueo de las programaciones de todo el mundo, la persona que envía la solicitud establece su disponibilidad en **gratis**. Puede ocultar estos eventos desde el calendario y la Galería actualizando un par de propiedades.

1. Establezca la propiedad **Items** de **CalendarEventsGallery** en esta fórmula:

    ```powerapps-dot
    SortByColumns(
        Filter(
            MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = 
                Text( _dateSelected, DateTimeFormat.ShortDate ),
            ShowAs <> "Free"
        ),
        "Start"
    )
    ```

    En esta fórmula, la función **Filter** oculta no solo los eventos que están programados para una fecha distinta de la seleccionada, sino también los eventos para los que la disponibilidad está establecida en **Free**.

1. En el calendario, establezca la propiedad **visible** del control de **círculo** en esta fórmula:

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    Esta fórmula contiene los mismos filtros que la fórmula anterior. Por lo tanto, el círculo del indicador de eventos aparece en una fecha solo si tiene uno o varios eventos que se encuentran en la fecha seleccionada y cuya disponibilidad no está establecida en **libre**.

## <a name="integrate-the-screen-into-an-app"></a>Integración de la pantalla en una aplicación

La pantalla calendario es un conjunto eficaz de controles que se encuentran en su propio derecho, pero normalmente se comporta mejor como parte de una aplicación más grande y versátil. Puede integrar esta pantalla en una aplicación más grande de varias maneras, como agregar estas opciones:

* [Vea los detalles del evento](calendar-screen-overview.md#view-event-details).
* [Mostrar asistentes de eventos](calendar-screen-overview.md#show-event-attendees).

### <a name="view-event-details"></a>Ver detalles del evento

Si los usuarios seleccionan un evento en **CalendarEventsGallery**, puede abrir otra pantalla que muestra más información sobre ese evento.

> [!NOTE]
> En este procedimiento se muestran los detalles de los eventos en una galería con contenido dinámico, pero puede obtener resultados similares si toma otros enfoques. Por ejemplo, puede obtener más control de diseño mediante una serie de etiquetas en su lugar.

1. Agregue una pantalla en blanco, denominada **EventDetailsScreen**, que contenga una galería de alto flexible en blanco y un botón que vuelva a la pantalla de calendario.

1. En la galería de alto flexible, agregue un control **etiqueta** y un control **texto html** y establezca la propiedad **autoheight** de ambos en **true**.

    > [!NOTE]
    > Power apps recupera el cuerpo del mensaje de cada evento como texto HTML, por lo que debe mostrar el contenido en un control de **texto HTML** .

1. Establezca la propiedad **Y** del control de **texto html** en esta expresión:

    `Label1.Y + Label1.Height + 20`

1. Ajuste las propiedades adicionales según sea necesario para ajustarse a sus necesidades de estilo.

    Por ejemplo, puede que desee agregar una línea de separación debajo del control de **texto HTML** .

1. Establezca la propiedad **Items** de la galería de alto flexible en esta fórmula:

    ```powerapps-dot
    Table(
        { Title: "Subject", Value: _selectedCalendarEvent.Subject },
        { 
            Title: "Time", 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        },
        { Title: "Body", Value: _selectedCalendarEvent.Body }
    )
    ```

    Esta fórmula crea una galería de datos dinámicos que se establece en los valores de campo de **_selectedCalendarEvent**, que se establece cada vez que el usuario selecciona un evento en el control **CalendarEventsGallery** . Puede extender esta galería para incluir más campos agregando más etiquetas, pero este conjunto proporciona un buen punto de partida.

1. Con los elementos de la galería en su lugar, establezca la propiedad **texto** del control **etiqueta** en `ThisItem.Title`y la propiedad **HtmlText** del control de **texto HTML** en `ThisItem.Value`.

1. En **CalendarEventsGallery**, establezca la propiedad **alseleccionar** del control **título** en esta fórmula:

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > En lugar de usar la variable **_selectedCalendarEvent** , podría usar **CalendarEventsGallery**. Seleccionadas.

### <a name="show-event-attendees"></a>Mostrar asistentes para eventos

La operación `Office365.GetEventsCalendarViewV2` recupera una variedad de campos para cada evento, incluido un conjunto de asistentes necesarios y opcionales, separados por punto y coma. En este procedimiento, analizará cada conjunto de asistentes, determinará qué asistentes se encuentran en su organización y recuperará los perfiles de Office 365 de cualquier usuario que sea.

1. Si la aplicación no contiene el conector de usuarios de Office 365, [agréguelo](../add-data-connection.md).

1. Para recuperar los perfiles de Office 365 de los asistentes de reunión, establezca la propiedad **alseleccionar** del control de **título** en **CalendarEventsGallery** en esta fórmula:

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ),
            !IsBlank( Result )
        )
    );
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len( Result ) - Find( "@", Result ) ) )
        )
    );
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, If( InOrg, Office365Users.UserProfile( Result ) ) ) 
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { DisplayName: Result, Id: "", JobTitle: "", UserPrincipalName: Result }
            )
        )
    )
    ```

En esta lista se describe lo que hace cada operación de **ClearCollect** :

- ClearCollect (AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    Esta fórmula concatena los asistentes necesarios y opcionales en una sola cadena y, a continuación, divide esa cadena en direcciones individuales en cada punto y coma. A continuación, la fórmula filtra los valores en blanco de ese conjunto y agrega los demás valores en una colección denominada **AttendeeEmailsTemp**.

- ClearCollect (AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    Esta fórmula determina aproximadamente si un asistente está en su organización. La definición de **_userDomain** es simplemente la dirección URL de dominio en la dirección de correo electrónico de la persona que ejecuta la aplicación. Esta línea crea una columna true/false adicional, denominada **InOrg**, en la colección **AttendeeEmailsTemp** . Esta columna contiene **true** si **userDomain** es equivalente a la dirección URL de dominio de la dirección de correo electrónico en esa fila concreta de **AttendeeEmailsTemp**.

    Este enfoque no siempre es preciso, pero se cierra bastante. Por ejemplo, algunos asistentes de la organización pueden tener una dirección de correo electrónico como Jane@OnContoso.com, mientras que **_userDomain** es contoso.com. El usuario de la aplicación y Julia podrían trabajar en la misma empresa, pero tienen ligeras variaciones en sus direcciones de correo electrónico. En casos como estos, puede que desee usar esta fórmula:

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    Sin embargo, esta fórmula coincide con las direcciones de correo electrónico como Jane@NotTheContosoCompany.com con un **_userDomain** como contoso.com y esas personas no trabajan en la misma compañía.

- ClearCollect (mis personas)

    ```powerapps-dot
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, 
            If( InOrg, 
                Office365Users.UserProfile( Result )
            )
        )
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result
                }
            )
        )
    );
    ```
    Para recuperar los perfiles de Office 365, debe usar la operación [Office365Users. userprofile](https://docs.microsoft.com/connectors/office365users/#userprofile) o [Office365Users. UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) . Estas operaciones primero reúnen todos los perfiles de Office 365 para los asistentes que se encuentran en la organización del usuario. A continuación, las operaciones agregan algunos campos a los asistentes desde fuera de la organización. Estos dos elementos se separan en operaciones distintas porque el bucle **forall** no garantiza el orden. Por lo tanto, **forall** podría recopilar primero un asistente de fuera de la organización. En este caso, el esquema de mis **personas** solo contiene **displayName**, **ID**, **JobTitle**y **UserPrincipalName**. Sin embargo, las operaciones de UserProfile recuperan datos mucho más completos que. Por lo tanto, se obliga a la colección **People** a agregar perfiles de Office 365 antes que a los demás perfiles.

    > [!NOTE]
    > Puede lograr el mismo resultado con una sola función **ClearCollect** :

    ```powerapps-dot
    ClearCollect( MyPeople, 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, 
                        ";"
                    ), 
                    !IsBlank( Result )
                ), 
                "InOrg", _userDomain = Right( Result, Len( Result ) - Find( "@", Result ) )
            ), 
            If( InOrg, 
                Office365Users.UserProfile( Result ), 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result, 
                    Department: "", 
                    OfficeLocation: "", 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

Para finalizar este ejercicio:

1. Agregue una pantalla que contenga una galería para la que la propiedad **Items** esté establecida en **People**.

1. En la propiedad **alseleccionar** del control **title** en **CalendarEventsGallery**, agregue una función **Navigate** a la pantalla que creó en el paso anterior.

## <a name="next-steps"></a>Pasos siguientes

* [Vea la documentación de referencia de esta pantalla](calendar-screen-reference.md).
* [Obtenga más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Obtenga más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
