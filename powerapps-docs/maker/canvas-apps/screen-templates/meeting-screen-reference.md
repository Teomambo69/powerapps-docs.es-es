---
title: Referencia para la plantilla de pantalla de la reunión para las aplicaciones de lienzo | Microsoft Docs
description: Conocer los detalles del funcionamiento de la plantilla de pantalla de la reunión para las aplicaciones de lienzo en PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a7559f84b43d3c0372dea71d49c35461ba9d4e57
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539711"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>Información de referencia acerca de la plantilla de pantalla de la reunión para las aplicaciones de lienzo

Para las aplicaciones de lienzo en PowerApps, comprender cómo contribuye cada control significativo en la plantilla de pantalla de la reunión a la funcionalidad de la pantalla general predeterminada. Este análisis detallado de presentan las fórmulas de comportamiento y los valores de otras propiedades que determinan cómo responden los controles a la entrada del usuario. Para un análisis de alto nivel de funcionalidad de forma predeterminada de la pantalla, consulte el [información general de la pantalla de la reunión](meeting-screen-overview.md).

En este tema se destacan algunos controles importantes y explica las expresiones o las fórmulas que varias propiedades (como **elementos** y **OnSelect**) de estos controles están establecidos:

* [Invite tab (LblInviteTab)](#invite-tab)
* [Pestaña programación (LblScheduleTab)](#schedule-tab)
* [Cuadro de búsqueda de texto](#text-search-box)
* [Agregar icono (AddIcon)](#add-icon)
* [Las personas Examinar Galería](#people-browse-gallery) (+ controles secundarios)
* [Galería de personas de reunión](#meeting-people-gallery) (+ controles secundarios)
* [Selector de fecha de la reunión (MeetingDateSelect)](#meeting-date-picker)
* [Reunión duración de la lista desplegable (MeetingDurationSelect)](#meeting-duration-drop-down)
* [Buscar horas de reunión galería](#find-meeting-times-gallery) (+ controles secundarios)
* [Sala Examinar Galería](#room-browse-gallery) (+ controles secundarios)
* [Botón Atrás de contenido adicional (RoomsBackNav)](#back-chevron) (puede no estar visible si el inquilino no dispone de listas de salas)
* [Icono enviar](#send-icon)

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="invite-tab"></a>Invitar a la pestaña

   ![LblInviteTab control](media/meeting-screen/meeting-invite-text.png)

* Propiedad: **Color**<br>
    Valor: `If( _showDetails; LblRecipientCount.Color; RectQuickActionBar.Fill )`

    **_showDetails** es una variable que se usa para determinar si el **LblInviteTab** control o la **LblScheduleTab** control está seleccionado. Si el valor de **_showDetails** es **true**, **LblScheduleTab** está seleccionado; si el valor es **false**, **LblInviteTab**  está seleccionada. Que significa que si el valor de **_showDetails** es **true** (esta pestaña *no es* seleccionado), el color de etiqueta coincide con el de **LblRecipientCount**. En caso contrario, coincide con el valor de relleno de **RectQuickActionBar**.

* Propiedad: **OnSelect**<br> 
    Valor: `Set( _showDetails; false )`

    Conjuntos de la **_showDetails** variable **false**, lo que significa que el contenido de la ficha de invitación está visible y el contenido de la **programación** ficha están ocultos.

## <a name="schedule-tab"></a>Pestaña programación

   ![LblInviteTab control](media/meeting-screen/meeting-schedule-text.png)

* Propiedad: **Color**<br>
    Valor: `If( !_showDetails; LblRecipientCount.Color; RectQuickActionBar.Fill )`

    **_showDetails** es una variable que se usa para determinar si el **LblInviteTab** control o la **LblScheduleTab** control está seleccionado. Si es true, **LblScheduleTab** está seleccionado; si es false, **LblInviteTab** es. Esto significa que si **_showDetails** es true (esta pestaña *es* seleccionado), el color de etiqueta coincide con el valor de relleno de **RectQuickActionBar**. En caso contrario, coincide con el valor de color **LblRecipientCount**.

* Propiedad: **OnSelect**<br>
    Valor: `Set( _showDetails; true )`

    Establece el **_showDetails** variable a **true**, lo que significa que el contenido de la ficha programación es visible y se oculta el contenido de la ficha de invitación.

## <a name="text-search-box"></a>Cuadro de búsqueda de texto

   ![Control TextSearchBox](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

Otros controles en la pantalla tienen una dependencia en este caso:

* Si un usuario empieza a escribir cualquier texto, **PeopleBrowseGallery** se vuelve visible.
* Si el usuario escribe una dirección de correo electrónico válida, **AddIcon** se vuelve visible.
* Cuando un usuario selecciona una persona en **PeopleBrowseGallery** se restablece el contenido de búsqueda.

## <a name="add-icon"></a>Icono Agregar

   ![AddIcon control](media/email-screen/email-add-icon.png)

Este control permite a los usuarios agregar personas que no existen dentro de su organización a la lista de asistentes para la que se componen de reunión.

* Propiedad: **Visible**<br>
    Valor: Tres lógica comprueba que todas deben evaluarse como **true** para el control sea visible:

    ```powerapps-comma
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text; Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  Línea por línea, este bloque de código indica que el **AddIcon** control es visible solo si:

  * El **TextSearchBox** contiene texto.
  * El texto en **TextSearchBox** es una dirección de correo electrónico válida.
  * El texto en **TextSearchBox** ya no existe en el **MyPeople** colección.

* Propiedad: **OnSelect**<br> 
    Valor: Un **recopilar** instrucción para agregar el usuario asistentes a la lista, otro para actualizar las horas de reunión disponible y varios conmutadores de variable:

    ```powerapps-comma
    Collect( MyPeople;
        { 
            DisplayName: TextSearchBox.Text; 
            UserPrincipalName: TextSearchBox.Text; 
            Mail: TextSearchBox.Text
        }
    );;
    Concurrent(
        Reset( TextSearchBox );
        Set( _showMeetingTimes; false );
        UpdateContext( { _loadMeetingTimes: true } );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false );
        ClearCollect( MeetingTimes; 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople; UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC );
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                        MaxCandidates: 15; 
                        MinimumAttendeePercentage:1; 
                        IsOrganizerOptional: false; 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions;
                "StartTime"; MeetingTimeSlot.Start.DateTime; 
                "EndTime"; MeetingTimeSlot.End.DateTime
            )
        )
    );;
    UpdateContext( { _loadingMeetingTimes: false } );;
    Set( _showMeetingTimes; true )
    ```

  Si selecciona este control agrega la dirección de correo electrónico válida (sólo está visible si no se escribe una dirección de correo electrónico válida en **TextSearchBox**) a la **MyPeople** colección (esta colección es la lista de asistentes) y, a continuación, actualiza las horas de reunión disponible con la nueva entrada de usuario.

  En un nivel bajo, este bloque de código:
  1. Recopila la dirección de correo electrónico en el **MyPeople** colección, recopilar la dirección de correo electrónico en el **DisplayName**, **UserPrincipalName**, y **correo**  campos.
  1. Restablece el contenido de la **TextSearchBox** control.
  1. Establece el **_showMeetingTimes** variable **false**. Esta variable controla la visibilidad de **FindMeetingTimesGallery**, que muestra abiertos tiempos para los asistentes seleccionados satisfacer.
  1. Establece el **_loadMeetingTimes** variable de contexto a **true**. Esta variable establece el estado de carga, que alterna la visibilidad de la carga de los controles de estado como **_LblTimesEmptyState** para indicar al usuario que se está cargando sus datos.
  1. Conjuntos de **_selectedMeetingTime** a **Blank()**. **_selectedMeetingTime** es el registro seleccionado desde la **FindMeetingTimesGallery** control. Aparece cubierto aquí porque la adición de otro asistente podría significar que la definición anterior de **_selectedMeetingTime** es que no estén disponibles para ese asistente.
  1. Conjuntos de **_selectedRoom** a **Blank()**. **_selectedRoom** es el registro seleccionado del espacio del **RoomBrowseGallery**. Disponibilidades de la sala se determinan a partir del valor de **_selectedMeetingTime**. Con ese valor en blanco, el **_selectedRoom** valor ya no es válido, por lo que debe estar en blanco.
  1. Conjuntos de **_roomListSelected** a **false**. Esta línea no se puede aplicar a todo el mundo. En la oficina, puede agrupar los salones por diferentes "listas de salas". Si tiene listas de salas, cuentas de esta pantalla para eso, lo que le permite seleccionar primero una lista de salas antes de seleccionar una sala desde dentro de esa lista. El valor de **_roomListSelected** es lo que determina si un usuario (en un inquilino con listas de salas sólo) para ver las salas dentro de una lista de salas o el conjunto de listas de salas. Se establece en **false** obligar a los usuarios para volver a seleccionar una nueva lista de salas.
  1. Usa el [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) operación para determinar y recopilar las horas de reunión disponible para los asistentes. Esta operación pasa:
      * El **UserPrincipalName** de cada usuario seleccionado en el *RequiredAttendees* parámetro.
      * **MeetingDurationSelect**. Selected.Minutes en el *MeetingDuration* parámetro.
      * MeetingDateSelect.SelectedDate + 8 horas en el *iniciar* parámetro. Ocho horas se agrega ya que, de forma predeterminada, la fecha y hora completa para el control de calendario es 12:00 A.M. de la fecha seleccionada. Probablemente desee recuperar availabilities dentro del horario laboral normal. Una hora de inicio del trabajo normal sería 8:00 AM.
      * **MeetingDateSelect**. SelectedDate + 17 horas en el *final* parámetro. se agrega 17 horas porque 12:00 AM + 17 = 5:00 PM. Una hora de finalización de trabajo normal sería 5:00 PM.
      * *15* en el *MaxCandidates* parámetro. Esto significa que la operación devuelve solo la parte superior de 15 horas disponibles para la fecha seleccionada. Esto tiene sentido porque hay fragmentos de dieciséis sólo 30 minutos en un día de trabajo de 8 horas y una reunión de 30 minutos es lo mínimo que puede establecer en esta pantalla.
      * *1* en el *MinimumAttendeePercentage* parámetro. En esencia, a menos que no hay asistentes están disponibles, se recupera la hora de reunión.
      * **false** en el *IsOrganizerOptional* parámetro. Usuario de la aplicación no es un asistente opcional para esta reunión.
      * "Trabajo" en el *ActivityDomain* parámetro. Esto significa que los tiempos de recuperados son solo aquellos dentro de un tiempo de trabajo normal período.
  1. El **ClearCollect** función también agrega dos columnas: "StartTime" y "EndTime". Esto simplifica los datos devueltos. 
  El campo que contiene el inicio disponible y las horas de finalización es el **MeetingTimeSlot** campo. Este campo es un registro que contiene el inicio y final registros, que a su vez contienen el **DateTime** y **TimeZone** valores de sus respectivas sugerencias. En lugar de intentar recuperar este anidamiento de registros, si agrega las columnas "StartTime" y "EndTime" a la **MeetingTimes** colección aporta las **Inicio > fecha y hora** y **final > Fecha y hora** valores a la superficie de la colección.
  1. Una vez que todas estas funciones se han completado, el **_loadingMeetingTimes** variable se establece en **false**, quitar el estado de carga y **_showMeetingTimes** está establecido en **true**, que muestran **FindMeetingTimesGallery**.

## <a name="people-browse-gallery"></a>Las personas examinar la Galería

   ![Control PeopleBrowseGallery](media/meeting-screen/meeting-browse-gall.png)

* Propiedad: **elementos**<br>
    Valor: 
    ```powerapps-comma
    If( !IsBlank( Trim( TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text); top: 15 } )
    )
    ```

Los elementos de esta galería se rellenan con los resultados de búsqueda desde el [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) operación. La operación toma el texto `Trim(**TextSearchBox**)` como su búsqueda de términos y devuelve los resultados de la parte superior a 15 según esa búsqueda.
  
**TextSearchBox** se encapsula en un **recortar** funciona porque una búsqueda de usuario en espacios de no es válida. El `Office365Users.SearchUser` operación se encapsula en un `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` funciona porque al recuperar los resultados de búsqueda antes de que un usuario ha buscado en es una pérdida de rendimiento.

### <a name="people-browse-gallery-title"></a>La gente navega por título de la Galería

   ![Control PeopleBrowseGallery título](media/meeting-screen/meeting-browse-gall-title.png)

* Propiedad: **Texto**<br>
    Valor: `ThisItem.DisplayName`

    Muestra el nombre para mostrar de la persona de su perfil de Office 365.

* Propiedad: **OnSelect**<br>
    Valor: Un **recopilar** instrucción para agregar el usuario asistentes a la lista, otro para actualizar las horas de reunión disponible y varios conmutadores de variable:

    ```powerapps-comma
    Concurrent(
        Reset( TextSearchBox );
        Set( _selectedUser; ThisItem );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem );; 
            Concurrent(
                Set( _showMeetingTimes; false );
                UpdateContext( { _loadMeetingTimes: true } );
                Set( _selectedMeetingTime; Blank() );
                Set( _selectedRoom; Blank() );
                Set( _roomListSelected; false );
                ClearCollect( MeetingTimes; 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" );
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC );
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                                MaxCandidates: 15; 
                                MinimumAttendeePercentage: 1; 
                                IsOrganizerOptional: false; 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions;
                        "StartTime"; MeetingTimeSlot.Start.DateTime; 
                        "EndTime"; MeetingTimeSlot.End.DateTime
                    )
                )
            );;
            UpdateContext( { _loadingMeetingTimes: false } );;
            Set( _showMeetingTimes; true )
        )
    )
    ```

    En un nivel alto, si selecciona este control agrega la persona a la **MyPeople** (almacenamiento de la aplicación de la lista de asistentes) de la colección y las actualizaciones de las horas de reunión disponible en función de la incorporación de un usuario nuevo.

    Al seleccionar este control es muy similar a seleccionar el **AddIcon** control; la única diferencia es que el `Set(_selectedUser; ThisItem)` instrucción y el orden de ejecución de las operaciones. Por lo tanto, esta explicación no será tan profunda. Para obtener una explicación más completa, lea el [AddIcon control](#add-icon) sección.

    Si selecciona este control se restablece **TextSearchBox**. A continuación, si la selección no está en el **MyPeople** colección, el control:
    1. Conjuntos de la **_loadMeetingTimes** estado **true** y **_showMeetingTimes** estado **false**, espacios en blanco la **_ selectedMeetingTime** y **_selectedRoom** variables y las actualizaciones de la **MeetingTimes** colección con la nueva incorporación a la **MyPeople** colección. 
    1. Establece el **_loadMeetingTimes** estado **false**y establece **_showMeetingTimes** a **true**. Si la selección ya está en el **MyPeople** colección, restablece solo el contenido de **TextSearchBox**.

## <a name="meeting-people-gallery"></a>Galería de personas de reunión

   ![Control MeetingPeopleGallery](media/meeting-screen/meeting-people-gall.png)

* Propiedad: **elementos**<br>
    Valor: `MyPeople`

    El **MyPeople** es la colección de personas inicializado o agregado a seleccionando el **PeopleBrowseGallery título** control.

* Propiedad: **Height**<br>
    Valor: Lógica para permitir que la Galería crecer hasta una altura máxima de 350:

    ```powerapps-comma
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2; 0 );
        350
    )
    ```

  
   El alto de esta galería se ajusta al número de elementos de la galería, hasta una altura máxima de 350. La fórmula toma 76 como el alto de una sola fila de **MeetingPeopleGallery**, a continuación, se multiplica por el número de filas. El **WrapCount** propiedad está establecida en 2, por lo que es el número de filas true `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2; 0)`.

* Propiedad: **ShowScrollbar**<br>
    Valor: `MeetingPeopleGallery.Height >= 350`

    Cuando se llega a la altura máxima de la Galería (350), está visible la barra de desplazamiento.

### <a name="meeting-people-gallery-title"></a>Título de la Galería de personas reunión

   ![Control MeetingPeopleGallery título](media/meeting-screen/meeting-people-gall-title.png)

* Propiedad: **OnSelect**<br>
    
    Valor: `Set(_selectedUser; ThisItem)`
    
    Establece el **_selectedUser** variable para el elemento seleccionado en **MeetingPeopleGallery**.

### <a name="meeting-people-gallery-iconremove"></a>Reunión personas Galería iconRemove

   ![MeetingPeopleGallery iconRemove control](media/meeting-screen/meeting-people-gall-delete.png)

* Propiedad: **OnSelect**<br>
    Valor: Un **quitar** instrucción para quitar el usuario de la lista de asistentes, un **recopilar** instrucción para actualizar las horas de reunión disponible y varios conmutadores de variable:

    ```powerapps-comma
    Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) );;
    Concurrent(
        Reset( TextSearchBox );
        Set( _showMeetingTimes; false );
        UpdateContext( { _loadMeetingTimes: true } );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false );
        ClearCollect( MeetingTimes; 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" ); 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC ); 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                        MaxCandidates: 15; 
                        MinimumAttendeePercentage: 1; 
                        IsOrganizerOptional: false; 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions;
                "StartTime"; MeetingTimeSlot.Start.DateTime; 
                "EndTime"; MeetingTimeSlot.End.DateTime
            )
        )
    );;
    UpdateContext( { _loadingMeetingTimes: false } );;
    Set( _showMeetingTimes; true )
    ```

  Al seleccionar este control en un nivel alto, quita a la persona de la lista de asistentes y actualiza las horas de reunión disponible en función de la eliminación de esta persona.

  Después de la primera línea del código anterior, al seleccionar este control es casi idéntico al seleccionar el **AddIcon** control. Por lo tanto, no será tan profunda esta discusión. Para obtener una explicación más completa, lea el [sección control de AddIcon](#add-icon).

  En la primera línea de código, se quita el elemento seleccionado de la **MyPeople** colección. A continuación, el código:
  1. Restablece **TextSearchBox**y, a continuación, quita la selección de la **MyPeople** colección. 
  1. Conjuntos de la **_loadMeetingTimes** estado **true** y **_showMeetingTimes** estado **false**, espacios en blanco la **_ selectedMeetingTime** y **_selectedRoom** variables y las actualizaciones de la **MeetingTimes** colección con la nueva incorporación a la **MyPeople** colección. 
  1. Establece el **_loadMeetingTimes** estado **false**y establece **_showMeetingTimes** a **true**.

## <a name="meeting-date-picker"></a>Selector de fecha de reunión

   ![Control MeetingDateSelect](media/meeting-screen/meeting-datepicker.png)

* Propiedad: **DisplayMode**<br>
    Valor: `If( IsEmpty(MyPeople); DisplayMode.Disabled; DisplayMode.Edit )`

    No se puede elegir una fecha para una reunión hasta que se ha agregado al menos un asistente a la **MyPeople** colección.

* Propiedad: **OnChange**<br>
    Valor: `Select( MeetingDateSelect )`

    Cambiar la fecha seleccionada, desencadenará el código en el **OnSelect** propiedad de este control para ejecutar.

* Propiedad: **OnSelect**<br>
    Valor: Un **recopilar** instrucción para actualizar las horas de reunión disponible y varios conmutadores de variable:
  
    ```powerapps-comma
    Concurrent(
        Reset( TextSearchBox );
        Set( _showMeetingTimes; false );
        UpdateContext( { _loadingMeetingTimes: true } );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false );
        ClearCollect( MeetingTimes; 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" ); 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate; 8; Hours ); UTC ); 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate; 17; Hours ); UTC );
                        MaxCandidates: 15; 
                        MinimumAttendeePercentage: 1; 
                        IsOrganizerOptional: false; 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions;
                "StartTime"; MeetingTimeSlot.Start.DateTime; 
                "EndTime"; MeetingTimeSlot.End.DateTime
            )
        )
    );;
    UpdateContext( { _loadingMeetingTimes: false } );;
    Set( _showMeetingTimes; true )
    ```

  En un nivel alto, al seleccionar este control actualiza las horas de reunión disponible. Es útil porque si un usuario cambia la fecha, las horas de reunión disponible deben actualizarse para reflejar la disponibilidades de los asistentes para ese día.

  Con la excepción inicial **recopilar** instrucción, esto es idéntica a la **Alseleccionar** funcionalidad de la **AddIcon** control. Por lo tanto, no será tan profunda esta discusión. Para obtener una explicación más completa, lea el [AddIcon control](#add-icon) sección.

  Si selecciona este control se restablece **TextSearchBox**. A continuación: 
  1. Conjuntos de la **_loadMeetingTimes** estado **true** y **_showMeetingTimes** estado **false**, espacios en blanco la **_ selectedMeetingTime** y **_selectedRoom** variables y las actualizaciones de la **MeetingTimes** colección con la selección de la nueva fecha. 
  1. Establece el **_loadMeetingTimes** estado **false**y establece **_showMeetingTimes** a **true**.

## <a name="meeting-duration-drop-down"></a>Duración de la reunión desplegable

   ![Control MeetingDateSelect](media/meeting-screen/meeting-timepicker.png)

* Propiedad: **DisplayMode**<br>
    Valor: `If( IsEmpty(MyPeople); DisplayMode.Disabled; DisplayMode.Edit )`

    No se puede seleccionar una duración para una reunión hasta que se ha agregado al menos un asistente a la **MyPeople** colección.

* Propiedad: **OnChange**<br>
    Valor: `Select(MeetingDateSelect1)`

    Cambiar la duración seleccionada, desencadenará el código en el **Alseleccionar** propiedad de la **MeetingDateSelect** control para ejecutar.

## <a name="find-meeting-times-gallery"></a>Buscar horas de reunión Galería

   ![Control FindMeetingTimesGallery](media/meeting-screen/meeting-time-gall.png)

* Propiedad: **elementos**<br>
    Valor: `MeetingTimes`

    Recupera la colección de posibles horas de reunión el [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) operación.

* Propiedad: **Visible**<br>
    Valor: `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    La galería está visible solo si **_showMeetingTimes** está establecido en **true**, el usuario ha seleccionado la **LblScheduleTab** control y hay al menos un asistente que se agrega a la reunión.

