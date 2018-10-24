---
title: Almacenamiento y publicación de una aplicación de lienzo | Microsoft Docs
description: Instrucciones paso a paso para guardar y publicar aplicaciones de lienzo para creadores de aplicaciones
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/14/2017
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f52338d4eed8942259e7ae15a8df3b05c45a703d
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42837021"
---
# <a name="save-and-publish-a-canvas-app-in-powerapps"></a>Almacenamiento y publicación de una aplicación de lienzo en PowerApps
Siempre que guarde cambios en una aplicación de lienzo, se publican automáticamente solo para usted y para quien tenga permisos para modificar la aplicación. Cuando termine de realizar cambios, publíquelos explícitamente para que estén disponibles para todos los usuarios con los que se comparta la aplicación.

Para información sobre cómo compartir una aplicación, consulte [Compartir una aplicación](share-app.md).

## <a name="save-changes-to-an-app"></a>Guardar cambios en una aplicación
En PowerApps Studio, pulse o haga clic en **Guardar** en el menú **Archivo** (en el borde izquierdo) y siga cualquiera de estos pasos:

* Si no ha guardado la aplicación nunca, proporciónele un nombre y pulse o haga clic en **Guardar**.

    ![Guardar nueva aplicación](./media/save-publish-app/save-as.png)
* Si alguna vez ha guardado la aplicación, pulse o haga clic en **Guardar**.  

    ![Guardar aplicación actualizada](./media/save-publish-app/save-app.png)

PowerApps también puede guardar la aplicación periódicamente cada 2 minutos. Si ha guardado la aplicación una vez, PowerApps volverá a guardar una versión de ella periódicamente sin que el usuario tenga que hacer clic o pulsar la acción Guardar. Los autores pueden habilitar o deshabilitar la opción **Guardado automático** de la pestaña **Cuenta** del menú **Archivo**.

![Opción Guardado automático](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>Publicar una aplicación
1. En PowerApps Studio, pulse o haga clic en **Guardar** en el menú **Archivo** (en el borde izquierdo) y, después, en **Publicar esta versión**.

    ![Publicar la aplicación](./media/save-publish-app/publish-app.png)
2. En el cuadro de diálogo **Publicar**, pulse o haga clic en **Publicar esta versión** para publicar la aplicación para todos los usuarios con los que se comparte la aplicación.

   ![Revisar la publicación](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > Siempre que publique una aplicación de lienzo, esta se actualizará para ejecutarse en la versión más reciente de PowerApps, lo que significa que obtendrá las ventajas de todas las características más recientes y las actualizaciones de rendimiento que se han agregado desde que publicó por última vez. Si no ha publicado una actualización desde hace varios meses, probablemente verá una mejora de rendimiento inmediata al volver a publicar ahora.

## <a name="identify-the-live-version"></a>Identificar la versión activa
En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), pulse o haga clic en **Aplicaciones** en el menú **Archivo** (en el borde izquierdo), después en el icono de detalles para una aplicación y, por último, en la pestaña **Versiones**.

La versión **Activa** está publicada para todos los usuarios con quien se comparte la aplicación. La versión más reciente de cualquier aplicación está disponible solo para quienes tienen permisos de edición para ella.

![Publicar desde el portal](./media/save-publish-app/publish-portal.png)

Para publicar la versión más reciente, pulse o haga clic en **Publicar esta versión** y pulse o haga clic en **Publicar esta versión** en el cuadro de diálogo **Publicar**.

## <a name="next-steps"></a>Pasos siguientes
* [Cambie el nombre de una aplicación](set-name-tile.md) desde powerapps.com.
* [Restaure una aplicación](restore-an-app.md) si tiene varias versiones de una aplicación.
