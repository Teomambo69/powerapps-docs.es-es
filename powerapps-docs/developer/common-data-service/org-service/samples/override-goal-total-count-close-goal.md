---
title: 'Ejemplo: Reemplazar el recuento total de objetivos y cerrar el objetivo (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo reemplazar el recuento total de objetivos y cerrar el objetivo.
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
ms.openlocfilehash: 62d02e77e0008778e0526f7620bc5bda168c6f26
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749888"
---
# <a name="sample-override-goal-total-count-and-close-the-goal"></a>Ejemplo: reemplazar el recuento total de objetivos y cerrar el objetivo

Este ejemplo muestra cómo reemplazar el recuento total de objetivos y cerrar el objetivo. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OverrideGoalTotal).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree manualmente en **Office 365** el usuario necesario **tal cual**, como se indica a continuación. Reemplace `yourorg` por el valor de `OrgName` de su organización.

**Nombre**: Samantha<br/>
**Apellidos**: Smith<br/>
**Rol de seguridad**: director de marketing<br/>
**Nombre de usuario**: ssmith@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo


Este ejemplo muestra cómo reemplazar el recuento total de objetivos y cerrar el objetivo.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión de la organización.
2. Recupera el usuario jefe de ventas creado manualmente en **Office 365**.
3. Crea un registro `PhoneCall` y un registro de cuenta de apoyo para el ejemplo.
4. Crea ActivityPartys para el campo "De" de llamadas de teléfono.
5. Crea una llamada de teléfono abierta.
6. Cierra la primera llamada de teléfono y crea una segunda.
7. Cierra la segunda llamada de teléfono.

### <a name="demonstrate"></a>Demostración

1. Crea Métrica, y establece el tipo de métrica como `count` y establece `IsAmount` como falso.
2. `RollupFields` crea un campo consolidado destinado a llamadas (recibidas) completadas.
3. `GoalRollupQuery` crea consultas de consolidación de objetivos, localizando las llamadas de teléfono cerradas entrantes y salientes. 
4. Crea un objetivo para realizar un seguimiento de las llamadas telefónicas entrantes abiertas.
5. `RecalculateRequest` calcula el informe de objetivos. 
6. Reemplaza los valores real y en curso del objetivo.
7. Si se establece `goal.IsOverridden =true` se impide que se reemplacen los valores consolidados al recalcular.

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
