---
title: Actualizar desde el dominio de Dynamics 365 al dominio de portales de Power Apps | MicrosoftDocs
description: Instrucciones para actualizar desde el dominio de Dynamics 365 al dominio de portales de Power Apps.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b65ffaad5bebc7b5237f74dd09f96e2462d3fba7
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867079"
---
# <a name="update-to-power-apps-portals-domain"></a>Actualizar al dominio de portales de Power Apps

Si aprovisiona un portal utilizando el complemento de portal anterior, el dominio de su portal será `microsoftcrmportals.com`. Con la versión preliminar de portales de Power Apps, ahora puede actualizar el dominio de Dynamics 365 `microsoftcrmportals.com` al dominio de los portales de Power Apps `powerappsportals.com`.

> [!NOTE]
> El dominio `microsoftcrmportals.com` está en desuso y se limita solo a los portales aprovisionados con el complemento de portal anterior. En el periodo de desuso, esta característica seguirá funcionando y será totalmente compatible hasta que se quite oficialmente. Esta notificación de funcionalidad obsoleta pueden durar varios años.

1. Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2. Vaya a **Acciones del portal** > **Actualizar al dominio de portales de Power Apps**.

    > [!div class=mx-imgBorder]
    > ![Actualizar al dominio de portales de Power Apps](../media/update-portal-domain-button.png "Actualizar al dominio de portales de Power Apps")

3. En **Dirección URL del portal**, escriba la dirección del sitio web y seleccione **Aceptar**.

    > [!div class=mx-imgBorder]
    > ![Actualizar al dominio de portales de Power Apps](../media/update-portal-domain.png "Actualizar al dominio de portales de Power Apps")

Si ya usa el dominio de los portales de Power Apps y desea revertir al antiguo dominio, puede usar la acción **Actualizar al dominio del portal de Power Apps** para revertir al antiguo dominio. En este caso, el mensaje se muestra de la siguiente manera:

> [!div class=mx-imgBorder]
> ![Revertir al antiguo dominio](../media/revert-portal-domain.png "Revertir al antiguo dominio")
