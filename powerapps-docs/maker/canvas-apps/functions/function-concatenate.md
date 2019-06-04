---
title: Funciones Concat y Concatenate | Microsoft Docs
description: Información de referencia sobre las funciones Concat y Concatenate de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 889f612f3da208d4edfccc43a579ced07933b40d
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216120"
ms.PowerAppsDecimalTransform: true
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Funciones Concat y Concatenate de PowerApps

Concatena cadenas de texto individuales y cadenas en [tablas](../working-with-tables.md).

## <a name="description"></a>Descripción

La función **Concatenate** concatena una combinación de cadenas individuales y una tabla de cadenas con una sola columna. Cuando esta función se utiliza con cadenas individuales, es equivalente a utilizar el **&** [operador](operators.md).

La función **Concat** concatena el resultado de una fórmula que se aplica en todos los [registros](../working-with-tables.md#records) de una tabla, lo que genera una sola cadena. Use esta función para resumir las cadenas de una tabla, tal como hace la función **[Sum](function-aggregates.md)** para los números.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Use la [ **división** ](function-split.md) o [ **MatchAll** ](function-ismatch.md) función para dividir una cadena en una tabla de subcadenas.

## <a name="syntax"></a>Sintaxis

**Concat**( *Table*; *Formula* )

- *Table*: requerido.  La tabla sobre la cual se opera.
- *Formula*: requerido.  Fórmula para aplicar en todos los registros de la tabla.

**Concatenate**( *String1* [; *String2*; ...] )

- *String(s)* : requerido.  Combinación de cadenas individuales o una tabla de cadenas de una columna.

## <a name="examples"></a>Ejemplos

Los ejemplos en esta sección usan estas variables globales:

- **FirstName** = "Juana"
- **LastName** = "Doe"
- **Productos** = ![tabla con dos columnas y cuatro filas](media/function-concatenate/products.png)

Para crear estas variables globales en una aplicación, inserte un [ **botón** ](../controls/control-button.md) y establezca su **OnSelect** propiedad en esta fórmula:

```powerapps-comma
Set( FirstName; "Jane" );; Set( LastName; "Doe" );;
Set( Products;
    Table(
        { Name: "Violin"; Type: "String" };
        { Name: "Cello"; Type: "String" };
        { Name: "Trumpet"; Type: "Wind" }
    )
)
```

Seleccione el botón (haciendo clic en él mientras mantiene presionada la tecla Alt).

### <a name="concatenate-function-and-the--operator"></a>Función Concatenate y & (operador)

Para estos ejemplos, establezca el **texto** propiedad de un [ **etiqueta** ](../controls/control-text-box.md) control con una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concatenar (&nbsp;LastName,&nbsp;",&nbsp;",&nbsp;FirstName&nbsp;)** | Concatena el valor de **LastName**, la cadena **","** (una coma seguida de un espacio) y el valor de **FirstName**. | "Doe,&nbsp;Jane" |
| **LastName&nbsp;&&nbsp;",&nbsp;"&nbsp;&&nbsp;FirstName** | Igual que el ejemplo anterior, excepto utilizando el **&** operador en lugar de la función. | "Doe,&nbsp;Jane" |
| **Concatenar (&nbsp;FirstName,&nbsp;"&nbsp;",&nbsp;LastName&nbsp;)** | Concatena el valor de **FirstName**, la cadena **""** (un solo espacio) y el valor de **LastName**. | "Jane&nbsp;Doe" |
| **FirstName&nbsp;&&nbsp;"&nbsp;"&nbsp;&&nbsp;LastName** | Igual que el ejemplo anterior, utilizando el **&** operador en lugar de la función. | "Jane&nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>Concatenar con una sola columna de tabla

En este ejemplo, agregue un espacio en blanco, vertical [ **galería** ](../controls/control-gallery.md) , establezca su **elementos** propiedad a la fórmula en la tabla siguiente y, a continuación, agregue una etiqueta en la plantilla de la galería.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concatenar ("nombre:&nbsp;",&nbsp;Products.Name, ",&nbsp;tipo:&nbsp;",&nbsp;Products.Type)** | Para cada registro en el **productos** de tabla, concatena la cadena **"nombre:"** , el nombre del producto, la cadena **", tipo:"** y el tipo de producto.  | ![Tabla de productos](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Función concat

Para estos ejemplos, establezca el **texto** propiedad de una etiqueta en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concat (productos, nombre y ",")** | Evalúa la expresión **nombre & ","** para cada registro de **productos** y concatena los resultados en una cadena de texto.  | "Violín,&nbsp;Cello,&nbsp;trompeta,&nbsp;" |
| **Concat (filtro (&nbsp;productos,&nbsp;tipo&nbsp;=&nbsp;"String"&nbsp;), nombre de & ",")** | Evalúa la fórmula **nombre & ","** para cada registro de **productos** que cumplen el filtro **tipo = "String"** y se concatenan los resultados en una cadena de texto.   | "Violín,&nbsp;Cello,&nbsp;" |

### <a name="trimming-the-end"></a>Recorte final

Los dos últimos ejemplos incluyen adicional "," al final del resultado. La función anexa una coma y un espacio para el **nombre** valor de cada registro de la tabla, incluido el último registro.

En algunos casos, no importan estos caracteres adicionales. Por ejemplo, un espacio único compuestas separador no aparece si se muestra el resultado en una etiqueta. Si desea quitar estos caracteres adicionales, use el [ **izquierda** ](function-left-mid-right.md) o [ **coincidencia** ](function-ismatch.md) función.

Para estos ejemplos, establezca el **texto** propiedad de una etiqueta en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Izquierda (Concat (&nbsp;productos,&nbsp;nombre&nbsp;&&nbsp;",&nbsp;"&nbsp;), Len (&nbsp;Concat (&nbsp;productos,&nbsp;nombre&nbsp; & &nbsp;",&nbsp;"&nbsp;)&nbsp;)&nbsp;-&nbsp;2)** | Devuelve el resultado de **Concat** pero quita los dos últimos caracteres, que forman el separador extraño. | "Violín,&nbsp;Cello,&nbsp;trompeta" |
| **Match (Concat (&nbsp;productos,&nbsp;nombre&nbsp;&&nbsp;",&nbsp;"&nbsp;), "^ (?&lt; recortar&gt;. *),&nbsp;$") .trim** | Devuelve los caracteres de **Concat** desde el principio de la cadena de texto (^) al final ($), pero no incluye la coma no deseada y el espacio al final. | "Violín,&nbsp;Cello,&nbsp;trompeta" |

### <a name="split-and-matchall"></a>División y MatchAll

Si ha usado **Concat** con un separador, puede invertir la operación mediante la combinación del **división** y **MatchAll** funciones.

Para estos ejemplos, agregue una galería vertical, en blanco, establece su **elementos** propiedad en una fórmula en la tabla siguiente y, a continuación, agregue una etiqueta en la plantilla de la galería.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **División (Concat (&nbsp;productos,&nbsp;nombre&nbsp;&&nbsp;",&nbsp;"&nbsp;), ",")** | Divide la cadena de texto con el separador de **","** . La cadena finaliza con una coma y un espacio, por lo que la última fila en el resultado es una cadena vacía.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (Concat (&nbsp;productos;&nbsp;nombre&nbsp;&&nbsp;",&nbsp;"&nbsp;); "[^ \s,]+"). FullMatch** | Divide la cadena de texto en función de los caracteres que no son espacios o comas. Esta fórmula quita la coma adicional y el espacio al final de la cadena. | ![Table](media/function-concatenate/matchall.png)