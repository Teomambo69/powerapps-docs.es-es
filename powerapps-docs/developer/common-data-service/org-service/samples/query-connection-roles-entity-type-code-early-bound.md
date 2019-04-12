---
title: 'Ejemplo: consulta de rol de conexión por el código de tipo de entidad (Common Data Service) | Microsoft Docs'
description: En este ejemplo se muestra cómo hacer una consulta a una conexión
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
# <a name="sample-query-connection-roles-by-entity-type-code"></a>Ejemplo: consulta de roles de conexión por código de tipo de entidad

Este ejemplo muestra cómo usar una consulta para buscar un rol de conexión para una entidad cuenta mediante la especificación de un código de tipo de entidad. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryRoleByEntityType).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo usar una consulta para buscar un rol de conexión para una entidad cuenta mediante la especificación de un código de tipo de entidad.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.

### <a name="demonstrate"></a>Demostración

1. Define algunos tipos anónimos para definir el intervalo de los valores de propiedad de conexión posibles.
2. `ConnectionRole` crea un rol de conexión.
3. `QueryExpression` consulta todos los roles de conexión.
4. `ConnectionRoleObjectTypeCode` crea un rol de tipo de objeto de conexión del registro del código de la entidad de cuenta. 

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).
    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
