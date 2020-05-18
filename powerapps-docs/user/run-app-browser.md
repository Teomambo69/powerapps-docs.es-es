---
title: Ejecución de aplicaciones en un explorador web | Microsoft Docs
description: En este tema aprenderá a ejecutar aplicaciones en un explorador web
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 12/05/2019
ms.author: mkaur
manager: kvivek
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8ce6cfe213817cd603857bb5ea2735b188f8cb6c
ms.sourcegitcommit: 15c6b26ff085928459ad9b3f52fb607fae4a997d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "3302987"
---
# <a name="run-an-app-in-a-web-browser"></a>Ejecución de una aplicación en un explorador web
Cuando crea una aplicación o alguien comparte una aplicación con usted, puede ejecutarla en la aplicación móvil de Dynamics 365 o en un explorador web en una tableta. En este tema aprenderá a ejecutar una aplicación de lienzo o basada en modelos en un explorador web en una tableta desde la [página principal de Dynamics 365](https://home.dynamics.com).

Si quiere conseguir la funcionalidad completa y disfrutar de una experiencia optimizada, se recomienda encarecidamente usar la aplicación móvil de Dynamics 365 para teléfonos y tabletas. Si no tiene instalada la aplicación de Dynamics 365 para teléfonos y tabletas, puede seguir usando el explorador web de la tableta, siempre que el dispositivo tenga una resolución de pantalla lo suficientemente alta. Para más información: [Qué es compatible](https://docs.microsoft.com/dynamics365/mobile-app/support-phones-tablets#supported-devices-for-the-mobile-app).

> [!NOTE]
> El explorador web no se puede usar en un teléfono para ejecutar aplicaciones basadas en modelos; para ello, debe usar la aplicación Dynamics 365 para teléfonos.

Para seguir este inicio rápido, necesita:
- Una licencia de Power Apps. Esto está disponible con un plan de Power Apps, como el [Power Apps Plan 2 de prueba](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps) o cualquiera de los planes [Microsoft Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) o [Dynamics 365](https://dynamics.microsoft.com/pricing/) que incluyen Power Apps. 
- Acceso a una aplicación que haya compilado o que otra persona haya compilado y compartido con usted.
- Acceso a un explorador web y un sistema operativo compatibles.
   - Para las aplicaciones de lienzo, vea [Requisitos del sistema, límites y valores de configuración](../maker/canvas-apps/limits-and-config.md)
   - Para las aplicaciones controladas por modelos, vea: [Exploradores web y dispositivos móviles admitidos](https://docs.microsoft.com/dynamics365/customer-engagement/admin/supported-web-browsers-and-mobile-devices)


## <a name="sign-in-to-dynamics-365"></a>Iniciar sesión en Dynamics 365
Inicie sesión en Dynamics 365 en [https://home.dynamics.com](https://home.dynamics.com).

## <a name="find-an-app-on-the-home-page"></a>Buscar una aplicación en la página principal
En la página principal se pueden mostrar varios tipos de aplicaciones empresariales, pero se puede buscar una aplicación específica si se escribe al menos una parte de su nombre en el cuadro de búsqueda. También se puede filtrar la lista para mostrar solo las aplicaciones creadas por un origen específico, como Power Apps. Para ello, seleccione **Filtro** y, después, seleccione el origen.

Si ha instalado la aplicación recientemente, es posible que no aparezca inmediatamente en la lista de aplicaciones. Seleccione **Sincronizar** para mostrar todas las aplicaciones. Este proceso puede tardar hasta un minuto.

![](./media/run-app-browser/dynamics-365-home.png)


## <a name="run-an-app-from-a-url"></a>Ejecutar una aplicación desde una dirección URL
Se puede guardar la dirección URL de una aplicación como un marcador en el explorador de la tableta y ejecutarla seleccionando el marcador, o bien se puede enviar una dirección URL como un vínculo por correo electrónico. Si otro usuario creó una aplicación y la compartió con usted en un correo electrónico, puede ejecutarla seleccionando el vínculo del correo electrónico. Al ejecutar una aplicación desde una dirección URL, es posible que se le solicite que inicie sesión con las credenciales de Azure Active Directory.

![](./media/run-app-browser/web-login.png)

## <a name="connect-to-data"></a>Conectarse a los datos
Si una aplicación requiere una conexión a un origen de datos o permiso para usar las funcionalidades del dispositivo (como la cámara o los servicios de ubicación), debe dar su consentimiento antes de usar la aplicación. Habitualmente, solo se le solicitará la primera vez.

![Conexión](./media/run-app-browser/app-connection.png)

## <a name="close-an-app"></a>Cerrar una aplicación
Para cerrar una aplicación, cierre la sesión en la página de inicio de 365 Dynamics o abra otra aplicación.

## <a name="next-steps"></a>Pasos siguientes
En este tema ha aprendido a ejecutar una aplicación de lienzo o controlada por modelos en un explorador web. Para saber cómo:
- ejecutar una aplicación de lienzo en un dispositivo móvil, vea [Ejecución de una aplicación de lienzo en un dispositivo móvil](run-app-client.md).
- ejecutar una aplicación basada en modelos en un dispositivo móvil, vea [Ejecución de una aplicación basada en modelos en un dispositivo móvil](run-app-client-model-driven.md).
- usar una aplicación basada en modelos, vea [Uso de aplicaciones basadas en modelos](use-model-driven-apps.md).

