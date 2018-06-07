---
title: Creación de una conexión a SharePoint desde PowerApps | Microsoft Docs
description: En powerapps.com, cree una conexión a SharePoint, para usarla al generar una aplicación automáticamente o crear una desde cero.
documentationcenter: na
author: aftowen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 09/03/2016
ms.author: anneta
ms.openlocfilehash: 16c585f553373faee609683774e7938e8bd165f1
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31824599"
---
# <a name="create-a-connection-to-sharepoint-from-powerapps"></a>Creación de una conexión a SharePoint desde PowerApps
Cree una conexión a SharePoint Online o a SharePoint local para poder generar una aplicación automáticamente o crear una desde cero.

Si no está familiarizado con PowerApps, consulte [Introducción a PowerApps](getting-started.md).

A partir de la fecha de publicación de este artículo, PowerApps admite listas personalizadas pero no bibliotecas. Además, puede mostrar datos en algunos tipos de columnas, como **Opción** e **Imagen**, pero no puede actualizar esos datos. Para más información, consulte [Problemas conocidos](connections/connection-sharepoint-online.md#known-issues).

## <a name="specify-a-sharepoint-connection"></a>Especificar una conexión de SharePoint
1. Si aún no lo ha hecho, [suscríbase a PowerApps](../signup-for-powerapps.md).

2. Inicie sesión en [powerapps.com](https://web.powerapps.com) con las mismas credenciales que utilizó para suscribirse.

3. En la barra de navegación izquierda, haga clic o pulse en **Administrar** y, después, en **Conexiones**.

    ![Opción Nuevo en el menú Archivo](./media/connect-to-sharepoint/manage-connections.png)

4. Cerca de la esquina superior derecha, haga clic o pulse en **Nueva conexión**.

    ![Botón de nueva conexión](./media/connect-to-sharepoint/new-connection.png)

5. En la lista de conexiones, haga clic o pulse **SharePoint**.

    ![Agregar una conexión de SharePoint](./media/connect-to-sharepoint/add-sp-portal.png)

6. Siga los pasos descritos en cualquiera de estos procedimientos, que aparecen más adelante en este tema:

   * [Conectarse a un sitio de SharePoint Online](connect-to-sharepoint.md#connect-to-a-sharepoint-online-site).
   * [Conectarse a un sitio de SharePoint local](connect-to-sharepoint.md#connect-to-an-on-premises-sharepoint-site).

## <a name="connect-to-a-sharepoint-online-site"></a>Conectarse a un sitio de SharePoint Online
1. Haga clic o pulse **Conectar directamente (servicios en la nube)** y, después, haga clic o pulse en **Agregar conexión**.

    ![Elegir SharePoint Online](./media/connect-to-sharepoint/choose-online.png)

2. Vaya a [Pasos siguientes](connect-to-sharepoint.md#next-steps) al final de este tema.

## <a name="connect-to-an-on-premises-sharepoint-site"></a>Conectarse a un sitio de SharePoint local
1. Haga clic o pulse en **Conectar mediante una puerta de enlace de datos local**.

    ![Elegir SharePoint local](./media/connect-to-sharepoint/choose-onprem.png)

    > [!NOTE]
> Las puertas de enlace y las conexiones locales solo se pueden crear y usar en el [entorno predeterminado](working-with-environments.md) del usuario.

2. Especifique el nombre de usuario y la contraseña.

    Si las credenciales incluyen un nombre de dominio, especifíquelo como *Dominio\Alias*.

    ![Especificar las credenciales](./media/connect-to-sharepoint/specify-credentials.png)

3. Si no tiene una puerta de enlace de datos local instalada, [instale una](gateway-reference.md) y, después, haga clic o pulse en el icono para actualizar la lista de puertas de enlace.

    ![Instalar una puerta de enlace](./media/connect-to-sharepoint/install-gateway.png)

4. En **Elegir una puerta de enlace**, haga clic o pulse en la puerta de enlace que desea usar y, después, haga clic o pulse en **Agregar conexión**.

    ![Elegir una puerta de enlace](./media/connect-to-sharepoint/choose-gateway.png)

## <a name="next-steps"></a>Pasos siguientes
* [Genere una aplicación automáticamente](app-from-sharepoint.md) basándose en una lista que especifique. La aplicación tendrá tres pantallas de forma predeterminada: una para examinar registros, para mostrar detalles acerca de un registro y crear o actualizar un registro.
* [Crear una aplicación desde cero](get-started-create-from-blank.md). Este tema se escribió para Excel, pero los mismos principios se aplican a SharePoint.
