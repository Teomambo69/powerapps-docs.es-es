---
title: Envío de una notificación push | Microsoft Docs
description: Aprenda a enviar notificaciones push nativas a una aplicación en PowerApps.
author: kavishi
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/08/2017
ms.author: kaagar
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 22dfcb085c2de4aabd849e0a1fedc8a231f0e55f
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71987375"
ms.PowerAppsDecimalTransform: true
---
# <a name="send-a-push-notification-in-powerapps"></a>Envío de una notificación push en PowerApps
Las notificaciones push se utilizan en aplicaciones para dispositivos móviles en escenarios tanto empresariales como de consumo para interactuar con los usuarios de las aplicaciones y les ayuda a dar prioridad a las tareas clave. En PowerApps, se pueden enviar notificaciones mediante el conector PowerApps Notification. Puede enviarse notificaciones push nativas a cualquier aplicación que se cree en PowerApps. Está previsto agregar más tipos de notificación en el futuro.

![Ejemplo de cómo es una notificación push](./media/add-notifications/pic1-notification-screenshot.png)

Las notificaciones push se agregan a aplicaciones en los siguientes casos:

* Los usuarios necesitan conocer la información inmediatamente.
* Los usuarios deben completar tareas importantes mediante el uso de la aplicación en un contexto cargado previamente.
* Desea ponerse en contacto a los usuarios en un intervalo específico o necesita que los usuarios interactúen con la aplicación en un contexto concreto.

