---
title: 'Programadores: Prácticas recomendadas e instrucciones sobre la programación de complementos y flujos de trabajo para Common Data Service | Microsoft Docs'
description: Prácticas recomendadas e instrucciones sobre la programación de complementos y flujos de trabajo para desarrolladores de Common Data Service en Power Apps.
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
ms.date: 9/23/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8cf5d26243fe3c4f19eebebcdaea64477e364552
ms.sourcegitcommit: 5e23beed96cc14efae9ff264405956d59fae1e7c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "2944989"
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>Prácticas recomendadas e instrucciones sobre la programación de complementos y flujos de trabajo para Common Data Service

La siguiente lista contiene todas las instrucciones y prácticas recomendadas sobre la programación de complementos y flujos de trabajo en Common Data Service.

|Práctica recomendada  |Descripción  |
|---------|---------|
|[Evitar usar de tipos de solicitud por lotes en complementos y actividades de flujo de trabajo](avoid-batch-requests-plugin.md)|No debería usar clases de solicitud de mensajes ExecuteMultipleRequest o ExecuteTransactionRequest en situaciones con complementos o actividad de flujo de trabajo.|
|[Desarrollar implementaciones de IPlugin como sin estado](develop-iplugin-implementations-stateless.md)     |Los miembros de clases que implementan IPlugin se exponen a problemas potenciales de seguridad de los subprocesos que pueden llevar a incoherencia o problemas de rendimiento.         |
|[No duplicar el registro de paso de complemento](do-not-duplicate-plugin-step-registration.md)     |Duplicar el registro de paso de complemento provocará que el complemento se desencadene varias veces en el mismo mensaje o evento.         |
|[No utilizar ejecución en paralelo en complementos y actividades de flujo de trabajo](do-not-use-parallel-execution-in-plug-ins.md)|No se admite el subprocesamiento múltiple o paralelo en complementos o actividades de flujo de trabajo personalizadas.|
|[Implemente todos los tipos de consultas al filtrar resultados mediante PreOperation RetrieveMultiple](implement-all-types-of-queries-when-filtering-preoperation-retrievemultiple.md)|Para obtener el máximo rendimiento y resultados coherentes para todas las aplicaciones debe implementar el filtrado para todos los tipos de consultas que se pueden usar con complementos que se registran para la fase PreOperation de RetrieveMultiple|
|[Incluir atributos de filtrado con el registro de complementos](include-filtering-attributes-plugin-registration.md)     |Si no se configura ningún atributo de filtrado para un paso de registro de complementos, el complemento se ejecutará cada vez que un mensaje de la actualización se produzca para ese evento.         |
|[Limitar el registro de complementos para los mensajes Retrieve y de RetrieveMultiple](limit-registration-plugins-retrieve-retrievemultiple.md)     |Si se agrega lógica de complementos síncrona a los eventos de mensaje Retrieve y de RetrieveMultiple, se puede producir lentitud.         |
|[Optimizar el desarrollo de ensamblados personalizados](optimize-assembly-development.md)     |Considere combinar actividades separadas de complementos y flujo de trabajo personalizado en un único ensamblado personalizado para mejorar el rendimiento y la capacidad de retención y traspase actividades de complementos y flujo de trabajo personalizado a múltiples ensamblados personalizados si el tamaño de un ensamblado está cerca de los límite de tamaño de ensamblados en espacios independientes.         |
|[Quitar código no admitido que usa reflexión en actividades de flujo de trabajo personalizadas](remove-unsupported-code-using-reflection-workflow-activities.md)|Las actividades de flujo de trabajo que contienen código no admitido que usa reflexión aparecerán en los próximos meses a menos que se quiten.|
|[Establecer KeepAlive en false para interactuar con hosts externos en un complemento](set-keepalive-false-interacting-external-hosts-plugin.md)     |La propiedad KeepAlive establecida en true en el encabezado de solicitud HTTP o que no se haya definido explícitamente en false puede prolongar el tiempo de ejecución de los complementos.         |
|[Establecer tiempo de espera al realizar llamadas externas en un complemento](set-timeout-for-external-calls-from-plug-ins.md)     |Limite el período de tiempo que las llamadas externas esperarán una respuesta en los complementos.|   
|[Utilizar InvalidPluginExecutionException en actividades de complementos y de flujo de trabajo](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |Use InvalidPluginExecutionException al publicar errores en el contexto de las actividades de complemento o de flujo de trabajo.         |
|[Verificar dependencias de certificación para complementos que realizan llamadas salientes](verify-certification-dependencies.md)|Asegúrese de que los certificados de los que depende su código para las llamadas salientes tengan una cadena de certificados válida.|

### <a name="see-also"></a>Vea también

[Aplicar la lógica de negocios usando código](../../apply-business-logic-with-code.md)<br />
[Use complementos para ampliar los procesos de negocio](../../plug-ins.md)<br />
[Extensiones de flujo de trabajo](../../workflow/workflow-extensions.md)<br />