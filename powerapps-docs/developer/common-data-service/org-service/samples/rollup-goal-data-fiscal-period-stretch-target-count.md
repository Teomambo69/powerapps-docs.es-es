---
title: 'Ejemplo: Datos de objetivos consolidados para un período fiscal en comparación con el recuento de destino extendido(Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo consolidar datos de objetivos para un período fiscal en comparación con el recuento de destino extendido.
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
ms.openlocfilehash: a99f10644768cf5d9f7cba07460b673c3e198786
ms.sourcegitcommit: 3bf59896a98e5f01289a2489e185f27518aeaec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "2956151"
---
# <a name="sample-rollup-goal-data-for-a-fiscal-period-against-the-stretch-target-count"></a>Ejemplo: Datos de objetivos consolidados para un período fiscal en comparación con el recuento de destino extendido

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rollup-goal-data-fiscal-period-stretch-target-count -->

Este ejemplo muestra cómo resumir los datos del objetivo de un período fiscal frente al recuento de destino extendido que representa varias llamadas telefónicas completadas. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GoalDataForFiscalYear).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los tres usuarios necesarios **tal cual** se muestran a continuación manualmente en **Office 365**. Reemplace `yourorg` por el nombre de la organización.

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

Este ejemplo muestra cómo resumir los datos del objetivo de un período fiscal frente al recuento de destino extendido que representa varias llamadas telefónicas completadas.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión de la organización.
2. Recupera el jefe de ventas y a 2 representantes de ventas, creados manualmente en **Office 365**.
3. Crea un registro `PhoneCall` y un registro de cuenta de apoyo para el ejemplo.
4. Crea ActivityPartys para el campo **De** de llamadas de teléfono.
5. Crea una llamada de teléfono abierta.
6. Cierra la primera llamada de teléfono y crea una segunda.
7. Cierra la segunda llamada de teléfono.

### <a name="demonstrate"></a>Demostración

1. Crea métrica, y establece el tipo de métrica como **recuento** y habilita el seguimiento extendido.
2. Crea un campo consolidado destinado a las llamadas de teléfono completadas (recibidas).
3. La `GoalRollupQuery` crea consultas de consolidación de objetivos, localizando las llamadas de teléfono cerradas entrantes y salientes. 
4. Crea tres objetivos, un objetivo global y dos objetivos secundarios.
5. La `RecalculateRequest` calcula el informe para objetivos. 

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
