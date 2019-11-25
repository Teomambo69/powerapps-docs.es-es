---
title: Configurar un contacto para su uso en un portal | MicrosoftDocs
description: Instrucciones para agregar y configurar un contacto para usarse en un portal.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761116"
---
# <a name="configure-a-contact-for-use-on-a-portal"></a>Configurar un contacto para su uso en un portal

Tras completar la información básica para un contacto (o pedir a un usuario que rellene el formulario de suscripción en un portal), vaya hasta la pestaña de autenticación web en el formulario de contacto del portal para configurar un contacto utilizando autenticación local. Para más información sobre opciones de autenticación federadas, consulte [Establecer identidad de autenticación para un portal](set-authentication-identity.md). Para configurar un contacto para portales mediante autenticación local, siga estas instrucciones:  

1.  Escriba un **nombre de usuario**.
2.  En la cinta de opciones de comando, vaya a **Más comandos** &gt; **Cambiar contraseña**.

Complete el flujo de trabajo de cambio de contraseña y los campos requeridos se configurarán automáticamente. Cuando haya terminado, el contacto estará configurado para los portales.

## <a name="change-password-for-a-contact-from-portal-management-app"></a>Cambiar contraseña de un contacto desde la aplicación Administración del portal

1.  Abra la aplicación [Administración del portal](configure-portal.md).

2.  Vaya a **Portales** > **Contactos**, y abra el contacto para el que desea cambiar la contraseña.
    Como alternativa, también puede abrir la página **Contactos** del panel [Compartir](../manage-existing-portals.md#share). 

3.  Seleccione **Flujo de tarea** en la barra de herramientas situada en la parte superior.

    > [!div class="mx-imgBorder"]
    > ![Icono Flujo de tareas](../media/task-flow.png "Icono Flujo de tareas")

4.  Seleccione el flujo de tareas **Cambiar contraseña de contacto del portal**.

5.  En el panel **Cambiar contraseña de contacto del portal**, seleccione o crea un contacto para cambiar la contraseña y, a continuación seleccione **Siguiente**.

    > [!div class="mx-imgBorder"]
    > ![Seleccione un contacto para cambiar la contraseña](../media/change-password-select-contact.png "Seleccione un contacto para cambiar la contraseña")

6.  En el campo **Nueva contraseña**, escriba una nueva contraseña y, a continuación seleccione **Siguiente**.

    > [!div class="mx-imgBorder"]
    > ![Especifique una contraseña nueva para el contacto](../media/change-password-new-password.png "Especifique una contraseña nueva para el contacto")

    Si no escribe una contraseña y selecciona **Siguiente**, se le preguntarán si desea quitar la contraseña del contacto seleccionado.

    > [!div class="mx-imgBorder"]
    > ![Quitar contraseña nueva para el contacto](../media/change-password-remove-password.png "Quitar contraseña nueva para el contacto")

7.  Después de realizar los cambios, seleccione **Hecho**.


### <a name="see-also"></a>Vea también
[Invitar a contactos a los portales](invite-contacts.md)  
[Establecer identidad de autenticación para un portal](set-authentication-identity.md)  