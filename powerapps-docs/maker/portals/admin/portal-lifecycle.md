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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756804"
---
# <a name="about-portal-lifecycle"></a>Acerca del ciclo de vida de portales

Un portal se crea siempre como prueba. Un portal de prueba, que expira después de 30 días, es útil para probar sus funciones sin coste alguno. Después de la caducidad, se suspende y se cierra un portal. Siete días después de la suspensión, el portal de prueba se elimina. En cada cambio de fase del ciclo de vida del portal, por ejemplo, al aproximarse la suspensión, suspendido, eliminado y convertido de prueba a producción, recibirá notificaciones del sistema y mediante correo electrónico.

Como administrador, puede convertir un portal en prueba o suspendido a un portal de producción. Mientras convierte un portal de prueba a producción, asegúrese de que el entorno es también un entorno de producción. No es posible convertir un portal de prueba en producción en un entorno de prueba. Si elimina el entorno en el que se crea un portal de prueba, el portal también se elimina.

El primer portal se crea gratis en un entorno en un inquilino. Si necesita crear más de un portal, debe tener 1 GB de espacio de almacenamiento no usado en el inquilino.

## <a name="stages-in-portal-lifecycle"></a>Fases en el ciclo de vida del portal

### <a name="trial-portal"></a>Portal de prueba

Un portal se crea siempre como portal de prueba. Puede convertirlo a producción desde el Centro de administración de portales de PowerApps si tiene las licencias requeridas. Para obtener información sobre convertir un portal de prueba a producción, consulte [Convertir un portal de prueba en producción](#convert-a-trial-portal-to-production).

Para convertir un portal de prueba en producción, el entorno debe tener complementos requeridos para usuarios externos, o una licencia para usuarios internos. Para obtener más información sobre las licencias, consulte [Preguntas frecuentes sobre licencias de PowerApps y Microsoft Flow ](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq) y [Licencias de portales de PowerApps](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing).

### <a name="suspended-portal"></a>Portal suspendido

Seguirán mostrándose notificaciones en el Centro de administración de portales de PowerApps sobre la caducidad del portal de prueba. Los portales de prueba expiran después de 30 días. Si no convierte el portal a producción en el período de prueba, el portal se cierra y se sitúa en estado suspendido. No podrá obtener acceso al portal después de su caducidad.

Sin embargo, el portal suspendido se puede seguir convertiendo a producción en un plazo de siete días de la suspensión. 

### <a name="deleted-portal"></a>Portal eliminado

Si no convierte el portal a producción en el período de siete días desde la suspensión, se elimina el portal. Los datos del portal no se eliminan del entorno, pero el espacio usado por el portal en un entorno se liberará, y podrá crear un nuevo portal.

## <a name="convert-a-trial-portal-to-production"></a>Convertir un portal de prueba a producción

Puede convertir un portal de prueba a producción desde las notificaciones mostradas en el Centro de administración de portales de PowerApps.

> [!NOTE]
> Debe tener asignado uno de los siguientes roles para convertir un portal de prueba a producción:
> - Administrador global
> - Administrador del sistema

Al abrir el [Centro de administración de portales de PowerApps](admin-overview.md) y navegar a la pestaña [Detalles del portal](portal-details.md), verá la notificación sobre la caducidad de prueba mostrada en el campo **Tipo**.

> [!div class=mx-imgBorder]
> ![Notificación de prueba en pestaña Detalles del portal](../media/admin-center-convert-notif.png "Notificación de prueba en pestaña Detalles del portal")

En otras páginas en el centro de administración, la notificación se muestra en la parte superior de la página.

> [!div class=mx-imgBorder]
> ![Notificación de prueba en otras pestañas](../media/admin-center-convert-notif-all.png "Notificación de prueba en otras pestañas")

Para convertir un portal de prueba a producción:

1.  En la notificación, seleccione **Convertir**.

2.  Seleccione **Confirmar**.

    > [!div class=mx-imgBorder]
    > ![Confirmación de prueba a producción](../media/trial-to-prod-confirm.png "Confirmación de prueba a producción")
