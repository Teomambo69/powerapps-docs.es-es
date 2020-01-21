---
title: 'Ejemplo: Crear una actividad personalizada (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear una actividad personalizada.
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
ms.openlocfilehash: f3d94d015c4fedc2bff838436c71bce9b8ddc13b
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934376"
---
# <a name="sample-create-a-custom-activity"></a>Ejemplo: crear una actividad personalizada

El ejemplo muestra cómo crear una actividad personalizada con [CreateEntityRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createentityrequest?view=dynamics-general-ce-9) y [CreateAttributeRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.createattributerequest?view=dynamics-general-ce-9). Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CustomActivity). 

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `CreateEntityRequest` y el mensaje `CreateAttributeRequest` están diseñados para usarse en un escenario para crear actividad personalizada.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprueba la versión actual de la organización actual.

### <a name="demonstrate"></a>Demostración

1. Crea la entidad de actividad personalizada con el mensaje `CreateEntityRequest`.
2. Publica la entidad de actividad personalizada creada.
3. Crea unos cuantos atributos para la entidad de actividad personalizada usando el mensaje `CreateAttributeRequest`.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
