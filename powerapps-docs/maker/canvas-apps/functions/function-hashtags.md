---
title: Función HashTags | Microsoft Docs
description: Información de referencia para la función HashTags en PowerApps, incluidos ejemplos y sintaxis
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
ms.openlocfilehash: ebeecf7ae429f9e18c1b41b7c0f0ddd7da5be07c
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31826227"
---
# <a name="hashtags-function-in-powerapps"></a>Función HashTags en PowerApps
Extrae los hashtags (#cadenas) de una cadena de texto.

## <a name="description"></a>Descripción
La función **HashTags** analiza una cadena en busca de hashtags. Los hashtags comienzan por un carácter de almohadilla (#), que va seguido de cualquier combinación de:

* letras mayúsculas y minúsculas
* números
* caracteres de subrayado
* símbolos de moneda (por ejemplo, $)

**HashTags** devuelve una [tabla](../working-with-tables.md) de una sola columna que contiene los hashtags de la cadena.  Si la cadena no contiene ningún hashtag, la función devuelve una tabla de una sola columna que está [vacía](function-isblank-isempty.md).

## <a name="syntax"></a>Sintaxis
**HashTags**( *Cadena* )

* *Cadena*: requerido.  Cadena en la que se van a buscar hashtags.

## <a name="examples"></a>Ejemplos
### <a name="step-by-step"></a>Paso a paso
1. Agregue un control **[Entrada de texto](../controls/control-text-input.md)**, asígnele el nombre **Tweet** y escriba esta frase:
   
    **Esta #aplicación es #SORPRENDENTE y puede #contar123 # o #123abc, pero no #1-23 ni #$\*(#@")**
2. Agregue una galería vertical personalizada y establezca su propiedad **[Elementos](../controls/properties-core.md)** en esta función:
   
    **HashTags(Tweet.Text)**
3. Agregue un control **[Etiqueta](../controls/control-text-box.md)** a la plantilla de la galería.
   
    La galería mostrará estos hashtags:
   
   * **\#aplicación**
   * **\#SORPRENDENTE**
   * **\#contar123**
   * **\#123abc**
   * **\#1**

