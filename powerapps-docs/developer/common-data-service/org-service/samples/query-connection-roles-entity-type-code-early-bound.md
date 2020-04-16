---
title: 'Ejemplo: consulta de rol de conexión por el código de tipo de entidad (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo hacer una consulta a un rol de conexión
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
ms.openlocfilehash: d4354e2a861f6b0f68916c2c9ca2104429c2b443
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155696"
---
# <a name="sample-query-connection-roles-by-entity-type-code-early-bound"></a>Ejemplo: roles de conexión de consulta por código de tipo de entidad (enlace en tiempo de compilación)

Este ejemplo muestra cómo usar una consulta para buscar un rol de conexión para una entidad cuenta mediante la especificación de un código de tipo de entidad. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryRoleByEntityType).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo usar una consulta para buscar un rol de conexión para una entidad cuenta mediante la especificación de un código de tipo de entidad.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Define algunos tipos anónimos para definir el intervalo de los valores de propiedad de conexión posibles.
2. `ConnectionRole` crea un rol de conexión.
3. `QueryExpression` consulta todos los roles de conexión.
4. `ConnectionRoleObjectTypeCode` crea un rol de tipo de objeto de conexión del registro del código de la entidad de cuenta. 

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
