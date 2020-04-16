---
title: 'Ejemplo: promocionar un mensaje de correo electrónico (Common Data Service) | Microsoft Docs'
description: <Description>
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
ms.openlocfilehash: c75b3d4b147888345812aed5d7267b08a9adb8a4
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155700"
---
# <a name="sample-promote-an-email-message"></a>Ejemplo: promover un mensaje de correo electrónico 

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-promote-email-message -->

Este ejemplo muestra cómo crear una instancia de actividad de correo electrónico a partir del mensaje de correo electrónico especificado en Common Data Service, mediante el mensaje [DeliverPromoteEmailRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.deliverpromoteemailrequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PromoteEmail).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `DeliverPromoteEmailRequest` está diseñado para usarse en un escenario donde contenga datos necesarios para crear el registro de la entidad de correo electrónico de un mensaje de correo electrónico específico.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Crea un contacto para enviar un correo electrónico a (a: campo).
2. El `WhoAmIRequest` recupera el usuario del sistema para intenta enviar el correo electrónico (de: campo).
3. El mensaje `DeliverPromoteEmailRequest` crea la solicitud y también la ejecuta.
4. Compruebe el éxito definiendo los tipos anónimos que definen los valores posibles para el estado de su correo electrónico. 
5. Consulta el correo electrónico entregado y comprueba que el código de estado es `sent`.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
