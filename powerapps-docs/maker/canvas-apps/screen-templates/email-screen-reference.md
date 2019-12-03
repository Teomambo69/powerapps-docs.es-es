---
title: Referencia de la plantilla de pantalla de correo electrónico para las aplicaciones de Canvas | Microsoft Docs
description: Información detallada sobre cómo funciona la plantilla de pantalla de correo electrónico para las aplicaciones de canvas en PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7226433c5e95537346841f2e2f9474ea68e42dda
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675082"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>Información de referencia sobre la plantilla de pantalla de correo electrónico para las aplicaciones de Canvas

En el caso de las aplicaciones de canvas en Power Apps, comprenda cómo contribuye cada control significativo de la plantilla de pantalla de correo electrónico a la funcionalidad predeterminada general de la pantalla. Esta profundización presenta las fórmulas de comportamiento y los valores de otras propiedades que determinan cómo responden los controles a los datos proporcionados por el usuario. Para obtener una descripción de alto nivel de la funcionalidad predeterminada de esta pantalla, consulte la [información general de la pantalla de correo electrónico](email-screen-overview.md).

En este tema se resaltan algunos controles significativos y se explican las expresiones o fórmulas en las que se establecen varias propiedades (como **Items** y **alseleccionar**) de estos controles:

* [Cuadro de búsqueda de texto](#text-search-box)
* [Agregar icono](#add-icon)
* [Galería de exploración de personas](#people-browse-gallery)
* [Galería de personas de correo electrónico](#email-people-gallery) (+ controles secundarios)
* [Icono correo](#mail-icon)

## <a name="prerequisite"></a>Requisito previo

Está familiarizado con cómo agregar y configurar pantallas y otros controles a medida que [crea una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Cuadro de búsqueda de texto

   ![Control TextSearchBox](media/email-screen/email-search-box.png)

Algunos otros controles de la pantalla tienen una dependencia en el control **cuadro de búsqueda de texto** :

* Si un usuario comienza a escribir texto, aparece **PeopleBrowseGallery** .
* Si un usuario escribe una dirección de correo electrónico válida, aparece **AddIcon** .
* Cuando un usuario selecciona una persona dentro de **PeopleBrowseGallery**, se restablece el contenido de la búsqueda.

## <a name="add-icon"></a>Icono Agregar

   ![Control AddIcon](media/email-screen/email-add-icon.png)

El control **Agregar icono** permite a los usuarios de la aplicación agregar personas que no existen dentro de su organización a la lista de destinatarios del correo electrónico que se está creando.

* Propiedad: **visible**<br>
    Valor: lógica para mostrar el control solo cuando un usuario escribe una dirección de correo electrónico válida en el cuadro de búsqueda:

    ```powerapps-comma
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text; Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  Línea por línea, el bloque de código anterior indica que el control de **icono Agregar** solo será visible si:

    * **TextSearchBox** contiene texto.
    * El texto de **TextSearchBox** es una dirección de correo electrónico válida.
    * El texto de **TextSearchBox** ya no existe en la colección **People** .

* Propiedad: **Alseleccionar**<br>
    Valor: al seleccionar esta opción se agrega la dirección de correo electrónico válida a la colección **People** . La pantalla usa esta colección como la lista de destinatarios:

    ```powerapps-comma
    Collect( MyPeople;
        { 
            DisplayName: TextSearchBox.Text; 
            UserPrincipalName: TextSearchBox.Text; 
            Mail: TextSearchBox.Text
        }
    );;
    Reset( TextSearchBox )
    ```
  
  Este bloque de código agrega una fila a la colección **People** y rellena tres campos con el texto en **TextSearchBox**. Estos tres campos son **displayName**, **UserPrincipalName**y **mail**. A continuación, restablece el contenido de **TextSearchBox**.

## <a name="people-browse-gallery"></a>Galería de exploración de personas

   ![Control PeopleBrowseGallery](media/email-screen/email-browse-gall.png)

* Propiedad: **elementos**<br>
    Valor: los 15 resultados principales de la búsqueda del texto de búsqueda escrito en el control **TextSearchBox** :
    
    ```powerapps-comma
    If( !IsBlank( Trim(TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ); top: 15} )
    )
    ```

  Los elementos de esta galería se rellenan con los resultados de búsqueda de la operación [Office365. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) . La operación toma el texto de `Trim(TextSearchBox)` como término de búsqueda y devuelve los 15 resultados principales en función de la búsqueda.
  
  **TextSearchBox** está encapsulado en una función `Trim()` porque un usuario que busca espacios no es válido. La operación de `Office365Users.SearchUser` se encapsula en una función de `If(!IsBlank(Trim(TextSearchBox.Text)) ... )`, lo que significa que la operación se realiza solo si el cuadro de búsqueda contiene texto escrito por el usuario. Esto mejora el rendimiento. 

### <a name="people-browse-gallery-title-control"></a>Control de título de la galería de exploración de personas

   ![Control de título de PeopleBrowseGallery](media/email-screen/email-browse-gall-title.png)

* Propiedad: **texto**<br>
    Valor: `ThisItem.DisplayName`

  Muestra el nombre para mostrar de la persona de su perfil de Office 365.

* Propiedad: **Alseleccionar**<br>
    Valor: código para agregar el usuario a una colección de nivel de aplicación y, a continuación, seleccione el usuario:

    ```powerapps-comma
    Concurrent(
        Set( _selectedUser; ThisItem );
        Reset( TextSearchBox );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem )
        )
    )
    ```
La selección de este control realiza tres acciones simultáneamente:

   * Establece la variable de **_selectedUser** en el elemento seleccionado.
   * Restablece el término de búsqueda en **TextSearchBox**.
   * Agrega el elemento seleccionado a la colección **People** , una colección de todos los usuarios seleccionados que utiliza la pantalla correo electrónico como un conjunto de destinatarios.

## <a name="email-people-gallery"></a>Galería de personas de correo electrónico

   ![Control EmailPeopleGallery](media/email-screen/email-people-gall.png)

* Propiedad: **elementos**<br>
    Valor: `MyPeople`

  Esta es la colección de personas inicializadas o agregadas a seleccionando el control de **título PeopleBrowseGallery** .

* Propiedad: **alto**<br>
    Valor: lógica para establecer el alto, en función del número de elementos que se encuentran actualmente en la Galería:

    ```powerapps-comma
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2; 0 );
        304
    )
    ```

  El alto de esta galería se ajusta al número de elementos de la galería, con un alto máximo de 304.
  
  Toma `TemplateHeight + TemplatePadding * 2` como el alto total de una sola fila de **EmailPeopleGallery**y, a continuación, lo multiplica por el número de filas. Desde `WrapCount = 2`, el número de filas verdaderas es `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2; 0)`.

* Propiedad: **ShowScrollbar**<br>
    Valor: `EmailPeopleGallery.Height >= 304`
  
  Cuando el alto de la Galería alcanza el 304, la barra de desplazamiento está visible.

### <a name="email-people-gallery-title-control"></a>Control de título de la galería de personas de correo electrónico

   ![Control de título de EmailPeopleGallery](media/email-screen/email-people-gall-text.png)

* Propiedad: **Alseleccionar**<br>
    Valor: `Set(_selectedUser; ThisItem)`

  Establece la variable de **_selectedUser** en el elemento seleccionado en **EmailPeopleGallery**.

### <a name="email-people-gallery-iconremove-control"></a>Control iconRemove de la galería de personas de correo electrónico

   ![Control de título de MonthDayGallery](media/email-screen/email-people-gall-delete.png)

* Propiedad: **Alseleccionar**<br>
    Valor: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

  Busca el registro en la colección **People** , donde **UserPrincipalName** coincide con el **userPrincipalName** del elemento seleccionado y quita ese registro de la colección.

## <a name="mail-icon"></a>Icono correo

* Propiedad: **Alseleccionar**<br>
    Valor: lógica para enviar el mensaje de correo electrónico del usuario:

    ```powerapps-comma
    Set( _emailRecipientString; Concat( MyPeople; Mail & ";" ) );;
    'Office365'.SendEmail( _emailRecipientString; 
        TextEmailSubject.Text;  
        TextEmailMessage.Text; 
        { Importance:"Normal" }
    );;
    Reset( TextEmailSubject );;
    Reset( TextEmailMessage );;
    Clear( MyPeople )
    ```

  El envío de un mensaje de correo electrónico requiere una cadena separada por punto y coma de direcciones de correo electrónico. En el código anterior:
  1. La primera línea de código toma el campo **mail** de todas las filas de la colección **People** , los concatena en una sola cadena de direcciones de correo electrónico separadas por punto y coma, y establece la variable **_emailRecipientString** en el valor de cadena.

  1. A continuación, usa la operación [Office365. sendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) para enviar el correo electrónico a los destinatarios.
    La operación tiene tres parámetros necesarios, **para**, **asunto**y **cuerpo**, y un parámetro opcional--**importancia**. En el código anterior, se **_emailRecipientString**, **TextEmailSubject**. Texto, **TextEmailMessage**. Texto y **normal**, respectivamente.
  1. Por último, restablece los controles **TextEmailSubject** y **TextEmailMessage** y borra la colección **People** .

* Propiedad: **DisplayMode**<br>
    Valor: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ); DisplayMode.Edit; DisplayMode.Disabled )` para enviar un correo electrónico, la línea de asunto del correo electrónico debe tener texto y la colección de destinatarios (mis**personas**) no debe estar vacía.

## <a name="next-steps"></a>Pasos siguientes

* [Más información acerca de esta pantalla](./email-screen-overview.md)
* [Más información sobre el conector de Office 365 Outlook en PowerApps](../connections/connection-office365-outlook.md)
* [Más información sobre el conector de usuarios de Office 365 en PowerApps](../connections/connection-office365-users.md)
