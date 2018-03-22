---
title: Funciones EncodeUrl y PlainText | Microsoft Docs
description: Información de referencia sobre las funciones EncodeUrl y PlainText de PowerApps, incluidos ejemplos y sintaxis
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: a511d731c8dd94c57ec9846d853fec1bef10ab0a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Funciones EncodeUrl y PlainText en PowerApps
Codifica y descodifica las cadenas.

## <a name="description"></a>Descripción
La función **EncodeUrl** codifica una cadena de dirección URL, para lo que reemplaza los caracteres no alfanuméricos por % y un número hexadecimal.  

La función **PlainText** quita las etiquetas HTML y XML, y convierte etiquetas como las siguientes en un símbolo adecuado:

* **&amp;nbsp;**
* **&amp;quot;**

El valor devuelto de estas funciones es la cadena codificada o descodificada.   

## <a name="syntax"></a>Sintaxis
**EncodeUrl**( *String* )

* *String*: requerido.  Dirección URL que se va a codificar.

**PlainText**( *String* )

* *Cadena*: requerido. Cadena de la que se van a quitar las etiquetas HTML y XML.

## <a name="examples"></a>Ejemplos
Si muestra una fuente RSS en una galería de texto y, después, establece la propiedad **[Text](../controls/properties-core.md)** de una etiqueta de esa galería en **ThisItem.description**, la etiqueta podría mostrar el código HTML o XML sin formato, como en este ejemplo:

    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>

Si establece la propiedad **[Text](../controls/properties-core.md)** de la etiqueta en **PlainText(ThisItem.description)**, el texto aparece como en este ejemplo:

    We have done an unusually "deep" globalization and localization.
