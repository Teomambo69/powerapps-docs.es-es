---
title: Función Char | Microsoft Docs
description: Información de referencia para la función Char en PowerApps, incluidos ejemplos y sintaxis
dauthor: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aec27b788fff8434cfdc4e0e130487f718a42aa6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42826374"
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

