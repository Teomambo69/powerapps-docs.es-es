---
title: 'Ejemplo: Especificar un elemento de cola para trabajar en él (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo especificar un usuario que trabajará en un elemento de cola.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-specify-a-queue-item-to-work-on"></a>Ejemplo: Especificar un elemento de cola para trabajar

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-specify-queue-item-work-early-bound -->

Este ejemplo muestra cómo usar [PickFromQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.pickfromqueuerequest?view=dynamics-general-ce-9) para especificar un usuario que va a trabajar en un elemento de cola. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SpecifyQueueItem).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `PickFromQueueRequest` está diseñado para usarse en un escenario donde contenga datos necesarios para asignar un elemento de cola a un usuario y opcionalmente quitar el elemento de la cola.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `Queue` crea una instancia de cola privada y establece sus valores de propiedad.
3. El método `QueueItem` crea una nueva instancia de un queueitem e inicializa sus propiedades.

### <a name="demonstrate"></a>Demostración

1. El método `WhoAmIRequest` recupera información del usuario actual.
1. El método `PickFromQueueRequest` crea una instancia de un queueitem existente para especificar el usuario que trabajará en él.


### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
