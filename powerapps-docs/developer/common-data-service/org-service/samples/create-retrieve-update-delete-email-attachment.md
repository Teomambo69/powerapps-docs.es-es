---
title: 'Ejemplo: CRUD datos adjuntos de correo electrónico <Topic Title> (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo realizar operaciones CRUD en datos adjuntos de correo electrónico
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
ms.openlocfilehash: 93b995fb9e76416e7d34a0540f6b96dc50577243
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155860"
---
# <a name="sample-create-retrieve-update-and-delete-an-email-attachment"></a>Ejemplo: crear, recuperar, actualizar y eliminar datos adjuntos de correo electrónico

Este ejemplo muestra cómo crear, recuperar, actualizar y eliminar datos adjuntos de correo electrónico mediante el uso de los siguientes métodos:

- [IOrganizationService.Create](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.create?view=dynamics-general-ce-9)
- [IOrganizationService.Retrieve](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.retrieve?view=dynamics-general-ce-9)
- [IOrganizationService.Update](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.update?view=dynamics-general-ce-9)
- [IOrganizationService.Delete](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.iorganizationservice.delete?view=dynamics-general-ce-9)

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CRUDEmailAttachements).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `IOrganizationService` está diseñado para usarse en un escenario que proporciona acceso mediante programación a los metadatos y los datos de una organización.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `Email` crea la actividad de correo electrónico necesaria para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `ActivityMimeAttachment` crea tres datos adjuntos de correo electrónico. 
1. El método `Retrieve` recupera datos adjuntos incluido el Id., tema, nombre de archivo y cuerpo.
1. El método `Update` actualiza el nombre del archivo adjunto existente.


### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.


