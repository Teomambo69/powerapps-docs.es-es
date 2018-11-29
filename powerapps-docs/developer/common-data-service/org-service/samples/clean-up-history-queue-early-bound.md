---
title: 'Ejemplo: Limpiar historial de una cola (Common Data Service para aplicaciones) | Microsoft Docs'
description: En este ejemplo se muestra cómo liberar el historial de una cola
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-clean-up-history-for-a-queue"></a>Ejemplo: limpiar el historial de una cola

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-clean-up-history-queue-early-bound -->

 Este ejemplo muestra cómo limpiar el historial de la cola mediante [RemoveFromQueueRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.removefromqueuerequest?view=dynamics-general-ce-9) con elementos inactivos. Encuentra las llamadas de teléfono completadas en la cola y quita los elementos asociados de la cola. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/CleanHistoryQueue).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `RemoveFromQueueRequest` está diseñado para usarse en un escenario para liberar el historial de cola con elementos inactivos.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Crea una instancia de cola y establece sus valores de propiedad.
3. Se crea una instancia de actividad de llamada de teléfono y también una instancia de queueitems y se inicializan sus propiedades.
4. Marca la llamada de teléfono como completada. 

### <a name="demonstrate"></a>Demostración

1. Recupera el queueitem con llamadas de teléfono inactivas de una cola con el mensaje [RemoveFromQueueRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.removefromqueuerequest?view=dynamics-general-ce-9).

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
