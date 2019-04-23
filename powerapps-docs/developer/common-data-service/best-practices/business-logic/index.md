---
title: 'Desarrolladores: Procedimientos recomendados e instrucciones para el desarrollo de complementos y flujos de trabajo en Common Data Service | Microsoft Docs'
description: Procedimientos recomendados e instrucciones dirigidos a desarrolladores que trabajan en el desarrollo de complementos y flujos de trabajo con Common Data Service en PowerApps.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 60e489ffd35f0e07f9a22f65336b242b7e0e2652
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61528421"
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>Procedimientos recomendados e instrucciones para el desarrollo de complementos y flujos de trabajo en Common Data Service

Aquí se enumeran todas las instrucciones y procedimientos recomendados para el desarrollo de complementos y flujos de trabajo en Common Data Service.

|Procedimiento recomendado  |Descripción  |
|---------|---------|
|[Evitar el uso de tipos de solicitud por lotes en actividades de complementos y flujos de trabajo](avoid-batch-requests-plugin.md)     |No se deben usar las clases de solicitud de mensaje ExecuteMultipleRequest o ExecuteTransactionRequest en el contexto de un complemento o una actividad de flujo de trabajo.         |
|[Desarrollar implementaciones IPlugin como sin estado](develop-iplugin-implementations-stateless.md)     |Los miembros de clases que implementan IPlugin están expuestos a posibles problemas de seguridad de subprocesos que podrían producir problemas de rendimiento o incoherencia de datos.         |
|[No duplicar el registro de pasos en complementos](do-not-duplicate-plugin-step-registration.md)     |El registro de pasos duplicados en un complemento hará que dicho complemento se desencadene varias veces en el mismo mensaje o evento.         |
|[Incluir atributos de filtro con el registro de complementos](include-filtering-attributes-plugin-registration.md)     |Si no se establecen atributos de filtro para un paso de registro de complemento, el complemento se ejecutará cada vez que se produzca un mensaje de actualización para ese evento.         |
|[Limitar el registro de complementos para mensajes Retrieve y RetrieveMultiple](limit-registration-plugins-retrieve-retrievemultiple.md)     |Agregar lógica de complemento sincrónico a los eventos de mensajes Retrieve y RetrieveMultiple puede provocar ralentización.         |
|[Optimizar el desarrollo de ensamblados personalizados](optimize-assembly-development.md)     |Considere la posibilidad de combinar actividades distintas de flujos de trabajo y complementos en un único ensamblado personalizado para mejorar el rendimiento y el mantenimiento, y mueva las actividades de flujos de trabajo y complementos a varios ensamblados personalizados si el tamaño de un ensamblado está próximo a las restricciones de tamaño de ensamblado.         |
|[Establecer KeepAlive en False al interactuar con hosts externos en un complemento](set-keepalive-false-interacting-external-hosts-plugin.md)     |Si se establece la propiedad KeepAlive en True en el encabezado de solicitud HTTP o no se define explícitamente como False, podría provocar que los complementos tarden más tiempo en ejecutarse.         |
|[Usar InvalidPluginExecutionException en actividades de complementos y flujos de trabajo](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |Use InvalidPluginExecutionException al provocar errores en el contexto de un complemento o una actividad de flujo de trabajo.         |

# <a name="see-also"></a>Vea también
[Aplicar lógica de negocios con código](../../apply-business-logic-with-code.md)<br />
[Usar complementos para extender procesos de negocio](../../plug-ins.md)<br />
[Extensiones de flujo de trabajo](../../workflow/workflow-extensions.md)<br />