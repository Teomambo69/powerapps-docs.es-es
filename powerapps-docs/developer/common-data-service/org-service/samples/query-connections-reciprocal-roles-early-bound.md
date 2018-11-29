---
title: 'Ejemplo: conexiones de la consulta por los roles recíprocos (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo crear las conexiones de consulta con roles recíprocos.
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
# <a name="sample-query-connections-by-reciprocal-roles"></a>Ejemplo: consultar conexiones por roles recíprocos

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-query-connections-reciprocal-roles-early-bound -->

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

1. `QueryExpression` recupera todos los roles de conexión que tienen este rol enumerado como rol recíproco.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los registros creados en [Configuración](#setup).
    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
