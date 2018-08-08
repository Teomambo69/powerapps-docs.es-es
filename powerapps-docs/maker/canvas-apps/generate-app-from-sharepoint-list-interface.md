---
title: Generar una aplicación de lienzo a partir de una lista de SharePoint | Microsoft Docs
description: Genere una aplicación de lienzo de tres pantallas para administrar los datos en una lista de SharePoint, independientemente de si el sitio es local o está en la nube.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: 9230c96c1b1c5e07ea5129f73a8edd95772aad84
ms.sourcegitcommit: e3f5a2bef64085d02aec82e62ff94ae8a4d01d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39471429"
---
# <a name="generate-a-canvas-app-from-within-sharepoint-by-using-powerapps"></a>Generar una aplicación de lienzo desde SharePoint mediante PowerApps

En PowerApps, genere automáticamente una aplicación de lienzo en la que los usuarios puedan administrar los elementos de una lista personalizada de SharePoint Online. La aplicación tendrá tres pantallas para que los usuarios puedan:

* navegar por todos los registros de la lista (**BrowseScreen1**)
* ver todos los campos de un registro específico (**DetailsScreen1**)
* crear o editar un registro (**EditScreen1**)

Si crea una aplicación de una lista personalizada desde la barra de comandos de SharePoint Online, la aplicación aparece como una vista de esa lista. También se puede ejecutar la aplicación en un dispositivo iOS o Android, además de un explorador web.

> [!IMPORTANT]
> PowerApps no admite todos los tipos de datos de SharePoint. Para más información, consulte [Problemas conocidos](connections/connection-sharepoint-online.md#known-issues).

## <a name="generate-an-app"></a>Generar una aplicación
1. Abra una lista personalizada en SharePoint Online, pulse o haga clic en **PowerApps** en la barra de comandos y, después, pulse o haga clic en **Crear una aplicación**.

    ![Crear una aplicación](./media/generate-app-from-sharepoint-list-interface/generate-new-app.png)

2. En el panel que aparece, escriba un nombre para la aplicación y pulse o haga clic en **Crear**.

    ![Asignar un nombre a la aplicación](./media/generate-app-from-sharepoint-list-interface/app-name.png)

    Aparece una nueva pestaña en el explorador web que muestra la aplicación generada automáticamente basada en la lista de SharePoint. La aplicación aparece en PowerApps Studio, donde se puede personalizar.

    ![Aplicación predeterminada](./media/generate-app-from-sharepoint-list-interface/default-app.png)  
3. Pulse o haga clic en la pestaña del explorador de la lista de SharePoint y, a continuación, pulse o haga clic en **Abrir**.

> [!NOTE]
> Es posible que deba actualizar la ventana del explorador (por ejemplo, presionando F5) para que se abra la aplicación.

La aplicación se abre en una pestaña independiente del explorador.

## <a name="manage-the-app"></a>Administración de la aplicación
![Barra de comandos](./media/generate-app-from-sharepoint-list-interface/command-bar.png)

* Al pulsar o hacer clic en **Editar en PowerApps**, la aplicación se abre en una pestaña independiente del explorador donde se puede actualizar en PowerApps Studio.

* Al pulsar o hacer clic en **Hacer pública esta vista**, otras personas de su organización podrán verla. De forma predeterminada, solo puede ver las vistas que cree. Si quiere permitir a otros usuarios editar la aplicación, tendrá que [compartirla con ellos](share-app.md) y concederles permisos **Puede editar**.

* Al pulsar o hacer clic en **Quitar esta vista**, quitará la vista de SharePoint, pero la aplicación seguirá estando en PowerApps, a menos que la [elimine](delete-app.md).

## <a name="next-steps"></a>Pasos siguientes
* Personalizar la [galería](customize-layout-sharepoint.md), [formularios](customize-forms-sharepoint.md) y [tarjetas](customize-card.md) predeterminados.
