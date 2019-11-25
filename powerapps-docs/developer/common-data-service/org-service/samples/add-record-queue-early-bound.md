---
title: 'Ejemplo: agregar un registro a una cola (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo agregar registros a una cola.
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
ms.openlocfilehash: e342e7192f85112d682727e145aaf12f73a65ff8
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749681"
---
# <a name="sample-add-a-record-to-a-queue"></a>Ejemplo: agregar un registro a una cola

Este ejemplo muestra cómo agregar registros a una cola. Crea colas de origen y de destino. Agrega una actividad de carta a la cola de origen y luego la traslada a la cola de destino. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RecordToQueue).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los usuarios manualmente en **Office 365** para ejecutar el ejemplo sin errores. Para este ejemplo cree un perfil de usuario **tal cual** se muestra abajo. 

**Nombre**: Kevin<br/>
**Apellidos**: Cook<br/>
**Rol de seguridad**: jefe de ventas<br/>
**Nombre de usuario**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `AddToQueueRequest` está diseñado para usarse en un escenario donde contenga datos necesarios para mover el registro de la entidad de una cola de origen a la cola de destino.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. El método `Queue` crea colas de origen y de destino y almacena sus GUID devueltas en variable.
3. Crea una entidad Carta.
4. El método `AddToQueueRequest` agrega un registro de entidad en una cola, en este ejemplo asocia la carta a la primera cola.
5. Recupera el usuario creado manualmente en **Office 365** para asignar los elementos de la cola a la cola de usuario.

### <a name="demonstrate"></a>Demostración

1. El mensaje `RetrieveUserQueueRequest` recupera las colas privadas que el usuario conoce.
2. El mensaje `AddToQueueRequest` agrega el registro de una cola de origen a la cola de destino.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
