---
title: Funciones Concat y Concatenate | Microsoft Docs
description: Información de referencia para las funciones Concat y Concatenate en Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 01bf9b2ea165fd24a06725f4f09427bd05c3fe14
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731310"
ms.PowerAppsDecimalTransform: true
---
# <a name="concat-and-concatenate-functions-in-power-apps"></a>Funciones Concat y Concatenate en Power apps

Concatena cadenas de texto individuales y cadenas en [tablas](../working-with-tables.md).

## <a name="description"></a>Descripción

La función **Concatenate** concatena una combinación de cadenas individuales y una tabla de cadenas con una sola columna. Cuando se usa esta función con cadenas individuales, es equivalente a usar el [operador](operators.md) **&** .

La función **Concat** concatena el resultado de una fórmula que se aplica en todos los [registros](../working-with-tables.md#records) de una tabla, lo que genera una sola cadena. Use esta función para resumir las cadenas de una tabla, tal como hace la función **[Sum](function-aggregates.md)** para los números.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Use la función [**Split**](function-split.md) o [**MatchAll**](function-ismatch.md) para dividir una cadena en una tabla de subcadenas.

## <a name="syntax"></a>Sintaxis

**Concat**( *Table*; *Formula* )

- *Table*: requerido.  La tabla sobre la cual se opera.
- *Formula*: requerido.  Fórmula para aplicar en todos los registros de la tabla.

**Concatenate**( *String1* [; *String2*; ...] )

- *String(s)* : requerido.  Combinación de cadenas individuales o una tabla de cadenas de una columna.

## <a name="examples"></a>Ejemplos

En los ejemplos de esta sección se usan estas variables globales:

- **FirstName** = "Julia"
- **LastName** = "DOE"
- **Products** = ![tabla con dos columnas y cuatro filas](media/function-concatenate/products.png)

Para crear estas variables globales en una aplicación, inserte un control de [**botón**](../controls/control-button.md) y establezca su propiedad **alseleccionar** en esta fórmula:

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

### <a name="concatenate-function-and-the--operator"></a>Función Concatenate y el operador &

En estos ejemplos, establezca la propiedad **texto** de un control [**etiqueta**](../controls/control-text-box.md) en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concatenate (&nbsp;LastName,&nbsp;",&nbsp;",&nbsp;FirstName&nbsp;)** | Concatena el valor de **LastName**, la cadena **","** (una coma seguida de un espacio) y el valor en **FirstName**. | "Doe,&nbsp;Julia" |
| **LastName&nbsp;&&nbsp;",&nbsp;"&nbsp;&&nbsp;FirstName** | Igual que el ejemplo anterior, excepto mediante el operador **&** en lugar de la función. | "Doe,&nbsp;Julia" |
| **Concatenate (&nbsp;FirstName,&nbsp;"&nbsp;"&nbsp;LastName&nbsp;)** | Concatena el valor de **FirstName**, la cadena **""** (un solo espacio) y el valor de **LastName**. | "Jane&nbsp;DOE" |
| **FirstName&nbsp;&&nbsp;"&nbsp;"&nbsp;&&nbsp;LastName** | Igual que en el ejemplo anterior, con el operador **&** en lugar de la función. | "Jane&nbsp;DOE" |

### <a name="concatenate-with-a-single-column-table"></a>Concatenar con una tabla de una sola columna

En este ejemplo, agregue un control [**Galería**](../controls/control-gallery.md) vertical en blanco, establezca la propiedad **elementos** en la fórmula de la siguiente tabla y, a continuación, agregue una etiqueta en la plantilla de la galería.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concatenate ("Name:&nbsp;",&nbsp;Products.Name, ",&nbsp;Type:&nbsp;",&nbsp;Products. Type)** | Para cada registro de la tabla **Products** , concatena la cadena **"Name:"** , el nombre del producto, la cadena **", Type:"** y el tipo del producto.  | ![Tabla de productos](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat (función)

En estos ejemplos, establezca la propiedad **texto** de una etiqueta en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concat (productos, nombre & ",")** | Evalúa el nombre de la expresión **& ","** para cada registro de **productos** y concatena los resultados en una sola cadena de texto.  | "Violin,&nbsp;cello,&nbsp;Trumpet,&nbsp;" |
| **Concat (filtrar (&nbsp;productos, tipo de&nbsp;&nbsp;=&nbsp;"cadena"&nbsp;), nombre & ",")** | Evalúa el nombre de la fórmula **& ","** para cada registro de **productos** que satisface el tipo de filtro **= "String"** y concatena los resultados en una sola cadena de texto.   | "Violin,&nbsp;cello&nbsp;" |

### <a name="trimming-the-end"></a>Recortar el final

Los dos últimos ejemplos incluyen un "," extra al final del resultado. La función anexa una coma y un espacio al valor de **nombre** de cada registro de la tabla, incluido el último registro.

En algunos casos, estos caracteres adicionales no importan. Por ejemplo, un separador de espacio único no aparece si se muestra el resultado en una etiqueta. Si desea quitar estos caracteres adicionales, utilice la función [**left**](function-left-mid-right.md) o [**Match**](function-ismatch.md) .

En estos ejemplos, establezca la propiedad **texto** de una etiqueta en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Left (CONCAT (&nbsp;Products, nombre de&nbsp;&nbsp;&&nbsp;",&nbsp;"&nbsp;), Len (&nbsp;,&nbsp;,&nbsp;&nbsp;&&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-&nbsp;)** | Devuelve el resultado de **concat** , pero quita los dos últimos caracteres, que forman el separador extraño. | "Violin,&nbsp;cello,&nbsp;Trumpet" |
| **Match (CONCAT (&nbsp;Products,&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;), "^ (?&lt;Trim&gt;. *),&nbsp;$ "). Trim** | Devuelve los caracteres de **concat** desde el principio de la cadena de texto (^) al final ($), pero no incluye la coma y el espacio no deseados al final. | "Violin,&nbsp;cello,&nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Split y MatchAll

Si usó **concat** con un separador, puede invertir la operación combinando las funciones **Split** y **MatchAll** .

En estos ejemplos, agregue una galería vertical en blanco, establezca la propiedad **elementos** en una fórmula de la tabla siguiente y, a continuación, agregue una etiqueta a la plantilla de la galería.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Split (CONCAT (&nbsp;productos,&nbsp;nombre&nbsp;&&nbsp;",&nbsp;"&nbsp;), ",")** | Divide la cadena de texto con el separador **","** . La cadena finaliza con una coma y un espacio, por lo que la última fila del resultado es una cadena vacía.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (CONCAT (&nbsp;Products;&nbsp;Name&nbsp;&&nbsp;",&nbsp;"&nbsp;); "[^ \s,] +"). FullMatch** | Divide la cadena de texto basándose en caracteres que no son espacios ni comas. Esta fórmula quita la coma y el espacio adicionales al final de la cadena. | ![Table](media/function-concatenate/matchall.png)