---
title: 'Ejemplo: datos de objetivos consolidados para un período personalizado en comparación con los ingresos de destino (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo resumir los datos de objetivos para un período personalizado en comparación con los ingresos de destino.
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
ms.openlocfilehash: 90867101361c8f2ca5bf9ed29e8712890ba162c3
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749867"
---
# <a name="sample-rollup-goal-data-for-a-custom-period-against-the-target-revenue"></a>Ejemplo: datos de objetivos consolidados para un período personalizado en comparación con los ingresos de destino

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rollup-goal-data-custom-period-target-revenue -->

Este ejemplo muestra cómo resumir los datos de objetivos para un período personalizado en comparación con los ingresos de destino. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RollupGoalData).

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

Este ejemplo muestra cómo resumir los datos de objetivos para un período personalizado en comparación con los ingresos de destino.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión de la organización.
2. Recupera el jefe de ventas y a 2 representantes de ventas creados manualmente en **Office 365**.
3. Crea una unidad de venta de ejemplo y recupera el Id. predeterminado de la unidad. 
4. Crea algunos productos y nueva lista de descuentos.
5. El `PriceLevel` crea la lista de precios.
6. El `ProductPriceLevel` crea un elemento de lista de precios para el primer producto y aplica descuentos por volumen.
7. Crea un registro de cuenta para el Id. de posible cliente de la oportunidad.
8. Crea una nueva oportunidad con los ingresos estimados especificados por el usuario.
9. Crea productos de un catálogo y reemplaza el precio listado.
10. Crea un nuevo producto fuera de catálogo de oportunidad con un descuento manual aplicado.

### <a name="demonstrate"></a>Demostración

1. Crea métrica, y establece el Tipo de datos de importe en `Money`.
2. Crea un campo consolidado dirigido a los valores estimados y los valores reales.
3. La `GoalRollupQuery` crea consultas de informe de objetivos, localizando las oportunidades en el área del representante de ventas. 
4. Crea tres objetivos, un objetivo global y dos objetivos secundarios.
5. La `RecalculateRequest` calcula el informe para objetivos. 

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
