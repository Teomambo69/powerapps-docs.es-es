---
title: "Uso compartido de una aplicación | Microsoft Docs"
description: "Comparta su aplicación proporcionando a otros usuarios permiso para ejecutarla o modificarla"
services: 
suite: powerapps
documentationcenter: na
author: linhtranms
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/28/2016
ms.author: litran
ms.openlocfilehash: 1d32873009c337a835a047df38b9ef18d5bf2064
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="share-an-app-in-powerapps"></a>Compartir una aplicación en PowerApps
Es estupendo crear aplicaciones que satisfagan sus propias necesidades empresariales, pero lo realmente estupendo de PowerApps es que puede compartir las aplicaciones con otras personas. En este tema, obtendrá información sobre cómo compartir aplicaciones con usuarios o grupos de seguridad específicos, o cómo compartirlas con toda la organización.

## <a name="open-the-share-app-screen"></a>Abrir la pantalla para compartir aplicaciones
Para compartir una aplicación, debe abrir powerapps.com. Ya no se pueden compartir aplicaciones en PowerApps Studio ni PowerApps Mobile.

**Desde PowerApps Studio**

* Opción 1: en el menú **Archivo**, pulse o haga clic en **Compartir**.
  
    ![Archivo y Compartir](./media/share-app/studio-share.png)
* Opción 2: en el menú **Archivo**, pulse o haga clic en **Abrir** y, luego, pulse o haga clic en el icono para compartir de una aplicación.
  
    ![Puntos suspensivos y Compartir](./media/share-app/studio-share-icon.png)

