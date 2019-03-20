---
title: Funciones EncodeUrl y PlainText | Microsoft Docs
description: Información de referencia sobre las funciones EncodeUrl y PlainText de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
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
ms.openlocfilehash: 9956332c35b4df2773b2634cb7f66d2ea96469e4
ms.sourcegitcommit: 1b8578e38a09220ac66c5123644714139fc3c9e5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "57800454"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>Funciones EncodeUrl y PlainText en PowerApps
Codifica y descodifica las cadenas.

## <a name="description"></a>Descripción
El **EncodeUrl** función codifica una cadena de dirección URL, reemplazando algunos caracteres no alfanuméricos por % y un número hexadecimal.  

El **PlainText** función quita las etiquetas HTML y XML, convierte determinadas etiquetas como las siguientes en un símbolo adecuado:

* **&amp;nbsp;**
* **&amp;quot;**

El valor devuelto de estas funciones es la cadena codificada o descodificada. Esta función no quita todas las etiquetas HTML y XML. 

## <a name="syntax"></a>Sintaxis
**EncodeUrl**( *String* )

* *String*: requerido.  Dirección URL que se va a codificar.

**PlainText**( *String* )

* *String*: requerido. Cadena de la que se van a quitar las etiquetas HTML y XML.

## <a name="examples"></a>Ejemplos
Si muestra una fuente RSS en una galería de texto y, después, establece la propiedad **[Text](../controls/properties-core.md)** de una etiqueta de esa galería en **ThisItem.description**, la etiqueta podría mostrar el código HTML o XML sin formato, como en este ejemplo:

    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>

Si establece la propiedad **[Text](../controls/properties-core.md)** de la etiqueta en **PlainText(ThisItem.description)**, el texto aparece como en este ejemplo:

    We have done an unusually "deep" globalization and localization.
