---
title: Función Valor | Microsoft Docs
description: Información de referencia para la función Value en Power Apps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/06/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 51ceb1dfc67e24ff0f38f9bf51db37b78410544e
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "77089774"
ms.PowerAppsDecimalTransform: true
---
# <a name="value-function-in-power-apps"></a>Función Value en Power apps
Convierte una cadena de texto en un número.

## <a name="description"></a>Descripción
La función **Value** convierte una cadena de texto que contiene caracteres numéricos en un valor numérico. Use esta función cuando necesite realizar cálculos con los números que los usuarios escriben como texto.

Los distintos idiomas interpretan los signos **,** y **.** de manera diferente.  De manera predeterminada, el texto se interpreta en el idioma del usuario actual.  Para especificar el idioma que se usará con una etiqueta de idioma, puede utilizar las mismas etiquetas de lenguaje que devuelve la función **[Language](function-language.md)** .

Notas sobre el formato de la cadena:

* La cadena puede tener como prefijo el símbolo de moneda del idioma actual.  El símbolo de moneda se omite.  Los símbolos de moneda de los demás idiomas no se omiten.
* La cadena se puede incluir un signo de porcentaje ( **%** ) al final, que indica que es un porcentaje.  El número se dividirá entre 100 antes de devolverse.  No se pueden mezclar porcentajes y símbolos de moneda.
* La cadena puede estar en notación científica; 12 x 10<sup>3</sup> se expresa como "12e3".

Si el número no tiene el formato correcto, **Value** devolverá un valor *blank*.

Para convertir valores de fecha y hora, use las funciones [**DateValue**](function-datevalue-timevalue.md), [**TimeValue**](function-datevalue-timevalue.md) o [**DateTimeValue**](function-datevalue-timevalue.md).

## <a name="syntax"></a>Sintaxis
**Value**( *String* [; *LanguageTag* ] )

* *String*: requerido. Cadena que se convertirá en un valor numérico.
* *LanguageTag*: opcional.  Etiqueta del idioma en el que se va a analizar la cadena.  Si no se especifica, se usa el idioma del usuario actual.

## <a name="examples"></a>Ejemplos:
El usuario que ejecuta estas fórmulas se encuentra en Estados Unidos y seleccionó inglés como idioma.  La función **Language** muestra "en-US".

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Value( "123.456" )** |Se usará el idioma predeterminado "en-US", que utiliza un punto como separador decimal. |123.456 |
| **Value( "123.456"; "es-ES" )** |"es-es" es la etiqueta de idioma para español de España.  En España, el punto es el separador de miles. |123456 |
| **Value( "123,456" )** |Se usará el idioma predeterminado "en-US", que utiliza una coma como separador de miles. |123456 |
| **Value( "123,456"; "es-ES" )** |"es-es" es la etiqueta de idioma para español de España.  En España, la coma es el separador decimal. |123.456 |
| **Value( "12.34%" )** |El signo de porcentaje al final de la cadena indica que se trata de un porcentaje. |0.1234 |
| **Value( "$ 12.34" )** |Se omite el símbolo de moneda del idioma actual. |12.34 |
| **Value( "24e3" )** |Notación científica para 24 x 10<sup>3</sup>. |24000 |

