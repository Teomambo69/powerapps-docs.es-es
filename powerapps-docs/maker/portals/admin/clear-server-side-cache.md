---
title: Borrar la memoria caché del servidor para un portal | MicrosoftDocs
description: Instrucciones para forzar el portal para que actualice la memoria caché inmediatamente.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ab1e3a278127105b338893bbbc989774756d3fca
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978301"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>Borrar la memoria caché del servidor para un portal

Como administrador de portal, puede borrar la memoria caché de servidor de todo el portal para reflejar los datos actualizados de Common Data Service inmediatamente en el portal. Las actualizaciones de Common Data Service se comunican al portal en modo asincrónico, por lo que puede haber conflictos entre la hora en que se actualizan los datos en Common Data Service y la hora en que los datos actualizados aparecen en el portal. Para eliminar este retardo&mdash;por ejemplo cuando interfiere con la configuración del portal&mdash;puede forzar una actualización inmediata de la memoria caché.

> [!NOTE]
> La actualización del SLA de la memoria caché (transferencia de datos entre Common Data Service y el portal) dura 15 minutos.

Para borrar la memoria caché del servidor

1.  Inicie sesión en el portal como administrador.

2.  Navegue a la dirección URL de la siguiente manera: `<portal_path>/_services/about`

3.  Seleccione **Borrar caché**. 

Se elimina la memoria caché del servidor, y los datos se vuelven a cargar de Common Data Service. Tenga en cuenta que al borrar la memoria caché del servidor de portal se producirá una caída temporal del rendimiento del portal mientras los datos se vuelven a cargar desde Common Data Service.

> [!div class=mx-imgBorder]
> ![Borrar la memoria caché del portal](../media/clear-portal-cache.png "Borrar la memoria caché del portal")
