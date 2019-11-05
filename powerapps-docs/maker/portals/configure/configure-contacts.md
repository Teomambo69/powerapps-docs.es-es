---
title: Configuración de un contacto para su uso en un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar un contacto que se usará en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4a8c70304385007c132f2c13ec0ddca4b68e2231
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553196"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>Configuración de un contacto para su uso en un portal

Después de rellenar la información básica de un contacto (o hacer que un usuario rellene el formulario de registro en un portal), vaya a la pestaña autenticación Web del formulario de contacto del portal para configurar un contacto mediante la autenticación local. Para obtener más información sobre las opciones de autenticación federada, consulte [set Authentication Identity for a portal](set-authentication-identity.md). Para configurar un contacto para portales mediante la autenticación local, siga estas instrucciones:  

1.  Escriba un **nombre de usuario**.
2.  En la cinta de comandos, vaya a **más comandos** &gt; **Cambiar contraseña**.

Complete el flujo de trabajo cambiar contraseña y los campos necesarios se configurarán automáticamente. Cuando lo haya hecho, el contacto se configurará para los portales.

## <a name="change-password-for-a-contact-from-portal-management-app"></a>Cambiar la contraseña de un contacto desde la aplicación de administración del portal

1.  Abra la [aplicación administración del portal](configure-portal.md).

2.  Vaya a **portales** > **contactos**y abra el contacto para el que desea cambiar la contraseña.
    Como alternativa, también puede abrir la página **contactos** desde el panel [compartir](../manage-existing-portals.md#share) . 

3.  Seleccione **flujo de tareas** en la barra de herramientas de la parte superior.

    > [!div class="mx-imgBorder"]
    > ![Icono flujo de tareas](../media/task-flow.png "Icono flujo de tareas")

4.  Seleccione el flujo **de tareas cambiar contraseña para contacto del portal** .

5.  En el panel **Cambiar contraseña para contacto del portal** , seleccione o cree un contacto para cambiar la contraseña y, a continuación, seleccione **siguiente**.

    > [!div class="mx-imgBorder"]
    > ![Seleccionar un contacto para cambiar la contraseña](../media/change-password-select-contact.png "Seleccionar un contacto para cambiar la contraseña")

6.  En el campo **nueva contraseña** , escriba una contraseña nueva y, a continuación, seleccione **siguiente**.

    > [!div class="mx-imgBorder"]
    > ![Escriba la nueva contraseña del contacto](../media/change-password-new-password.png "Escriba la nueva contraseña del contacto")

    Si no escribe una contraseña y selecciona **siguiente**, se le preguntará si desea quitar la contraseña para el contacto seleccionado.

    > [!div class="mx-imgBorder"]
    > ![Quitar la contraseña del contacto](../media/change-password-remove-password.png "Quitar la contraseña del contacto")

7.  Después de realizar los cambios, seleccione **listo**.


### <a name="see-also"></a>Vea también
[Invitar a los contactos a los portales](invite-contacts.md)  
[Establecimiento de la identidad de autenticación para un portal](set-authentication-identity.md)  