---
title: Introducción a la conexión de Usuarios de Office 365 | Microsoft Docs
description: Ver cómo conectarse a Usuarios de Office 365 a través de algunos ejemplos y examinar todas las funciones
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/07/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 507bac0b57cdc1e348bd384d5544d7b664a3e0f5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42851273"
---
# <a name="connect-to-office-365-users-connection-from-powerapps"></a>Conectarse a la conexión de los usuarios de Office 365 desde PowerApps
![Usuarios de Office 365](./media/connection-office365-users/office365icon.png)

Usuarios de Office 365 le permite acceder a los perfiles de usuario de su organización mediante su cuenta de Office 365. Puede realizar diversas acciones, como obtener su perfil, el perfil de un usuario o el administrador y los subordinados directos de un usuario.

Puede mostrar esta información en una etiqueta en la aplicación. Puede mostrar una función, varias funciones o incluso combinar funciones diferentes. Por ejemplo, puede crear una expresión que combine el nombre de usuario y el número de teléfono y luego mostrar esta información en la aplicación.

En este tema se muestra cómo agregar Usuarios de Office 365 como una conexión y como un origen de datos a su aplicación y cómo utilizar datos de tabla en un control de la galería.

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="add-a-connection"></a>Agregar una conexión
1. [Agregue una conexión de datos](../add-data-connection.md) y seleccione **Usuarios de Office 365**:  

    ![Conexión a Office 365](./media/connection-office365-users/add-office.png)
2. Seleccione **Connect** (Conectar) y, si se pide que inicie sesión, escriba su cuenta profesional.

La conexión de Usuarios de Office 365 se ha creado y agregado a la aplicación. Ahora, está lista para utilizarse.

## <a name="use-the-connection-in-your-app"></a>Uso de la conexión en la aplicación
### <a name="show-information-about-the-current-user"></a>Mostrar información sobre el usuario actual
1. En el menú **Insertar**, seleccione **Etiqueta**.
2. En la barra de funciones, establezca su propiedad **[Text](../controls/properties-core.md)** en cualquiera de las siguientes fórmulas:

    `Office365Users.MyProfile().Department`  
    `Office365Users.MyProfile().DisplayName`  
    `Office365Users.MyProfile().GivenName`  
    `Office365Users.MyProfile().Id`  
    `Office365Users.MyProfile().JobTitle`  
    `Office365Users.MyProfile().Mail`  
    `Office365Users.MyProfile().MailNickname`  
    `Office365Users.MyProfile().Surname`  
    `Office365Users.MyProfile().TelephoneNumber`  
    `Office365Users.MyProfile().UserPrincipalName`  
    `Office365Users.MyProfile().AccountEnabled`  

La etiqueta muestra la información que ha especificado sobre el usuario actual.

### <a name="show-information-about-another-user"></a>Mostrar información sobre otro usuario
1. En el menú **Insert** (Insertar), seleccione **Text** (Texto) y luego seleccione **Text input** (Entrada de texto). Cambie su nombre por **InfoAbout**:  

    ![Cambiar el nombre del control](./media/connection-office365-users/renameinfoabout.png)
2. En **InfoAbout**, escriba o pegue una dirección de correo electrónico de un usuario de su organización. Por ejemplo, escriba *yourName*@*yourCompany.com*.
3. Agregue una **etiqueta** (menú **Insertar**) y establezca su propiedad **[Texto](../controls/properties-core.md)** en alguna de las siguientes fórmulas:

   * Para mostrar información sobre otro usuario:  

       `Office365Users.UserProfile(InfoAbout.Text).Department`  
       `Office365Users.UserProfile(InfoAbout.Text).DisplayName`  
       `Office365Users.UserProfile(InfoAbout.Text).GivenName`  
       `Office365Users.UserProfile(InfoAbout.Text).Id`  
       `Office365Users.UserProfile(InfoAbout.Text).JobTitle`  
       `Office365Users.UserProfile(InfoAbout.Text).Mail`  
       `Office365Users.UserProfile(InfoAbout.Text).MailNickname`  
       `Office365Users.UserProfile(InfoAbout.Text).Surname`  
       `Office365Users.UserProfile(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.UserProfile(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.UserProfile(InfoAbout.Text).AccountEnabled`  
   * Para mostrar información sobre el administrador de otro usuario:  

       `Office365Users.Manager(InfoAbout.Text).Department`  
       `Office365Users.Manager(InfoAbout.Text).DisplayName`  
       `Office365Users.Manager(InfoAbout.Text).GivenName`  
       `Office365Users.Manager(InfoAbout.Text).Id`  
       `Office365Users.Manager(InfoAbout.Text).JobTitle`  
       `Office365Users.Manager(InfoAbout.Text).Mail`  
       `Office365Users.Manager(InfoAbout.Text).MailNickname`  
       `Office365Users.Manager(InfoAbout.Text).Surname`  
       `Office365Users.Manager(InfoAbout.Text).TelephoneNumber`  
       `Office365Users.Manager(InfoAbout.Text).UserPrincipalName`  
       `Office365Users.Manager(InfoAbout.Text).AccountEnabled`  

