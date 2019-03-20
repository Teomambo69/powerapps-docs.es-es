---
title: Plantilla de pantalla de calendario | Microsoft Docs
description: Comprender el funcionamiento de la plantilla de pantalla de calendario para las aplicaciones de lienzo, modificar la pantalla y ampliarlo como parte de una aplicación
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 745b4232a43a06c46866e83ca2452f8a55afeddf
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459514"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>Información general de la plantilla de pantalla de calendario para las aplicaciones de lienzo

En una aplicación de lienzo, agregue una pantalla de calendario que se muestra a los usuarios en los próximos eventos de sus cuentas de Office 365 Outlook. Los usuarios pueden seleccionar una fecha en un calendario y desplazarse por una lista de eventos de ese día. Puede cambiar qué detalles aparecen en la lista, agregue una segunda pantalla que muestra más detalles sobre cada evento, mostrar una lista de los asistentes para cada evento y realizar otras personalizaciones.

También puede agregar otras pantallas basadas en plantillas que muestren diferentes datos de Office 365, como [correo electrónico](email-screen-overview.md), [personas](people-screen-overview.md) en una organización, y [disponibilidad](meeting-screen-overview.md) de usuarios de personas es posible que desee invitar a una reunión.

Esta información general aprenderá:
> [!div class="checklist"]
> * Cómo usar la pantalla predeterminada de calendario.
> * Cómo modificarlo.
> * Cómo se integran en una aplicación.

Para un análisis más profundo de la funcionalidad de la pantalla de forma predeterminada, consulte el [referencia de la pantalla de calendario](calendar-screen-reference.md).

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="default-functionality"></a>Funcionalidad predeterminada

Para agregar una pantalla de calendario de la plantilla:

1. [Inicie sesión en](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) a PowerApps y, a continuación, crear una aplicación o abrir una aplicación existente en PowerApps Studio.

    En este tema se muestra una aplicación de teléfono, pero los mismos conceptos se aplican a una aplicación de tableta.

1. En el **inicio** pestaña de la cinta de opciones, seleccione **nueva pantalla** > **calendario**.

    De forma predeterminada, la pantalla tiene un aspecto similar al siguiente:

    ![Pantalla de calendario](media/calendar-screen/calendar-initial.png)

1. Para mostrar los datos, seleccione una opción en la lista desplegable en la parte superior de la pantalla.

    ![Pantalla de calendario una vez completada la carga](./media/calendar-screen/calendar-screen.png)

Algunas notas útiles:

* Fecha de hoy en día está activada de forma predeterminada, y puede volver fácilmente a él seleccionando el icono de calendario en la esquina superior derecha.
* Si selecciona una fecha diferente, un círculo alrededor de él y un rectángulo de color claro (azul si se aplica el tema predeterminado) rodea la fecha de hoy.
* Si al menos un evento está programado para una fecha concreta, aparece un pequeño círculo coloreado en esa fecha en el calendario.
* Si selecciona una fecha para el que se programan uno o más eventos, los eventos aparecen en una lista en el calendario.

## <a name="modify-the-screen"></a>Modificar la pantalla

Puede modificar la funcionalidad predeterminada de esta pantalla de varias maneras comunes:

