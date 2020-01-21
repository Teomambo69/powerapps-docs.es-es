---
title: 'Ejemplo: Enviar un mensaje de correo electrónico usando una plantilla(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo enviar un mensaje de correo electrónico usando una plantilla.
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
ms.openlocfilehash: ad31b71f2e3d7482d58df853872577c80c727cf4
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934172"
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
