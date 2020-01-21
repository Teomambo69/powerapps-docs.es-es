---
title: 'Ejemplo: Reprogramar y cancelar una cita periódica(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo reprogramar y cancelar una cita periódica.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2d59aa35a81ed776f712b55e7f7179087dfaf061
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934240"
---
# <a name="sample-reschedule-and-cancel-a-recurring-appointment"></a>Ejemplo: reprogramar y cancelar una cita periódica

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-reschedule-cancel-recurring-appointment -->

Este ejemplo muestra cómo reprogramar y cancelar las instancias de cita de una serie de citas periódicas mediante el mensaje [RescheduleRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.reschedulerequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RecurringAppointment).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RescheduleRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para reprogramar una cita, una cita periódica o una cita de servicio (actividad de servicio).

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización. 
2. Define un tipo anónimo para definir los valores y los valores y valores posibles de patrón periódico para días de la semana.
3. Define un tipo anónimo para definir los valores posibles para el tipo de finalización de patrón de reglas periódicas.
4. El `RecurringAppointmentMaster` crea una nueva cita periódica.

### <a name="demonstrate"></a>Demostración

1. El mensaje `QueryExpression` consulta la instancia de cita individual que corresponde a hoy o 10 días después. Básicamente será la segunda instancia de la serie de citas periódicas.
3. El mensaje `RescheduleRequest` actualiza las fechas de inicio y finalización de la programación de la cita.
4. El mensaje `SetStateRequest` cancela la última instancia de la cita. El estado de esta instancia de cita se establece como `canceled`. Puede ver esta instancia de cita en la vista `All Activities`.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
