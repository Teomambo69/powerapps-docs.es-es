---
title: Administración de una puerta de enlace de datos local para aplicaciones de lienzo | Microsoft Docs
description: Administración de una puerta de enlace de datos local y sus conexiones
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2019
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b7d4471fde0bf22ec2900f303347d5d4783381ed
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729558"
---
# <a name="manage-an-on-premises-data-gateway-in-power-apps"></a>Administración de una puerta de enlace de datos local en Power apps

Instale una puerta de enlace de datos local para transferir datos de forma rápida y segura entre una aplicación de lienzo integrada en Power apps y un origen de datos que no esté en la nube, como una base de datos de SQL Server local o un sitio de SharePoint local. Vea todas las puertas de enlace para las que tiene permisos administrativos y administre los permisos y las conexiones para estas puertas de enlace.

Con una puerta de enlace, puede conectarse a datos locales a través de estas conexiones:

* SharePoint
* SQL Server
* Oracle
* Informix
* Filesystem
* DB2

## <a name="prerequisites"></a>Requisitos previos

* El nombre de usuario y la contraseña que usó para [suscribirse](../signup-for-powerapps.md) a Power apps.
* Los permisos administrativos de una puerta de enlace. De forma predeterminada, tiene estos permisos para cada puerta de enlace que instala, y un administrador de otra puerta de enlace puede concederle estos permisos para esa puerta de enlace.
* Una licencia que permite el acceso a los datos locales mediante una puerta de enlace local. Para más información, consulte la sección "Conectividad" de la [página de precios](https://powerapps.microsoft.com/pricing/).
* Las puertas de enlace y las conexiones locales solo se pueden crear y usar en el [entorno predeterminado](working-with-environments.md) del usuario.

## <a name="install-a-gateway"></a>Instalar una puerta de enlace

Para instalar una puerta de enlace, siga los pasos descritos en [instalación de una puerta de enlace de datos local](/data-integration/gateway/service-gateway-install). Instale la puerta de enlace en modo estándar porque la _puerta de enlace de datos local (modo personal)_ solo está disponible para Power BI.

## <a name="view-and-manage-gateway-permissions"></a>Ver y administrar los permisos de la puerta de enlace

1. En la barra de navegación izquierda de [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), pulse o haga clic en **Puertas de enlace** y, luego, pulse o haga clic en una puerta de enlace.

2. Agregue un usuario a una puerta de enlace haciendo clic o pulsando en **Usuarios**, especificando un usuario o grupo y, finalmente, especificando un nivel de permiso:

   * **Puede usar**: usuarios que pueden crear conexiones en la puerta de enlace para las aplicaciones y los flujos, pero no pueden compartir la puerta de enlace. Use este permiso para los usuarios que ejecutan aplicaciones pero no las comparten.
   * **Puede usar + compartir**: usuarios que pueden crear una conexión en la puerta de enlace para las aplicaciones y los flujos, y compartir automáticamente la puerta de enlace cuando se comparte una aplicación. Use este permiso con usuarios que tienen que compartir aplicaciones con otros usuarios o con la organización.
   * **Administración**: administradores que tienen control total sobre la puerta de enlace, lo que incluye agregar usuarios, establecer permisos, crear conexiones a todos los orígenes de datos disponibles y eliminar la puerta de enlace.

Para los niveles de permiso **Puede usar** y **Puede usar y compartir**, seleccione los orígenes de datos a los que puede conectarse el usuario mediante la puerta de enlace.

## <a name="view-and-manage-gateway-connections"></a>Ver y administrar las conexiones de puerta de enlace

1. En la barra de navegación izquierda de [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), pulse o haga clic en **Puertas de enlace** y, luego, pulse o haga clic en una puerta de enlace.

2. Pulse o haga clic en **Conexiones** y luego pulse o haga clic en una conexión para ver sus detalles, editar la configuración o eliminarla.

3. Para compartir una conexión, haga clic o pulse en **Compartir** y, a continuación, agregue o quite usuarios.

    > [!NOTE]
   > Solo puede compartir algunos tipos de conexiones, como SQL Server. Para más información, consulte [Share app resources](share-app-resources.md) (Uso compartido de recursos de la aplicación).

Para más información sobre cómo administrar una conexión, consulte [Administración de conexiones](add-manage-connections.md).

## <a name="troubleshooting-and-advanced-configuration"></a>Solución de problemas y configuración avanzada

Para más información sobre la solución de problemas con las puertas de enlace, consulte solución de problemas de [la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot). Para obtener más información acerca de la configuración, consulte [uso de la aplicación de puerta de enlace de datos local](/data-integration/gateway/service-gateway-app).

## <a name="next-steps"></a>Pasos siguientes

* [Instale la puerta de enlace de datos local](/data-integration/gateway/service-gateway-install).
* Cree una aplicación que se conecte a un origen de datos local, como [SQL Server](connections/connection-azure-sqldatabase.md) o [SharePoint](connections/connection-sharepoint-online.md).
* [Comparta una aplicación](share-app.md) que permita conectarse a un origen de datos local.
