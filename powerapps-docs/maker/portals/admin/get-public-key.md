---
title: Descargar la clave pública de un portal | MicrosoftDocs
description: Aprenda a descargar la clave pública de un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 39e909acb325bd870f73e16a72da78b4bec07c79
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975987"
---
# <a name="download-public-key-of-portal"></a>Descarga de la clave pública del portal

La clave pública de un portal se usa para configurar Live Assist para aplicaciones controladas por modelos en Dynamics 365 para trabajar con visitantes autenticados en un portal. [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/), por CafeX, proporciona una solución de chat a través de la cual los usuarios pueden insertar ayuda de chat en directo en su portal. Más información sobre cómo usar la clave pública para insertar un chat en un portal: [visitantes autenticados en el portal del cliente de Dynamics](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **acciones del Portal** > **obtener clave pública**. Se muestra la clave.

    > [!div class=mx-imgBorder]
    > ![Obtención de la clave pública de un portal](../media/get-public-key.png "obtención de la clave pública de un portal")

3.  Seleccione **Descargar como texto** para descargar la clave en un archivo de texto.

Como alternativa, también puede obtener la clave pública yendo a la dirección URL: `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> Si el portal se está aprovisionando actualmente o la instalación del paquete no se ha completado en la organización, se muestra un error si intenta descargar la clave pública. Debe esperar hasta que se complete el aprovisionamiento del portal y el portal esté en funcionamiento.
