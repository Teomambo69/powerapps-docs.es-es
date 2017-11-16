---
title: "Creación o modificación de aplicaciones en un explorador | Microsoft Docs"
description: Cree o modifique aplicaciones en un explorador utilizando PowerApps Studio para web.
services: 
suite: powerapps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/06/2017
ms.author: karthikb
ms.openlocfilehash: 3c675e84f03e008a7f478d358a99fe3fff602002
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="create-or-edit-apps-in-powerapps-studio-for-web"></a>Creación o modificación de aplicaciones en PowerApps Studio para web
Cree y modifique aplicaciones en PowerApps Studio para web, que se abre en una ventana del explorador de Windows o en otras plataformas.

**Requisitos previos**

* [Inicie sesión](signup-for-powerapps.md) en PowerApps.
* Microsoft Edge, Google Chrome o Internet Explorer 11 en un equipo que ejecute Windows o un equipo Mac.

## <a name="open-powerapps-studio-for-web"></a>Abra PowerApps Studio para web
1. Inicie sesión en [powerapps.com](http://go.microsoft.com/fwlink/p/?LinkId=708209).
2. En la esquina inferior izquierda, pulse o haga clic en **Nueva aplicación**.
   
    ![Nueva aplicación en la barra de navegación izquierda](./media/create-app-browser/left-nav.png)

PowerApps Studio para web se abre en una nueva pestaña del explorador, donde podrá crear y modificar aplicaciones de la misma manera que lo haría en PowerApps Studio para Windows.

## <a name="next-steps"></a>Pasos siguientes
* Genere automáticamente una aplicación de los datos en [Excel](get-started-create-from-data.md) o [SharePoint](app-from-sharepoint.md), por ejemplo.
* Aprenda a [agregar un control y establecer propiedades](add-configure-controls.md) para determinar el aspecto y el comportamiento de la aplicación.
* Deje volar su imaginación al [crear una aplicación desde cero](get-started-create-from-blank.md).

## <a name="known-limitations"></a>Limitaciones conocidas
1. **Crear una conexión**.
   
    Para [crear una conexión](add-manage-connections.md) a un origen de datos que requiera la autenticación del servicio, vaya a [powerapps.com](https://web.powerapps.com) y [agregue la conexión](add-data-connection.md) a una aplicación en PowerApps Studio para web.
2. **Editar y guardar la aplicación en un entorno local**.
   
    Con PowerApps Studio para Windows obtendrá mejores resultados al modificar y guardar aplicaciones en el entorno local. En un explorador no se pueden guardar los cambios de una aplicación local. Debe guardar un archivo nuevo en lugar de reemplazar el que ha abierto.
3. **Usar funciones de señal**.
   
    Las funciones **[Aceleración y Brújula](functions/signals.md)** devuelven valores precisos en una aplicación publicada, pero valores de cero al crear o modificar la aplicación en un explorador.
4. **Exportar e importar datos**.
   
    Puede [exportar e importar datos](controls/control-export-import.md) en una aplicación publicada, pero no al crear o modificar una aplicación en un explorador.
5. **Copiar un control de una sesión a otra**.
   
    No se pueden copiar controles de una sesión de PowerApps Studio para web en otra sesión de PowerApps Studio para web.

