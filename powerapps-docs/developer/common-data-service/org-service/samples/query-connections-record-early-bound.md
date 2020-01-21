---
title: 'Ejemplo: Consultar conexiones para un registro (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo consultar conexiones para un registro concreto.
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
ms.openlocfilehash: c38b1709e34ea85f7de84b0c9eaea0a2c9256c2d
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934256"
---
# <a name="sample-query-connections-by-a-record"></a>Ejemplo: consultar conexiones para un registro 

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-connections-record-early-bound -->

Este ejemplo muestra cómo consultar conexiones para un registro concreto. Crea conexiones entre un contacto y dos cuentas, y después busca para las conexiones del contacto. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryByRecord).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo crea registros de cuenta y contacto y crea los roles de conexión entre ellos. `QueryExpression` recupera las conexiones a un registro en particular.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Define algunos tipos anónimos para definir el intervalo de los valores de propiedad de conexión posibles.
3. `ConnectionRole` crea un rol de conexión.
4. `ConnectionRoleObjectType` crea un rol de tipo de objeto de conexión del registro del código de la entidad de cuenta. 
5. Crea algunos registros de cuenta y contacto para su uso en la conexión.

### <a name="demonstrate"></a>Demostración

`QueryExpression` recupera todas las conexiones asociadas al contacto creado en el ejemplo.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
