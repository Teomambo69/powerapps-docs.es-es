---
title: 'Ejemplo: Enviar los resultados de supervisión y correo electrónico en masa(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo enviar mensajes de correo electrónico en masa y supervisar los resultados
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
ms.openlocfilehash: 38fc84985d86d44524b557a90a84f5a071600aaa
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749866"
---
# <a name="sample-send-bulk-email-and-monitor-results"></a>Ejemplo: enviar los resultados de supervisión y correo electrónico en masa

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-send-bulk-email-monitor-results -->

Este ejemplo muestra cómo enviar correos electrónicos en masa mediante <xref:Microsoft.Crm.Sdk.Messages.SendBulkMailRequest> y controlar los resultados recuperando registros de la entidad `AsyncOperation`. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/BulkEmail).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `SendBulkMailRequest` está diseñada para usarse en un escenario para enviar mensajes de correo electrónico en masa.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización
1. El método `Contact` crea 2 registros de contacto para este ejemplo.

### <a name="demonstrate"></a>Demostración

1. Obtiene el usuario del sistema para usar como remitente.
2. Establezca el Id. de seguimiento para la solicitud de correo electrónico en masa.
3. Crea una expresión de consulta para que la operación en masa recupere los contactos de la lista de correo electrónico.
4. Establezca el Id. referente a y ejecute la solicitud de correo electrónico en masa.
5. Recupere la operación asincrónica de correo electrónico en masa y supervísela mediante sondeo.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
