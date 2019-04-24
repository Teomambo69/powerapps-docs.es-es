---
title: Funciones Lower, Upper y Proper | Microsoft Docs
description: Información de referencia de las funciones Lower, Upper y Proper de PowerApps, con sintaxis y ejemplos
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
ms.openlocfilehash: 72e1bd234a9cbccc24cf35723ee10bacd175b278
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61563848"
---
# <a name="lower-upper-and-proper-functions-in-powerapps"></a>Funciones Lower, Upper y Proper en PowerApps
Convierte las letras de una cadena de texto en todo minúsculas, todo mayúsculas o en mayúsculas o minúsculas, según corresponda.

## <a name="description"></a>Descripción
Las funciones **Lower**, **Upper** y **Proper** convierten las letras de una cadena en mayúsculas o minúsculas.

* **Lower** convierte las letras mayúsculas en minúsculas.
* **Upper** convierte las letras minúsculas en mayúsculas.
* **Proper** convierte la primera letra de cada palabra en mayúscula si está en minúscula o en minúscula si está en mayúscula.

Las tres funciones omiten los caracteres que no son letras.

Si se pasa una cadena única, el valor devuelto es la versión convertida de dicha cadena.  Si se pasa una [tabla](../working-with-tables.md) de una columna que contiene cadenas, el valor devuelto es una tabla de una columna de cadenas convertidas. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

## <a name="syntax"></a>Sintaxis
**Lower**( *String* )<br>**Upper**( *String* )<br>**Proper**( *String* )

* *String*: requerido. La cadena que se va a convertir.

**Lower**( *SingleColumnTable* )<br>**Upper**( *SingleColumnTable* )<br>**Proper**( *SingleColumnTable* )

* *SingleColumnTable*: requerido. Una tabla de una columna de cadenas para convertir.

## <a name="examples"></a>Ejemplos
### <a name="single-string"></a>Cadena única
En los ejemplos de esta sección se usa un control de entrada de texto, llamado **Author**, como [origen de datos](../working-with-data-sources.md). El control contiene la cadena "E". E. CummINGS".

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Lower(&nbsp;Author.Text&nbsp;)** |Convierte las letras mayúsculas de la cadena a minúsculas. |"e. e. cummings" |
| **Upper(&nbsp;Author.Text&nbsp;)** |Convierte las letras minúsculas de la cadena a mayúsculas. |"E. E. CUMMINGS" |
| **Proper(&nbsp;Author.Text&nbsp;)** |Convierte la primera letra de cada palabra a mayúscula si está en minúscula y convierte cualquier otra letra que esté en mayúsculas a minúsculas. |"E. E. Cummings" |

### <a name="single-column-table"></a>Tabla de una sola columna
Los ejemplos de esta sección convierten las cadenas de la [columna](../working-with-tables.md#columns) **Address** del origen de datos **People**, que contiene estos datos:

![](media/function-lower-upper-proper/people-table.png)

Cada fórmula devuelve una tabla de una columna que contiene las cadenas convertidas.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Lower( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |Convierte cualquier letra que está en minúscula a mayúscula. |<style> img { max-width:none; } </style> ![](media/function-lower-upper-proper/people-table-lower.png) |
| **Upper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |Convierte cualquier letra que está en minúscula a mayúscula. |![](media/function-lower-upper-proper/people-table-upper.png) |
| **Proper( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;) )** |Convierte la primera letra de una palabra en minúsculas a mayúsculas y convierte cualquier otra letra que esté en mayúsculas a minúsculas. |![](media/function-lower-upper-proper/people-table-proper.png) |

### <a name="step-by-step-example"></a>Ejemplo paso a paso
1. Agregue un control **[Entrada de texto](../controls/control-text-input.md)** y denomínelo **Origen**.
2. Agregue una etiqueta y establezca su propiedad **[Text](../controls/properties-core.md)** en esta función:<br>**Proper(Source.Text)**
3. Presione F5 y, a continuación, escriba **WE ARE THE BEST!** en el cuadro **Origen**.<br>La etiqueta muestra **We Are The Best!**

