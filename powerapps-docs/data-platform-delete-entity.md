---
title: "Eliminación de una entidad personalizada y borrado de los datos | Microsoft Docs"
description: Elimine una entidad personalizada y borre todos los datos.
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: d3e83ad17fcafcfd65aab47b065413c5b72b4f35
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="delete-a-custom-entity"></a>Eliminar una entidad personalizada
Puede eliminar entidades personalizadas pero no entidades estándar.

1. En [powerapps.com](https://web.powerapps.com), expanda la sección **Common Data Service** y pulse o haga clic en **Entidades** en el panel de navegación izquierdo. Para filtrar la lista de entidades, escriba uno o varios caracteres en la barra de búsqueda, encima de la lista.
2. En la lista de entidades, pulse o haga clic en la entidad que va a eliminar y, después, pulse o haga clic en el icono de papelera en la esquina superior derecha.
3. En el cuadro de diálogo que aparece, haga clic o pulse en **Eliminar** para eliminar la entidad.

>[!NOTE]
>Cuando se elimina una entidad, se eliminan su definición y todos los datos que contiene.

>[!NOTE]
>Puede que se interrumpa una aplicación si elimina una entidad que se usa en ella.

>[!NOTE]
>Si la entidad A tiene [campos de búsqueda](data-platform-entity-lookup.md) a la entidad B, quizás tenga que eliminar la entidad B para poder eliminar la entidad A.