**Desde [powerapps.com](http://web.powerapps.com)**

* En la barra de navegación izquierda, pulse o haga clic en **Aplicaciones**, pulse o haga clic en los puntos suspensivos (...) y, luego, en **Compartir**.
  
   ![Puntos suspensivos en el portal](./media/share-app/portal-share.png)

## <a name="share-an-app"></a>Compartir una aplicación
Desde aquí puede compartir una aplicación siguiendo estos pasos.

1. Especifique los nombres de uno o varios usuarios o grupos de seguridad en Azure Active Directory o especifique que desea compartir la aplicación con toda la organización. Tenga en cuenta que solo puede compartir la aplicación con toda la organización con el permiso **Usuario**.
   
    ![Especificar usuarios en powerapps.com](./media/share-app/portal-users.png)
2. Especifique el nivel de permisos:
   
   * **Usuario**: los usuarios o grupos pueden ejecutar la aplicación, pero no compartirla.
   * **Colaborador**: los usuarios o grupos pueden ejecutar la aplicación, personalizarla y compartir la versión personalizada con otros usuarios.
     
       ![Portal para compartir la aplicación](./media/share-app/portal-permissions.png)
3. Haga clic o pulse en **Guardar**.

Para cambiar los permisos de un usuario o grupo, repita el paso 1 de este procedimiento y especifique una opción distinta en la lista de permisos para dicho usuario o grupo. Para quitar todos los permisos de un usuario o grupo, haga clic o pulse en el icono **x** de ese usuario o grupo.

### <a name="send-email-notification"></a>Enviar notificación por correo electrónico
Cuando comparte una aplicación, puede seleccionar si desea notificar a los usuarios o al grupo de seguridad a través del correo electrónico. Si elige esta opción, se enviará un mensaje de correo electrónico para notificar a los usuarios o grupos de seguridad. El mensaje de correo electrónico contiene un vínculo con el que pueden acceder a la aplicación. Si es necesario, se pide a los usuarios se suscriban a PowerApps y lo instalen.

Tenga en cuenta que se envían diferentes plantillas de correo electrónico según el permiso con el que decida compartir la aplicación. Cuando se comparte la aplicación con el permiso **Usuario**, el mensaje de correo electrónico contiene el vínculo para ejecutar la aplicación. Cuando se comparte la aplicación con el permiso **Colaborador**, el mensaje de correo electrónico contiene el vínculo para editar la aplicación en PowerApps Studio o para ejecutarla.

### <a name="how-do-my-users-see-the-app-i-shared"></a>¿Cómo ven mis usuarios la aplicación que he compartido?
Después de compartir una aplicación con uno o varios usuarios o grupos de seguridad, la forma en que estos ven la aplicación depende del permiso con el que la haya compartido.

##### <a name="if-you-shared-app-with-user-permission"></a>Si ha compartido la aplicación con el permiso *Usuario*
Las personas con las que haya compartido la aplicación recibirán una notificación por correo electrónico si ha seleccionado esa casilla en la pantalla para compartir aplicaciones. En el mensaje de correo electrónico, pueden pulsar o hacer clic en un vínculo para ejecutar la aplicación en [Dynamics 365](http://home.dynamics.com). Pronto se admitirán vínculos universales, lo que implica que si tiene PowerApps Studio o PowerApps Mobile instalados, la aplicación se abrirá en ese programa.

Los usuarios también pueden ver la aplicación en AppSource en [Dynamics 365](http://home.dynamics.com) (por ejemplo, si no ha enviado un mensaje de correo electrónico). [Obtenga más información](app-source.md) sobre cómo pueden obtener los usuarios aplicaciones mediante AppSource.

##### <a name="if-you-shared-an-app-with-contributor-permission"></a>Si ha compartido la aplicación con el permiso *Colaborador*
Las personas con las que haya compartido la aplicación recibirán una notificación por correo electrónico si ha seleccionado esa casilla en la pantalla para compartir aplicaciones. En el mensaje de correo electrónico, pueden pulsar o hacer clic en un vínculo que abrirá la aplicación directamente para su edición mediante PowerApps Studio para la Web. También hay un vínculo para ejecutar la aplicación en [Dynamics 365](http://home.dynamics.com). Pronto se admitirán vínculos universales, lo que implica que si tiene PowerApps Studio o PowerApps Mobile instalados, la aplicación se abrirá en ese programa.

Los usuarios también pueden ver la aplicación en [powerapps.com](http://web.powerapps.com) (por ejemplo, si no ha enviado un mensaje de correo electrónico). Este es el lugar en el que los creadores de aplicaciones pueden examinar todas las aplicaciones que han creado o que han compartido con ellos con el permiso **Colaborador**. En cambio, [Dynamics 365](http://home.dynamics.com) es donde los usuarios pueden ejecutar rápidamente aplicaciones de PowerApps y otras aplicaciones empresariales.

## <a name="other-things-to-know"></a>Otros aspectos que debe conocer
* Para compartir una aplicación, debe guardarla en la nube, no de forma local.
* Antes de compartir una aplicación, tenga en cuenta con qué usuarios y grupos de seguridad la va a compartir y el rol que desea que tengan: usuario o colaborador. Si comparte una aplicación con un grupo, los miembros de ese grupo y cualquier persona que se una a él tienen los permisos que especifique. Cualquier persona que abandone el grupo pierde los permisos a menos que sean miembros de un grupo diferente que tenga acceso o que especifique explícitamente permisos para ellos.
* Todos los miembros de un grupo tienen los mismos permisos para una aplicación que el grupo general. Sin embargo, puede especificar mayores permisos para uno o varios miembros de ese grupo para permitirles mayor acceso. Por ejemplo, puede compartir una aplicación con un grupo de seguridad A con permiso Usuario. Todos los miembros del grupo de seguridad A podrán ejecutar la aplicación. Ahora suponga que comparte la aplicación con el usuario B, que forma parte del grupo de seguridad A, con permiso Colaborador. El usuario B ahora puede editar la aplicación, mientras que todos los demás miembros del grupo de seguridad A solo pueden usarla. Si especifica menos permisos para uno o varios miembros de un grupo, seguirán teniendo todos los permisos concedidos al grupo global.
* Puede compartir una aplicación con toda la organización, pero piense detenidamente si todos los usuarios necesitan acceso a la aplicación.
* Tenga en cuenta que los cambios que realice en una aplicación compartida llegarán a los usuarios con los que la compartió tan pronto como guarde los cambios. Esto puede ser bueno si mejora la aplicación, pero también puede afectar a otros usuarios si quita o cambia de forma significativa las características.
* Antes de compartir una aplicación, asígnele un nombre significativo y una descripción para que los usuarios sepan de qué trata la aplicación y puedan elegirla fácilmente de una lista. En el menú **Archivo** de PowerApps Studio, pulse o haga clic en **Configuración de la aplicación** y escriba una descripción.
  
  ![Descripción de la aplicación](./media/share-app/description.png)

### <a name="app-sharing-and-the-resources-the-app-uses"></a>Compartir una aplicación y los recursos que usa
La mayoría de las aplicaciones se basan en al menos uno de estos tipos de recursos:

* una conexión a un origen de datos
* una puerta de enlace de datos local
* un conector personalizado
* un libro de Excel u otro servicio
* un flujo

Los usuarios y colaboradores necesitan permisos para todas las conexiones de datos y puertas de enlace que utilice la aplicación. Algunos permisos vienen implícitos en la aplicación, pero otros se deben conceder explícitamente. Para más información, consulte [Share app resources](share-app-resources.md) (Uso compartido de recursos de la aplicación).

Cuando comparta una aplicación que use Common Data Service, tenga en cuenta la barra de información que indica que debe compartir el permiso de tiempo de ejecución para Common Data Service por separado. Si no tiene permiso para hacerlo, póngase en contacto con su administrador de entorno. [Obtenga más información](database-security.md) sobre la seguridad para Common Data Service.

![Recursos de la aplicación al compartirla](./media/share-app/app-sharing-resources.png)

### <a name="what-isnt-supported"></a>¿Qué es lo que no se admite?
* Puede compartir la aplicación con un grupo de seguridad, pero no con un grupo de distribución.
* Puede compartir aplicaciones con usuarios de su organización, pero no con los usuarios de otro espacio empresarial.
* Puede compartir una aplicación desde [powerapps.com](http://web.powerapps.com), pero no desde PowerApps Studio. (Pulse o haga clic en un icono para compartir en PowerApps Studio para abrir [powerapps.com](http://web.powerapps.com)).
* Puede volver a compartir una aplicación si tiene permiso Colaborador (no Usuario) para esa aplicación.

