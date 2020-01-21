---
title: 'Ejemplo: Publicar un elemento en la cola (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo usar el mensaje ReleaseToQueueRequest.
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
ms.openlocfilehash: 9b773c8493b1305cea9b40f26499cc8f152f51d1
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934244"
---
# <a name="sample-release-a-queue-item-to-the-queue"></a>Ejemplo: Liberar un elemento en la cola

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-release-queue-item-queue-early-bound
Couldn't each of the operations in this series of samples be added to just one sample?
 -->
 Este ejemplo muestra cómo usar [ReleaseToQueueRequest](https://docs.microsoft.com/dotnet/api/microsoft.crm.sdk.messages.releasetoqueuerequest?view=dynamics-general-ce-9) para anular la asociación de un usuario de un elemento de cola con el que trabajó y devolver un elemento de cola a la cola. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ReleaseQueueItems).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `ReleaseToQueueRequest` está diseñado para usarse en un escenario donde contenga datos necesarios para volver a asignar un elemento de cola al propietario de la cola para que otros puedan seleccionarlo.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El mensaje `Queue` crea una nueva cola y almacena su GUID devuelto en una variable.
3. El mensaje `QueueItem` crea una nueva instancia de un queueitem e inicializa sus propiedades.
4. El `WhoAMIRequest` recupera información del usuario actual.

### <a name="demonstrate"></a>Demostración

El mensaje `ReleaseToQueueRequest` quita al trabajador del elemento de cola para liberar al objeto en cola de la cola de trabajador.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
