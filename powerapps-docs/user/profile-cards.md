---
title: Visualización de la tarjeta de perfil de un contacto o usuario | Microsoft Docs
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
ms.openlocfilehash: 276c7d3cbf95947306fab768da8af3c4c66b33e0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543372"
---
# <a name="view-the-profile-card-for-a-contact-or-user"></a>Visualización de la tarjeta de perfil de un contacto o usuario

Use la tarjeta de perfil para obtener información rápida sobre un contacto o usuario. Al seleccionar un campo de contacto o usuario en aplicaciones basadas en modelos de Dynamics 365, como Dynamics 365 Sales y Dynamics 365 Customer Service, puede encontrar información relacionada con él en su tarjeta de perfil. Para obtener más información sobre las tarjetas de perfil, vea [Tarjetas de perfil en Office 365](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

> [!NOTE]
>  - La tarjeta de perfil está disponible para las entidades **Contacto** y **Usuario**. Para obtener información, vea [Habilitar visualización de tarjetas de perfil (para administradores)](https://docs.microsoft.com/dynamics365/customer-engagement/admin/enable-profile-card).
>  - La tarjeta de perfil de Common Data Service no se muestra si la autenticación multifactor está activada para el servicio Delve de Office en Azure Active Directory.

## <a name="view-a-contacts-profile"></a>Visualización del perfil de un contacto

1.  Vaya a **Actividades**.
2.  Seleccione una actividad existente o cree una nueva.
3.  Mantenga el mouse sobre el campo **Llamar a** cuando tenga un registro de contacto. 

Puede ver detalles del contacto alineados que incluyen su imagen, nombre, título y cuenta.

4. Para ver más detalles, seleccione **Mostrar más** para expandir el perfil del contacto.
 
    > [!div class="mx-imgBorder"] 
    > ![Expansión de detalles de tarjeta de perfil de contacto](media/profile1.png "Expansión de detalles de tarjeta de perfil de contacto")
   
 ## <a name="view-a-users-profile"></a>Visualización del perfil de un usuario
 
1.  Vaya a **Cuentas**.
2.  Seleccione un registro de cuenta.
3.  Mantenga el mouse sobre el campo de propietario cuando tenga un registro de usuario. Puede ver los detalles del usuario alineados.
4.  Para ver más detalles, como mensajes de correo electrónico y archivos compartidos con el usuario, seleccione **Mostrar más** para expandir el perfil del contacto.
 
    > [!div class="mx-imgBorder"] 
    > ![Expansión de detalles de tarjeta de perfil de usuario](media/profile2.png "Expansión de detalles de tarjeta de perfil de usuario")


 ## <a name="faqs"></a>Preguntas más frecuentes
 
### <a name="where-can-i-see-profile-cards-in-dynamics-365"></a>¿Dónde puedo ver tarjetas de perfil en Dynamics 365?
Las tarjetas de perfil pueden verse en los registros de contactos y usuarios. Solo se pueden ver cuando están en una búsqueda.

### <a name="where-is-information-shown-in-the-profile-card-coming-from"></a>¿De dónde procede la información que se muestra en la tarjeta de perfil?
La información que se muestra en la tarjeta de perfil de contacto se captura de Common Data Service (y no de Microsoft Exchange). Esto significa que los detalles de contacto proceden de Dynamics 365.

La información que se muestra en la tarjeta de perfil de usuario se captura de Office 365 (Azure Active Directory). Para obtener más información, vea [Tarjetas de perfil en Office 365 (sección para administradores)](https://support.office.com/article/Profile-cards-in-Office-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501).

### <a name="how-can-i-customize-the-fields-shown-on-the-profile-card"></a>¿Cómo puedo personalizar los campos que se muestran en la tarjeta de perfil?
Actualmente, la lista de campos que se muestran en la tarjeta de perfil no está sujeta a personalización.

### <a name="why-is-the-start-chat-option-on-the-profile-card-disabled-greyed-out"></a>¿Por qué está deshabilitada (atenuada) la opción **Iniciar chat** de la tarjeta de perfil?
Las opciones **Iniciar chat** y **Enviar correo electrónico** de la tarjeta de perfil abren las aplicaciones predeterminadas de correo electrónico y mensajería instantánea. La opción **Iniciar chat** se habilita si la persona con la que intenta ponerse en contacto está en el mismo entorno de Azure Active Directory que usted o es un contacto federado.


  
