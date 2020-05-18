---
title: Agregar una aplicación a Microsoft Teams | Microsoft Docs
description: Vea cómo agregar una aplicación a un canal de Microsoft Teams para que los usuarios con los que la comparta puedan abrirla en ese canal.
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 11/16/2018
ms.author: mduelae
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 97be49797df13b82901425ae9389e85538068f5d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302826"
---
# <a name="add-an-app-to-microsoft-teams"></a>Agregar una aplicación a Microsoft Teams

Microsoft Teams es una plataforma de colaboración basada en chat basada en las tecnologías de Office 365. Se puede personalizar la experiencia de Teams mediante la adición de aplicaciones de lienzo de Power Apps a los canales de Teams. En este tema aprenderá a agregar la aplicación de ejemplo Presentación de productos a un canal de Teams y abrirla luego desde ese canal. 

![Aplicación integrada en Microsoft Teams](./media/open-app-embedded-in-teams/embedded-app.png)

Si no está registrado para Power Apps, [regístrese gratuitamente](https://make.powerapps.com/signup?redirect=marketing&email=) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para seguir este procedimiento, necesita una [suscripción a Office 365](https://signup.microsoft.com/Signup?OfferId=467eab54-127b-42d3-b046-3844b860bebf&dl=O365_BUSINESS_PREMIUM&ali=1) y [un canal en Teams](https://www.youtube.com/watch?v=he2f1quaR7M).

## <a name="sign-in-to-power-apps"></a>Iniciar sesión en Power Apps

Inicie sesión en Power Apps en [https://make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

## <a name="add-an-app"></a>Incorporación de una aplicación

1. En Microsoft Teams, seleccione un equipo y un canal bajo ese equipo. En este ejemplo, es el canal **General** del equipo **Desarrollo empresarial**.

    ![](./media/open-app-embedded-in-teams/teams-select-channel.png)

2. Haga clic en **+** para agregar una pestaña.

    ![](./media/open-app-embedded-in-teams/teams-add-tab.png)

3. En el cuadro de diálogo **Agregar una pestaña**, haga clic en **PowerApps**.

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

En la aplicación de escritorio para Microsoft Teams:

* Las aplicaciones tienen que cargar contenido, como imágenes y archivos .pdf a través de una conexión segura (https).
* No todos los sensores, como **Aceleración**, **Brújula**, y **Ubicación**, son compatibles.
* Se admiten únicamente estos formatos de audio: AAC, H264, OGG Vorbis y WAV.

## <a name="clean-up-resources"></a>Limpieza de recursos

Para quitar la aplicación del canal, haga clic en la pestaña **Presentación de productos** > **Quitar**.

## <a name="next-steps"></a>Pasos siguientes

En este tema ha agregado la aplicación de ejemplo Presentación de productos a un canal de Teams y luego la ha abierto en ese canal. Para obtener más información sobre Power Apps, continúe con los tutoriales de Power Apps.

> [!div class="nextstepaction"]
> [Tutoriales de Power Apps](../maker/canvas-apps/get-started-create-from-blank.md)
