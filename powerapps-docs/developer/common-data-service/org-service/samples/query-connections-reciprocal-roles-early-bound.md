---
title: 'Ejemplo: Consultar conexiones por roles recíprocos (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo crear las conexiones de consulta con roles recíprocos.
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
ms.openlocfilehash: e3c61a2d9205aedb37f0956960ed78fc7b27494f
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155692"
---
# <a name="sample-query-connections-by-reciprocal-roles-early-bound"></a>Ejemplo: conexiones de consulta por roles recíprocos (con enlace en tiempo de ejecución)

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-query-connections-reciprocal-roles-early-bound -->

Este ejemplo muestra cómo crear roles coincidentes y después encontrar un rol coincidente para un rol determinado. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueryByReciprocalRole).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo crear roles coincidentes y después encontrar un rol coincidente para un rol determinado.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Define algunos tipos anónimos para definir el intervalo de los valores de propiedad de conexión posibles.
3. `ConnectionRole` crea de la instancia de conexión el rol primaria.
4. `ConnectionRoleObjectTypeCode` crea un rol de tipo de objeto de conexión del registro del código de la entidad Cuenta y Contacto.
5. `AssociateRequest` asocia los roles de conexión.

### <a name="demonstrate"></a>Demostración

`QueryExpression` recupera todos los roles de conexión que tienen este rol enumerado como rol recíproco.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
