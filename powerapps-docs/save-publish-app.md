---
title: "Almacenamiento y publicación de una aplicación | Microsoft Docs"
description: Instrucciones paso a paso para guardar y publicar aplicaciones para creadores de aplicaciones
services: 
suite: powerapps
documentationcenter: na
author: SKjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/14/2017
ms.author: sharik
ms.openlocfilehash: 739813b2b4905653543461008986901d4e2ee95b
ms.sourcegitcommit: faaf9adebd72794d2988fba1b27a31d70b5268f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="save-and-publish-an-app-in-powerapps"></a>Guardar y publicar una aplicación en PowerApps
Siempre que guarde cambios en una aplicación, se publican automáticamente solo para usted y para quien tenga permisos para modificar la aplicación. Cuando termine de realizar cambios, publíquelos explícitamente para que estén disponibles para todos los usuarios con los que se comparta la aplicación.

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
> Es aconsejable que actualice o vuelva a publicar la aplicación dentro de los seis meses posteriores a la última vez que lo hizo, con el fin de que esté sincronizada con la versión más reciente de PowerApps. Si no lo hace, la aplicación puede dejar de funcionar sin previo aviso.

## <a name="identify-the-live-version"></a>Identificar la versión activa
En [powerapps.com](https://web.powerapps.com), pulse o haga clic en **Aplicaciones** en el menú **Archivo** (en el borde izquierdo), después en el icono de detalles para una aplicación y, por último, en la pestaña **Versiones**.

La versión **Activa** está publicada para todos los usuarios con quien se comparte la aplicación. La versión más reciente de cualquier aplicación está disponible solo para quienes tienen permisos de edición para ella.

![Publicar desde el portal](./media/save-publish-app/publish-portal.png)

Para publicar la versión más reciente, pulse o haga clic en **Publicar esta versión** y pulse o haga clic en **Publicar esta versión** en el cuadro de diálogo **Publicar**.

## <a name="next-steps"></a>Pasos siguientes
* [Cambie el nombre de una aplicación](set-name-tile.md) desde powerapps.com.
* [Restaure una aplicación](restore-an-app.md) si tiene varias versiones de una aplicación.
