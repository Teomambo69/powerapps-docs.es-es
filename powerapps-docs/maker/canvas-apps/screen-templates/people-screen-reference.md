---
title: 'People: referencia de la plantilla de pantalla | Microsoft Docs'
description: Información detallada sobre el funcionamiento de la plantilla de pantalla People para aplicaciones de canvas en PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a1626583300e6fe696415a91de68ff08596f081
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71989377"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Información de referencia sobre la plantilla de pantalla People para aplicaciones de Canvas

En el caso de las aplicaciones de canvas en PowerApps, comprenda cómo contribuye cada control significativo de la plantilla de pantalla People a la funcionalidad predeterminada general de la pantalla. En esta profundización se presentan las fórmulas de comportamiento y los valores de otras propiedades que determinan cómo responden los controles a los datos proporcionados por el usuario. Para obtener una descripción de alto nivel de la funcionalidad predeterminada de esta pantalla, consulte la [información general de la pantalla People](people-screen-overview.md).

En este tema se resaltan algunos controles significativos y se explican las expresiones o fórmulas en las que se establecen varias propiedades (como **Items** y **alseleccionar**) de estos controles:

* [Cuadro de búsqueda de texto](#text-search-box)
* [Galería de exploración de usuarios](#user-browse-gallery) (+ controles secundarios)
* [Personalizó la Galería](#people-added-gallery) (+ controles secundarios)

## <a name="prerequisite"></a>Requisito previo

Está familiarizado con cómo agregar y configurar pantallas y otros controles a medida que [crea una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Cuadro de búsqueda de texto

![Control TextSearchBox](media/people-screen/people-search-box.png)

Un par de otros controles interactúan o tienen una dependencia en el cuadro de búsqueda de texto:

* Si un usuario comienza a escribir cualquier texto, **UserBrowseGallery** se vuelve visible.
* Cuando un usuario selecciona una persona dentro de **UserBrowseGallery**, se restablece el contenido de la búsqueda.

## <a name="user-browse-gallery"></a>Galería de exploración de usuarios

![Control UserBrowseGallery](media/people-screen/people-browse-gall.png)

* Propiedad **Elementos**<br>
    Valor Lógica para buscar usuarios cuando el usuario comienza a escribir:
    
    ```powerapps-comma
    If( !IsBlank( Trim( TextSearchBox.Text ) ); 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ); 
                top: 15
            }
        )
    )
    ```
    
Los elementos de esta galería se rellenan con los resultados de búsqueda de la operación [Office365. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) . La operación toma el texto de `Trim(TextSearchBox)` como término de búsqueda y devuelve los 15 resultados principales en función de la búsqueda. **TextSearchBox** está encapsulado en una función `Trim()` porque un usuario que busca espacios no es válido.

La operación `Office365Users.SearchUser` se encapsula en una función `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` porque solo tiene que llamar a la operación cuando el cuadro de búsqueda contiene texto escrito por el usuario. Esto mejora el rendimiento.

### <a name="userbrowsegallery-title-control"></a>Control de título de UserBrowseGallery

![Control de título de UserBrowseGallery](media/people-screen/people-browse-gall-title.png)

* Propiedad **Texto**<br>Valor: `ThisItem.DisplayName`

  Muestra el nombre para mostrar de la persona de su perfil de Office 365.

* Propiedad **Alseleccionar**<br>
    Valor Código para agregar el usuario a una colección de nivel de aplicación y, a continuación, seleccione el usuario:

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

   * Establece la variable **\_selectedUser** en el elemento seleccionado.
   * Restablece el término de búsqueda en **TextSearchBox**.
   * Agrega el elemento seleccionado a la colección **People** , una colección de todas las personas que ha seleccionado el usuario de la aplicación.

### <a name="userbrowsegallery-profileimage-control"></a>Control UserBrowseGallery ProfileImage

![Control UserBrowseGallery ProfileImage](media/people-screen/people-browse-gall-image.png)

* Propiedad **Imagen**<br>
    Valor Lógica para recuperar la foto de Perfil de un usuario.

    ```powerapps-comma
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto;
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

El control de **imagen** recupera la imagen del usuario con la operación [Office365Users. UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) . Sin embargo, antes de hacerlo, comprueba dos cosas:
  
   * Indica si el campo de ID. está vacío o no está vacío. Esto impide que el control de **imagen** intente recuperar una foto de usuario antes de que se haya rellenado la galería con los resultados de la búsqueda.
   * Si el usuario tiene una foto (con la operación [Office365Users. UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) ). Esto evita que la búsqueda `Office365Users.UserPhoto` devuelva una excepción si el usuario no tiene una imagen de perfil.

Tenga en cuenta que si no se recupera una imagen, el control de **imagen** está en blanco y el control **iconUser** está visible en su lugar.

## <a name="people-added-gallery"></a>Galería agregada por personas

![Control PeopleAddedGallery](media/people-screen/people-people-gall.png)

* Propiedad **Elementos**<br>
    Valor: `MyPeople`

Esta es la colección de personas inicializadas o agregadas a seleccionando el control de **título UserBrowseGallery** .

### <a name="peopleaddedgallery-title-control"></a>Control de título de PeopleAddedGallery

![Control de título de PeopleAddedGallery](media/people-screen/people-people-gall-title.png)

* Propiedad **Alseleccionar**<br>
    Valor: `Set( _selectedUser; ThisItem )`

Establece la variable **_selectedUser** en el elemento seleccionado en **EmailPeopleGallery**.

### <a name="peopleaddedgallery-iconremove-control"></a>Control PeopleAddedGallery iconRemove

![Control PeopleAddedGallery iconRemove](media/people-screen/people-people-gall-delete.png)

* Propiedad **Alseleccionar**<br>
    Valor: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

Busca el registro en la colección **People** , donde **UserPrincipalName** coincide con el **userPrincipalName** del elemento seleccionado y, a continuación, quita ese registro de la colección.

## <a name="next-steps"></a>Pasos siguientes

* [Más información acerca de esta pantalla](./people-screen-overview.md).
* [Obtenga más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Obtenga más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
