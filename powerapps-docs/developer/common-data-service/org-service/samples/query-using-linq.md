---
title: Consultar datos con LINQ (Common Data Service)| Microsoft Docs
description: En este ejemplo se muestra cómo asignar registros a un equipo.
ms.custom: ''
ms.date: 02/05/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: phecke
ms.author: pehecke
manager: KumarVivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 00717d61a34fa600c7dd6139f2c1d7bc3ca9d8f4
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155684"
---
# <a name="sample-query-data-using-linq"></a>Ejemplo: Consultar datos con LINQ

Estos ejemplos muestran cómo consultar datos profesionales utilizando [Consulta integrada del lenguaje (LINQ)](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries). Puede descargar el ejemplo desde [aquí](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/QueriesUsingLINQ). 

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

Vea [Cómo ejecutar ejemplos](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/README.md) para obtener información sobre cómo ejecutar este ejemplo. Hay múltiples proyectos en la solución. Cada proyecto demuestra algún aspecto de las consultas LINQ.

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Lea los comentarios de cada muestra para averiguar qué hace cada una. Hay muestras que:
* Crean una consulta LINQ sencilla
* Crean una consulta LINQ utilizando el enlace en tiempo de ejecución de entidad
* Recuperan varios registros con operadores de condición
* Consultas complejas: una amplia variedad de ejemplos de LINQ

## <a name="how-this-sample-works"></a>Cómo funciona este ejemplo

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), el ejemplo hará lo siguiente:

### <a name="setup"></a>Programa de instalación

Crea cualquier instancia de entidad requerida por la región `Demonstrate` de cada método `Main`().

### <a name="demonstrate"></a>Demostración

El código en la región `Demonstrate` del método `Main`() realiza una o más consultas LINQ.

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en [Configuración](#setup).

La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.