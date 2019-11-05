---
title: Invitación de contactos al portal | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552230"
---
# <a name="invite-contacts-to-your-portals"></a>Invitar a los contactos a los portales

Use la característica invitación de portales para invitar a los contactos a su portal a través de correos electrónicos automatizados creados en el Common Data Service. Las personas a las que invite reciben un correo electrónico, totalmente personalizable, con un vínculo al portal y un código de invitación. Este código se puede usar para obtener acceso especial configurado por el usuario. Con esta característica tiene la capacidad de:

- Enviar invitaciones individuales o de grupo
-   Especifique una fecha de expiración si lo desea
-   Especifique un contacto de usuario o de portal como el invitador si lo desea
-   Asignar automáticamente los contactos invitados a una cuenta tras el canje de invitación
-   Ejecutar automáticamente un flujo de trabajo al canje de invitación
-   Asignar automáticamente los contactos invitados a un rol Web tras el canje

El canje de invitación se puede realizar con cualquiera de nuestras muchas opciones de autenticación. Para obtener documentación sobre la autenticación del portal, consulte configuración [de la identidad de autenticación para un portal](set-authentication-identity.md) y elección del modelo aplicable a la configuración y la versión del portal. El usuario adoptará la configuración proporcionada por el administrador tras el canje. Se creará una actividad invite Valor_de_rescate para la invitación y el contacto.

Las invitaciones se envían mediante el flujo de trabajo **Enviar invitación** . De forma predeterminada, el flujo de trabajo crea un correo electrónico con un mensaje genérico y lo envía a la dirección de correo electrónico principal del contacto invitado. El flujo de trabajo de **envío de invitación** contiene una plantilla de correo electrónico que deberá editarse para que contenga un mensaje específico para el portal y el hipervínculo correcto a la página de **canje de invitación**del portal.

Para editar la plantilla de correo electrónico de flujo de trabajo **Enviar invitación** , búsquela y desactívelo. Una vez desactivada, edite la plantilla de correo electrónico para enviar el mensaje que quiera y proporcione un vínculo a la **Página invite canje** del portal.

> [!NOTE]
> La invitación se envía solo al correo electrónico principal (emailaddress1) del contacto. La invitación no se enviará al correo electrónico secundario (emailaddress2) o al correo electrónico alternativo (emailaddress3) del registro de contacto.

## <a name="create-invitations-from-portal-management-app"></a>Crear invitaciones desde la aplicación de administración del portal

1.  Abra la [aplicación administración del portal](configure-portal.md).

2.  Vaya a **portales** > **contactos**.
    Como alternativa, también puede abrir la página **contactos** desde el panel [compartir](../manage-existing-portals.md#share) . 

3.  Seleccione un contacto o abra el registro de contacto que se va a invitar.

4.  En la barra de comandos, seleccione **crear invitación**.

5.  En la página **invitación** , escriba los valores adecuados en los campos. Más información: [atributos de invitación](#invitation-attributes)

6.  Seleccione **Guardar**.

7.  En la barra de comandos, seleccione **Flow** > **Enviar invitación**.

    > [!div class="mx-imgBorder"]
    > ![Enviar flujo de trabajo de invitación](../media/send-invitation-portal-app.png "Enviar flujo de trabajo de invitación")

8.  En la ventana de confirmación, haga clic en **Aceptar**. La invitación se enviará al contacto seleccionado.

    > [!div class="mx-imgBorder"]
    > ![Confirmación para enviar una invitación](../media/confirm-invitation-portal-app.png "Confirmación para enviar una invitación")

### <a name="send-multiple-invitations"></a>Enviar varias invitaciones

Puede crear invitaciones para sus contactos y, a continuación, enviar todas las invitaciones a la vez.

1.  Cree invitaciones para los contactos necesarios y, a continuación, vaya a **portales** > **invitaciones**.

2.  Seleccione las invitaciones creadas.

3.  En la barra de comandos, seleccione **Flow** > **Enviar invitación**.

    > [!div class="mx-imgBorder"]
    > ![Enviar flujo de trabajo de invitación](../media/send-invitation-portal-app.png "Enviar flujo de trabajo de invitación")

4.  En la ventana de confirmación, haga clic en **Aceptar**. Las invitaciones se enviarán a los contactos seleccionados.

    > [!div class="mx-imgBorder"]
    > ![Confirmación para enviar varias invitaciones](../media/confirm-multiple-invites-portal-app.png "Confirmación para enviar varias invitaciones")

## <a name="invitation-attributes"></a>Atributos de invitación

En la tabla siguiente se explican los atributos de la página **invitación** :


|  Nombre    |    Descripción    |
|-------|------------|
|                 Nombre                  |                                                                                                      Un nombre descriptivo para ayudar a reconocer la invitación.                                                                                                      |
|                 Tipo                  |                                             **Único** o **Grupo**. Single solo permitirá invitar a un contacto y solo a un canje. Grupo permite que se inviten varios contactos y varios canjes.                                              |
|             Propietario/remitente              | Usuario que será el remitente del correo electrónico cuando se envíe la invitación. Esto se puede invalidar en el flujo de trabajo **Enviar invitación** si el correo electrónico creado ya contiene un usuario en el campo de. |
|            Código de invitación            |                                                                 Un código único para la invitación que solo conocerá el invitado. Esto se genera automáticamente al crear una nueva invitación.                                                                  |
|              Fecha de expiración              |                                                                                     Fecha que representa el momento en que la invitación dejará de ser válida para el canje. Opcional.                                                                                     |
|                Invitador                |                                                                                               Se puede usar cuando un contacto es el remitente de la invitación. Opcional.                                                                                                |
|          Contactos (s) invitados           |                                                                                                             Los contactos a los que se va a invitar a un portal.                                                                                                              |
|           Asignar a cuenta           |                                                                        Un registro de cuenta que se va a asociar como el cliente primario del contacto de canje cuando se canjea la invitación. Opcional.                                                                        |
| Ejecutar flujo de trabajo al canjear contacto |                                                         Proceso de flujo de trabajo que se va a ejecutar cuando se canjea la invitación. Se pasará al flujo de trabajo el contacto de canje como entidad principal. Opcional.                                                          |
|          Asignar a roles Web          |                                                                               Conjunto de roles web que se van a asociar al contacto de canje cuando se canjea la invitación. Opcional.                                                                                |
|          Contactos canjeados          |                                                                                                   Los contactos que han canjeado correctamente la invitación.                                                                                                   |
|      Máximo de canjes permitidos      |                                                                                   El número de veces que se puede canjear la invitación. Solo está disponible para invitaciones de tipo de grupo.                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>Vea también

[Configuración de un contacto para su uso en un portal](configure-contacts.md)  
[Establecimiento de la identidad de autenticación para un portal](set-authentication-identity.md)  
