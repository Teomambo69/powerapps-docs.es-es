---
title: "Generación de una aplicación para administrar datos en una lista de SharePoint | Microsoft Docs"
description: "Genere una aplicación de tres pantallas para administrar los datos en una lista de SharePoint independientemente de si el sitio es local o está en la nube."
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
ms.date: 06/05/2017
ms.author: sharik
ms.openlocfilehash: 5d47366fafa137d8e5b0311f8820b11ff60f648a
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="generate-an-app-to-manage-data-in-a-sharepoint-list"></a>Generar una aplicación para administrar datos en una lista de SharePoint
[!VIDEO nb:cid:UUID:34ccfd46-7826-49ce-90d8-cf6a144b6968]


En PowerApps, genere una aplicación de tres pantallas para administrar automáticamente los datos en una lista de SharePoint independientemente de si el sitio es local o está en la nube.

De forma predeterminada, cada aplicación generada tiene una pantalla de exploración de registros, una pantalla para mostrar los detalles de un registro y una pantalla para crear o actualizar los registros. El diseño y contenido inicial de cada pantalla se determinan automáticamente, pero probablemente necesitará personalizar la aplicación para que se adapte a sus necesidades.

Si no está familiarizado con PowerApps, consulte [Introducción a PowerApps](getting-started.md).

A partir de la fecha de publicación de este artículo, PowerApps admite listas personalizadas pero no bibliotecas. Además, puede mostrar datos en algunos tipos de columnas, como **Opción** e **Imagen**, pero no puede actualizar esos datos. Para más información, consulte [Problemas conocidos](connections/connection-sharepoint-online.md#known-issues).

**Nota:** Si cualquier nombre de columna contiene algún espacio, PowerApps mostrará este como **"\_x0020\_"**. Por ejemplo, **"Nombre de columna"** se mostrará como **"Nombre_x0020_de_columna"**.

## <a name="specify-a-sharepoint-app"></a>Especificar una aplicación de SharePoint
1. Si no ha creado todavía una [conexión a SharePoint](connect-to-sharepoint.md), cree una.
2. Abra PowerApps de *alguna* de estas maneras:
   
   * [Instale PowerApps Studio para Windows](http://aka.ms/powerappsinstall), ábralo e inicie sesión con las mismas credenciales que usó para registrarse. Cerca del borde izquierdo, haga clic o pulse en **Nuevo**.
     
       ![Opción Nuevo en el menú Archivo](./media/app-from-sharepoint/file-menu.png)
   * [Abra PowerApps Studio para la web](https://create.powerapps.com/api/start) en un explorador.
     
       Para obtener una lista de exploradores admitidos y las limitaciones de la versión preliminar de PowerApps Studio para la web, consulte [Create or edit apps in a browser](create-app-browser.md) (Crear o editar aplicaciones en un explorador).
3. En **Comenzar con los datos**, pulse o haga clic en **Diseño de teléfono** en el icono SharePoint.
   
    ![](./media/app-from-sharepoint/sharepoint-tile.png)

## <a name="specify-a-site-and-a-list"></a>Especifique un sitio y una lista
1. En **Conectar con un sitio de SharePoint**, escriba o pegue la dirección URL del sitio que contiene la lista que desea utilizar y, a continuación, haga clic o pulse en **Ir**.
   
    **Nota**: No incluya una lista específica en la dirección URL.
   
    ![](./media/app-from-sharepoint/specify-site.png)
2. En **Elija una lista**, haga clic o pulse en el nombre de la lista que desea utilizar.
   
    Puede ordenar los nombres de la lista alfabéticamente haciendo clic o pulsando el botón de ordenación.
   
    ![](./media/app-from-sharepoint/sort-button.png)
   
    También puede escribir o pegar al menos una letra en el cuadro de búsqueda para que aparezcan solo los nombres de lista que contienen el texto que especifique.
   
    ![](./media/app-from-sharepoint/choose-list.png)
   
    No todos los tipos de listas aparecen de forma predeterminada. Si el nombre de la lista que desea usar no aparece, desplácese a la parte inferior y escriba el nombre de la lista en el cuadro que contiene el texto **Enter a custom list name** (Escriba el nombre de lista personalizado).
   
    ![](./media/app-from-sharepoint/custom-list.png)
3. Haga clic o pulse en **Conectar** para generar la aplicación.
   
    ![Botón Conectar](./media/app-from-sharepoint/connect-button.png)
4. Si se le pide que realice un paseo introductorio, haga clic o pulse en **Siguiente** para familiarizarse con las áreas principales de la interfaz de PowerApps (o haga clic o pulse en **Omitir**).
   
    ![Pantalla inicial del paseo introductorio](./media/app-from-sharepoint/quick-tour.png)
   
    Siempre puede realizar el paseo más tarde haciendo clic o pulsando en el icono del signo de interrogación situado cerca de la esquina superior derecha de la pantalla y, a continuación, haciendo clic o pulsando en **Take the intro tour** (Realizar paseo introductorio).

## <a name="next-steps"></a>Pasos siguientes
* Para guardar la aplicación que acaba de generar, presione Ctrl-S.
* Para personalizar la pantalla de exploración (que aparece de forma predeterminada), consulte [Personalizar un diseño](customize-layout-sharepoint.md).
* Para personalizar los detalles o editar las pantallas, consulte [Personalizar un formulario](customize-forms-sharepoint.md).

