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
ms.openlocfilehash: b17da30916b06b5b76b16cc6bf9758b988549f6f
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218657"
---
# <a name="delete-a-custom-entity"></a>Eliminar una entidad personalizada
Puede eliminar entidades personalizadas pero no entidades estándar.

1. En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y pulse o haga clic en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de la entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. En la lista de entidades, pulse o haga clic en la entidad que se va a eliminar y, después, pulse o haga clic en la opción **Eliminar entidad** de la barra de comandos.

3. En el cuadro de diálogo que aparece, haga clic o pulse en **Eliminar** para eliminar la entidad.

>[!NOTE]
>Cuando se elimina una entidad, se eliminan su definición y todos los datos que contiene. Las entidades y los datos que contienen no se pueden recuperar si se eliminan.

>[!NOTE]
>Si se elimina una entidad que se usa en una aplicación, es posible que se interrumpa una aplicación o un flujo.

>[!NOTE]
>Si la entidad A tiene [campos de búsqueda](data-platform-entity-lookup.md) a la entidad B, quizás tenga que eliminar la entidad B para poder eliminar la entidad A.