### <a name="find-meeting-times-gallery-title"></a>Buscar horas de reunión título de la Galería

   ![Control FindMeetingTimesGallery título](media/meeting-screen/meeting-time-gall-title.png)

* Propiedad: **Texto**<br>
    Valor: Una conversión de la hora de inicio que se mostrará en la hora local del usuario:

    ```powerapps-comma
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime );
            - TimeZoneOffset(); 
            Minutes
        );
        DateTimeFormat.ShortTime
    )
    ```

  El valor recuperado de **StartTime** está en formato UTC. Para [convertir a la hora UTC a la hora local](../functions/function-dateadd-datediff.md#converting-from-utc), **DateAdd** se aplica la función.
  El [función Text](../functions/function-text.md#datetime) toma una fecha y hora como su primer argumento y formatos en función de su segundo argumento. Se le pasa la conversión de hora local de **ThisItem.StartTime**y mostrarlo como **DateTimeFormat.ShortTime**.

* Propiedad: **OnSelect**<br>
    Valor: Varios **recopilar** instrucciones para recopilar sus availabilities sugeridos y salas de reuniones, así como varios conmutadores de variable:

    ```powerapps-comma
    Set( _selectedMeetingTime; ThisItem );;
    UpdateContext( { _loadingRooms: true } );;
    If( IsEmpty( RoomsLists );
        ClearCollect( RoomsLists; 'Office365'.GetRoomLists().value) );;
    If( CountRows( RoomsLists ) <= 1;
        Set( _noRoomLists; true );;
        ClearCollect( AllRooms; 'Office365'.GetRooms().value );;
        Set( _allRoomsConcat; Concat( FirstN( AllRooms; 20 ); Address & ";" ) );;
        ClearCollect( RoomTimeSuggestions; 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat; 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                    Start: _selectedMeetingTime.StartTime & "Z"; 
                    End: _selectedMeetingTime.EndTime & "Z"; 
                    MinimumAttendeePercentage: "1";
                    IsOrganizerOptional: "false"; 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );;
        ClearCollect( AvailableRooms; 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability;
                        Availability="Free"
                    ); 
                    "Address"; Attendee.EmailAddress.Address
                ); 
                "Name"; LookUp( AllRooms; Address = Attendee.EmailAddress.Address ).Name 
            )
        );;
        ClearCollect( AvailableRoomsOptimal; 
            DropColumns(
                DropColumns( AvailableRooms; "Availability" ); 
                "Attendee" 
            )
        );
        Set( _roomListSelected; false) 
    );;
    UpdateContext( {_loadingRooms: false} )
    ```

  En un nivel alto, este bloque de código reúne salas disponibles para los usuarios que no tienen salones de listas, en función de la fecha y hora seleccionada para la reunión. En caso contrario, simplemente recupera las listas de salas.

  En un nivel bajo, este bloque de código:
  1. Conjuntos de **_selectedMeetingTime** al elemento seleccionado. Esto sirve para encontrar qué salas están disponibles durante ese tiempo.
  1. Establece la carga variable de estado **_loadingRooms** a **true**, activar el estado de carga.
  1. Si el **RoomsLists** colección está vacía, recupera las listas de salas del inquilino del usuario y los almacena en el **RoomsLists** colección.
  1. Si el usuario no tiene ninguna lista de espacio o una sala:
      1. El **noRoomLists** variable se establece en **true**, y esta variable se usa para determinar los elementos mostrados en la **RoomBrowseGallery** control.
      1. El `Office365.GetRooms()` operación se usa para recuperar los 100 primeros locales en su inquilino. Estos se almacenan en el **AllRooms** colección.
      1. El **_allRoomsConcat** variable se establece en una cadena separada por comas de las primeras direcciones de correo 20 electrónico de las salas de la **AllRooms** colección. Esto es porque el [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) se limita a la búsqueda de las horas disponibles de 20 objetos person en una sola operación.
      1. El **RoomTimeSuggestions** colección utiliza el [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) para recuperar la disponibilidades de los 20 primeros locales en el **AllRooms** colección, en función en los valores de tiempo desde la **_selectedMeetingTime** variable. Tenga en cuenta que el `& "Z"` se usa para formatear correctamente el **DateTime** valor.
      1. El **AvailableRooms** se crea la colección. Esto es simplemente el **RoomTimeSuggestions** colección de availabilities asistentes con dos columnas adicionales agregadas a él: "Address" y "Name". "Address" es la dirección de correo electrónico de la sala de reuniones y "Name" es el nombre de la sala.
      1. A continuación, la **AvailableRoomsOptimal** se crea la colección. Esto es simplemente el **AvailableRooms** quitado de la colección con las columnas "Disponibilidad" y "Opcional". Esto coincide con los esquemas de **AvailableRoomsOptimal** y **AllRooms**. Esto permite usar ambas colecciones en el **elementos** propiedad de la **RoomBrowseGallery**.
      1. **_roomListSelected** está establecido en **false**.
  1. El estado de carga, **_loadingRooms**, se establece en **false** una vez que todo lo demás ha terminado de ejecutarse.

## <a name="room-browse-gallery"></a>Galería de exploración de sala

   ![Control RoomBrowseGallery](media/meeting-screen/meeting-rooms-gall.png)

* Propiedad: **elementos**<br>
    Valor: Lógicamente se establece en dos colecciones internas del esquema idéntico, dependiendo de si el usuario ha seleccionado una lista de salas o tiene listas de salas en su inquilino:

    ```powerapps-comma
    Search(
        If( _roomListSelected || _noRoomLists; AvailableRoomsOptimal; RoomsLists );
        Trim(TextMeetingLocation1.Text); 
        "Name"; 
        "Address"
    )
    ```

  Esta galería muestra el **AvailableRoomsOptimal** colección si **_roomListSelected** o **_noRoomLists** es **true**. De lo contrario, muestra el **RoomsLists** colección. Esto puede realizarse porque el esquema de estas colecciones son idénticos.

* Propiedad: **Visible**<br>
    Valor: ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    La galería está visible solo si las tres instrucciones anteriores se evalúan como **true**.

### <a name="roombrowsegallery-title"></a>Título RoomBrowseGallery

   ![Control RoomBrowseGallery título](media/meeting-screen/meeting-rooms-gall-title.png)

* Propiedad: **OnSelect**<br>
    Valor: Un conjunto de lógicamente enlazado **recopilar** y **establecer** instrucciones, que pueden o no se podrían desencadenar, dependiendo de si el usuario está viendo listas de salas o salones:

    ```powerapps-comma
    UpdateContext( { _loadingRooms: true } );;
    If( !_roomListSelected && !noRoomLists;
        Set( _roomListSelected; true );;
        Set( _selectedRoomList; ThisItem.Name );;
        ClearCollect( AllRooms; 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );;
        Set( _allRoomsConcat; Concat( FirstN( AllRooms; 20 ); Address & ";" ) );;
        ClearCollect( RoomTimeSuggestions; 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat; 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes;
                        Start: _selectedMeetingTime.StartTime & "Z"; 
                    End: _selectedMeetingTime.EndTime & "Z"; 
                    MinimumAttendeePercentage: "1";
                    IsOrganizerOptional: "false"; 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );;
        ClearCollect( AvailableRooms; 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability; 
                        Availability = "Free"
                    );
                    "Address"; Attendee.EmailAddress.Address 
                ); 
                "Name"; LookUp( AllRooms; Address = Attendee.EmailAddress.Address ).Name
            )
        );;
        ClearCollect( AvailableRoomsOptimal; 
            DropColumns(
                DropColumns( AvailableRooms; "Availability" )
            ); 
            "Attendee" )
        );
        Set( _selectedRoom; ThisItem )
    );;
    UpdateContext( {_loadingRooms: false} )
    ```

  Las acciones que se producen cuando se selecciona este control dependen de si un usuario está viendo actualmente un conjunto de listas de salas o un conjunto de salas. Si es la primera, a continuación, al seleccionar este control recupera los locales que están disponibles en el momento seleccionado en la lista de espacio seleccionado. Si trata del último caso, al seleccionar este control se establece la **_selectedRoom** variable al elemento seleccionado. La instrucción anterior es muy similar a la **seleccione** instrucción para [ **FindMeetingTimesGallery título**](#find-meeting-times-gallery).

  En un nivel bajo, el bloque de código anterior:
  1. Activa el estado de la carga de las salas de estableciendo **_loadingRooms** a **true**.
  1. Comprueba ver si se ha seleccionado una lista de salas y si el inquilino tiene espacio listas. Si es así:
      1. Establece **_roomListSelected** a **true** y establece **_selectedRoomList** al elemento seleccionado.
      1. El **_allRoomsConcat** variable se establece en una cadena separada por comas de las primeras direcciones de correo 20 electrónico de las salas de la **AllRooms** colección. Esto es porque el [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) operación se limita a la búsqueda de las horas disponibles de 20 objetos person en una sola operación.
      1. El **RoomTimeSuggestions** colección utiliza el [Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times) operación para recuperar la disponibilidades de los 20 primeros locales en el **AllRooms** colección, basándose en los valores de tiempo desde la **_selectedMeetingTime** variable. Tenga en cuenta que `& "Z"` se usa para formatear correctamente el **DateTime** valor.
      1. El **AvailableRooms** se crea la colección. Esto es simplemente el **RoomTimeSuggestions** colección de availabilities asistentes con dos columnas adicionales agregadas a él: "Address" y "Name". "Address" es la dirección de correo electrónico de la sala de reuniones y "Name" es el nombre de la sala.
      1. A continuación, la **AvailableRoomsOptimal** se crea la colección. Esto es simplemente el **AvailableRooms** quitado de la colección con las columnas "Disponibilidad" y "Opcional". Esto coincide con los esquemas de **AvailableRoomsOptimal** y **AllRooms**. Esto permite usar ambas colecciones en el **elementos** propiedad de **RoomBrowseGallery**.
      1. **_roomListSelected** está establecido en **false**.
  1. El estado de carga, **_loadingRooms**, se establece en **false** una vez que todo lo demás ha terminado de ejecutarse.

## <a name="back-chevron"></a>Realizar una copia de cheurón

   ![Control RoomsBackNav](media/meeting-screen/meeting-back.png)

* Propiedad: **Visible**<br>
    Valor: `_roomListSelected && _showDetails`

    Este control sólo está visible si se ha seleccionado una lista de salas y **programación** pestaña está seleccionada.

* Propiedad: **OnSelect**<br>
    Valor: `Set( _roomListSelected; false )`

    Cuando **_roomListSelected** está establecido en **false**, cambia el **RoomBrowseGallery** control para mostrar los elementos de la **RoomsLists** colección.

## <a name="send-icon"></a>Icono enviar

   ![Control IconSendItem](media/meeting-screen/meeting-send-icon.png)

* Propiedad: **DisplayMode**<br>
    Valor: Lógica para forzar el usuario escriba algunos detalles de reunión antes de que el icono pasa a ser editable.
    
    ```powerapps-comma
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime );
        DisplayMode.Edit; DisplayMode.Disabled
    )
    ```
  El icono es seleccionable solo si se rellena el asunto de la reunión, hay al menos un Asistente para la reunión y se ha seleccionado una hora de reunión. En caso contrario, está deshabilitado.

* Propiedad: **OnSelect**<br>

    Valor: Código para enviar la invitación de reunión a los asistentes seleccionados y borrar todos los campos de entrada:

    ```powerapps-comma
    Set( _myCalendarName; LookUp( 'Office365'.CalendarGetTables().value; DisplayName = "Calendar" ).Name );;
    Set( _myScheduledMeeting; 
        'Office365'.V2CalendarPostItem( _myCalendarName;
            TextMeetingSubject1.Text; 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime); -TimeZoneOffset(); Minutes) );
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime); -TimeZoneOffset(); Minutes) );
            {
                RequiredAttendees: Concat( MyPeople; UserPrincipalName & ";" ) & _selectedRoom.Address; 
                Body: TextMeetingMessage1.Text; 
                Location: _selectedRoom.Name; 
                Importance: "Normal"; 
                ShowAs: "Busy"; 
                ResponseRequested: true
            }
        )
    );;
    Concurrent(
        Reset( TextMeetingLocation1 );
        Reset( TextMeetingSubject1 );
        Reset( TextMeetingMessage1 );
        Clear( MyPeople );
        Set( _selectedMeetingTime; Blank() );
        Set( _selectedRoomList; Blank() );
        Set( _selectedRoom; Blank() );
        Set( _roomListSelected; false )
    )
    ```
  
  En un nivel bajo, este bloque de código:
  1. Conjuntos de **_myCalendarName** en el calendario en la [Office365.CalendarGetTables()](https://docs.microsoft.com/connectors/office365/#get-calendars) operación con un **DisplayName** "Calendar".
  1. Las programaciones de la reunión con toda la entrada los valores de las selecciones de varias el usuario haya hecho a lo largo de la pantalla mediante el [Office365.V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-) operación.
  1. Restablece todos los campos de entrada y las variables utilizadas en la creación de la reunión.

> [!NOTE]
> Dependiendo de su región, el calendario que desea no podría tener un nombre para mostrar de "Calendar". Vaya a Outlook para ver lo que es el título del calendario y realizar el cambio correspondiente en la aplicación.

## <a name="next-steps"></a>Pasos siguientes

* [Más información sobre esta pantalla](./meeting-screen-overview.md)
* [Más información sobre el conector de Office 365 Outlook en PowerApps](../connections/connection-office365-outlook.md)
* [Más información sobre el conector de usuarios de Office 365 en PowerApps](../connections/connection-office365-users.md)
