---
title: 'Ejemplo: Enviar un mensaje de correo electrónico usando una plantilla(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo enviar un mensaje de correo electrónico usando una plantilla.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: ebfdb8d72d9a14cd6f87eb0a5244752dfa7e0d70
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155588"
---
# <a name="sample-send-an-email-using-a-template"></a>Ejemplo: enviar un mensaje de correo electrónico usando una plantilla

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-send-email-template -->

Este ejemplo muestra cómo enviar un mensaje de correo electrónico usando una plantilla con el mensaje de [SendEmailFromTemplateRequest.](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.sendemailfromtemplaterequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SendEmailUsingTemp).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `SendEmailFromTemplateRequest` está diseñado para usarse en un escenario donde contenga datos necesarios para enviar un correo electrónico usando una plantilla.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea un registro de contacto al que enviar un correo electrónico (campo Para:).

### <a name="demonstrate"></a>Demostración

1. La `ActivityParty` crea el grupo de actividad `From:` y `To:` para el correo electrónico.
2. Crea un mensaje de correo electrónico.
3. La `QueryExpression` consulta para obtener una de las plantillas de correo electrónico de tipo `Contact`.
4. La `SendEmailFromTemplateRequest` envía un mensaje de correo electrónico usando una plantilla.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
