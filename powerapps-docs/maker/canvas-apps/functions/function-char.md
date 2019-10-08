---
title: Función Char | Microsoft Docs
description: Información de referencia para la función Char en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 099afb1e89d1551c6c6b969c3ae3688a3cdec777
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992949"
ms.PowerAppsDecimalTransform: true
---
# <a name="char-function-in-powerapps"></a>Función Char en PowerApps

Traduce un código de carácter en una cadena.

## <a name="description"></a>Descripción

La función **Char** convierte un número en una cadena con el carácter ASCII correspondiente.

## <a name="syntax"></a>Sintaxis

**Char**( *CharacterCode* )

- *CharacterCode*: requerido. Código de carácter ASCII que se va a traducir.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Char( 65 )** |Devuelve el carácter que corresponde al código ASCII 65. |UN |
| **Char( 105 )** |Devuelve el carácter que corresponde al código ASCII 105. |Configur |
| **Char( 35 )** |Devuelve el carácter que corresponde al código ASCII 35. |"#" |

### <a name="display-a-character-map"></a>Mostrar un mapa de caracteres

1. En una pantalla vacía de una aplicación de Tablet PC, agregue un control [**Galería**](../controls/control-gallery.md) con un diseño **horizontal en blanco** y, a continuación, establezca estas propiedades:

    - **Elementos**: `[0;1;2;3;4;5;6;7]`
    - **Ancho**: 800
    - **Alto**: 500
    - **Plantillas**: 100
    - **Espaciadointernodeplantilla**: 0

1. Dentro de esa Galería, agregue un control **Galería** con un diseño **vertical en blanco** y, a continuación, establezca estas propiedades:

    - **Elementos**: `ForAll( [0;2;3;4;5;6;7;8;9;10;11;12;13;14;15]; Value + ThisItem.Value * 16 )`
    - **Ancho**: 100
    - **Alto**: 500
    - **Plantillas**: 30
    - **Espaciadointernodeplantilla**: 0

    El valor de la propiedad **Items** multiplica 16 por el número de columna proporcionado por la columna valor de la propiedad **Items** de la primera galería (0-7 en `ThisItem.Value`). A continuación, la fórmula agrega el resultado a uno de los números de fila de la segunda galería (0-15 en el ámbito de registro que proporciona la función [**forall**](function-forall.md) ).

1. Dentro de la segunda galería (vertical), agregue un control **etiqueta** y establezca estas propiedades:

    - **Texto**: `ThisItem.Value`
    - **Ancho**: 50

1. Dentro de la segunda galería (vertical), agregue otro control **etiqueta** y establezca estas propiedades:

    - **Texto**: `Char( ThisItem.Value )`
    - **Ancho**: 50
    - **X**: 50

Ha creado un gráfico con los primeros 128 caracteres ASCII. Los caracteres que aparecen como un cuadrado pequeño no se pueden imprimir.

![Primeros 128 caracteres ASCII](media/function-char/chart-lower.png)

Para mostrar los caracteres ASCII extendidos, establezca la propiedad **Items** de la segunda galería en esta fórmula, que agrega 128 a cada valor de carácter:

`ForAll( [0;2;3;4;5;6;7;8;9;10;11;12;13;14;15]; Value + ThisItem.Value * 16 + 128)`

![Caracteres ASCII extendidos](media/function-char/chart-higher.png)

Para mostrar los caracteres en una fuente diferente, establezca la propiedad **Font** de la segunda etiqueta en un valor como **"script baile"** .

![Script de baile](media/function-char/chart-higher-dancing-script.png)
