---
title: Actualizar un portal | MicrosoftDocs
description: Aprenda a actualizar un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 7f8837179ccf9edb7376db88ee421e4cb424909f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978565"
---
# <a name="upgrade-a-portal"></a>Actualizar un portal

Esta sección le ayuda a comprender el proceso de publicación de los portales de Dynamics 365 para la preparación adecuada de una nueva versión y para la reducción de cualquier impacto en los clientes. También trata sobre distintos componentes que forman parte del portal.

Un portal consta de los componentes siguientes:

|Componente|Descripción|Proceso de actualización|
|---------|-----------|--------------|
|Soluciones de portal|Las soluciones que están instaladas en el entorno de Common Data Service y que contienen las entidades de metadatos para cualquier portal.|Actualizado por los propios clientes desde la página del Centro de administración de Dynamics 365.|
|Host del sitio web del portal|El host del sitio web del portal es el código de portal que forma el verdadero sitio web.|El host del sitio web del portal se actualiza automáticamente para todos los portales.<br>**Nota**: Una nueva versión del host del sitio web del portal es compatible con todas las versiones anteriores admitidas de soluciones de portal. Sin embargo, una vez que una versión de la solución no es compatible, no se certifica su ejecución con la nueva versión del host del sitio web del portal.|
|||

## <a name="impact-of-new-releases-on-a-portal-solution"></a>Impacto de las nuevas versiones en una solución de portal

Como parte de la versión del portal, los hosts del sitio web del portal se actualizan de forma automática a las últimas versiones y los clientes actualizan las soluciones de portal. Es importante comprender el impacto de cada actualización del componente en su portal en directo, por lo que puede realizar la planificación como corresponda.

### <a name="portal-website-host-update"></a>Actualización del host del sitio web del portal

Si está ejecutando una versión de producción del portal (puede verlo en el Centro de administración de portales de Power Apps), no habrá tiempo de inactividad en el portal en directo cuando se actualice el portal. Sin embargo, si está ejecutando una versión de prueba del portal, habrá aproximadamente 6-10 minutos de tiempo de inactividad, y no podrá obtener acceso al portal.

### <a name="portal-solution-update"></a>Actualización de la solución de portal

Cuando instale o actualice una solución en la instancia, detectará alguna inestabilidad en la instancia. El proceso de actualización de la solución de portal actualiza las soluciones disponibles en la instancia y afectará a la instancia que a su vez tendrá un impacto en su portal. Por lo tanto, se recomienda siempre realizar actualizaciones de soluciones en la instancia durante las horas de menor actividad.

## <a name="get-notified-about-new-releases"></a>Obtener notificaciones sobre las nuevas versiones

Se avisará a los clientes sobre la nueva versión del portal a través del Centro de mensajes de Office 365 (en el Centro de administración de Microsoft 365). Asegúrese de que dispone de acceso al Centro de mensajes de Office 365 (el administrador global y el administrador de servicios tienen acceso) o que ha hablado con su administrador global o de servicios sobre la nueva versión del portal.

Las notificaciones se envían en 2-5 días laborables después del lanzamiento. Las notificaciones se envían solo a los clientes cuyos portales se piensan actualizar. Cada notificación proporciona información del tipo de actualización y la fecha/hora de implementación junto con el vínculo a las notas de la versión.

## <a name="enable-a-portal-for-new-release"></a>Habilitar un portal para el nuevo lanzamiento

Puede habilitar el portal de prueba o desarrollo para recibir una actualización anticipada antes que todos los clientes. De esa manera, podrá probar todos los escenarios principales en su portal de prueba antes de que las actualizaciones se implementen en su portal en directo. Las actualizaciones anticipadas se implementan al menos una semana antes de la implementación global de cualquier lanzamiento. Además, las notificaciones de actualizaciones anticipadas se envían según se describe en la sección [Obtener notificaciones sobre las nuevas versiones](#get-notified-about-new-releases).

Para habilitar un portal para una actualización anticipada:

1.  Abra [Centro de administración de Portales de Power Apps](admin-overview.md).

2.  En la pestaña **Acciones del portal**, seleccione **Habilitar portal para la actualización anticipada**.

    > [!div class="mx-imgBorder"]
    > ![Habilitar un portal para la actualización anticipada](../media/upgrade-portal.png "Habilitar un portal para la actualización anticipada")

> [!NOTE]
> Puede habilitar o deshabilitar un portal para la actualización anticipada en cualquier momento. Sin embargo, se toma una instantánea para todos los portales marcados para el acceso anticipado dos días antes de cualquier publicación, y cualquier portal marcado para el acceso anticipado que no esté garantizado para obtener una actualización anticipada.

Si se produce algún problema durante la fase de actualización anticipada, puede informar de él a través del soporte técnico de Microsoft.


