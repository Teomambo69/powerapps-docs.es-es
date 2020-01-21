---
title: Aplica la lógica de negocios en Common Data Service | MicrosoftDocs
description: Obtenga información sobre los diferentes tipos de lógica de negocios que puede usar en su aplicación
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9267f8385e19d3c0b87a36b495a4ff2b88b4d420
ms.sourcegitcommit: f70be39855e4931312fe0035525586a15ed4487b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2019
ms.locfileid: "2922389"
---
# <a name="apply-business-logic-in-common-data-service"></a>Aplicar la lógica de negocios en Common Data Service
Hay varias opciones disponibles para aplicar la lógica de negocios en Common Data Service. 

## <a name="business-rules"></a>Reglas de negocio
Puede crear reglas de negocio y recomendaciones para aplicar lógica y validaciones sin escribir código ni crear complementos. Las reglas de negocio proporcionan una interfaz básica para implementar y mantener reglas de rápida evolución y de uso general.

Defina las *reglas de negocio* de una entidad que se aplica a todos los formularios de entidad y en el nivel de servidor. Las reglas de negocio definidas para una entidad se aplican a las *aplicaciones de lienzo* y las *aplicaciones basadas en modelos* si la entidad se usa en la aplicación. Más información: [Crear una regla de negocio para una entidad](data-platform-create-business-rule.md).

> [!NOTE]
> Para definir una regla de negocio que se aplique a un formulario en una aplicación basada en modelos, consulte [Crear reglas de negocio para un formulario de aplicaciones controladas por modelos](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

## <a name="power-automate"></a>Power Automate
Power Automate tiene varios flujos diferentes que puede usar para crear flujos de trabajo automatizados en Common Data Service o entre Common Data Service y otra aplicación o servicio que se puede utilizar para sincronizar archivos, recibir notificaciones, recopilar datos y más. 


|Tipo de flujo  |Descripción  |Más información  |
|---------|---------|---------|
|Flujos de proceso de negocio     | Defina un conjunto de pasos que se ejecutan en una aplicación basada en modelos de Power Apps para que la gente los siga para obtener el resultado deseado.        | [Más información](/power-automate/create-business-process-flow)     |
|Flujos automatizados     |  Cree un flujo que realizará una o varias tareas automáticamente después de que un evento lo desencadene.    | [Más información](/power-automate/get-started-logic-flow)        |
|Flujos de botones   | Ejecute tareas repetitivas desde cualquier lugar, en cualquier momento, a través de una aplicación de flujo en su dispositivo móvil.        | [Más información](/power-automate/introduction-to-button-flows)        |
|Flujos programados   | Cree un flujo que realiza una o más tareas en una programación.    | [Más información](/power-automate/run-scheduled-tasks)        |
|Flujos de interfaz de usuario   | Grabe y automatice la reproducción de pasos manuales en software heredado.    | [Más información](/power-automate/ui-flows/overview)     |


## <a name="classic-common-data-service-processes"></a>Procesos de Common Data Service clásicos
También puede usar los procesos de Common Data Service clásicos, que son flujos de trabajo y acciones. Más información: [Power Automate: Usar procesos de flujo de trabajo](/flow/workflow-processes) y [Power Automate: Información general sobre acciones](/flow/actions).

### <a name="see-also"></a>Vea también

[Aplicar la lógica de negocios en aplicaciones basadas en modelos](../model-driven-apps/guide-staff-through-common-tasks-processes.md)
