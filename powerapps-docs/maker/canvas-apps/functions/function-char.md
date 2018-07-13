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
ms.openlocfilehash: b5d63b26498b94943f5340d9f57f3255390c7c94
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37895992"
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

