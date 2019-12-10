---
title: Funciones And, Or y Not | Microsoft Docs
description: Información de referencia de las funciones and, or y not en Power Apps, incluidos ejemplos y sintaxis.
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
ms.openlocfilehash: 1dae72a288c93b624d232402e32fe0e82cbaaead
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730618"
ms.PowerAppsDecimalTransform: true
---
# <a name="and-or-and-not-functions-in-power-apps"></a>Funciones and, or y not en Power apps

Funciones de lógica booleana usadas comúnmente para manipular los resultados de pruebas y comparaciones.

## <a name="description"></a>Descripción

La función **And** devuelve **true** si todos los argumentos son **verdaderos**.

La función **Or** devuelve **true** si todos sus argumentos son **verdaderos**.

La función **Not** devuelve **true** si su argumento es **falso** y devuelve **false** si su argumento es **verdadero**.

Estas funciones funcionan de la misma manera que en Excel. También puede usar [operadores](operators.md) para realizar estas mismas operaciones, usando la sintaxis de Visual Basic o JavaScript:

| Notación de función | Visual Basic notación de operador | Notación del operador de JavaScript |
| -------------|------------|--------|
| **And (x, y)** | **x e y** | **x & & y** |
| **O (x, y)** | **x o y** | **x &#124; &#124; y** |
| **Not (x)** | **No x** | **! x1** |

Estas funciones trabajan con valores lógicos. No se pueden pasar un número o una cadena directamente. en su lugar, debe realizar una comparación o una prueba. Por ejemplo, esta fórmula lógica **x > 1** se evalúa como el valor booleano **true** si **x** es mayor que **1**. Si **x** es menor que **1**, la fórmula se evalúa como **false**.

## <a name="syntax"></a>Sintaxis

**And**( *LogicalFormula1*; *LogicalFormula2* [; *LogicalFormula3*; ... ] )<br>
**Or**( *LogicalFormula1*; *LogicalFormula2* [; *LogicalFormula3*; ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* : requerido.  Fórmulas lógicas para evaluar y con las que operar.

## <a name="examples"></a>Ejemplos

En los ejemplos de esta sección se usan estas variables globales:

- **un** = *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hola mundo"

Para crear estas variables globales en una aplicación, inserte un control de [**botón**](../controls/control-button.md) y establezca su propiedad **alseleccionar** en esta fórmula:

```powerapps-comma
Set( a; false );; Set( b; true );; Set( x; 10 );; Set( y; 100 );; Set( s; "Hello World" )
```

Seleccione el botón (haciendo clic en él mientras mantiene presionada la tecla Alt) y, a continuación, establezca la propiedad **texto** de un control [**etiqueta**](../controls/control-text-box.md) en una fórmula de la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Y (a, b)** | Comprueba los valores de **a** y **b**.  Uno de los argumentos es *false*, por lo que la función devuelve *false*. | *false* |
| **a y b** | Igual que el ejemplo anterior, utilizando Visual Basic notación. | *false* |
| **un & & b** | Igual que en el ejemplo anterior, con la notación JavaScript. | *false* |
| **O (a, b)** | Comprueba los valores de **a** y **b**. Uno de los argumentos es *true*, por lo que la función devuelve *true*. | *true* |
| **a o b** | Igual que el ejemplo anterior, utilizando Visual Basic notación. | *true* |
| **a &#124; &#124; b** | Igual que en el ejemplo anterior, con la notación JavaScript. | *true* |
| **No (a)** | Comprueba el valor de **un**. El argumento es *false*, por lo que la función devuelve el resultado opuesto. | *true* |
| **No es un** | Igual que el ejemplo anterior, utilizando Visual Basic notación. | *true* |
| **! un** | Igual que en el ejemplo anterior, con la notación JavaScript. | *true* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 y&nbsp;no&nbsp;esblanco (&nbsp;s&nbsp;)** | Comprueba si la longitud de **s** es menor que 20 y si no es un valor **en blanco** . La longitud es menor que 20 y el valor no está en blanco. Por lo tanto, el resultado es *true*. | *true* |
| **Or (&nbsp;Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;10, x&nbsp;<&nbsp;100, y&nbsp;<&nbsp;100&nbsp;)** | Comprueba si la longitud de **s** es menor que 10, si **x** es menor que 100 y si **y** es menor que 100. El primer y el tercer argumento son false, pero el segundo es true. Por lo tanto, la función devuelve *true*. | *true* |
| **No esblanco (&nbsp;s&nbsp;)** | Comprueba si **s** está *en blanco*, lo que devuelve *false*. **No** devuelve el opuesto de este resultado, que es *true*. | *true* |