---
title: Cambiar la dirección URL base de un portal | MicrosoftDocs
description: Aprenda cómo cambiar la dirección URL base de un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a0ccf3fe2178b711a5eb61bc64814d343c648d25
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867343"
---
# <a name="change-the-base-url-of-a-portal"></a>Cambiar la dirección URL base de un portal

Puede cambiar la dirección URL base de un portal después de que se aprovisione. Por ejemplo, si elige `contosocommunity.microsoftcrmportals.com` como la dirección URL base el aprovisionar el portal, podrá cambiarlo posteriormente a `contosocommunityportal.microsoftcrmportals.com` para satisfacer sus requisitos.

> [!NOTE]
> Una vez que cambie la dirección URL base del portal, la dirección URL más antigua ya no será accesible y estará disponible para que otros clientes la usen para sus portales.

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  Vaya a **Acciones del portal** > **Cambiar dirección URL base**. 

    > [!div class=mx-imgBorder]
    > ![Cambiar dirección URL base de un portal](../media/change-base-url-action.png "Cambiar dirección URL base de un portal")

3.  En la ventana Cambiar dirección URL base, escriba la nueva dirección URL base para el portal.

    > [!div class=mx-imgBorder]
    > ![Especificar una nueva dirección URL base del portal](../media/change-base-url.png "Especificar una nueva dirección URL base del portal")

4.  Haga clic en **Cambiar dirección URL** en la ventana de confirmación.

## <a name="troubleshooting"></a>Solución de problemas

En esta sección se ofrece información acerca de la solución de problemas al cambiar la dirección URL base de un portal.

### <a name="changing-the-base-url-fails"></a>Error al cambiar la dirección URL base

Si se produce un error al cambia la dirección URL base de un portal, se mostrará un error como el de la siguiente imagen:

> [!div class=mx-imgBorder]
> ![Error al cambiar la dirección URL base del portal](../media/change-base-url-error.png "Error al cambiar la dirección URL base del portal")

Normalmente, estos son errores transitorios y debe seleccionar **Cambiar dirección URL base** para volver a intentar cambiar la dirección URL base. Si el problema persiste, póngase en contacto con el soporte técnico de Microsoft.