La etiqueta muestra la información que ha escrito sobre el usuario especificado o sobre el administrador de ese usuario.

> [!NOTE]
> Si va a desarrollar una aplicación basada en una entidad en Common Data Service, puede especificar un usuario basado en el id. en lugar de la dirección de correo electrónico.

Por ejemplo, puede [crear una aplicación automáticamente](../data-platform-create-app.md), agregar una pantalla que contenga un control **Etiqueta** y establecer la propiedad **Texto** del control en esta fórmula:
<br>**Office365Users.UserProfile(BrowseGallery1.Selected.CreatedByUser).DisplayName**

Si crea un contacto y lo selecciona en la pantalla de exploración de la aplicación, el control **Etiqueta** mostrará su nombre para mostrar.

### <a name="show-the-direct-reports-of-another-user"></a>Mostrar los subordinados directos de otro usuario
1. Agregue un control **Entrada de texto** (menú **Insert** [Insertar] > **Text** [Texto]) y cambie su nombre por **InfoAbout**.
2. En **InfoAbout**, escriba la dirección de correo electrónico de un usuario de su organización. Por ejemplo, escriba *yourManagersName*@*yourCompany.com*.
3. Agregue una galería **With text** (Con texto) (menú **Insert** [Insertar] > **Gallery** [Galería]) y establezca su propiedad **[Items](../controls/properties-core.md)** en la siguiente fórmula:

    `Office365Users.DirectReports(InfoAbout.Text)`

    La galería muestra información sobre los subordinados directos del usuario especificado.

    Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
4. En la segunda lista, seleccione **JobTitle**. En la tercera lista, seleccione **DisplayName**. La galería se actualiza para mostrar estos valores.  

> [!NOTE]
> El primer cuadro es en realidad un control de imagen. Si no tiene ninguna imagen, puede eliminar el control de imagen y agregar una etiqueta en su lugar. [Agregar y configurar controles](../add-configure-controls.md) es un buen recurso.

### <a name="search-for-users"></a>Búsqueda de usuarios
1. Agregue un control **Entrada de texto** (menú **Insert** [Insertar] > **Text** [Texto]) y cambie su nombre por **SearchTerm**. Escriba un nombre para buscar. Por ejemplo, escriba su nombre.
2. Agregue una galería **With text** (Con texto) (menú **Insert** [Insertar] > **Gallery** [Galería]) y establezca su propiedad **[Items](../controls/properties-core.md)** en la siguiente fórmula:

    `Office365Users.SearchUser({searchTerm: SearchTerm.Text})`

    La galería muestra los usuarios cuyo nombre contiene el texto de búsqueda que ha escrito.

    Con la galería seleccionada, el panel derecho muestra opciones para esa galería.
3. En la segunda lista, seleccione **Mail**. En la tercera lista, seleccione **DisplayName**.

    La segunda y tercera etiqueta de la galería se actualizan.

## <a name="view-the-available-functions"></a>Visualización de las funciones disponibles
Esta conexión incluye las siguientes funciones:

