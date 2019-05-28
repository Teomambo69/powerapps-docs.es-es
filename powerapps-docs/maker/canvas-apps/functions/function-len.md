---
title: Función Len | Microsoft Docs
description: Información de referencia de la función Len de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d99cf1129ae23eda97b79457cb2b93db6a74a5ea
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216020"
ms.PowerAppsDecimalTransform: true
---
# <a name="len-function-in-powerapps"></a>Función Len en PowerApps
Devuelve la longitud de una cadena de texto.

## <a name="description"></a>Descripción
Si especifica una cadena única como argumento, el valor devuelto es la longitud como un número.  Si especifica una [tabla](../working-with-tables.md) de una columna que contiene cadenas, el valor devuelto es una tabla de una columna que contiene la longitud de cada cadena. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

Si especifica un [en blanco](function-isblank-isempty.md) cadena, **Len** devuelve 0.

## <a name="syntax"></a>Sintaxis
**Len**( *String* )

* *String*: requerido. La cadena que se va a medir.

**Len**( *SingleColumnTable* )

* *SingleColumnTable*: requerido. Una tabla de una columna de cadenas para medir.

## <a name="examples"></a>Ejemplos
### <a name="single-string"></a>Cadena única
En los ejemplos de esta sección, el [origen de datos](../working-with-data-sources.md) es un control de entrada de texto que se denomina **Autor** y que contiene la cadena "E". E. Cummings".

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Len( Author.Text )** |Mide la longitud de la cadena en el control **Author**. |14 |
| **Len( "" )** |Mide la longitud de una cadena vacía. |0 |

### <a name="single-column-table"></a>Tabla de una sola columna
En el primer ejemplo de esta sección, el origen de datos se denomina **People** y contiene estos datos:

![](media/function-len/people-table.png)

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Len( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;) )** |En la columna **Address** [de la tabla](../working-with-tables.md#columns)**People**:<br><ul><li>Mide la longitud de cada cadena.</li><li>Devuelve una tabla de una columna que contiene la longitud de cada cadena.</li> |<style> img { max-width: none } </style> ![](media/function-len/people-table-len.png) |
| **Len( [ "Hello"; "to the"; "World"; "" ] )** |En la columna **[Value](function-value.md)** de la tabla insertada:<br><ul><li>Mide la longitud de cada cadena.</li><li>Devuelve una tabla de una columna que contiene la longitud de cada cadena.</li> |![](media/function-len/people-table-len-inline.png) |

