---
title: 'Ejemplo: Ejecutar varias solicitudes (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo ejecutar varias solicitudes de mensaje de la organización mediante una sola llamada al método de servicio web.
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
ms.openlocfilehash: e3e83344f0573ca2196fbdb30d5027e06cd37414
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749896"
---
# <a name="sample-execute-multiple-requests"></a>Ejemplo: ejecutar varias solicitudes

En este ejemplo se muestra cómo ejecutar varias solicitudes de la organización mediante una sola llamada al método de servicio web, pasando [ExecuteMultipleRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.executemultiplerequest?view=dynamics-general-ce-9) como parámetro. Reducir el número de solicitudes de mensajes que se deben transferir a través de la red da lugar a un mayor rendimiento del procesamiento de mensajes.

Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExecutemultipleRequests).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `ExecuteMultipleRequest` está diseñado para usarse en un escenario donde contiene los datos necesarios para ejecutar una o varias solicitudes de mensajes como una sola operación por lotes y devolver opcionalmente una colección de resultados.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `ExecuteMultipleRequest` crea el objeto `ExecuteMultipleRequest`.
1. El método `ExecutingMultipleSettings` asigna los valores que definen el comportamiento de la ejecución: continuar con error, respuestas devolución.
1. El método `OrganizationRequestCollection` crea una colección vacía de solicitudes de la organización.
1. El método `CreateRequest` se agrega a cada entidad a la colección de la solicitud.
1. La clase `GetCollectionOdEntitiesToUpdate` actualiza las entidades que se crearon anteriormente.


### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en la [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
