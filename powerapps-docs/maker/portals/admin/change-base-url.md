---
title: Cambiar la dirección URL base de un portal | MicrosoftDocs
description: Obtenga información acerca de cómo cambiar la dirección URL base de un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cfc2fd0ca753aebfe7bc77b73c7e7ec1ca011387
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977482"
---
# <a name="change-the-base-url-of-a-portal"></a>Cambio de la dirección URL base de un portal

Puede cambiar la dirección URL base de un portal una vez aprovisionada. Por ejemplo, si elige `contosocommunity.microsoftcrmportals.com` como la dirección URL base al aprovisionar el portal, puede cambiarla posteriormente a `contosocommunityportal.microsoftcrmportals.com` para satisfacer sus necesidades.

> [!NOTE]
> Una vez que cambie la dirección URL base de su portal, la dirección URL anterior dejará de ser accesible y estará disponible para que otros clientes la usen en sus portales.

1.  Abra el [centro de administración de portales de PowerApps](admin-overview.md).

2.  Vaya a **acciones del Portal** > **cambiar dirección URL base**. 

    > [!div class=mx-imgBorder]
    > ![Cambio de la dirección URL base de un portal](../media/change-base-url-action.png "cambio de la dirección URL base de un portal")

3.  En la ventana cambiar dirección URL base, escriba la nueva dirección URL base para el portal.

    > [!div class=mx-imgBorder]
    > ![Especifique una nueva dirección URL base del portal](../media/change-base-url.png "especifique una nueva dirección URL base del portal")

4.  Seleccione **cambiar dirección URL** en la ventana de confirmación.

## <a name="troubleshooting"></a>Solución de problemas

En esta sección se proporciona información sobre la solución de problemas al cambiar la dirección URL base de un portal.

### <a name="changing-the-base-url-fails"></a>No se puede cambiar la dirección URL base

Si no se puede cambiar la dirección URL base de un portal, se muestra un error como se muestra en la siguiente imagen:

> [!div class=mx-imgBorder]
> ![Error al cambiar la dirección URL base del portal](../media/change-base-url-error.png "error al cambiar la dirección URL base del portal")

Normalmente, se trata de errores transitorios y debe seleccionar **cambiar dirección URL base** para volver a intentar cambiar la dirección URL base. Si el problema persiste, póngase en contacto con el soporte técnico de Microsoft.