> [!NOTE]
> Para recibir notificaciones push, cada usuario debe haber abierto una vez la aplicación en PowerApps Mobile, o haber recibido de AppSource en [Dynamics 365](https://home.dynamics.com/).

## <a name="before-you-start"></a>Antes de comenzar
En una aplicación en la que tenga permiso de **colaborador**, agregue una conexión de PowerApps Notification. Si no tiene una aplicación, puede [crearla rápidamente a partir de una plantilla](get-started-test-drive.md), y tendrá el permiso necesario de forma predeterminada. Este tutorial y éste usan una aplicación basada en la plantilla de administración de casos.

## <a name="send-a-notification-from-a-flow"></a>Envío de una notificación desde un flujo
> [!NOTE]
> Si desencadena una notificación push desde un flujo, actualmente no se puede enviar a más de un usuario o grupo de seguridad a la vez.

1. En [Microsoft Flow](https://flow.microsoft.com), cree un desencadenador que especifique cuándo se envía la notificación push.

    Por ejemplo, puede enviar una notificación cuando se agregue un registro a la entidad **Case** de Common Data Service.

    ![Captura de pantalla de la creación de un flujo con un desencadenador de Common Data Service](./media/add-notifications/pic4-step1-flowupdated.png)
2. Cree una acción para el flujo mediante el conector **PowerApps Notification** y escriba la **identificador** de la aplicación a la que desea enviar notificaciones.

    También puede cambiar el nombre de la conexión para que refleje su escenario.

    ![Captura de pantalla de creación de una conexión con la instancia de PowerApps que recibirá las notificaciones push](./media/add-notifications/pic5-step2-create-connection.jpg)
3. (opcional) Pase parámetros a la aplicación cuando se abra (después de que el usuario pulse la notificación push).

    En este ejemplo, se distribuyen los campos **Case ID** e **Initial Owner** del contacto seleccionado.

    ![Captura de pantalla del paso de parámetros opcionales en la notificación push](./media/add-notifications/pic6-step3-configure-notif.jpg)

## <a name="send-a-notification-from-an-app"></a>Envío de una notificación desde una aplicación
Puede enviar una notificación push de una aplicación a otra o a la misma aplicación.

1. En [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), vaya a la aplicación a la que desea enviar notificaciones push.
2. En la pestaña **Detalles**, copie el contenido de **Id. de la aplicación** de dicha aplicación.

    ![Obtener el identificador de la aplicación](./media/add-notifications/grab-id.png)
3. Vaya a la pestaña **Conexiones**, cree una conexión con el conector PowerApps Notification y péguela en el identificador de la aplicación del paso anterior.

    ![Crear conexión](./media/add-notifications/create-connection.png)
4. Agregue la conexión a la aplicación de desencadenador.

    En nuestro ejemplo, usamos la misma aplicación que la aplicación de desencadenador. El usuario que se reasigna el caso también desencadena una notificación push para el nuevo propietario del caso.

    ![Añadir conexión](./media/add-notifications/add-connection.png)
5. Desde la conexión de la notificación push, llame al método **SendPushNotification**.

    En nuestro ejemplo, esta notificación se desencadena mediante el uso de la propiedad **OnSuccess** en un formulario.

    ![Fórmula de PowerApps](./media/add-notifications/powerapps-function.png)

## <a name="load-a-specific-page-and-context-when-a-user-taps-the-notification"></a>Carga de una página y contexto concretos cuando un usuario pulsa la notificación
### <a name="pass-parameters"></a>Paso de parámetros
Su notificación push puede pasar parámetros concretos a la aplicación. Por ejemplo, para leer el valor de **CaseID**, use *Param("CaseID")* . Para identificar rápidamente dicho parámetro, agregue un control **Etiqueta** a la aplicación. Establezca la propiedad **Texto** de dicho control en **Param("CaseID")** . Si el usuario abre la aplicación desde la lista **Todas las aplicaciones**, el valor estará vacío. Si el usuario abre la aplicación desde otra ubicación del dispositivo, el valor se rellena con el valor de **CaseID**.

### <a name="set-the-start-page"></a>Establecimiento de la página de inicio
Puede establecer que la aplicación abra, por ejemplo, la página **Detalles del caso** en cuanto se abra la aplicación:

1. Agregue un control **Timer** (Temporizador) y establezca su propiedad **OnTimerEnd** en esta fórmula:
   <br>**Navigate(EditCase; ScreenTransition.None)**
2. (opcional) Oculte el control **Timer** (Temporizador) estableciendo la propiedad **Visible** en **false**.
3. Establezca la propiedad **AlEstarVisible** de la pantalla en **Timer.Start()** .

> [!TIP]
> Se recomienda crear una primera página única en la aplicación para la notificación:
> 
> 1. Cree una página vacía que la aplicación no abra, agregue un control **Entrada de texto** y establezca su valor **timer.Duration**.
> 2. Cuando cree la aplicación, establezca el temporizador en un valor distinto de cero. Cuando esté listo para publicar la aplicación, establezca el valor en **0** para desencadenar inmediatamente el temporizador.

## <a name="syntax"></a>Sintaxis

| Nombre | Descripción |
| --- | --- |
| SendPushNotification |Envía una notificación push a la aplicación que se especifica en la configuración de conexión de la notificación. |

### <a name="parameters"></a>Parámetros

| Nombre | Tipo | Descripción |
| --- | --- | --- |
| recipients |Matriz de cadenas, se requiere |Una lista de: <ul> <li>Direcciones de correo electrónico para usuarios o grupos de seguridad</li> <li>Identificadores de objeto para usuarios o grupos de seguridad de Azure Active Directory</li></ul> |
| message |Cadena, se requiere |El cuerpo del mensaje de la notificación push. |
| openApp |Booleano, opcional |Si la aplicación se abre cuando el usuario pulsa la notificación push. |
| params |Parámetros, opcional |Parámetros de clave y valor que se pasan con la notificación. Se pueden procesar más en la aplicación para abrir una página concreta y cargar un estado concreto. |

### <a name="sample-formulas"></a>Fórmulas de ejemplo
Enviar una notificación básica.

```powerapps-comma
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["f60ccf6f-7579-4f92-967c-2920473c966b"; "72f988bf-86f1-41af-91ab-2d7cd011db47"];
        message: "A new case was assigned to you."
    }
)
```

Enviar una notificación que abra una aplicación y distribuya parámetros concretos.

```powerapps-comma
PowerAppsNotification.SendPushNotification(
    {
        recipients: ["email1@contoso.com"; "email2@contoso.com"];
        message: "message in the notif toast";
        params: Table({key:"notificationKey"; value:"The value for notificationKey"});
        openApp: true
    }
)
```

## <a name="known-limitations"></a>Limitaciones conocidas
* Actualmente, las notificaciones no se muestran en PowerApps Mobile para Windows Phone.
* Actualmente, no proporcionamos notificaciones push a los usuarios que ejecutan aplicaciones solo en un explorador web.
* Las notificaciones muestran el icono de PowerApps genérico, en lugar de un icono específico de la aplicación.
* Cuando se utiliza Microsoft Flow, no se pueden enviar notificaciones push a varios destinatarios a la vez.

Para obtener información de referencia, consulte el artículo [PowerApps Notification (versión preliminar)](https://docs.microsoft.com/connectors/powerappsnotification/).

