---
title: Función Char | Microsoft Docs
description: Información de referencia para la función Char en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b7d29d883a14e34dd89d766a6aeffb17275bde6b
ms.sourcegitcommit: 825daacc9a812637815afc1ce6fad28f0cebd479
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57803467"
---
# <a name="char-function-in-powerapps"></a>Función Char en PowerApps

Traduce un código de carácter en una cadena.

## <a name="description"></a>Descripción

El **Char** función convierte un número en una cadena con el carácter ASCII correspondiente.

## <a name="syntax"></a>Sintaxis

**Char**( *CharacterCode* )

- *CharacterCode*: requerido. Código de carácter ASCII que se va a traducir.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Char( 65 )** |Devuelve el carácter que corresponde al código ASCII 65. |"A" |
| **Char( 105 )** |Devuelve el carácter que corresponde al código ASCII 105. |"i" |
| **Char( 35 )** |Devuelve el carácter que corresponde al código ASCII 35. |"#" |

### <a name="display-a-character-map"></a>Mostrar un mapa de caracteres

1. En una pantalla vacía en una aplicación de tableta, agregue un [ **galería** ](../controls/control-gallery.md) controlar con un **en blanco Horizontal** diseño y, a continuación, establezca estas propiedades:

    - **elementos**: `[0,1,2,3,4,5,6,7]`
    - **ancho**: 800
    - **alto**: 500
    - **TemplateSize**: 100
    - **TemplatePadding**: 0

1. Dentro de esa galería, agregue un **galería** controlar con un **en blanco Vertical** diseño y, a continuación, establezca estas propiedades:

    - **elementos**: `ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **ancho**: 100
    - **alto**: 500
    - **TemplateSize**: 30
    - **TemplatePadding**: 0

    El valor de la **elementos** propiedad multiplica 16 por el número de columna proporcionada por la columna valor de la **elementos** propiedad desde la Galería primera (0-7 en ThisItem.Value). La fórmula, a continuación, agrega el resultado a uno de los números de fila desde la Galería de segundo (0-15 en el registro de ámbito que la [ **ForAll** ](function-forall.md) función proporciona).

1. Dentro de la segunda Galería (vertical), agregue un **etiqueta** controlar y establecer estas propiedades:

    - **Texto**: `ThisItem.Value`
    - **ancho**: 50

1. Dentro de la Galería (vertical) segundo, agregue otro **etiqueta** controlar y establecer estas propiedades:

    - **Texto**: `Char( ThisItem.Value )`
    - **ancho**: 50
    - **X**: 50

Ha creado un gráfico de los primeros 128 caracteres ASCII. Caracteres que aparecen cuando no se puede imprimir un cuadrado pequeño.

![En primer lugar 128 caracteres ASCII](media/function-char/chart-lower.png)

Para mostrar los caracteres ASCII extendidos, establezca el **elementos** propiedad de la Galería de segundo en esta fórmula, que agrega 128 a cada valor de carácter:

`ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![Caracteres ASCII extendidos](media/function-char/chart-higher.png)

Para mostrar los caracteres en una fuente diferente, establezca la **fuente** propiedad de la segunda etiqueta a un valor como **bailar secuencia de comandos**.

![¿Bailar Script](media/function-char/chart-higher-dancing-script.png)