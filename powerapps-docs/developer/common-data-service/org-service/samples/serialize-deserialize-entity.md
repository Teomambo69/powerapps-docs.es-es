---
title: " Serializar y deserializar instancias de entidad (Common Data Service) | Microsoft Docs"
description: En este ejemplo se muestra cómo serializar y deserializar instancias de entidad.
ms.custom: ''
ms.date: 12/20/2019
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
ms.openlocfilehash: 6bc85049df107821dd8cdaba0a33b1ec0f15a979
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934577"
---
# <a name="serialize-and-deserialize-an-entity-instance"></a>Serializar y deserializar una instancia de entidad 

Este ejemplo muestra cómo serializar las instancias de entidad de enlace en tiempo de compilación y en tiempo de ejecución a un formato XML, y cómo deserializar de un formato XML a una instancia de entidad de enlace en tiempo de compilación.

Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/SerializeDeserializeEntity).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

Vea [Cómo ejecutar ejemplos](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) para obtener información sobre cómo ejecutar este ejemplo.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

El mensaje `DataContractSerializer` está destinado a utilizarse en un escenario en el que serializa y deserializa una instancia de un tipo en una secuencia o documento XML utilizando un contrato de datos suministrado. Esta clase no puede heredarse.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
1. El método `CreateRequiredRecords` crea los datos de ejemplo necesarios para el ejemplo.

### <a name="demonstrate"></a>Demostración

1. El método `DataContractSerializer` serializa los registros de contacto en XML y los escribe en el disco duro. 
1. El método `earlyBoundSerializer` deserializa la instancia de la entidad.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.

