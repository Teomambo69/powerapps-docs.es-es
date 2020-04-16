---
title: 'Ejemplo: Convertir consultas entre entre Fetch y QyeryExpression (Common Data Service) | Microsoft Docs'
description: Este ejemplo muestra cómo convertir consultas entre FetchXML y QueryExpression
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7eafaf7efc28e592cf35280777c1e08a83d3b0ae
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155900"
---
# <a name="sample-convert-queries-between-fetchxml-and-queryexpression"></a>Ejemplo: convertir consultas entre FetchXML y QueryExpression

Este ejemplo muestra cómo convertir consultas entre FetchXML y QueryExpression. Puede descargar el ejemplo desde [aquí](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/Convertqueriesfetchqueryexpressions).

## <a name="how-to-run-this-sample"></a>Cómo ejecutar esta muestra

[!include[cc-how-to-run-samples](../../includes/cc-how-to-run-samples.md)]

## <a name="what-this-sample-does"></a>Qué hace este ejemplo

Los mensajes `QueryExpression` y `fetchExpression` están diseñados para usarse en un escenario que contiene consultas complejas en una jerarquía de expresiones y FetchXML respectivamente.

## <a name="how-this-sample-works"></a>Cómo funciona esta muestra

Para simular el escenario descrito en [Qué hace este ejemplo](#what-this-sample-does), la muestra hará lo siguiente:

### <a name="setup"></a>Configuración

1. Comprobaciones para la versión actual de la organización. 
1. El método `CreateRequireRecords` crea una cuenta y dos registros de contactos que el ejemplo usa.
1. `QueryExpression` crea una expresión de consulta que convertiremos en FetchXML.
1. La clase `DoFetchXmlToQueryExpressionConversion` crea una consulta Fetch que convertiremos en una expresión de consulta.
1. El método `conversionRequest` convierte la expresión de consulta generada en FetchXML y viceversa.
1. Use la consulta convertida para realizar una solicitud de varias recuperaciones. 

### <a name="clean-up"></a>Limpiar

Muestra una opción para eliminar los registros creados en la [Configuración](#setup). La eliminación es opcional en caso de que desee examinar las entidades y los datos creados por el ejemplo. Puede eliminar manualmente los registros para obtener el mismo resultado.
