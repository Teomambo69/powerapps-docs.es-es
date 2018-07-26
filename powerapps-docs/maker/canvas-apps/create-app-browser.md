---
title: Creación o modificación de aplicaciones en un explorador | Microsoft Docs
description: Cree o modifique aplicaciones en un explorador utilizando PowerApps Studio para web.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/08/2018
ms.author: anneta
ms.openlocfilehash: 25a06525fba038dda2deebb333f53583301540f7
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2018
ms.locfileid: "39195174"
---
# <a name="create-or-edit-apps-in-powerapps-studio-for-web"></a>Creación o modificación de aplicaciones en PowerApps Studio para web
Cree y modifique aplicaciones en PowerApps Studio para web, que se abre en una ventana del explorador de Windows o en otras plataformas.

## <a name="prerequisites"></a>Requisitos previos
* [Inicie sesión](../signup-for-powerapps.md) en PowerApps.
* Asegúrese de que está usando un [explorador compatible](limits-and-config.md#supported-browsers-for-powerapps-studio).

## <a name="open-powerapps-studio-for-web"></a>Abra PowerApps Studio para web
1. Inicie sesión en [powerapps.com](http://go.microsoft.com/fwlink/p/?LinkId=708209).
2. En la esquina inferior izquierda, pulse o haga clic en **Nueva aplicación**.

    ![Nueva aplicación en la barra de navegación izquierda](./media/create-app-browser/left-nav.png)

PowerApps Studio para web se abre en una nueva pestaña del explorador, donde podrá crear y modificar aplicaciones de la misma manera que lo haría en PowerApps Studio para Windows.

## <a name="known-limitations"></a>Limitaciones conocidas
1. **Crear una conexión**.

    Para [crear una conexión](add-manage-connections.md) a un origen de datos que requiera la autenticación del servicio, vaya a [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y [agregue la conexión](add-data-connection.md) a una aplicación en PowerApps Studio para web.
2. **Editar y guardar la aplicación en un entorno local**.

    Con PowerApps Studio para Windows obtendrá mejores resultados al modificar y guardar aplicaciones en el entorno local. En un explorador no se pueden guardar los cambios de una aplicación local. Debe guardar un archivo nuevo en lugar de reemplazar el que ha abierto.
3. **Usar funciones de señal**.

    Las funciones **[Aceleración y Brújula](functions/signals.md)** devuelven valores precisos en una aplicación publicada, pero valores de cero al crear o modificar la aplicación en un explorador.
4. **Exportar e importar datos**.

    Puede [exportar e importar datos](controls/control-export-import.md) en una aplicación publicada, pero no al crear o modificar una aplicación en un explorador.
5. **Copiar un control de una sesión a otra**.

    No se pueden copiar controles de una sesión de PowerApps Studio para web en otra sesión de PowerApps Studio para web.

## <a name="next-steps"></a>Pasos siguientes
* Genere automáticamente una aplicación de los datos en [Excel](get-started-create-from-data.md) o [SharePoint](app-from-sharepoint.md), por ejemplo.
* Aprenda a [agregar un control y establecer propiedades](add-configure-controls.md) para determinar el aspecto y el comportamiento de la aplicación.
* Deje volar su imaginación al [crear una aplicación desde cero](get-started-create-from-blank.md).
