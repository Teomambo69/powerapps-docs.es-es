---
title: Borrar la memoria caché del lado servidor para un portal | MicrosoftDocs
description: Instrucciones para obligar al portal a actualizar su caché inmediatamente.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8351ca8d3befec80a9e97da03ca62980383b01b1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976010"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>Borrar la memoria caché del lado servidor para un portal

Como administrador del portal, puede borrar la memoria caché del lado servidor para todo el portal de forma que los datos actualizados de Common Data Service se reflejen inmediatamente en el portal. Las actualizaciones de Common Data Service se comunican al portal en modo asincrónico, por lo que es posible que se produzca un retraso entre el momento en que se actualizan los datos en Common Data Service y el momento en que los datos actualizados aparecen en el portal. Para eliminar este retraso&mdash;por ejemplo, cuando interfiere con la configuración del portal&mdash;puede forzar que el portal actualice su caché inmediatamente.

> [!NOTE]
> El acuerdo de nivel de servicio para la actualización de caché (transferencia de datos entre Common Data Service y portal) es de 15 minutos.

Para borrar la memoria caché del lado servidor

1.  Inicie sesión en el portal como administrador.

2.  Vaya a la dirección URL de la siguiente manera: `<portal_path>/_services/about`

3.  Seleccione **Borrar caché**. 

Se elimina la memoria caché del lado servidor y se recargan los datos de Common Data Service. Tenga en cuenta que si borra la memoria caché del servidor del portal, se producirá un rendimiento deficiente del portal mientras se recargan los datos desde Common Data Service.

> [!div class=mx-imgBorder]
> ![Borrar la memoria caché del portal](../media/clear-portal-cache.png "borrar la memoria caché del portal")
