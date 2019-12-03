---
title: Almacenamiento y publicación de una aplicación de lienzo | Microsoft Docs
description: Instrucciones paso a paso para guardar y publicar aplicaciones de lienzo para creadores de aplicaciones
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/14/2017
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7a64c7e0eeff1a48385ea251597a9e8d91c075f1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675339"
---
# <a name="save-and-publish-a-canvas-app-in-powerapps"></a>Almacenamiento y publicación de una aplicación de lienzo en PowerApps
Siempre que guarde cambios en una aplicación de lienzo, se publican automáticamente solo para usted y para quien tenga permisos para modificar la aplicación. Cuando termine de realizar cambios, publíquelos explícitamente para que estén disponibles para todos los usuarios con los que se comparta la aplicación.

Para información sobre cómo compartir una aplicación, consulte [Compartir una aplicación](share-app.md).

## <a name="save-changes-to-an-app"></a>Guardar cambios en una aplicación
En Power apps Studio, pulse o haga clic en **Guardar** en el menú **archivo** (en el borde izquierdo) y, a continuación, siga uno de estos pasos:

* Si no ha guardado la aplicación nunca, proporciónele un nombre y pulse o haga clic en **Guardar**.

    ![Guardar nueva aplicación](./media/save-publish-app/save-as.png)
* Si alguna vez ha guardado la aplicación, pulse o haga clic en **Guardar**.  

    ![Guardar aplicación actualizada](./media/save-publish-app/save-app.png)

Power apps también puede guardar la aplicación periódicamente cada 2 minutos. Si ha guardado la aplicación una vez, Power apps seguirá guardando una versión de la aplicación periódicamente sin necesidad de que el usuario pulse o haga clic en la acción guardar. Los autores pueden habilitar o deshabilitar la opción **Guardado automático** de la pestaña **Cuenta** del menú **Archivo**.

![Opción Guardado automático](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>Publicar una aplicación
1. En Power apps Studio, pulse o haga clic en **Guardar** en el menú **archivo** (en el borde izquierdo) y, después, pulse o haga clic en **publicar esta versión**.

    ![Publicar la aplicación](./media/save-publish-app/publish-app.png)
2. En el cuadro de diálogo **Publicar**, pulse o haga clic en **Publicar esta versión** para publicar la aplicación para todos los usuarios con los que se comparte la aplicación.

   ![Revisar la publicación](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > Siempre que publique una aplicación de lienzo, la aplicación se actualizará para que se ejecute en la versión más reciente de Power Apps, lo que significa que obtendrá la ventaja de las últimas características y actualizaciones de rendimiento que hemos agregado desde la última vez que publicó. Si no ha publicado una actualización desde hace varios meses, probablemente verá una mejora de rendimiento inmediata al volver a publicar ahora.

## <a name="identify-the-live-version"></a>Identificar la versión activa
En [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), pulse o haga clic en **Aplicaciones** en el menú **Archivo** (en el borde izquierdo), después en el icono de detalles para una aplicación y, por último, en la pestaña **Versiones**.

La versión **Activa** está publicada para todos los usuarios con quien se comparte la aplicación. La versión más reciente de cualquier aplicación está disponible solo para quienes tienen permisos de edición para ella.

![Publicar desde el portal](./media/save-publish-app/publish-portal.png)

Para publicar la versión más reciente, pulse o haga clic en **Publicar esta versión** y pulse o haga clic en **Publicar esta versión** en el cuadro de diálogo **Publicar**.

## <a name="next-steps"></a>Pasos siguientes
* Busque y ejecute la aplicación en un [Explorador](../../user/run-app-browser.md) o en un [teléfono](../../user/run-app-client.md).
* [Cambie el nombre de una aplicación](set-name-tile.md) desde powerapps.com.
* [Restaure una aplicación](restore-an-app.md) si tiene varias versiones de una aplicación.
