---
title: Función Carácter | Microsoft Docs
description: Información de referencia para la función Char en PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 2e8281f401088f43aa7785ac5dcf7b2f07bb6f96
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31826231"
---
# <a name="char-function-in-powerapps"></a>Función Char en PowerApps
Traduce un código de carácter en una cadena.

## <a name="description"></a>Descripción
La función **Char** devuelve una cadena que contiene el carácter ASCII adecuado para su plataforma.

## <a name="syntax"></a>Sintaxis
**Char**( *CharacterCode* )

* *CharacterCode*: requerido. Código de carácter ASCII que se va a traducir.

## <a name="examples"></a>Ejemplos
| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Char( 65 )** |Devuelve el carácter que corresponde al código ASCII 65. |A |
| **Char( 105 )** |Devuelve el carácter que corresponde al código ASCII 105. |i |
| **Char( 35 )** |Devuelve el carácter que corresponde al código ASCII 35. |# |

