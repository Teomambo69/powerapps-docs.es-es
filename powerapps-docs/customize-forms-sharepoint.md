---
title: "Personalización de formularios | Microsoft Docs"
description: "Especifique qué datos se mostrarán, en qué orden y en qué controles."
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: sharik
ms.openlocfilehash: 7c2b8149d32d488e389eec273158870f0b1c5d34
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="customize-forms-in-powerapps"></a>Personalizar formularios en PowerApps
Personalice un control **Mostrar formulario** y un control **Editar formulario** para que muestren los datos más importantes, en el orden más intuitivo y en los controles que ayudarán a los usuarios a comprender y actualizar los datos fácilmente.

Cada formulario consta de una o más tarjetas, cada una de las cuales muestra datos de una columna determinada del origen de datos. Siga los pasos descritos en este tema para especificar qué tarjetas aparecen en un formulario, subir o bajar las tarjetas dentro de un formulario y configurar cómo aparecen los datos de cada columna dentro de una tarjeta.

Si no está familiarizado con PowerApps, consulte [Introducción a PowerApps](getting-started.md).

## <a name="prerequisites"></a>Requisitos previos
Puede consultar este tutorial para ver los conceptos generales o puede seguirlo exactamente y completar estos pasos.

1. [Crear una conexión](connect-to-sharepoint.md) desde PowerApps a SharePoint.
2. Crear la lista de SharePoint que se describe en [Personalizar un diseño](customize-layout-sharepoint.md).
3. [Generar una aplicación automáticamente](app-from-sharepoint.md) basándose en esa lista.
4. En la barra de navegación izquierda, haga clic o pulse en uno de los iconos de la esquina superior derecha para cambiar a la vista en miniatura.
   
    ![Alternancia de las vistas](./media/customize-forms-sharepoint/toggle-view.png)

## <a name="show-and-hide-cards"></a>Mostrar y ocultar las tarjetas
1. En la barra de navegación izquierda, haga clic o pulse la miniatura intermedia para seleccionar **DetailsScreen1**.
   
    ![Pantalla de selección de detalles](./media/customize-forms-sharepoint/details-thumbnail.png)
2. Haga clic o pulse en cualquier tarjeta para seleccionarla y mostrar las opciones de personalización de formularios en el panel derecho.
   
    ![Seleccionar una tarjeta](./media/customize-forms-sharepoint/select-card.png)
3. En el panel derecho, haga clic o pulse en la casilla de la tarjeta **AccountID** para ocultarla y en la casilla de la columna **ID** para mostrarla.
   
    ![Mostrar tarjeta](./media/customize-forms-sharepoint/checkbox.png)

## <a name="reorder-the-cards"></a>Reordenar las tarjetas
* Haga clic o pulse en la tarjeta **Title** para seleccionarla y arrastre la barra de título hasta que la tarjeta **OrderDate** aparezca resaltada.
  
    ![Mover tarjeta](./media/customize-forms-sharepoint/move-card.png)
  
    La tarjeta que se va a mover aparecerá justo encima de la tarjeta que se resalta cuando se suelta el botón del mouse.
  
    ![Tarjetas reordenadas](./media/customize-forms-sharepoint/reordered-card.png)

## <a name="run-the-app"></a>Ejecutar la aplicación
1. En la barra de navegación izquierda, haga clic o pulse en la miniatura superior para seleccionar **BrowseScreen1**.
   
    ![Miniatura de BrowseScreen1](./media/customize-forms-sharepoint/browse-thumbnail.png)
2. Para abrir el modo de vista previa, presione F5 (o seleccione el icono de **vista previa** situado cerca de la esquina superior derecha).  
   
    ![Icono de vista previa](./media/customize-forms-sharepoint/open-preview.png)
3. En la esquina superior derecha, haga clic o pulse en el icono del signo más para agregar un registro a **EditScreen1**.
   
    ![Agregar registro](./media/customize-forms-sharepoint/add-record.png)
4. Agregue los datos que desee y haga clic o pulse en el icono de marca de verificación, en la esquina superior derecha, para guardar el nuevo registro en la lista de SharePoint y volver a **BrowseScreen1**.
   
    ![Guardar registro](./media/customize-forms-sharepoint/save-record.png)
5. Haga clic o pulse en la flecha del elemento que acaba de crear para mostrar detalles acerca de ese elemento en **DetailScreen1**.  
   
    ![Flecha derecha](./media/customize-forms-sharepoint/right-arrow.png)
6. En la esquina superior derecha, haga clic o pulse en el icono de edición para actualizar el registro en **EditScreen1**.
   
    ![Editar registro](./media/customize-forms-sharepoint/edit-record.png)
7. Cambie la información de uno o varios campos y haga clic o pulse en la marca de verificación de la esquina superior derecha para guardar los cambios en la lista de SharePoint y volver a **DetailScreen1**.  
   
    ![Guardar cambios](./media/customize-forms-sharepoint/save-record.png)
8. Cerca de la esquina superior derecha, pulse o haga clic en el icono de papelera para eliminar el registro que acaba de actualizar y volver a **ExaminarPantalla1**.
   
    ![Eliminar registro](./media/customize-forms-sharepoint/delete-record.png)
9. Para cerrar el modo de vista previa, presione Esc (o pulse o haga clic en el icono Cerrar situado cerca de la esquina superior izquierda, *debajo* de la barra de título de PowerApps).
   
    ![Cerrar el modo de vista previa](./media/customize-forms-sharepoint/close-preview.png)

## <a name="next-steps"></a>Pasos siguientes
* Presione Ctrl-S para guardar la aplicación de forma que se pueda ejecutar desde otros dispositivos.
* [Comparta la aplicación](share-app.md) para que otras personas puedan ejecutarla.

