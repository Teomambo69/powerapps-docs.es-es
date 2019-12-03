---
title: Funciones EncodeUrl y PlainText | Microsoft Docs
description: Información de referencia para las funciones EncodeUrl y PlainText en Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fe02683e0b420a97fe674543a2f0d16bb076f266
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731030"
---
# <a name="encodeurl-and-plaintext-functions-in-power-apps"></a>Funciones EncodeUrl y PlainText en Power apps
Codifica y descodifica las cadenas.

## <a name="description"></a>Descripción
La función **EncodeUrl** codifica una cadena de dirección URL, reemplazando algunos caracteres no alfanuméricos por% y un número hexadecimal.  

La función **Plaintext** quita las etiquetas HTML y XML, convirtiendo algunas etiquetas como estas en un símbolo adecuado:

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

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>
```

Si establece la propiedad **[Text](../controls/properties-core.md)** de la etiqueta en **PlainText(ThisItem.description)** , el texto aparece como en este ejemplo:

```
    We have done an unusually "deep" globalization and localization.
```