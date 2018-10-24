---
title: Ejecución de aplicaciones en un explorador web | Microsoft Docs
description: En este tema aprenderá a ejecutar aplicaciones en un explorador web
author: Mattp123
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 07/09/2018
ms.author: matp
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f72d4b5192bd30da676e65e232bc2a3090cb77bb
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42832434"
---
# <a name="run-an-app-in-a-web-browser"></a>Ejecución de una aplicación en un explorador web
Cuando crea una aplicación o alguien comparte una aplicación con usted, puede ejecutar la aplicación en Windows, iOS, Android o en un explorador web. En este tema aprenderá a ejecutar una aplicación de lienzo o controlada por modelos en un explorador web desde la [página principal de Dynamics 365](https://home.dynamics.com).

Para seguir este inicio rápido, necesita:
- Una licencia de PowerApps. Esta está disponible con un plan de PowerApps, como la versión de prueba del [Plan 2 de PowerApps](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps), o cualquiera de los planes de [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) o [Dynamics 365](https://dynamics.microsoft.com/pricing/) que incluyen PowerApps. 
- Acceso a una aplicación que haya compilado o que otra persona haya compilado y compartido con usted.
- Acceso a un explorador web y un sistema operativo compatibles.
   - Para las aplicaciones de lienzo, vea [Requisitos del sistema, límites y valores de configuración](../maker/canvas-apps/limits-and-config.md)
   - Para las aplicaciones controladas por modelos, vea: [Exploradores web y dispositivos móviles admitidos](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>Inicio de sesión en Dynamics 365
Inicie sesión en Dynamics 365 en [https://home.dynamics.com](https://home.dynamics.com).

## <a name="find-an-app-on-the-home-page"></a>Buscar una aplicación en la página principal
En la página principal se pueden mostrar varios tipos de aplicaciones empresariales, pero se puede buscar una aplicación específica si se escribe al menos una parte de su nombre en el cuadro de búsqueda. También se puede filtrar la lista para mostrar solo las aplicaciones creadas por un origen específico, como PowerApps. Para ello, pulse o haga clic en **Filtro** y, después, seleccione el origen.

Si ha instalado la aplicación recientemente, es posible que no aparezca inmediatamente en la lista de aplicaciones. Pulse o haga clic en **Sincronizar** para mostrar todas las aplicaciones. Este proceso puede tardar hasta un minuto.

![](./media/run-app-browser/dynamics-365-home.png)

## <a name="run-an-app-from-the-task-pane"></a>Ejecutar una aplicación desde el panel de tareas
Una vez encontrada la aplicación, se puede anclar al panel de tareas para facilitar el acceso. Para anclar una aplicación, haga clic en o pulse en los puntos suspensivos (...) en el icono de la aplicación y, a continuación, haga clic o toque en **Anclar esta aplicación**.

![](./media/run-app-browser/homepage-pin.png)

Para ejecutar la aplicación anclada desde el panel de tareas, pulse o haga clic en **Dynamics 365** en la esquina superior izquierda, busque la aplicación en **Mis aplicaciones** y, después, pulse o haga clic en ella.

![](./media/run-app-browser/taskpane.png)

## <a name="run-an-app-from-a-url"></a>Ejecutar una aplicación desde una dirección URL
Se puede guardar la dirección URL de una aplicación como un marcador en el explorador y ejecutarla seleccionando el marcador, o bien se puede enviar una dirección URL como un vínculo por correo electrónico. Si otro usuario creó una aplicación y la compartió con usted en un correo electrónico, puede ejecutar la aplicación, si pulsa o hace clic en el vínculo del correo electrónico. Al ejecutar una aplicación desde una dirección URL, es posible que se le solicite que inicie sesión con las credenciales de Azure Active Directory.

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>Conectarse a datos
Si una aplicación requiere una conexión a un origen de datos o permiso para usar las funcionalidades del dispositivo (como la cámara o los servicios de ubicación), debe dar su consentimiento antes de usar la aplicación. Habitualmente, solo se le solicitará la primera vez.

![Conexión](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>Cerrar una aplicación
Para cerrar una aplicación, cierre la sesión en la página de inicio de 365 Dynamics o abra otra aplicación.

## <a name="next-steps"></a>Pasos siguientes
En este tema ha aprendido a ejecutar una aplicación de lienzo o controlada por modelos en un explorador web. Para ver cómo ejecutar una aplicación de lienzo en un dispositivo móvil, continúe en el tema siguiente.

> [!div class="nextstepaction"]
> [Ejecución de una aplicación de lienzo en un dispositivo móvil](run-app-client.md)
