---
title: Referencia de plantillas de pantalla de las personas | Microsoft Docs
description: Conocer los detalles del funcionamiento de la plantilla de pantalla de las personas para las aplicaciones de lienzo en PowerApps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09b92a1e2bc87ac6f4e2ec651aa67a845e0f07b1
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540778"
ms.PowerAppsDecimalTransform: true
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>Información de referencia acerca de la plantilla de pantalla de las personas para las aplicaciones de lienzo

Para las aplicaciones de lienzo en PowerApps, comprender cómo contribuye cada control significativo en la plantilla de pantalla de las personas a la funcionalidad de la pantalla general predeterminada. Este análisis detallado de presentan las fórmulas de comportamiento y los valores de otras propiedades que determinan cómo responden los controles a la entrada del usuario. Para un análisis de alto nivel de funcionalidad de forma predeterminada de la pantalla, consulte el [información general de la pantalla de las personas](people-screen-overview.md).

En este tema se destacan algunos controles importantes y explica las expresiones o las fórmulas que varias propiedades (como **elementos** y **OnSelect**) de estos controles están establecidos:

* [Cuadro de búsqueda de texto](#text-search-box)
* [Usuario examinar galería](#user-browse-gallery) (+ controles secundarios)
* [Los usuarios agregaron galería](#people-added-gallery) (+ controles secundarios)

## <a name="prerequisite"></a>Requisito previo

Estar familiarizado con cómo agregar y configurar las pantallas y otros controles como [crear una aplicación en PowerApps](../data-platform-create-app-scratch.md).

## <a name="text-search-box"></a>Cuadro de búsqueda de texto

![Control TextSearchBox](media/people-screen/people-search-box.png)

Otros controles de un par interactúan o tienen una dependencia en el cuadro de búsqueda de texto:

* Si un usuario empieza a escribir cualquier texto, **UserBrowseGallery** se vuelve visible.
* Cuando un usuario selecciona una persona en **UserBrowseGallery**, se restablece el contenido de búsqueda.

## <a name="user-browse-gallery"></a>Usuario examinar la Galería

![Control UserBrowseGallery](media/people-screen/people-browse-gall.png)

* Propiedad: **elementos**<br>
    Valor: Lógica para buscar los usuarios cuando el usuario empieza a escribir:
    
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
    
Los elementos de esta galería se rellenan con los resultados de búsqueda desde el [Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser) operación. La operación toma el texto `Trim(TextSearchBox)` como su búsqueda de términos y devuelve los resultados de la parte superior a 15 según esa búsqueda. **TextSearchBox** se encapsula en un `Trim()` funciona porque una búsqueda de usuario en espacios de no es válida.

El `Office365Users.SearchUser` operación se encapsula en un `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` función porque solo se debe llamar a la operación cuando el cuadro de búsqueda contiene texto escrito por el usuario. Esto mejora el rendimiento.

### <a name="userbrowsegallery-title-control"></a>Control UserBrowseGallery título

![Control UserBrowseGallery título](media/people-screen/people-browse-gall-title.png)

* Propiedad: **Texto**<br>Valor: `ThisItem.DisplayName`

  Muestra el nombre para mostrar de la persona de su perfil de Office 365.

* Propiedad: **OnSelect**<br>
    Valor: Para agregar el usuario a una colección de nivel de aplicación de código y, a continuación, seleccione el usuario:

    ```powerapps-comma
    Concurrent(
        Set( _selectedUser; ThisItem );
        Reset( TextSearchBox );
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ); 
            Collect( MyPeople; ThisItem )
        )
    )
    ```
Al seleccionar este control hace tres cosas simultáneamente:

   * Establece el  **\_selectedUser** variable del elemento seleccionado.
   * Restablece el término de búsqueda en **TextSearchBox**.
   * Agrega el elemento seleccionado a la **MyPeople** colección, una colección de todas las personas seleccionado por el usuario de la aplicación.

### <a name="userbrowsegallery-profileimage-control"></a>Control UserBrowseGallery ProfileImage

![Control UserBrowseGallery ProfileImage](media/people-screen/people-browse-gall-image.png)

* Propiedad: **Imagen**<br>
    Valor: Lógica para recuperar la foto del perfil del usuario.

    ```powerapps-comma
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto;
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

El **imagen** control recupera la imagen del usuario con el [Office365Users.UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-) operación. Sin embargo, antes de hacerlo, comprueba dos cosas:
  
   * Si el campo Id. está vacío o no está vacío. Esto evita la **imagen** control de intenta recuperar una foto del usuario antes de la galería se ha rellenado con los resultados de búsqueda.
   * Si el usuario tiene una foto (con el [Office365Users.UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata) operación). Esto evita que el `Office365Users.UserPhoto` búsqueda devuelva una excepción si el usuario no tiene una imagen de perfil.

Tenga en cuenta que si no se puede recuperar una imagen, el **imagen** control está en blanco y el **iconUser** control está visible en su lugar.

## <a name="people-added-gallery"></a>Agregado de las personas de la Galería

![Control PeopleAddedGallery](media/people-screen/people-people-gall.png)

* Propiedad: **elementos**<br>
    Valor: `MyPeople`

Esta es la colección de personas inicializado o agregado a seleccionando el **UserBrowseGallery título** control.

### <a name="peopleaddedgallery-title-control"></a>Control PeopleAddedGallery título

![Control PeopleAddedGallery título](media/people-screen/people-people-gall-title.png)

* Propiedad: **OnSelect**<br>
    Valor: `Set( _selectedUser; ThisItem )`

Establece el **_selectedUser** variable para el elemento seleccionado en **EmailPeopleGallery**.

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery iconRemove control

![PeopleAddedGallery iconRemove control](media/people-screen/people-people-gall-delete.png)

* Propiedad: **OnSelect**<br>
    Valor: `Remove( MyPeople; LookUp( MyPeople; UserPrincipalName = ThisItem.UserPrincipalName ) )`

Busca el registro en el **MyPeople** colección, donde **UserPrincipalName** coincide con el **UserPrincipalName** el elemento seleccionado y, a continuación, quita que grabar desde el colección.

## <a name="next-steps"></a>Pasos siguientes

* [Más información sobre esta pantalla](./people-screen-overview.md).
* [Más información sobre el conector de Office 365 Outlook](../connections/connection-office365-outlook.md).
* [Más información sobre el conector de usuarios de Office 365](../connections/connection-office365-users.md).
