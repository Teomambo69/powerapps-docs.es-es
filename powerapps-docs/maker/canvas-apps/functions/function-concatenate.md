---
title: Funciones Concat y Concatenate | Microsoft Docs
description: Información de referencia sobre las funciones Concat y Concatenate de PowerApps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: 0a56230539990ce51cc9270f71d8c2b7c9a1db73
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992895"
ms.PowerAppsDecimalTransform: true
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Funciones Concat y Concatenate de PowerApps

Concatena cadenas de texto individuales y cadenas en [tablas](../working-with-tables.md).

## <a name="description"></a>Descripción

La función **Concatenate** concatena una combinación de cadenas individuales y una tabla de cadenas con una sola columna. Cuando se usa esta función con cadenas individuales, es equivalente a usar el operador **&** [. ](operators.md)

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
- **Products** =  @ No__t-2Table con dos columnas y cuatro filas @ no__t-3

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
| **Concatenate (&nbsp;LastName, &nbsp; ", &nbsp;", &nbsp;FirstName @ no__t-5)** | Concatena el valor de **LastName**, la cadena **","** (una coma seguida de un espacio) y el valor en **FirstName**. | "Doe, &nbsp;Jane" |
| **LastName @ no__t-1 @ no__t-2 @ no__t-3 ", &nbsp;" &nbsp; @ no__t-6 @ no__t-7FirstName** | Igual que el ejemplo anterior, excepto mediante el operador **&** en lugar de la función. | "Doe, &nbsp;Jane" |
| **Concatenate (&nbsp;FirstName, &nbsp; "&nbsp;", &nbsp;LastName @ no__t-5)** | Concatena el valor de **FirstName**, la cadena **""** (un solo espacio) y el valor de **LastName**. | "Jane @ no__t-0Doe" |
| **FirstName @ no__t-1 @ no__t-2 @ no__t-3 "&nbsp;" &nbsp; @ no__t-6 @ no__t-7LastName** | Igual que en el ejemplo anterior, con el operador **&** en lugar de la función. | "Jane @ no__t-0Doe" |

### <a name="concatenate-with-a-single-column-table"></a>Concatenar con una tabla de una sola columna

En este ejemplo, agregue un control [**Galería**](../controls/control-gallery.md) vertical en blanco, establezca la propiedad **elementos** en la fórmula de la siguiente tabla y, a continuación, agregue una etiqueta en la plantilla de la galería.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concatenate ("Name: &nbsp;", &nbsp;Products.Name, ", &nbsp;Type: &nbsp;", &nbsp;Products. Type)** | Para cada registro de la tabla **Products** , concatena la cadena **"Name:"** , el nombre del producto, la cadena **", Type:"** y el tipo del producto.  | ![Tabla de productos](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat (función)

En estos ejemplos, establezca la propiedad **texto** de una etiqueta en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Concat (productos, nombre & ",")** | Evalúa el nombre de la expresión **& ","** para cada registro de **productos** y concatena los resultados en una sola cadena de texto.  | "Violin, &nbsp;Cello, &nbsp;Trumpet, &nbsp;" |
| **Concat (filtro (&nbsp;Products, &nbsp;Type @ no__t-3 @ no__t-4 @ no__t-5 "cadena" &nbsp;), nombre & ",")** | Evalúa el nombre de la fórmula **& ","** para cada registro de **productos** que satisface el tipo de filtro **= "String"** y concatena los resultados en una sola cadena de texto.   | "Violin, &nbsp;Cello, &nbsp;" |

### <a name="trimming-the-end"></a>Recortar el final

Los dos últimos ejemplos incluyen un "," extra al final del resultado. La función anexa una coma y un espacio al valor de **nombre** de cada registro de la tabla, incluido el último registro.

En algunos casos, estos caracteres adicionales no importan. Por ejemplo, un separador de espacio único no aparece si se muestra el resultado en una etiqueta. Si desea quitar estos caracteres adicionales, utilice la función [**left**](function-left-mid-right.md) o [**Match**](function-ismatch.md) .

En estos ejemplos, establezca la propiedad **texto** de una etiqueta en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Left (CONCAT (&nbsp;Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), Len (&nbsp;Concat (&nbsp;Products, 0Name @ no__t-11 @ no__t-12 @ no__t-13 ", 4" 5) 6) 7 @ no__t-18 @ no__t-192)** | Devuelve el resultado de **concat** , pero quita los dos últimos caracteres, que forman el separador extraño. | "Violin, &nbsp;Cello, &nbsp;Trumpet" |
| **Match (CONCAT (&nbsp;Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), "^ (? &lt;trim @ no__t-9. *), @no__t-$10"). Trim** | Devuelve los caracteres de **concat** desde el principio de la cadena de texto (^) al final ($), pero no incluye la coma y el espacio no deseados al final. | "Violin, &nbsp;Cello, &nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Split y MatchAll

Si usó **concat** con un separador, puede invertir la operación combinando las funciones **Split** y **MatchAll** .

En estos ejemplos, agregue una galería vertical en blanco, establezca la propiedad **elementos** en una fórmula de la tabla siguiente y, a continuación, agregue una etiqueta a la plantilla de la galería.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Split (CONCAT (&nbsp;Products, &nbsp;Name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), ",")** | Divide la cadena de texto con el separador **","** . La cadena finaliza con una coma y un espacio, por lo que la última fila del resultado es una cadena vacía.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (CONCAT (&nbsp;Products; &nbsp;Name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;); "[^ \s,] +"). FullMatch** | Divide la cadena de texto basándose en caracteres que no son espacios ni comas. Esta fórmula quita la coma y el espacio adicionales al final de la cadena. | ![Table](media/function-concatenate/matchall.png)