---
title: Invitar contactos al portal | MicrosoftDocs
description: Instrucciones para crear y configurar invitaciones en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 631f17d9764fbfc209fd193ddabe4882f8ad8042
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761107"
---
# <a name="invite-contacts-to-your-portals"></a>Invitar a contactos a los portales

Use la característica de invitación a los portales para invitar a contactos a su portal a través de correo electrónico automatizado creado en el sistema Common Data Service. Los invitados recibirán un correo electrónico, completamente personalizable por usted, con un vínculo al portal y un código de invitación. Este código puede usarse para tener acceso especial configurado por usted. Con esta característica tiene la capacidad de:

- Enviar invitaciones individuales o de grupo
-   Especificar una fecha de vencimiento si lo desea
-   Especificar un usuario o contacto del portal como invitador si lo desea
-   Asignar automáticamente los contactos invitados a una cuenta tras canjear la invitación
-   Ejecutar automáticamente un flujo de trabajo tras canjear la invitación
-   Asignar automáticamente los contactos invitados a uno o vario roles web tras el canje

El canje de invitación se puede conseguir usando cualquier de las muchas opciones de autenticación. Para documentación respecto a la autenticación del portal, vea [Establecer identidad de autenticación para un portal](set-authentication-identity.md) y elija el modelo aplicable a la versión y la configuración del portal. El usuario adoptará los valores proporcionados por el administrador tras el canje. Se creará una actividad de canje de invitación para la invitación y el contacto.

Las invitaciones se envían a través del flujo de trabajo **Enviar invitación**. De forma predeterminada, el flujo de trabajo crea un correo electrónico con un mensaje genérico y lo envía a la dirección de correo electrónico principal del contacto invitado. El flujo de trabajo **Enviar invitación** contiene una plantilla de correo electrónico que debe modificarse para contener un mensaje específico para el portal y el hipervínculo correcto a la página **Canje de invitación del portal**.

Para editar el flujo de trabajo de plantilla de correo electrónico **Enviar invitación**, búsquelo y desactívelo. Una vez desactivado, modifique la plantilla de correo electrónico para enviar el mensaje que desea y proporcionar un vínculo a la página **Canje de invitación del portal** del portal.

> [!NOTE]
> Se envía la invitación solo para el mensaje principal (emailaddress1) del contacto. La invitación no se enviará al correo electrónico secundario (emailaddress2) o correo electrónico alternativo (emailaddress3) del registro de contacto.

## <a name="create-invitations-from-portal-management-app"></a>Crear invitaciones desde la aplicación Administración del portal

1.  Abra la aplicación [Administración del portal](configure-portal.md).

2.  Vaya a **Portales** > **Contactos**.
    Como alternativa, también puede abrir la página **Contactos** del panel [Compartir](../manage-existing-portals.md#share). 

3.  Seleccione un contacto o abra el registro de contacto para ser invitado.

4.  En la barra de comandos, seleccione **Crear invitación**.

5.  En la página **Invitación** , escriba los valores apropiados en los campos. Más información: [Atributos de invitación](#invitation-attributes)

6.  Seleccione **Guardar**.

7.  En la barra de comandos, seleccione **Flujo** > **Enviar invitación**.

    > [!div class="mx-imgBorder"]
    > ![Ejecutar flujo de trabajo de invitación](../media/send-invitation-portal-app.png "Ejecutar flujo de trabajo de invitación")

8.  En la ventana de confirmación, seleccione **Aceptar**. La invitación se enviará al contacto seleccionado.

    > [!div class="mx-imgBorder"]
    > ![Confirmación para enviar una invitación](../media/confirm-invitation-portal-app.png "Confirmación para enviar una invitación")

### <a name="send-multiple-invitations"></a>Enviar varias invitaciones

Puede crear invitaciones para sus contactos y después enviar todas las invitaciones al mismo tiempo.

1.  Cree invitaciones para contactos necesarios y vaya a **Portales** > **Invitaciones**.

2.  Seleccione las invitaciones creadas.

3.  En la barra de comandos, seleccione **Flujo** > **Enviar invitación**.

    > [!div class="mx-imgBorder"]
    > ![Ejecutar flujo de trabajo de invitación](../media/send-invitation-portal-app.png "Ejecutar flujo de trabajo de invitación")

4.  En la ventana de confirmación, seleccione **Aceptar**. Las invitaciones se enviarán a los contactos seleccionados.

    > [!div class="mx-imgBorder"]
    > ![Confirmación para enviar varias invitaciones](../media/confirm-multiple-invites-portal-app.png "Confirmación para enviar varias invitaciones")

## <a name="invitation-attributes"></a>Atributos de invitación

La tabla de abajo explica los atributos de la página **Invitación**:


|  Nombre    |    Descripción    |
|-------|------------|
|                 Nombre                  |                                                                                                      Un nombre descriptivo para ayudar a reconocer la invitación.                                                                                                      |
|                 Tipo                  |                                             **Único** o **Grupo**. Único permitirá invitar solo a un contacto y un solo canje. Grupo permite invitar a varios contactos y varios canjes.                                              |
|             Propietario/remitente              | El usuario que sea el remitente del correo electrónico al enviar la invitación. Esto se puede reemplazar en el flujo de trabajo **Enviar invitación** si el correo electrónico creado ya contiene alguien en el campo De. |
|            Código de invitación            |                                                                 Un código único para la invitación que sólo el invitado conocerá. Se genera automáticamente al crear una nueva invitación.                                                                  |
|              Fecha de expiración              |                                                                                     Fecha que representa cuándo la invitación dejará de ser válida para canje. Opcional.                                                                                     |
|                Invitador                |                                                                                               Puede usarse cuando un contacto sea el remitente de la invitación. Opcional.                                                                                                |
|          Contacto invitado           |                                                                                                             El contacto o contactos que se invitan a un portal.                                                                                                              |
|           Asignar a cuenta           |                                                                        Un registro de cuenta que se asociará como cliente primario del contacto cuando se canjee la invitación. Opcional.                                                                        |
| Ejecutar flujo de trabajo al canjear contacto |                                                         Un proceso de flujo de trabajo que se ejecutará cuando se canjee la invitación. El flujo de trabajo se pasará al contacto que canjea como entidad principal. Opcional.                                                          |
|          Asignar a roles web          |                                                                               Un conjunto de roles de red que se asociará al contacto que canjea cuando se cuando se canjee la invitación. Opcional.                                                                                |
|          Contacto canjeado          |                                                                                                   El contacto o contactos que han canjeado correctamente la invitación.                                                                                                   |
|      Canjes máximos permitidos      |                                                                                   El número de veces que la invitación pueden ser canjeada. Disponible solo para invitaciones de tipo Grupo.                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>Vea también

[Configurar un contacto para su uso en un portal](configure-contacts.md)  
[Establecer identidad de autenticación para un portal](set-authentication-identity.md)  
