---
title: Ver la tarjeta de Perfil de un contacto o usuario | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67441e506ba2715a9994f6b81cd08426e37e0fc8
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "71950919"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>Ver la tarjeta de Perfil de un contacto o usuario

Use la tarjeta de perfil para obtener información rápida sobre un contacto o un usuario. Al seleccionar un campo de contacto o de usuario en las aplicaciones controladas por modelos en Dynamics 365, como Dynamics 365 sales y Dynamics 365 Customer Service, puede encontrar información relacionada con ellos en su tarjeta de perfil. Para obtener más información acerca de las tarjetas de perfil, consulte [tarjetas de perfil en Office 365](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

> [!NOTE]
>  - La tarjeta de perfil está disponible para la entidad **contacto** y **usuario** . Para obtener más información, consulte [Habilitar la tarjeta de perfil (para administradores)](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/admin/enable-profile-card).
>  - La tarjeta de Perfil de Common Data Service no se muestra si la autenticación multifactor está activada para el servicio de Office Delve en Azure Active Directory.

## <a name="view-a-contacts-profile"></a>Ver el perfil de un contacto

1.  Vaya a **Actividades**.
2.  Seleccione una actividad existente o cree una nueva.
3.  Mantenga el mouse sobre el campo **llamada a** cuando tenga un registro de contacto. 

Puede ver los detalles del contacto insertado, que incluye la imagen del contacto, el nombre, el título y la cuenta.

4. Para ver más detalles, seleccione **Mostrar más** para expandir el perfil del contacto.
 
    > [!div class="mx-imgBorder"] 
    > ![Expandir detalles de la tarjeta de Perfil de contacto](media/profile1.png "Expandir detalles de la tarjeta de Perfil de contacto")
   
 ## <a name="view-a-users-profile"></a>Ver el perfil de un usuario
 
1.  Vaya a **cuentas**.
2.  Seleccione un registro de cuenta.
3.  Mantenga el mouse sobre el campo propietario cuando tenga un registro de usuario. Puede ver los detalles del usuario en línea.
4.  Para ver más detalles, como los mensajes de correo electrónico y los archivos compartidos con el usuario, seleccione **Mostrar más** para expandir el perfil del contacto.
 
    > [!div class="mx-imgBorder"] 
    > ![Detalles de la tarjeta de Perfil de usuario](media/profile2.png "Detalles de la tarjeta de Perfil de usuario")


 ## <a name="faqs"></a>+
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>¿Dónde puedo ver las tarjetas de perfil en Dynamics 365?
Las tarjetas de perfil pueden verse en registros de contactos y usuarios. Solo se pueden ver cuando se encuentran en una búsqueda.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>¿De dónde procede la información que se muestra en la tarjeta de perfil?
La información que se muestra en la tarjeta de Perfil de contacto se captura de Common Data Service (y no de Microsoft Exchange). Esto significa que los detalles de contacto provienen de Dynamics 365.

La información que se muestra en la tarjeta de Perfil de usuario se captura de Office 365 (Azure Active Directory). Para obtener más información, vea [tarjetas de perfil en Office 365 (sección de administración)](https://support.office.com/en-us/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>¿Cómo puedo personalizar los campos que se muestran en la tarjeta de perfil?
Actualmente, la lista de campos que se muestra en la tarjeta de perfil no está abierta para la personalización.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>¿Por qué está deshabilitada la opción **iniciar chat** en la tarjeta de perfil (atenuada)?
Las opciones **iniciar chat** y **Enviar correo electrónico** de la tarjeta de perfil abrirán las aplicaciones de correo electrónico y mensajes instantáneos predeterminadas. La opción **iniciar chat** está habilitada si la persona a la que está intentando ponerse en contacto en el mismo entorno de Azure Active Directory que usted o es un contacto federado.


  
