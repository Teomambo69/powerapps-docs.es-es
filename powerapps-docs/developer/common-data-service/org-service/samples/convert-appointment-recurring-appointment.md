---
title: 'Ejemplo: Convertir una cita en una cita periódica (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo convertir una cita en una serie de citas periódicas.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4125ffa1bf8d5c21646265fc2020484916af291f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749534"
---
# <a name="sample-convert-an-appointment-to-a-recurring-appointment"></a>Ejemplo: convertir una cita en una cita periódica

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-convert-appointment-recurring-appointment -->

Este ejemplo muestra cómo convertir una cita en una serie de citas periódicas mediante el mensaje [AddRecurrenceRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.addrecurrencerequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ConvertToRecurring).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `AddRecurrenceRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para agregar la información de periodicidad a una cita existente.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. Se crea una cita de ejemplo que se convierte más adelante en una cita periódica.

### <a name="demonstrate"></a>Demostración

1. Especifica la información de frecuencia que es necesario agregar a la cita creada en [Configuración](#setup).
2. Define los tipos anónimos que definen los valores de patrón periódico posibles y también los valores posibles para días.
3. Define los tipos anónimos que definen los valores posibles para el tipo y el patrón de reglas periódicas.
4. `RecurringAppointmentMaster` especifica la información de la frecuencia. 
5. El mensaje `AddRecurrence` convierte la cita creada en una cita periódica.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). 

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los datos de ejemplo para obtener el mismo resultado.
