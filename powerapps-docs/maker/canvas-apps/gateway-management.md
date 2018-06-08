---
title: Administración de una puerta de enlace de datos local | Microsoft Docs
description: Administración de una puerta de enlace de datos local y sus conexiones
documentationcenter: na
author: archnair
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 10/30/2016
ms.author: archanan
ms.openlocfilehash: d51d134878b04f3cb10ff876ef488f1390e4ef30
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31826807"
---
# <a name="manage-an-on-premises-data-gateway-in-powerapps"></a>Administración de una puerta de enlace de datos local en PowerApps
Instale una puerta de enlace de datos local para transferir datos de manera rápida y segura entre PowerApps y un origen de datos que no esté en la nube, como una base de datos de SQL Server local o un sitio de SharePoint local. Vea todas las puertas de enlace para las que tiene permisos administrativos y administre los permisos y las conexiones para estas puertas de enlace.

Con una puerta de enlace, puede conectarse a datos locales a través de estas conexiones:

* SharePoint
* SQL Server
* Oracle
* Informix
* Filesystem
* DB2

## <a name="prerequisites"></a>Requisitos previos
* El nombre de usuario y la contraseña que usó para [registrarse](../signup-for-powerapps.md) en PowerApps.
* Los permisos administrativos de una puerta de enlace. De forma predeterminada, tiene estos permisos para cada puerta de enlace que instala, y un administrador de otra puerta de enlace puede concederle estos permisos para esa puerta de enlace.
* Una licencia que permite el acceso a los datos locales mediante una puerta de enlace local. Para más información, consulte la sección "Conectividad" de la [página de precios](https://powerapps.microsoft.com/pricing/).
* Las puertas de enlace y las conexiones locales solo se pueden crear y usar en el [entorno predeterminado](working-with-environments.md) del usuario.

## <a name="install-a-gateway"></a>Instalar una puerta de enlace
1. En la barra de navegación izquierda de [powerapps.com](https://web.powerapps.com), pulse o haga clic en **Puertas de enlace**.

    ![Puertas de enlace en la barra de navegación izquierda](./media/gateway-management/manage-gateway.png)

2. Si no tiene permisos administrativos para una puerta de enlace, haga clic o pulse en [Install a gateway now](http://go.microsoft.com/fwlink/?LinkID=820931) (Instalar una puerta de enlace ahora)(o en **Nueva puerta de enlace** en la esquina superior derecha) y, a continuación, siga las indicaciones del asistente que aparece.

    ![Instalación de puertas de enlace](./media/gateway-management/no-gateway-installed.png)

    Para más información sobre cómo instalar una puerta de enlace, consulte [Información sobre las puertas de enlace de datos locales](gateway-reference.md).

## <a name="view-and-manage-gateway-permissions"></a>Ver y administrar los permisos de la puerta de enlace
1. En la barra de navegación izquierda de [powerapps.com](https://web.powerapps.com), pulse o haga clic en **Puertas de enlace** y, luego, pulse o haga clic en una puerta de enlace.

2. Agregue un usuario a una puerta de enlace haciendo clic o pulsando en **Usuarios**, especificando un usuario o grupo y, finalmente, especificando un nivel de permiso:

   * **Puede usar**: usuarios que pueden crear conexiones en la puerta de enlace para las aplicaciones y los flujos, pero no pueden compartir la puerta de enlace. Use este permiso para los usuarios que ejecutan aplicaciones pero no las comparten.
   * **Puede usar + compartir**: usuarios que pueden crear una conexión en la puerta de enlace para las aplicaciones y los flujos, y compartir automáticamente la puerta de enlace cuando se comparte una aplicación. Use este permiso con usuarios que tienen que compartir aplicaciones con otros usuarios o con la organización.
   * **Administración**: administradores que tienen control total sobre la puerta de enlace, lo que incluye agregar usuarios, establecer permisos, crear conexiones a todos los orígenes de datos disponibles y eliminar la puerta de enlace.

Para los niveles de permiso **Puede usar** y **Puede usar y compartir**, seleccione los orígenes de datos a los que puede conectarse el usuario mediante la puerta de enlace.

## <a name="view-and-manage-gateway-connections"></a>Ver y administrar las conexiones de puerta de enlace
1. En la barra de navegación izquierda de [powerapps.com](https://web.powerapps.com), pulse o haga clic en **Puertas de enlace** y, luego, pulse o haga clic en una puerta de enlace.

2. Pulse o haga clic en **Conexiones** y luego pulse o haga clic en una conexión para ver sus detalles, editar la configuración o eliminarla.

3. Para compartir una conexión, haga clic o pulse en **Compartir** y, a continuación, agregue o quite usuarios.

    > [!NOTE]
> Solo puede compartir algunos tipos de conexiones, como SQL Server. Para más información, consulte [Share app resources](share-app-resources.md) (Uso compartido de recursos de la aplicación).

Para más información sobre cómo administrar una conexión, consulte [Administración de conexiones](add-manage-connections.md).

## <a name="troubleshooting-and-advanced-configuration"></a>Solución de problemas y configuración avanzada
Para más información sobre la solución de problemas con las puertas de enlace o la configuración del servicio de puerta de enlace de la red, consulte [Información sobre las puertas de enlace de datos locales](gateway-reference.md).

## <a name="next-steps"></a>Pasos siguientes
* Cree una aplicación que se conecte a un origen de datos local, como [SQL Server](connections/connection-azure-sqldatabase.md) o [SharePoint](connections/connection-sharepoint-online.md).
* [Comparta una aplicación](share-app.md) que permita conectarse a un origen de datos local.
