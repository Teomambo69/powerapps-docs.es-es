---
title: Acerca del ciclo de vida de los portales de PowerApps | MicrosoftDocs
description: Información sobre el ciclo de vida de los portales de PowerApps y su conversión de prueba a producción.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5476bb0306b5d9e0767f451fba36a567a70c4c54
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542952"
---
# <a name="about-portal-lifecycle"></a>Acerca del ciclo de vida del portal

Un portal siempre se crea como una versión de prueba. Un portal de prueba, que expira después de 30 días, es útil para probar sus funcionalidades sin costo alguno. Después de la expiración, se suspende y se cierra un portal. Siete días después de la suspensión, se elimina el portal de prueba. En cada cambio de fase del ciclo de vida del portal, como cerca de la suspensión, la suspensión, la eliminación y la conversión de la versión de evaluación a la de producción, recibirá notificaciones como notificación del sistema y por correo electrónico.

Como administrador, puede convertir un portal de evaluación o de suspensión en un portal de producción. Al convertir un portal de prueba en producción, asegúrese de que el entorno también sea un entorno de producción. No se puede convertir un portal de prueba a producción en un entorno de prueba. Si elimina el entorno en el que se crea un portal de prueba, también se elimina el portal.

El primer portal se puede crear de forma gratuita en un entorno de un inquilino. Si necesita crear más de un portal, debe tener 1 GB de espacio de almacenamiento sin usar en el inquilino.

## <a name="stages-in-portal-lifecycle"></a>Fases en el ciclo de vida del portal

### <a name="trial-portal"></a>Portal de prueba

Un portal siempre se crea como un portal de prueba. Puede convertirlo en producción desde el centro de administración de portales de PowerApps si tiene las licencias necesarias. Para obtener información sobre cómo convertir un portal de prueba en producción, consulte [conversión de un portal de prueba en producción](#convert-a-trial-portal-to-production).

Para convertir un portal de prueba en producción, el entorno debe tener complementos necesarios para usuarios externos o una licencia para usuarios internos. Para obtener más información sobre las licencias, consulte [powerapps y preguntas más frecuentes sobre licencias de Microsoft Flow](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq) y licencias de [portales de powerapps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing).

### <a name="suspended-portal"></a>Portal suspendido

Seguirá viendo notificaciones en el centro de administración de portales de PowerApps sobre la expiración del portal de prueba. Los portales de prueba expiran transcurridos 30 días. Si no convierte el portal en producción durante el período de prueba, el portal se apaga y se coloca en el estado suspendido. No podrá acceder a su portal después de su expiración.

Sin embargo, el portal suspendido se puede convertir en producción en los siete días siguientes a la suspensión. 

### <a name="deleted-portal"></a>Portal eliminado

Si no convierte su portal en producción en el período de suspensión de siete días, se eliminará el portal. Los datos del portal no se eliminan del entorno, pero se lanzará el espacio usado por el portal en un entorno y podrá crear un nuevo portal.

## <a name="convert-a-trial-portal-to-production"></a>Convertir un portal de prueba en producción

Puede convertir un portal de prueba en producción desde las notificaciones que se muestran en el centro de administración de portales de PowerApps.

> [!NOTE]
> Debe tener asignado uno de los roles siguientes para convertir un portal de prueba en producción:
> - Administrador global
> - Administrador del sistema

Cuando abra el [centro de administración](admin-overview.md) de portales de PowerApps y navegue hasta la pestaña detalles del [portal](portal-details.md) , verá la notificación sobre la expiración de la prueba que se muestra debajo del campo **tipo** .

> [!div class=mx-imgBorder]
> ![Notificación de prueba en la pestaña detalles del portal](../media/admin-center-convert-notif.png "Notificación de prueba en la pestaña detalles del portal")

En otras páginas del centro de administración, la notificación se muestra en la parte superior de la página.

> [!div class=mx-imgBorder]
> ![Notificación de prueba en otras pestañas](../media/admin-center-convert-notif-all.png "Notificación de prueba en otras pestañas")

Para convertir el portal de prueba en producción:

1.  En la notificación, seleccione **convertir**.

2.  Seleccione **confirmar**.

    > [!div class=mx-imgBorder]
    > ![Confirmación de prueba en producción](../media/trial-to-prod-confirm.png "Confirmación de prueba en producción")
