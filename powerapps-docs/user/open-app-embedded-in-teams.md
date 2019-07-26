---
title: Adición de una aplicación a Microsoft Teams | Microsoft Docs
description: Vea cómo agregar una aplicación a un canal de Microsoft Teams para que los usuarios con los que la comparta puedan abrirla en ese canal.
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: matp
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 34fc4f9603ebfcb9944b871f211a6b1541235ed5
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "63321664"
---
# <a name="add-an-app-to-microsoft-teams"></a>Adición de una aplicación a Microsoft Teams

Microsoft Teams es una plataforma de colaboración basada en chat creada sobre tecnologías de Office 365. Se puede personalizar la experiencia de Teams mediante la adición de aplicaciones de lienzo de PowerApps a los canales de Teams. En este tema aprenderá a agregar la aplicación de ejemplo Presentación de productos a un canal de Teams y abrirla luego desde ese canal. 

![Aplicación insertada en Microsoft Teams](./media/open-app-embedded-in-teams/embedded-app.png)

Si no está registrado para PowerApps, [regístrese gratuitamente](https://web.powerapps.com/signup?redirect=marketing&email=) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para seguir este procedimiento, necesita una [suscripción a Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) y un [canal en Teams](https://www.youtube.com/watch?v=he2f1quaR7M).

## <a name="sign-in-to-powerapps"></a>Inicio de sesión en PowerApps

Inicie sesión en PowerApps en [https://web.powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="add-an-app"></a>Incorporación de una aplicación

1. En Microsoft Teams, seleccione un equipo y un canal bajo ese equipo. En este ejemplo, es el canal **General** del equipo **Desarrollo empresarial**.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Haga clic en **+** para agregar una pestaña.

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. En el cuadro de diálogo **Add a tab** (Agregar una pestaña), haga clic en **PowerApps**.

    ![](./media/open-app-embedded-in-teams/add-a-tab.png)

4. Seleccione **Aplicaciones de ejemplo** > **Presentación de productos** > **Guardar**.

    ![](./media/open-app-embedded-in-teams/select-an-app.png)

    La aplicación ya está disponible para su uso en el canal.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

> [!NOTE]
> Debe [compartir](../maker/canvas-apps/share-app.md) sus propias aplicaciones antes de agregarlas a Teams (las aplicaciones de ejemplo se comparten de forma predeterminada).

## <a name="open-an-app"></a>Abrir una aplicación

1. En Microsoft Teams, seleccione el equipo y el canal que contiene la aplicación.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Haga clic en la pestaña **Presentación de productos**.

    ![](./media/open-app-embedded-in-teams/open-tab.png)

    La aplicación se abre en el canal.

    ![](./media/open-app-embedded-in-teams/app-in-channel.png)

## <a name="known-issues"></a>Problemas conocidos

En la aplicación de escritorio de Microsoft Teams:

* Las aplicaciones tienen que cargar contenido, como imágenes y archivos .pdf a través de una conexión segura (https).
* No todos los sensores, como **Aceleración**, **Brújula**, y **Ubicación**, son compatibles.
* Solo se admiten estos formatos de audio: AAC, H264, OGG Vorbis y WAV.

## <a name="clean-up-resources"></a>Limpieza de recursos

Para quitar la aplicación del canal, haga clic en la pestaña **Presentación de productos** > **Quitar**.

## <a name="next-steps"></a>Pasos siguientes

En este tema ha agregado la aplicación de ejemplo Presentación de productos a un canal de Teams y luego la ha abierto en ese canal. Para obtener más información sobre PowerApps, continúe con los tutoriales de PowerApps.

> [!div class="nextstepaction"]
> [Tutoriales de PowerApps](../maker/canvas-apps/get-started-create-from-blank.md)
