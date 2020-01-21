---
title: 'Ejemplo: Consultas de informe de usuario para seguir objetivos (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo usar consultas de informe para hacer un seguimiento de los objetivos
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
ms.openlocfilehash: 00461f0edf24e9d35d9e0b97233da34bb6faefd8
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934084"
---
# <a name="sample-use-rollup-queries-to-track-goals"></a>Ejemplo: usar consultas de informe para realizar un seguimiento de los objetivos

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-use-rollup-queries-track-goals -->

Este ejemplo muestra cómo usar consultas de informe para hacer un seguimiento de los objetivos. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueriesTrackGoals).

Este ejemplo requiere tres usuarios adicionales que no están presentes en el sistema. Cree los tres usuarios necesarios **tal cual** se muestran a continuación manualmente en **Office 365**. Reemplace `yourorg` por el nombre de la organización.

**Nombre**: Nancy<br/>
**Apellidos**: Anderson<br/>
**Rol de seguridad**: Comercial<br/>
**Nombre de usuario**: nanderson@yourorg.onmicrosoft.com<br/>

**Nombre**: David<br/>
**Apellido**: Bristol<br/>
**Rol de seguridad**: Comercial<br/>
**Nombre de usuario**: dbristol@yourorg.onmicrosoft.com<br/>

**Nombre**: Kevin<br/>
**Apellidos**: Cook<br/>
**Rol de seguridad**: SalesManager<br/>
**Nombre de usuario**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo usar consultas de informe para hacer un seguimiento de los objetivos.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización.
2. Recupera el jefe de ventas y a 2 representantes de ventas, creados manualmente en **Office 365**.
3. Crea registros para admitir registros de `SalesOrder`.
4. Crea una nueva unidad de venta para el ejemplo.
5. Recupera el Id. de unidad predeterminado que se crea automáticamente al crear una nueva unidad de venta.
6. El `Product` crea pocos productos que se necesitan para el ejemplo.
7. El `PriceLevel` crea una nueva lista de precios.
8. El `ProductPriceLevel` crea un elemento de lista de precios para el primer producto y aplica descuentos por volumen.
9. Crea un registro de cuenta para el Id. de posible cliente del pedido de venta. 
10. El `SalesOrderDetails` agrega el producto al pedido con el precio reemplazado con un valor negativo.

### <a name="demonstrate"></a>Demostración

1. Crea métrica, y establece el tipo de métrica como `Amount` y establece el tipo de datos de importe como `Money`.
2. El `RollupField` crea un campo consolidado destinado a los totales reales.
3. La `GoalRollupQuery` crea consultas consolidadas de objetivos, localizando los pedidos de venta en la primera área del representante de ventas (código postal: 60661) y con un valor superior a 1000 $. 
4. Crea dos objetivos, un objetivo global y un objetivo secundario.
5. La `RecalculateRequest` calcula el informe para objetivos. 

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
