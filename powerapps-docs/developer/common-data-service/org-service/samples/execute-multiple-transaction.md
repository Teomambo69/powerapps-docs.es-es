---
title: 'Ejemplo: ejecutar varias solicitudes en transacción (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo ejecutar varias solicitudes en una transacción.
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
ms.openlocfilehash: 8c04354bf87aaeee43376fd974d8666895e463ff
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155776"
---
# <a name="sample-execute-multiple-requests-in-transaction"></a>Ejemplo: Ejecutar varias solicitudes en transacción

En este ejemplo se muestra cómo utilizar una sola llamada de método web para ejecutar todas las solicitudes de mensaje en una colección como parte de una sola transacción de base de datos. Un requisito común en aplicaciones de negocios es la coordinación de los cambios de varios registros en el sistema de modo que todos se produzcan todos los cambios de datos ninguno de ellos. En términos de la base de datos, esto se conoce como ejecutar varias operaciones en una sola transacción con la capacidad de revertir todos los cambios de los datos cuando hay error en una operación.

Puede ejecutar dos o varias solicitudes de servicio de la organización en una sola transacción de la base de datos mediante el uso de la solicitud de mensajes [ExecuteTransactionRequest](https://docs.microsoft.com/dotnet/api/microsoft.xrm.sdk.messages.executetransactionrequest?view=dynamics-general-ce-9). 

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/ExecuteMultipleInTransaction).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `ExecuteTransactionRequest` está diseñado para usarse en un escenario donde contiene los datos necesarios para ejecutar una o varias solicitudes de mensajes en una sola transacción de la base de datos y devolver opcionalmente una colección de resultados.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. El método `ExecuteTransactionRequest` crea el objeto `ExecuteTransactionRequest`.
2. El método `OrganizationRequestCollection` crea una colección vacía de solicitudes de la organización.
3. El método `CreateRequest` se agrega a cada entidad a la colección de la solicitud.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
