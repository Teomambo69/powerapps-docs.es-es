---
title: Aplicación de lógica de negocios con código | Microsoft Docs
description: Obtenga información sobre cómo los desarrolladores pueden usar código para aplicar la lógica de negocios en Common Data Service for Apps.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/26/2018
ms.author: jdaly
ms.openlocfilehash: 12925c57103b1ecc00dc19205af5f32d165bdc63
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="apply-business-logic-with-code"></a>Aplicación de lógica de negocios con código

Siempre que sea posible, primero se debe intentar aplicar una de las distintas opciones de proceso declarativo cuando un requisito implica la definición de lógica de negocios. Vea [Crear una lógica de negocios personalizada con procesos (Guía de personalización de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

Cuando un proceso declarativo no cumple un requisito, como desarrollador tiene varias opciones. En este tema se presentarán opciones comunes para escribir código.

## <a name="create-a-workflow-extension"></a>Crear una extensión de flujo de trabajo

Se puede escribir un ensamblado .NET para proporcionar nuevas opciones en el Diseñador de procesos. Este método proporciona una nueva opción para los usuarios que usan el Diseñador de flujos de trabajo para aplicar una condición o realizar una acción nueva. Después, los usuarios que no son desarrolladores pueden reutilizar una extensión de flujo de trabajo para aplicar la lógica en el código.

Más información: [Actividades de flujo de trabajo personalizadas (ensamblados de flujo de trabajo) (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies)

## <a name="create-a-plug-in"></a>Crear un complemento

Puede escribir un ensamblado .NET como complemento para el flujo de transacciones de datos para aplicar la lógica de negocios en el servidor. Con la plataforma de aplicaciones Common Data Service for Apps hay un marco que permite registrar eventos específicos para ejecutar en un ensamblado el código definido en una clase. Esa clase hereda una interfaz específica que expone un [método Execute](/dotnet/api/microsoft.xrm.sdk.iplugin.execute). Cuando se produce el evento registrado, se invoca el método `Execute` de la clase y se pasan datos contextuales sobre el evento.

Para registrar los ensamblados se usa la *herramienta de registro de complementos*.

En el método `Execute`, se puede usar el modelo de objetos definido en los ensamblados del SDK para evaluar los datos de evento contextuales y realizar las acciones oportunas para hacer lo siguiente:
- Determinar si se debe cancelar la operación generando un error.
- Realizar cambios en los datos contextuales pasados al método Execute.
- Realizar operaciones adicionales para automatizar los procesos mediante el servicio de la organización.

### <a name="synchronous-and-asynchronous-plug-ins"></a>Complementos sincrónicos y asincrónicos
Los complementos se pueden registrar para ejecutarse de forma sincrónica dentro de la transacción, o bien se pueden diferir y enviar a una cola que aplicará la lógica en el momento de menor impacto en el servidor. Por este motivo, se prefieren los complementos asincrónicos.

Al registrar el complemento para que se ejecute de forma sincrónica para un evento, se puede elegir cuándo se debe ejecutar el código. Hay tres fases:

|Evento  |Descripción  |
|---------|---------|
|Anterior a la validación|Se produce antes de que comience la transacción de base de datos. Se trata de un buen lugar para aplicar la lógica de negocios para determinar si se debe cancelar la operación antes de que comience la transacción para evitar la penalización de rendimiento que supone revertir la transacción.|
|Anterior a la operación|Se produce una vez iniciada la transacción de base de datos. Si en esta fase se cancela una operación, se debe revertir la transacción|
|Posterior a la operación|Se produce dentro de la transacción de base de datos una vez completada la operación de datos principal. Incluye los cambios que se hayan aplicado en los eventos anteriores pero se produce una penalización incluso mayor al cancelar la operación.|

> [!NOTE]
> Los complementos sincrónicos tienen restricciones sobre la cantidad de recursos del sistema que pueden usar. Si un complemento supera los umbrales o deja de responder, se producirá una excepción si se cancela la operación.

Más información: [Desarrollo de complementos para la ampliación del proceso de negocio (Guía para desarrolladores de Dynamics 365 Customer Engagement)](/dynamics365/customer-engagement/developer/write-plugin-extend-business-processes)

### <a name="see-also"></a>Vea también

[Common Data Service for Apps Developer Overview](overview.md) (Introducción para desarrolladores de Common Data Service for Apps)
