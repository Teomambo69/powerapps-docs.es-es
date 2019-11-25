---
title: 'Ejemplo: Enviar un mensaje de correo electrónico (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo enviar un correo electrónico.
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
ms.openlocfilehash: 0484580dd9e385866feb18cb25999436b726f4de
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749863"
---
# <a name="sample-send-an-email"></a>Ejemplo: enviar un mensaje de correo electrónico

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-send-email -->

Este ejemplo muestra cómo enviar un mensaje [SendEmailRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.sendemailrequest?view=dynamics-general-ce-9) por correo electrónico. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SenEmail).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `SendEmailRequest` está diseñado para usarse en un escenario donde contenga los datos necesarios para enviar un mensaje de correo electrónico.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Contact` crea un contacto al que enviar un correo electrónico a `(To: field)`.
1. El método `WhoAmIRequest` obtiene la información de usuario actual para enviar el correo electrónico `(From: field)`.
1. El método `ActivityParty` crea el grupo de actividad `To` y `From` para el correo electrónico.
1. El método `Email` crea un mensaje de correo electrónico.

### <a name="demonstrate"></a>Demostración

1. El método `SendEmailRequest` envía un mensaje de correo electrónico creado en [Configuración](#setup).

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en la [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
