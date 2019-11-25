---
title: Eliminar una entidad personalizada | Microsoft Docs
description: Instrucciones paso a paso para ver cómo eliminar una entidad personalizada y borrar todos los datos de PowerApps
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8b4b9fb7942a7977bf6795ca21985b93c5469d26
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754935"
---
# <a name="delete-a-custom-entity"></a>Eliminación de entidades personalizadas
Puede eliminar entidades personalizadas, pero no puede eliminar entidades estándar.

1. En [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), expanda la sección **Datos** y haga clic o pulse en **Entidades** en el panel de navegación de la izquierda.

    ![Detalles de entidad](./media/data-platform-cds-create-entity/entitylist.png "Lista de entidades")

2. En la lista de entidades, haga clic o pulse en la entidad para eliminar, y haga clic o pulse en la opción **Eliminar entidad** de la barra de comandos.

3. En el cuadro de diálogo que aparece, haga clic o pulse en **Eliminar** para eliminar la entidad.

>[!NOTE]
>Cuando se elimina una entidad, se elimina tanto la definición de la entidad como todos los datos que contiene. Las entidades y los datos incluidos no se pueden recuperar si se eliminan.

>[!NOTE]
>Es posible que dañe una aplicación o un flujo si elimina una entidad que se usa en esa aplicación.

>[!NOTE]
>Si la entidad A tiene [campos de búsqueda](data-platform-entity-lookup.md) respecto a la entidad B, es posible que deba eliminar la entidad B para poder eliminar la entidad. A.

