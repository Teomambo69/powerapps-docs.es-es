---
title: Uso compartido de una aplicación | Microsoft Docs
description: Comparta su aplicación proporcionando a otros usuarios permiso para ejecutarla o modificarla
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: c87f0e644668e9b9804b001560402972fd3d4531
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "32329143"
---
# <a name="share-an-app-in-powerapps"></a>Compartir una aplicación en PowerApps
Es estupendo crear aplicaciones que satisfagan sus propias necesidades empresariales, pero lo realmente estupendo de PowerApps es que puede compartir las aplicaciones con otras personas. En este tema, obtendrá información sobre cómo compartir aplicaciones con usuarios o grupos de seguridad específicos, o cómo compartirlas con toda la organización.

## <a name="specify-an-app"></a>Especificar una aplicación
1. Inicie sesión en PowerApps y después pulse o haga clic en **Aplicaciones** cerca del borde izquierdo.

    ![Mostrar la lista de aplicaciones](./media/share-app/file-apps.png)

1. Haga clic o pulse en los puntos suspensivos (...) de la aplicación que quiera compartir y después pulse o haga clic en **Compartir**.

    ![Abrir la pantalla Compartir](./media/share-app/ellipsis-share.png)

## <a name="share-an-app"></a>Compartir una aplicación
1. Especifique con qué usuarios o grupos de seguridad de Azure Active Directory quiere compartir la aplicación y si quiere enviar un correo electrónico de notificación a esos usuarios.

    También se puede compartir la aplicación con toda la organización para que la puedan ejecutar, pero no podrán modificarla ni compartirla.

    ![Especificar usuarios](./media/share-app/share-list.png)

1. Especifique el nivel de permisos y haga clic o pulse en **Guardar**.

    * **Puede usar**: los usuarios o grupos pueden ejecutar la aplicación pero no compartirla.
    * **Puede editar**: los usuarios o grupos pueden ejecutar la aplicación, personalizarla y compartir la versión personalizada con otros usuarios.

        ![Especificar permisos](./media/share-app/edit-use.png)

Para cambiar los permisos de un usuario o grupo, repita el paso 1 de este procedimiento y especifique una opción distinta en la lista de permisos para dicho usuario o grupo. Para quitar todos los permisos de un usuario o grupo, haga clic o pulse en el icono **x** de ese usuario o grupo.

### <a name="send-email-notification"></a>Enviar notificación por correo electrónico
Cuando comparte una aplicación, puede seleccionar si desea notificar a los usuarios o al grupo de seguridad a través del correo electrónico. Si elige esta opción, se enviará un mensaje de correo electrónico para notificar a los usuarios o grupos de seguridad. El mensaje de correo electrónico contiene un vínculo con el que pueden acceder a la aplicación. Si es necesario, se le pedirá a los usuarios que se suscriban a PowerApps.

La notificación contiene otro tipo de vínculo en función del permiso que se asigne:

- Cuando se comparte la aplicación con el permiso **Puede usar**, el mensaje de correo electrónico contiene el vínculo para ejecutar la aplicación.
- Cuando se comparte la aplicación con el permiso **Puede editar**, el correo electrónico contiene el vínculo para ejecutar o editar la aplicación.

### <a name="how-do-my-users-see-the-app-i-shared"></a>¿Cómo ven mis usuarios la aplicación que he compartido?
Después de compartir una aplicación con uno o varios usuarios o grupos de seguridad, la forma en que estos ven la aplicación depende del permiso con el que la haya compartido.

