---
title: Almacenamiento y publicación de una aplicación de lienzo | Microsoft Docs
description: Instrucciones paso a paso para guardar y publicar aplicaciones de lienzo para creadores de aplicaciones
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/23/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 740107af85e59baf44c6cfbe89eb62a42daa08a2
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79211995"
---
# <a name="save-and-publish-a-canvas-app-in-power-apps"></a>Almacenamiento y publicación de una aplicación de lienzo en Power Apps
Siempre que guarde cambios en una aplicación de lienzo, se publican automáticamente solo para usted y para quien tenga permisos para modificar la aplicación. Cuando termine de realizar cambios, publíquelos explícitamente para que estén disponibles para todos los usuarios con los que se comparta la aplicación.

Para información sobre cómo compartir una aplicación, consulte [Compartir una aplicación](share-app.md).

## <a name="save-changes-to-an-app"></a>Guardar cambios en una aplicación
En Power Apps Studio, seleccione **Guardar** en el menú **Archivo** (en el borde izquierdo) y siga cualquiera de estos pasos:

* Si no ha guardado la aplicación nunca, proporciónele un nombre y seleccione **Guardar**.

    ![Guardar nueva aplicación](./media/save-publish-app/save-as.png)
* Si ha guardado la aplicación alguna vez, seleccione **Guardar**. También puede dejar notas o comentarios específicos de la versión.  

    ![Guardar aplicación actualizada](./media/save-publish-app/save-app.png)

Power Apps también puede guardar la aplicación periódicamente cada 2 minutos. Si ha guardado la aplicación una vez, Power Apps volverá a guardar una versión de esta periódicamente sin que el usuario tenga que hacer clic o pulsar la acción Guardar. Los autores pueden habilitar o deshabilitar la opción **Guardado automático** de la pestaña **Cuenta** del menú **Archivo**.

![Opción Guardado automático](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>Publicar una aplicación
1. En Power Apps Studio, seleccione **Guardar** en el menú **Archivo** (en el borde izquierdo) y seleccione **Publicar**.

    ![Publicar aplicación](./media/save-publish-app/publish-app.png)
2. En el cuadro de diálogo **Publicar**, seleccione **Publicar esta versión** para publicar la aplicación para todos los usuarios con los que se comparte la aplicación.

   ![Revisar la publicación](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > Siempre que publique una aplicación de lienzo, esta se actualizará para ejecutarse en la versión más reciente de Power Apps, lo que significa que obtendrá las ventajas de todas las características más recientes y las actualizaciones de rendimiento que se han agregado desde que publicó por última vez. Si no ha publicado una actualización desde hace varios meses, probablemente verá una mejora de rendimiento inmediata al volver a publicar ahora.

## <a name="identify-the-live-version"></a>Identificar la versión activa
En [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), seleccione **Aplicaciones** en el menú **Archivo** (en el borde izquierdo), seleccione el icono de detalles de una aplicación y, después, seleccione la pestaña **Versiones**.

La versión **Activa** está publicada para todos los usuarios con quien se comparte la aplicación. La versión más reciente de cualquier aplicación está disponible solo para quienes tienen permisos de edición para ella.

![Publicar desde el portal](./media/save-publish-app/publish-portal.png)

Para publicar la versión más reciente, resalte la versión y seleccione puntos suspensivos (...). Después, seleccione **publicar esta versión** en el menú desplegable.

## <a name="next-steps"></a>Pasos siguientes
* Busque y ejecute la aplicación en un [explorador](../../user/run-app-browser.md) o [teléfono](../../user/run-app-client.md).
* [Cambie el nombre de una aplicación](set-name-tile.md) desde powerapps.com.
* [Restaure una aplicación](restore-an-app.md) si tiene varias versiones de una aplicación.
