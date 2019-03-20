---
title: Referencia de la plantilla de filtro de correo electrónico para las aplicaciones de lienzo | Microsoft Docs
description: Conocer los detalles del funcionamiento de la plantilla de filtro de correo electrónico para las aplicaciones de lienzo en PowerApps
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
ms.openlocfilehash: 8f77fe1194ace2f8cb5abeb3f9657cc76aab263a
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459491"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>Información de referencia sobre la plantilla de filtro de correo electrónico para las aplicaciones de lienzo

Para las aplicaciones de lienzo en PowerApps, comprender cómo contribuye cada control significativo en la plantilla de filtro de correo electrónico a la funcionalidad de la pantalla general predeterminada. Este análisis detallado de presentan las fórmulas de comportamiento y los valores de otras propiedades que determinan cómo responden los controles a la entrada del usuario. Para un análisis de alto nivel de funcionalidad de forma predeterminada de la pantalla, consulte el [información general de la pantalla de correo electrónico](email-screen-overview.md).

En este tema se destacan algunos controles importantes y explica las expresiones o las fórmulas que varias propiedades (como **elementos** y **OnSelect**) de estos controles están establecidos:

* [Cuadro de búsqueda de texto](#text-search-box)
* [Agregar icono](#add-icon)
* [Las personas examinar la Galería](#people-browse-gallery)
* [Galería de personas por correo electrónico](#email-people-gallery) (+ controles secundarios)
* [Icono de correo electrónico](#mail-icon)

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Cuadro de búsqueda de texto

   ![Control TextSearchBox](media/email-screen/email-search-box.png)

Otros controles en la pantalla tienen una dependencia en el **cuadro de búsqueda de texto** control:

* Si un usuario empieza a escribir cualquier texto, **PeopleBrowseGallery** aparece.
* Si el usuario escribe a una dirección de correo electrónico válida, **AddIcon** aparece.
* Cuando un usuario selecciona una persona en **PeopleBrowseGallery**, se restablece el contenido de búsqueda.

## <a name="add-icon"></a>Icono Agregar

   ![AddIcon control](media/email-screen/email-add-icon.png)

El **icono Agregar** control permite a los usuarios de aplicación para las personas que no existen dentro de su organización a la lista de destinatarios del correo electrónico que se componen de agregar.

* Propiedad: **Visible**<br>
    Valor: Lógica para mostrar el control solo cuando un usuario escribe una dirección de correo electrónico válida en el cuadro de búsqueda:

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  Línea por línea, el bloque de código anterior indica que el **icono Agregar** control será visible solo si:

    * **TextSearchBox** contiene texto.
    * El texto en **TextSearchBox** es una dirección de correo electrónico válida.
    * El texto en **TextSearchBox** ya no existe en el **MyPeople** colección.

* Propiedad: **OnSelect**<br>
    Valor: Seleccionar esta opción agrega la dirección de correo electrónico válida para el **MyPeople** colección. Esta colección se usa por la pantalla como la lista de destinatarios:

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Reset( TextSearchBox )
    ```
  
  Este bloque de código agrega una fila a la **MyPeople** colección y rellena tres campos con el texto en **TextSearchBox**. Estos tres campos son **DisplayName**, **UserPrincipalName**, y **correo**. A continuación, restablece el contenido de **TextSearchBox**.

## <a name="people-browse-gallery"></a>Las personas examinar la Galería

   ![Control PeopleBrowseGallery](media/email-screen/email-browse-gall.png)

* Propiedad: **elementos**<br>
    Valor: Los resultados de búsqueda de 15 primeros del texto de búsqueda que escribió en el **TextSearchBox** control:
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  Los elementos de esta galería se rellenan con los resultados de búsqueda desde el [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) operación. La operación toma el texto `Trim(TextSearchBox)` como su búsqueda de términos y devuelve los resultados de la parte superior a 15 según esa búsqueda.
  
  **TextSearchBox** se encapsula en un `Trim()` funciona porque una búsqueda de usuario en espacios de no es válida. El `Office365Users.SearchUser` operación se encapsula en un `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` función, lo que significa que la operación se realiza únicamente si el cuadro de búsqueda contiene texto escrito por el usuario. Esto mejora el rendimiento. 

### <a name="people-browse-gallery-title-control"></a>La gente navega por control de título de la Galería

   ![Control PeopleBrowseGallery título](media/email-screen/email-browse-gall-title.png)

* Propiedad: **Texto**<br>
    Valor: `ThisItem.DisplayName`

  Muestra el nombre para mostrar de la persona de su perfil de Office 365.

* Propiedad: **OnSelect**<br>
    Valor: Para agregar el usuario a una colección de nivel de aplicación de código y, a continuación, seleccione el usuario:

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
Al seleccionar este control hace tres cosas simultáneamente:

   * Establece el **_selectedUser** variable del elemento seleccionado.
   * Restablece el término de búsqueda en **TextSearchBox**.
   * Agrega el elemento seleccionado a la **MyPeople** colección, una colección de todos los usuarios seleccionados que la pantalla de correo electrónico se usa como un conjunto de destinatarios.

## <a name="email-people-gallery"></a>Galería de personas por correo electrónico

   ![Control EmailPeopleGallery](media/email-screen/email-people-gall.png)

* Propiedad: **elementos**<br>
    Valor: `MyPeople`

  Esta es la colección de personas inicializado o agregado a seleccionando el **PeopleBrowseGallery título** control.

* Propiedad: **Height**<br>
    Valor: Lógica para establecer el alto, en función del número de elementos de la Galería:

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  El alto de esta galería se ajusta al número de elementos de la galería, con una altura máxima de 304.
  
  Tarda `TemplateHeight + TemplatePadding * 2` como el alto de una sola fila de total **EmailPeopleGallery**, a continuación, se multiplica por el número de filas. Puesto que `WrapCount = 2`, es el número de filas true `RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)`.

* Propiedad: **ShowScrollbar**<br>
    Valor: `EmailPeopleGallery.Height >= 304`
  
  Cuando llegue a la altura de la Galería 304, está visible la barra de desplazamiento.

### <a name="email-people-gallery-title-control"></a>Control de título de la Galería de personas por correo electrónico

   ![Control EmailPeopleGallery título](media/email-screen/email-people-gall-text.png)

* Propiedad: **OnSelect**<br>
    Valor: `Set(_selectedUser, ThisItem)`

  Establece el **_selectedUser** variable para el elemento seleccionado en **EmailPeopleGallery**.

### <a name="email-people-gallery-iconremove-control"></a>Correo electrónico personas Galería iconRemove control

   ![Control MonthDayGallery título](media/email-screen/email-people-gall-delete.png)

* Propiedad: **OnSelect**<br>
    Valor: `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  Busca el registro en el **MyPeople** colección, donde **UserPrincipalName** coincide con el **UserPrincipalName** el elemento seleccionado, y quita ese registro desde el colección.

## <a name="mail-icon"></a>Icono de correo electrónico

* Propiedad: **OnSelect**<br>
    Valor: Lógica para enviar el mensaje de correo electrónico del usuario:

    ```powerapps-dot
    Set( _emailRecipientString, Concat( MyPeople, Mail & ";" ) );
    'Office365'.SendEmail( _emailRecipientString, 
        TextEmailSubject.Text,  
        TextEmailMessage.Text, 
        { Importance:"Normal" }
    );
    Reset( TextEmailSubject );
    Reset( TextEmailMessage );
    Clear( MyPeople )
    ```

  Enviar un mensaje de correo electrónico requiere una cadena separada por comas de direcciones de correo electrónico. En el código anterior:
  1. Toma la primera línea de código la **correo** arrastrándolo desde todas las filas de la **MyPeople** colección, los concatena en una sola cadena de direcciones de correo electrónico separadas por punto y coma y establece el **_ emailRecipientString** variable a ese valor de cadena.

  1. A continuación, usa el [Office365.SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail) operación para enviar el correo electrónico a los destinatarios.
    La operación tiene tres parámetros obligatorios, **a**, **asunto**, y **cuerpo**y un parámetro opcional--**importancia**. En el código anterior, son **_emailRecipientString**, **TextEmailSubject**. Texto, **TextEmailMessage**. Texto, y **Normal**, respectivamente.
  1. Por último, restablece el **TextEmailSubject** y **TextEmailMessage** controla y borra el **MyPeople** colección.

* Propiedad: **DisplayMode**<br>
    Valor: `If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` Para que un envío de correo electrónico, debe tener la línea de asunto de correo electrónico, texto y el destinatario (**MyPeople**) colección no debe estar vacía.

## <a name="next-steps"></a>Pasos siguientes

* [Más información sobre esta pantalla](./email-screen-overview.md)
* [Más información sobre el conector de Office 365 Outlook en PowerApps](../connections/connection-office365-outlook.md)
* [Más información sobre el conector de usuarios de Office 365 en PowerApps](../connections/connection-office365-users.md)
