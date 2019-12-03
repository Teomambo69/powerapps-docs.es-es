---
title: Insertar una aplicación en Teams | Microsoft Docs
description: Puede insertar una aplicación creada en Power Apps en Microsoft Teams para compartirla.
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/29/2019
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0b8750733ac6c97d1669c1063700a3d075fbabbe
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678497"
---
# <a name="embed-an-app-in-teams"></a>Insertar una aplicación en Teams

Puede compartir una aplicación de Power apps que haya creado al insertarla directamente en Microsoft Teams. Cuando haya finalizado, los usuarios pueden seleccionar **+** para agregar su aplicación a cualquiera de **sus** canales o conversaciones del equipo en el que se encuentre. La aplicación aparece como un icono en **pestañas para el equipo**.

Un administrador puede cargar la aplicación para que se muestre a **todos los** equipos del inquilino en la **sección todas las pestañas**. Consulte [compartir una aplicación en Microsoft Teams](https://docs.microsoft.com/power-platform/admin/embed-app-teams).

> [!NOTE]
> Las directivas de aplicación personalizadas del equipo deben estar configuradas para permitir la carga de aplicaciones personalizadas. Si no puede insertar la aplicación en Teams, consulte con el administrador para ver si ha configurado la configuración de la [aplicación personalizada](https://docs.microsoft.com/MicrosoftTeams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

## <a name="prerequisites"></a>Requisitos previos

- Necesita una licencia de [Power apps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)válida.
- Para insertar una aplicación en Teams, necesita una aplicación existente [creada con PowerApps](data-platform-create-app.md).

## <a name="download-the-app"></a>Descarga de la aplicación

1. Inicie sesión en [make.powerapps.com](https://make.powerapps.com)y, a continuación, seleccione **aplicaciones** en el menú.

    ![Mostrar lista de aplicaciones](./media/embed-teams-app/file-apps2.png "Mostrar la lista de aplicaciones")

2. Seleccione **más acciones** (...) para la aplicación que desea compartir en Teams y, después, seleccione **Agregar a equipos**.

    ![Detalles de la aplicación](./media/embed-teams-app/add-to-teams.png "Agregar a equipos")

3. En el panel agregar a equipos, seleccione **Descargar**. Power apps generará el archivo de manifiesto de los equipos con la descripción y el logotipo de la aplicación que ya ha establecido en la aplicación.

    ![Detalles de la aplicación](./media/embed-teams-app/download-app.png "Descargar aplicación")

## <a name="add-the-app-as-a-personal-app"></a>Agregar la aplicación como una aplicación personal

1. Para agregar la aplicación como una aplicación personal o como una pestaña a cualquier canal o conversación, seleccione **aplicaciones** en el panel de navegación izquierdo y, a continuación, seleccione **cargar una aplicación personalizada**.

    > [!NOTE]
    > La **carga de una aplicación personalizada** solo aparece si el administrador del equipo ha creado una [Directiva de aplicación personalizada](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies) y activado **permite la carga de aplicaciones personalizadas**.

    ![Agregar aplicación como pestaña](./media/embed-teams-app/upload-custom-app.png "Carga de una aplicación personalizada")

2. Seleccione **Agregar** para agregar la aplicación como una aplicación personal o seleccione **Agregar al equipo** para agregar la aplicación como una pestaña dentro de un canal o una conversación existente.

## <a name="publish-the-app-to-the-teams-catalogue"></a>Publicar la aplicación en el catálogo de equipos

Si es un administrador, también puede [publicar la aplicación](https://docs.microsoft.com/microsoftteams/tenant-apps-catalog-teams) en el catálogo de Microsoft Teams.

### <a name="see-also"></a>Vea también

[Bienvenido a Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-overview)