##### <a name="if-you-shared-an-app-with-can-use-permission"></a>Si ha compartido una aplicación con el permiso *Puede usar*
Las personas con las que haya compartido la aplicación recibirán una notificación por correo electrónico si ha seleccionado esa casilla en la pantalla para compartir aplicaciones. En el mensaje de correo electrónico, pueden pulsar o hacer clic en un vínculo para ejecutar la aplicación en [Dynamics 365](http://home.dynamics.com). Pronto se admitirán vínculos universales, lo que implica que si tiene PowerApps Studio o PowerApps Mobile instalados, la aplicación se abrirá en ese programa.

Los usuarios también pueden ver la aplicación en AppSource en [Dynamics 365](http://home.dynamics.com) (por ejemplo, si no ha enviado un mensaje de correo electrónico). [Obtenga más información](../../user/app-source.md) sobre cómo pueden obtener los usuarios aplicaciones mediante AppSource.

##### <a name="if-you-shared-an-app-with-can-edit-permission"></a>Si ha compartido una aplicación con el permiso *Puede editar*
Las personas con las que haya compartido la aplicación recibirán una notificación por correo electrónico si ha seleccionado esa casilla en la pantalla para compartir aplicaciones. En el mensaje de correo electrónico, pueden pulsar o hacer clic en un vínculo que abrirá la aplicación directamente para la edición mediante PowerApps Studio. También hay un vínculo para ejecutar la aplicación en [Dynamics 365](http://home.dynamics.com). Pronto se admitirán vínculos universales, lo que implica que si tiene instalado PowerApps Studio o PowerApps Mobile, la aplicación se abrirá en ese programa.

Los usuarios también pueden ver la aplicación en [powerapps.com](http://web.powerapps.com) (por ejemplo, si no se ha enviado un correo electrónico). Este es el lugar en el que los creadores de aplicaciones pueden examinar todas las aplicaciones que han creado o que han compartido con ellos con el permiso **Colaborador**. En cambio, [Dynamics 365](http://home.dynamics.com) es donde los usuarios pueden ejecutar rápidamente aplicaciones de PowerApps y otras aplicaciones empresariales.

## <a name="other-things-to-know"></a>Otros aspectos que debe conocer
* Para compartir una aplicación, debe guardarla en la nube, no de forma local.
* Antes de compartir una aplicación, tenga en cuenta con qué usuarios y grupos de seguridad la va a compartir y el rol que quiere que tengan: **Puede editar** o **Puede usar**. Si comparte una aplicación con un grupo, los miembros de ese grupo y cualquiera que se una a él tendrán los permisos que especifique. Cualquier persona que abandone el grupo pierde los permisos a menos que sean miembros de un grupo diferente que tenga acceso o que especifique explícitamente permisos para ellos.
* Todos los miembros de un grupo tienen los mismos permisos para una aplicación que el grupo general. Sin embargo, puede especificar mayores permisos para uno o varios miembros de ese grupo para permitirles mayor acceso. Por ejemplo, puede asignar al Grupo de seguridad A el permiso **Puede usar**, pero también asignar al Usuario B, que pertenece a ese grupo, el permiso **Puede editar**. Todos los miembros del grupo de seguridad pueden ejecutar la aplicación, pero solo el usuario B puede modificarla. Si se asigna al Grupo de seguridad A el permiso **Puede editar** y al Usuario B el permiso **Puede usar**, ese usuario puede seguir editando la aplicación.
* Puede compartir una aplicación con toda la organización, pero piense detenidamente si todos los usuarios necesitan acceso a la aplicación.
* Tenga en cuenta que los cambios que realice en una aplicación compartida llegarán a los usuarios con los que la compartió tan pronto como guarde los cambios. Si la aplicación se mejora, todos los usuarios se benefician. Si se interrumpe la aplicación, todos los usuarios se ven afectados.
* Antes de compartir una aplicación, asígnele un nombre significativo y una descripción para que los usuarios sepan de qué trata la aplicación y puedan elegirla fácilmente de una lista. En el menú **Archivo** de PowerApps Studio, pulse o haga clic en **Configuración de la aplicación** y escriba una descripción.

### <a name="app-sharing-and-the-resources-the-app-uses"></a>Compartir una aplicación y los recursos que usa
La mayoría de las aplicaciones se basan en al menos uno de estos tipos de recursos:

* Una conexión a un origen de datos
* Una puerta de enlace de datos local
* Un conector personalizado
* Un libro de Excel u otro servicio
* Un flujo

Los usuarios y colaboradores necesitan permisos para todas las conexiones de datos y puertas de enlace que utilice la aplicación. Algunos permisos vienen implícitos en la aplicación, pero otros se deben conceder explícitamente. Para más información, consulte [Share app resources](share-app-resources.md) (Uso compartido de recursos de la aplicación).

Cuando comparta una aplicación que usa una versión anterior de Common Data Service, debe compartir el permiso de tiempo de ejecución para Common Data Service por separado. Si no tiene permiso para hacerlo, póngase en contacto con su administrador de entorno. Cuando comparta una aplicación que usa la versión más reciente de Common Data Service, debe crear un rol personalizado y asignarlo a los usuarios. [Obtenga más información](../../administrator/database-security.md) sobre la seguridad para Common Data Service.

### <a name="what-isnt-supported"></a>¿Qué es lo que no se admite?
* Puede compartir la aplicación con un grupo de seguridad, pero no con un grupo de distribución.
* Puede compartir aplicaciones con usuarios de su organización, pero no con los usuarios de otro espacio empresarial.
* Puede volver a compartir una aplicación si tiene el permiso **Puede editar** (no **Puede usar**) para esa aplicación.
