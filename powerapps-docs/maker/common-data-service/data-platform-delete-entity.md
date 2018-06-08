---
title: Eliminación de una entidad personalizada | Microsoft Docs
description: Instrucciones paso a paso sobre cómo eliminar una entidad personalizada y borrar todos los datos de PowerApps
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 6ef9dc3a1c82fdee9927ffd533ed41386345eaf7
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34167570"
---
# <a name="delete-a-custom-entity"></a>Eliminar una entidad personalizada
Puede eliminar entidades personalizadas pero no entidades estándar.

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. En la lista de entidades, pulse o haga clic en la entidad que se va a eliminar y, después, pulse o haga clic en la opción **Eliminar entidad** de la barra de comandos.

3. En el cuadro de diálogo que aparece, haga clic o pulse en **Eliminar** para eliminar la entidad.

>[!NOTE]
>Cuando se elimina una entidad, se eliminan su definición y todos los datos que contiene. Las entidades y los datos que contienen no se pueden recuperar si se eliminan.

>[!NOTE]
>Si se elimina una entidad que se usa en una aplicación, es posible que se interrumpa una aplicación o un flujo.

>[!NOTE]
>Si la entidad A tiene [campos de búsqueda](data-platform-entity-lookup.md) a la entidad B, quizás tenga que eliminar la entidad B para poder eliminar la entidad A.

