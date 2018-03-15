---
title: "Creación de una aplicación desde una lista de SharePoint | Microsoft Docs"
description: "Cree una aplicación de tres pantallas para administrar los datos en una lista de SharePoint, independientemente de si el sitio es local o está en la nube."
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: kfile
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/21/2017
ms.author: sharik
ms.openlocfilehash: e5299b12e3034978b14c70193151440626267c5a
ms.sourcegitcommit: 91851aebdf650e99d15374478901b3762d2b4a4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="generate-an-app-from-within-sharepoint-using-powerapps"></a>Creación de una aplicación desde SharePoint mediante PowerApps

En PowerApps, puede crear automáticamente una aplicación en la que los usuarios puedan administrar los elementos de una lista personalizada de SharePoint Online. La aplicación tendrá tres pantallas para que los usuarios puedan:

* navegar por todos los registros de la lista (**BrowseScreen1**)
* ver todos los campos de un registro específico (**DetailsScreen1**)
* crear o editar un registro (**EditScreen1**)

Si crea una aplicación de una lista personalizada desde la barra de comandos de SharePoint Online, la aplicación aparece como una vista de esa lista. También puede ejecutar la aplicación en un dispositivo Windows, iOS o Android, además de un explorador web.

> [!IMPORTANT]
> PowerApps no admite todos los tipos de datos de SharePoint. Para más información, consulte [Problemas conocidos](connections/connection-sharepoint-online.md#known-issues).

## <a name="generate-an-app"></a>Generar una aplicación
1. Abra una lista personalizada en SharePoint Online, pulse o haga clic en **PowerApps** en la barra de comandos y, después, pulse o haga clic en **Crear una aplicación**.
   
    ![](./media/generate-app-from-sharepoint-list-interface/generate-new-app.png)
2. En el panel que aparece, escriba un nombre para la aplicación y pulse o haga clic en **Crear**.
   
    ![](./media/generate-app-from-sharepoint-list-interface/enter-app-name.png)
   
    Aparece una nueva pestaña en el explorador web que muestra la aplicación generada automáticamente basada en la lista de SharePoint.
   
    ![](./media/generate-app-from-sharepoint-list-interface/powerapp-studio-for-web.png)  
3. Pulse o haga clic en la pestaña del explorador de la lista de SharePoint y, a continuación, pulse o haga clic en **Abrir**.
   
    > [!NOTE]
> Es posible que deba actualizar la ventana del explorador (por ejemplo, presionando F5) para que se abra la aplicación.
   
    ![](./media/generate-app-from-sharepoint-list-interface/open-app-in-browser.png)
   
    La aplicación se abre en una pestaña independiente del explorador.
   
    ![](./media/generate-app-from-sharepoint-list-interface/open-app.png)

## <a name="manage-the-app"></a>Administración de la aplicación
![](./media/generate-app-from-sharepoint-list-interface/command-bar.png)

* Al pulsar o hacer clic en **Editar en PowerApps**, la aplicación se abre en una pestaña independiente del explorador donde puede actualizar la aplicación en PowerApps Studio para la web.
* Al pulsar o hacer clic en **Hacer pública esta vista**, otras personas de su organización podrán verla. De forma predeterminada, solo puede ver las vistas que cree. Si desea permitir a otros usuarios editar esta aplicación, deberá [compartirla con ellos](share-app.md) y concederles permisos de **Colaborador**.
* Al pulsar o hacer clic en **Quitar esta vista**, quitará la vista de SharePoint, pero la aplicación seguirá estando en PowerApps, a menos que la [elimine](delete-app.md).

## <a name="next-steps"></a>Pasos siguientes
* Para agregar o actualizar elementos de la lista, consulte la sección "Administrar la lista mediante la aplicación" en [Abrir una aplicación desde una lista de SharePoint Online](open-app-embedded-in-sharepoint.md).
* Para personalizar la pantalla de exploración (que aparece de forma predeterminada), consulte [Personalizar un diseño](customize-layout-sharepoint.md).
* Para personalizar los detalles o editar las pantallas, consulte [Personalizar un formulario](customize-forms-sharepoint.md).
* Si desea eliminar la aplicación, quite la vista de SharePoint y después [elimine la aplicación](delete-app.md) de PowerApps.

