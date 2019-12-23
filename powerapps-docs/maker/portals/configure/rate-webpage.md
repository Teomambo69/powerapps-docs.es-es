---
title: Clasifique o vote sobre una página web en un portal | MicrosoftDocs
description: Instrucciones para habilitar y administrar calificaciones en una página web en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e32d2e7969481c3aea4ab3abefb5bfc5c48e8852
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866771"
---
# <a name="rate-or-vote-on-a-webpage-on-a-portal"></a>Clasifique o vote sobre una página web en un portal

Las clasificaciones proporcionan a los usuarios la capacidad valorar o votar sobre una página web. Las clasificaciones también se pueden habilitar para comentarios sobre páginas. De forma predeterminada esta característica está deshabilitada, pero se puede habilitar página por página.

Las clasificaciones son actividades personalizadas y, por tanto, se pueden usar igual que cualquier otra actividad como correos electrónicos, llamadas de teléfono, etc. Dado que las clasificaciones son actividades, es posible, mediante personalización, hacer que aparezcan clasificaciones para cualquier entidad que elija, que aparezca y se represente en el portal, incluidas las entidades personalizadas.

## <a name="enable-ratings-for-pages"></a>Habilitar clasificaciones para páginas

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya a **Portales** > **Páginas web**.

3. Seleccione la **página web** en la que necesita habilitar clasificaciones.

4. En la pestaña **General**, en **Opciones de página**, establezca **Habilitar calificaciones** en **Sí**.

5. Seleccione **Guardar y cerrar**.

## <a name="use-ratings"></a>Usar clasificaciones

Para las páginas web que tienen clasificaciones de páginas habilitadas y el desarrollador ha aplicado el control a la plantilla, los usuarios pueden clasificar la página mediante una escala de clasificación o votando en función del tipo elegido cuando el control se agregó a la plantilla de páginas.

### <a name="rating-type"></a>Tipo de clasificación

![Tipo de clasificación](../media/rating-type.png "Tipo de clasificación")  

### <a name="vote-type"></a>Tipo de voto

![Tipo de voto](../media/vote-type.png "Tipo de voto")  

## <a name="manage-ratings"></a>Administrar clasificaciones

Las clasificaciones para páginas web se pueden ver, modificar, o eliminar desde los portales de Power Apps.

1. Abra la aplicación [Administración del portal](configure-portal.md).

2. Vaya hasta la **página web** para la que quiere ver las calificaciones.

3. En la pestaña **Relacionado**, seleccione **Actividades**. La vista asociada muestra las clasificaciones para la página web seleccionada. Desde esta vista, los usuarios pueden editar o eliminar clasificaciones existentes.
