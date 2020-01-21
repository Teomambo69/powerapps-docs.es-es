---
title: 'Ejemplo: Validar una cita (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo validar una cita
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
ms.openlocfilehash: d49ad9ed6440076d20e771b099227b35dbf7ae36
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934160"
---
# <a name="sample-validate-an-appointment"></a>Ejemplo: validar una cita

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-validate-appointment -->

En este ejemplo se muestra cómo validar una cita usando el mensaje [ValidateRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.validaterequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ValidateAppointment).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `ValidateRequest` está diseñado para usarse en el escenario donde contiene datos necesarios para comprobar que una cita o una cita de servicio (actividad de servicio) tiene recursos disponibles válidos para la actividad, la duración, y el sitio, según sea necesario.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea registros de contactos y grupos de actividad de ejemplo.
3. Crea una cita de ejemplo.

### <a name="demonstrate"></a>Demostración

1. Recupera la cita para validar. 
2. El mensaje `ValidateRequest` valida la cita creada en la Setup(#setup).

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
