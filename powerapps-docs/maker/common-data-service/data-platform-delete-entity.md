---
title: Inicio rápido para eliminar una entidad personalizada y borrar datos | Microsoft Docs
description: Inicio rápido para eliminar una entidad personalizada y borrar todos los datos.
services: powerapps
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 399d3e8bac215df7612ac12d922dfe644dc59f96
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-delete-a-custom-entity"></a>Inicio rápido: Eliminación de una entidad personalizada
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