| Nombre de la función | Descripción |
| --- | --- |
| [MyProfile](connection-office365-users.md#myprofile) |Recupera el perfil del usuario actual. |
| [UserProfile](connection-office365-users.md#userprofile) |Recupera un perfil de usuario específico. |
| [Manager](connection-office365-users.md#manager) |Recupera el perfil de usuario del administrador del usuario especificado. |
| [DirectReports](connection-office365-users.md#directreports) |Devuelve los subordinados directos del usuario especificado. |
| [SearchUser](connection-office365-users.md#searchuser) |Recupera los resultados de búsqueda de los perfiles de usuario. |

### <a name="myprofile"></a>MyProfile
Obtener mi perfil: recupera el perfil del usuario actual.

#### <a name="input-properties"></a>Propiedades de entrada
Ninguna

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo | Descripción |
| --- | --- | --- |
| Departamento |string |Departamento del usuario. |
| DisplayName |string |Nombre para mostrar del usuario. |
| GivenName |string |Nombre dado del usuario. |
| Identificador |string |Id. de usuario |
| JobTitle |string |Puesto del usuario. |
| Correo |string |Id. de correo electrónico del usuario. |
| MailNickname |string |Alias del usuario. |
| Apellido |string |Apellido del usuario. |
| TelephoneNumber |string |Número de teléfono del usuario. |
| UserPrincipalName |string |Nombre principal de usuario. |
| AccountEnabled |boolean |Marca de cuenta habilitada. |

### <a name="userprofile"></a>UserProfile
Obtener perfil de usuario: recupera un perfil de usuario específico.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| Identificador |string |yes |Nombre principal de usuario o id. de correo electrónico. |

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo | Descripción |
| --- | --- | --- |
| Departamento |string |Departamento del usuario. |
| DisplayName |string |Nombre para mostrar del usuario. |
| GivenName |string |Nombre dado del usuario. |
| Identificador |string |Id. de usuario |
| JobTitle |string |Puesto del usuario. |
| Correo |string |Id. de correo electrónico del usuario. |
| MailNickname |string |Alias del usuario. |
| Apellido |string |Apellido del usuario. |
| TelephoneNumber |string |Número de teléfono del usuario. |
| UserPrincipalName |string |Nombre principal de usuario. |
| AccountEnabled |boolean |Marca de cuenta habilitada. |

### <a name="manager"></a>Manager
Obtener administrador: recupera el perfil de usuario del administrador del usuario especificado.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| Identificador |string |yes |Nombre principal de usuario o id. de correo electrónico. |

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo | Descripción |
| --- | --- | --- |
| Departamento |string |Departamento del usuario. |
| DisplayName |string |Nombre para mostrar del usuario. |
| GivenName |string |Nombre dado del usuario. |
| Identificador |string |Id. de usuario |
| JobTitle |string |Puesto del usuario. |
| Correo |string |Id. de correo electrónico del usuario. |
| MailNickname |string |Alias del usuario. |
| Apellido |string |Apellido del usuario. |
| TelephoneNumber |string |Número de teléfono del usuario. |
| UserPrincipalName |string |Nombre principal de usuario. |
| AccountEnabled |boolean |Marca de cuenta habilitada. |

### <a name="directreports"></a>DirectReports
Obtener subordinados directos: obtiene los subordinados directos.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| Identificador |string |yes |Nombre principal de usuario o id. de correo electrónico. |

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo | Descripción |
| --- | --- | --- |
| Departamento |string |Departamento del usuario. |
| DisplayName |string |Nombre para mostrar del usuario. |
| GivenName |string |Nombre dado del usuario. |
| Identificador |string |Id. de usuario |
| JobTitle |string |Puesto del usuario. |
| Correo |string |Id. de correo electrónico del usuario. |
| MailNickname |string |Alias del usuario. |
| Apellido |string |Apellido del usuario. |
| TelephoneNumber |string |Número de teléfono del usuario. |
| UserPrincipalName |string |Nombre principal de usuario. |
| AccountEnabled |boolean |Marca de cuenta habilitada. |

### <a name="searchuser"></a>SearchUser
Buscar usuarios: recupera los resultados de búsqueda de los perfiles de usuario.

#### <a name="input-properties"></a>Propiedades de entrada

| Nombre | Tipo de datos | Requerido | Descripción |
| --- | --- | --- | --- |
| searchTerm |string |no |Cadena de búsqueda. Se aplica a: nombre para mostrar, nombre dado, apellido, correo electrónico, alias de correo electrónico y nombre principal de usuario |

#### <a name="output-properties"></a>Propiedades de salida

| Nombre de la propiedad | Tipo | Descripción |
| --- | --- | --- |
| Departamento |string |Departamento del usuario. |
| DisplayName |string |Nombre para mostrar del usuario. |
| GivenName |string |Nombre dado del usuario. |
| Identificador |string |Id. de usuario |
| JobTitle |string |Puesto del usuario. |
| Correo |string |Id. de correo electrónico del usuario. |
| MailNickname |string |Alias del usuario. |
| Apellido |string |Apellido del usuario. |
| TelephoneNumber |string |Número de teléfono del usuario. |
| UserPrincipalName |string |Nombre principal de usuario. |
| AccountEnabled |boolean |Marca de cuenta habilitada. |

## <a name="helpful-links"></a>Vínculos útiles
* Consulte todas las [conexiones disponibles](../connections-list.md).
* Aprenda a [agregar conexiones](../add-manage-connections.md) a sus aplicaciones.

