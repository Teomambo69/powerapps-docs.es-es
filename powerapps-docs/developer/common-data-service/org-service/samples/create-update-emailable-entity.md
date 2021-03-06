---
title: " Crear y actualizar una entidad que se puede enviar por correo electrónico (Common Data Service) | Microsoft Docs"
description: Este ejemplo muestra cómo crear y actualizar una entidad que se puede enviar por correo electrónico.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 26150d445c129658b91c51810c99e74ff56e5f64
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155856"
---
# <a name="create-an-email-entity"></a>Crear una entidad de correo electrónico

Este ejemplo muestra cómo crear y actualizar una entidad mediante el mensaje [CreateEntityRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createentityrequest?view=dynamics-general-ce-9).

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CreateUpdateEmailableEntity).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `CreateEntityRequest` está diseñado para usarse en un escenario que contiene los datos necesarios para crear una entidad personalizada y, opcionalmente, para agregarla a una solución no administrada especificada.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `Entity` crea la entidad personalizada. Defina la entidad para habilitar el envío por correo electrónico. Para ello, `IsActivityParty` debe establecerse en verdadero.
2. El método `StringAttributeMetadata` se utiliza para definir el atributo principal de la entidad que se utiliza en las pantallas de ActivityParty. Asegúrese de seleccionar atributos descriptivos.
3. El método `PublishRequest` publica todas las personalizaciones.
4. El método `CreateFirstEmailAttributeRequest` crea un atributo de correo electrónico para crear correos electrónicos desde la entidad.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