* [Especifique el calendario](calendar-screen-overview.md#specify-the-calendar).
* [Mostrar detalles diferentes acerca de un evento](calendar-screen-overview.md#show-different-details-about-an-event).
* [Ocultar eventos de no bloqueo](calendar-screen-overview.md#hide-nonblocking-events).

Si desea modificar la pantalla adicional, utilice el [referencia de la pantalla de calendario](./calendar-screen-reference.md) como guía.

### <a name="specify-the-calendar"></a>Especifique el calendario

Si ya sabe qué calendario deben ver los usuarios, puede simplificar la pantalla mediante la especificación de dicho calendario antes de publicar la aplicación. Este cambio elimina la necesidad de la lista desplegable de calendarios, para que pueda quitarla.

1. Establecer el **[OnStart](../controls/control-screen.md)** propiedad de la pantalla predeterminada en la aplicación en esta fórmula:

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
    > Esta fórmula se modifica ligeramente el valor predeterminado de la **OnSelect** propiedad de la lista desplegable para seleccionar un calendario. Para obtener más información acerca de ese control, vea la sección en la [referencia de la pantalla de calendario](./calendar-screen-reference.md#calendar-drop-down).

1. Reemplace `{YourCalendarNameHere}`, incluidas las llaves, con el nombre del calendario que desea mostrar (por ejemplo, **calendario**).

    > [!IMPORTANT]
    > Los pasos siguientes se supone que ha agregado a la aplicación solo hay una pantalla de calendario. Si ha agregado más de uno, los nombres de control (como **iconCalendar1**) finalizará con un número diferente y necesita ajustar las fórmulas según sea necesario.

1. Establecer el **Y** propiedad de la **iconCalendar1** control en esta expresión:

    `RectQuickActionBar1.Height + 20`

1. Establecer el **Y** propiedad de la **LblMonthSelected1** control en esta expresión:

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. Establecer el **texto** propiedad de la **LblNoEvents1** control a este valor:

    `"No events scheduled"`

1. Establecer el **Visible** propiedad de **LblNoEvents1** en esta fórmula:

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. Elimine estos controles:

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. Si la pantalla de calendario no es la pantalla predeterminada, agregue un botón que navega desde la pantalla predeterminada a la pantalla de calendario para que pueda probar la aplicación.

    Por ejemplo, agregar un botón en **Screen1** que navega a **Screen2** si agrega una pantalla de calendario a una aplicación que ha creado desde cero.

1. Guarde la aplicación y, después, probarla en un explorador o en un dispositivo móvil.

### <a name="show-different-details-about-an-event"></a>Mostrar detalles diferentes acerca de un evento

De forma predeterminada, la galería en el calendario, denominado **CalendarEventsGallery**, se muestra la hora de inicio, la duración, el asunto y la ubicación de cada evento. Puede configurar la Galería para mostrar cualquier campo (por ejemplo, el organizador) que el [conector de Office 365](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive) admite.

1. En **CalendarEventsGallery**, establezca el **texto** propiedad de una nueva o una etiqueta existente a `ThisItem` seguido por un punto.

    IntelliSense muestra los campos que se pueden seleccionar.

1. Seleccione el campo que desee.

    La etiqueta muestra el tipo de información que especificó.

### <a name="hide-nonblocking-events"></a>Ocultar eventos sin bloqueo

En muchas de las oficinas, los miembros del equipo envían convocatorias de reunión para notificarse entre sí cuando estén fuera de la oficina. Para evitar el bloqueo de las programaciones de todo el mundo, la persona que envía la solicitud establece su disponibilidad **gratis**. Puede ocultar estos eventos en el calendario y la galería mediante la actualización de un par de propiedades.

1. Establecer el **elementos** propiedad de **CalendarEventsGallery** en esta fórmula:

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

    En esta fórmula, el **filtro** oculta la función no solo esos eventos que están programados para una fecha que no sea el seleccionado, sino también los eventos para el que la disponibilidad se establece en **gratis**.

1. En el calendario, establezca el **Visible** propiedad de la **círculo** control en esta fórmula:

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    Esta fórmula contiene los mismos filtros como la fórmula anterior. Por lo tanto, el círculo de indicador de evento en una fecha solo aparece si tiene uno o más eventos que se encuentran en la fecha seleccionada y para que la disponibilidad no está establecen en **gratis**.

## <a name="integrate-the-screen-into-an-app"></a>Integrar la pantalla en una aplicación

La pantalla de calendario es un conjunto eficaz de controles por derecho propio, pero normalmente realiza mejor como parte de una aplicación más grande y más versátil. Puede integrar esta pantalla en una aplicación de mayor tamaño en varios aspectos, incluida la adición de estas opciones:

* [Ver detalles del evento](calendar-screen-overview.md#view-event-details).
* [Mostrar los asistentes del evento](calendar-screen-overview.md#show-event-attendees).

### <a name="view-event-details"></a>Ver detalles del evento

Si los usuarios seleccionar un evento en **CalendarEventsGallery**, puede abrir otra pantalla que muestra más información sobre ese evento.

> [!NOTE]
> Este procedimiento muestra detalles del evento en una galería con contenido dinámico, pero puede lograr resultados similares tomando otros enfoques. Por ejemplo, puede obtener más control de diseño con una serie de etiquetas en su lugar.

1. Agregar una pantalla en blanco, denominada **EventDetailsScreen**, que contiene una galería de altura flexible en blanco y un botón que vuelve a la pantalla del calendario.

1. En la Galería de altura flexible, agregue un **etiqueta** control y un **texto HTML** y establezca el **AutoHeight** propiedad de ambas a **true** .

    > [!NOTE]
    > PowerApps recupera el cuerpo del mensaje de cada evento como texto HTML, por lo que necesita mostrar ese contenido en un **texto HTML** control.

1. Establecer el **Y** propiedad de la **texto HTML** control en esta expresión:

    `Label1.Y + Label1.Height + 20`

1. Ajuste las propiedades adicionales según sea necesario para satisfacer sus necesidades de estilo.

    Por ejemplo, desea agregar una línea de separador inferior el **texto HTML** control.

1. Establecer el **elementos** propiedad de la Galería de altura flexible en esta fórmula:

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

    Esta fórmula crea una galería de datos dinámicos que se establecen en los valores de campo de **_selectedCalendarEvent**, que se establece cada vez que el usuario selecciona un evento en el **CalendarEventsGallery** control. Puede extender esta galería para incluir más campos agregando más etiquetas a él, pero este conjunto proporciona un buen punto de partida.

1. Con los elementos de la galería en su lugar, establezca el **texto** propiedad de la **etiqueta** el control a `ThisItem.Title`y el **HtmlText** propiedad de la **texto HTML**  control `ThisItem.Value`.

1. En **CalendarEventsGallery**, establezca el **Alseleccionar** propiedad de la **título** control en esta fórmula:

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > En lugar de usar el **_selectedCalendarEvent** variable, también puede usar **CalendarEventsGallery**. Seleccionado.

### <a name="show-event-attendees"></a>Mostrar a los asistentes del evento

El `Office365.GetEventsCalendarViewV2` operación recupera una serie de campos para cada evento, incluido un conjunto separados por punto y coma de los asistentes obligatorios y opcionales. En este procedimiento, analizar cada conjunto de asistentes, determinar qué asistentes se encuentran en su organización y recuperar de cualquier quiénes son los perfiles de Office 365.

1. Si la aplicación no contiene el conector de usuarios de Office 365, [agregarlo](../add-data-connection.md).

1. Para recuperar los perfiles de Office 365 de los asistentes, establezca el **OnSelect** propiedad de la **título** en controlar la **CalendarEventsGallery** en esta fórmula:

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

Esta lista describe lo que cada **ClearCollect** operación hace:

- ClearCollect(AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    Esta fórmula concatena a los asistentes obligatorios y opcionales en una sola cadena y, a continuación, divide esa cadena en direcciones individuales en cada punto y coma. La fórmula, a continuación, filtra los valores en blanco de dicho conjunto y agrega los demás valores en una colección denominada **AttendeeEmailsTemp**.

- ClearCollect(AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    Esta fórmula aproximadamente determina si un asistente está en su organización. La definición de **_userDomain** es simplemente la dirección URL del dominio en la dirección de correo electrónico de la persona que se está ejecutando la aplicación. Esta línea crea una columna adicional de verdadero/falso, denominada **InOrg**, en el **AttendeeEmailsTemp** colección. Esta columna contiene **true** si **userDomain** es equivalente a la dirección URL de dominio de la dirección de correo electrónico en esa fila determinada de **AttendeeEmailsTemp**.

    Este enfoque no siempre es precisa, pero puede ser muy cerca. Por ejemplo, algunos asistentes en la organización podrían tener una dirección de correo electrónico como Jane@OnContoso.com, mientras que **_userDomain** es Contoso.com. El usuario de la aplicación y Jane podrían trabajar en la misma compañía pero tienen pequeñas variaciones en sus direcciones de correo electrónico. Para estos casos, es posible que desea usar esta fórmula:

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    Sin embargo, esta fórmula coincide con direcciones de correo electrónico como Jane@NotTheContosoCompany.com con un **_userDomain** como Contoso.com y estas personas no funcionan en la misma compañía.

- ClearCollect(MyPeople)

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
    Para recuperar perfiles de Office 365, se debe utilizar el [Office365Users.UserProfile](https://docs.microsoft.com/connectors/office365users/#userprofile) o [Office365Users.UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile) operación. Estas operaciones recopilación todos los perfiles de Office 365 para los asistentes que se encuentran en la organización de. del usuario A continuación, las operaciones de agregar unos cuantos campos para los asistentes de fuera de la organización. Separan estos dos elementos en distintas operaciones porque el **ForAll** bucle no garantiza el orden. Por lo tanto, **ForAll** podría recopilar primero un asistente desde fuera de la organización. En este caso, el esquema para **MyPeople** contiene sólo **DisplayName**, **Id**, **JobTitle**, y **UserPrincipalName** . Sin embargo, las operaciones de perfil de usuario recuperan muchos datos más completos que eso. Para que forzar la **MyPeople** colección para agregar perfiles de Office 365 antes de los otros perfiles.

    > [!NOTE]
    > Puede lograr el mismo resultado con un único **ClearCollect** función:

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

1. Agregar una pantalla que contenga una galería para que la **elementos** propiedad está establecida en **MyPeople**.

1. En el **OnSelect** propiedad de la **título** controlar en el **CalendarEventsGallery**, agregar un **Navigate** función a la pantalla que se creó en el paso anterior.

## <a name="next-steps"></a>Pasos siguientes

* [Consulte la documentación de referencia para esta pantalla](calendar-screen-reference.md).
* [Más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
