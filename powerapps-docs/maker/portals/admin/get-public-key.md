---
title: Descargar la clave pública de un portal de Dynamics 365 | MicrosoftDocs
description: Aprenda cómo descargar la clave pública de un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 120339aae2cc0f39bbdaa9a0343c31f42b98cfdd
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867299"
---
# <a name="download-public-key-of-portal"></a>Descargar clave pública del portal

La clave pública de un portal se usa para configurar Live Assist para alicaciones basadas en modelo para Dynamics 365 para que funcione con los visitantes autenticados de un portal. [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/), de CafeX, ofrece una solución de chat a través de la que los usuarios pueden incluir asistencia de chat en vivo en su portal. Puede encontrar más información sobre cómo usar la clave pública para incluir un chat en un portal en: [Visitantes autenticados en el portal para clientes de Dynamics](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/).

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Acciones del portal** > **Obtener clave pública**. Aparecerá la clave.

    > [!div class=mx-imgBorder]
    > ![Obtener clave pública de un portal](../media/get-public-key.png "Obtener clave pública de un portal")

3.  Seleccione **Descargar como texto** para descargar la clave en un archivo de texto.

También puede obtener la clave pública dirigiéndose a la dirección URL: `<portal_base_URL>/_ services/auth/publickey`. 

> [!NOTE]
> Si el portal se está aprovisionando actualmente o la instalación del paquete no ha finalizado en la organización, se mostrará un error si intenta descargar la clave pública. Debe esperar hasta que se complete el aprovisionamiento del portal y esté en funcionamiento.
