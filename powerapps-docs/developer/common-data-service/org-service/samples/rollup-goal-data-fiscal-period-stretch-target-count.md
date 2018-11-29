---
title: 'Ejemplo: Consolidar datos de objetivos para un período fiscal en comparación con el recuento de destino extendido (Common Data Service para aplicaciones) | Microsoft Docs'
description: Este ejemplo muestra cómo consolidar datos de objetivos para un período fiscal en comparación con el recuento de destino extendido.
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
# <a name="sample-rollup-goal-data-for-a-fiscal-period-against-the-stretch-target-count"></a>Ejemplo: Datos de objetivos consolidados para un período fiscal en comparación con el recuento de destino extendido

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-rollup-goal-data-fiscal-period-stretch-target-count -->

Este ejemplo muestra cómo resumir los datos del objetivo de un período fiscal frente al recuento de destino extendido que representa varias llamadas telefónicas completadas. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/GoalDataForFiscalYear).

Este ejemplo requiere usuarios adicionales que no están en el sistema. Cree los tres usuarios necesarios **tal cual** se muestran a continuación manualmente en **Office 365**. Reemplace `yourorg` por el nombre de la organización.

**Nombre**: Nancy<br/>
**Apellidos**: Anderson<br/>
**Rol de seguridad**: Comercial<br/>
**UserName**: nanderson@yourorg.onmicrosoft.com<br/>

**Nombre**: David<br/>
**Apellido**: Bristol<br/>
**Rol de seguridad**: Comercial<br/>
**UserName**: dbristol@yourorg.onmicrosoft.com<br/>

**Nombre**: Kevin<br/>
**Apellidos**: Cook<br/>
**Rol de seguridad**: SalesManager<br/>
**UserName**: kcook@yourorg.onmicrosoft.com<br/>

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Este ejemplo muestra cómo resumir los datos del objetivo de un período fiscal frente al recuento de destino extendido que representa varias llamadas telefónicas completadas.

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión de la organización.
2. Recupera el jefe de ventas y a 2 representantes de ventas creados manualmente en **Office 365**.
3. Crea un registro `PhoneCall` y un registro de cuenta de apoyo para el ejemplo.
4. Crea ActivityPartys para el campo **De** de llamadas de teléfono.
5. Crea una llamada de teléfono abierta.
6. Cierra la primera llamada de teléfono y crea una segunda.
7. Cierra la segunda una llamada de teléfono.

### <a name="demonstrate"></a>Demostración

1. Crea métrica, y establece el tipo de métrica como **recuento** y habilita el seguimiento extendido.
2. Crea un campo consolidado destinado a las llamadas de teléfono completadas (recibidas).
3. La `GoalRollupQuery` crea consultas de consolidación de objetivos, localizando las llamadas de teléfono cerradas entrantes y salientes. 
4. Crea tres objetivos, un objetivo global y dos objetivos secundarios.
5. La `RecalculateRequest` calcula el informe para objetivos. 

### <a name="clean-up"></a>Limpiar

1. Muestra una opción para eliminar los datos de ejemplo creados en [Configuración](#setup).

    La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
