---
title: Funciones And, Or y Not | Microsoft Docs
description: Información de referencia de las funciones And, Or y Not de PowerApps, con sintaxis y ejemplos
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
ms.openlocfilehash: 4eb020d854549b6dc8878f07ae26390523a1bc03
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215979"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>Funciones And, Or y Not en PowerApps

Funciones de lógica booleana usadas comúnmente para manipular los resultados de pruebas y comparaciones.

## <a name="description"></a>Descripción

La función **And** devuelve **true** si todos los argumentos son **verdaderos**.

La función **Or** devuelve **true** si todos sus argumentos son **verdaderos**.

La función **Not** devuelve **true** si su argumento es **falso** y devuelve **false** si su argumento es **verdadero**.

Estas funciones funcionan del mismo modo que en Excel. También puede usar [operadores](operators.md) para realizar estas mismas operaciones, mediante la sintaxis de Visual Basic o JavaScript:

| Notación de función | Notación de operador de Visual Basic | Notación de operador de JavaScript |
| -------------|------------|--------|
| **Y (x, y)** | **x y y** | **x & & y** |
| **O (x, y)** | **x o y** | **x &#124;&#124; y** |
| **No (x)** | **No x** | **! x** |

Estas funciones trabajan con valores lógicos. No puede pasar a un número o una cadena directamente; en su lugar, debe realizar una comparación o una prueba. Por ejemplo, esta fórmula lógica **x > 1** se evalúa como el valor booleano **true** si **x** es mayor que **1**. Si **x** es menor que **1**, la fórmula se evalúa como **false**.

## <a name="syntax"></a>Sintaxis

**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

- *LogicalFormula(s)* : requerido.  Fórmulas lógicas para evaluar y con las que operar.

## <a name="examples"></a>Ejemplos

Los ejemplos en esta sección usan estas variables globales:

- **a** = *false*
- **b** = *true*
- **x** = 10
- **y** = 100
- **s** = "Hello World"

Para crear estas variables globales en una aplicación, inserte un [ **botón** ](../controls/control-button.md) y establezca su **OnSelect** propiedad en esta fórmula:

```powerapps-dot
Set( a, false ); Set( b, true ); Set( x, 10 ); Set( y, 100 ); Set( s, "Hello World" )
```

Seleccione el botón (haciendo clic en él mientras se mantenga presionada la tecla Alt) y, a continuación, establezca el **texto** propiedad de un [ **etiqueta** ](../controls/control-text-box.md) control en una fórmula en la primera columna de la tabla siguiente.

| Fórmula | Descripción | Resultado |
|---------|-------------|--------|
| **Y (a, b)** | Comprueba los valores de **un** y **b**.  Uno de los argumentos es *false*, por lo que la función devuelve *false*. | *false* |
| **una b And** | Igual que el ejemplo anterior, mediante la notación de Visual Basic. | *false* |
| **un & & b** | Igual que el ejemplo anterior, mediante la notación de JavaScript. | *false* |
| **O (a, b)** | Comprueba los valores de **un** y **b**. Uno de los argumentos es *true*, por lo que la función devuelve *true*. | *true* |
| **una b Or** | Igual que el ejemplo anterior, mediante la notación de Visual Basic. | *true* |
| **a &#124;&#124; b** | Igual que el ejemplo anterior, mediante la notación de JavaScript. | *true* |
| **Not( a )** | Comprueba el valor de **un**. El argumento es *false*, por lo que la función devuelve el resultado opuesto. | *true* |
| **No una** | Igual que el ejemplo anterior, mediante la notación de Visual Basic. | *true* |
| **! una** | Igual que el ejemplo anterior, mediante la notación de JavaScript. | *true* |
| **Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;20 y&nbsp;no&nbsp;IsBlank (&nbsp;s&nbsp;)** | Las pruebas si la longitud de **s** es inferior a 20 y si no es un **en blanco** valor. La longitud es inferior a 20 y el valor no está en blanco. Por lo tanto, el resultado es *true*. | *true* |
| **O (&nbsp;Len (&nbsp;s&nbsp;)&nbsp;<&nbsp;x 10,&nbsp;<&nbsp;y 100,&nbsp;<&nbsp;100&nbsp;)** | Las pruebas si la longitud de **s** es menor que 10, si **x** es inferior a 100 y si **y** es menor que 100. El primero y tercer argumentos son false, pero la segunda es true. Por lo tanto, la función devuelve *true*. | *true* |
| **No ESBLANCO (&nbsp;s&nbsp;)** | Las pruebas si **s** es *en blanco*, que devuelve *false*. **No** devuelve este resultado, que es el opuesto *true*. | *true* |