---
title: 'Ejemplo: Finalizar una cita periódica (Common Data Service) | Microsoft Docs'
description: En este ejemplo muestra cómo finalizar una serie de citas periódicas
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
ms.openlocfilehash: 899a7111f4b206c1d405806522882e7f188e3642
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934300"
---
# <a name="sample-end-a-recurring-appointment-series"></a>Ejemplo: cerrar una serie de citas periódicas

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-end-recurring-appointment-series -->

Este ejemplo muestra cómo finalizar una serie de citas periódicas con el mensaje [DeleteOpenInstancesRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.deleteopeninstancesrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/EndRecurringAppointment).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `DeleteOpenInstanceRequest` está diseñado para usarse en un escenario con los datos que necesarios para eliminar las instancias de una cita periódica maestra con un estado `Open`.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Define los tipos anónimos que definen los posibles valores de patrón periódico, los valores posibles por días y los valores de tipo de finalización de patrón de reglas.
3. Crea una nueva cita periódica necesaria para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El mensaje `RecurringAppointmentMaster` recupera una serie de citas periódicas que se crea en [Configuración](#setup).
2. El mensaje `DeleteOpenInstanceRequest` finaliza la serie de citas periódicas hasta la última fecha de la instancia anterior que se produjo con respecto a la fecha de finalización de la serie.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
