---
title: Funciones Trim y TrimEnds | Microsoft Docs
description: Información de referencia, incluida la sintaxis y un ejemplo, para las funciones Trim y TrimEnd en Power apps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/09/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cf87c96e2e49f9bc01f6d6c749844bd473099cad
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729950"
---
# <a name="trim-and-trimends-functions-in-power-apps"></a>Trim and TrimEnd functions in Power apps
Quita los espacios de una cadena de texto.

## <a name="description"></a>Descripción
La función **Trim** quita todos los espacios de una cadena de texto, excepto los espacios individuales entre palabras.  

La función **TrimEnds** quita todos los espacios del principio y del final de una cadena de texto, pero deja intactos los espacios entre las palabras.

Si especifica una sola cadena de texto, cada función devuelve una cadena a la que se han quitado todos los espacios adicionales. Si especifica una [tabla](../working-with-tables.md) con una sola columna que contiene cadenas, el valor devuelto es una tabla con una sola columna de cadenas recortadas. Si tiene una tabla con varias columnas, puede convertirla en una tabla de una sola columna, como se describe en cómo [trabajar con tablas](../working-with-tables.md).

Al recortar los espacios entre las palabras, **Trim** es coherente con la función del mismo nombre en Microsoft Excel. Sin embargo, **TrimEnds** es coherente con las herramientas de programación, que quitan los espacios solo del principio y el final de cada cadena.

## <a name="syntax"></a>Sintaxis
**Trim**( *String* )<br>**TrimEnds**( *String* )

* *String*: requerido. Cadena de texto a la que se van a quitar los espacios.

**Trim**( *SingleColumnTable* )<br>**TrimEnds**( *SingleColumnTable* )

* *SingleColumnTable*: requerido. Tabla de una sola columna a la que se van a quitar los espacios.

## <a name="example"></a>Ejemplo

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Trim(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |Quita todos los espacios del principio y del final de una cadena, y los espacios adicionales de dentro de la cadena. |"Hello World" |
| **TrimEnds(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |Quita todos los espacios del principio y del final de una cadena. |"Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World" |

Los ejemplos siguientes usan una colección de una sola columna, llamada **Spaces**, que contiene estas cadenas:

![](media/function-trim/input-strings.png)

Para crear esta colección, establezca la propiedad **OnSelect** de un control **[Botón](../controls/control-button.md)** en esta fórmula, abra el modo de vista previa y, a continuación, pulse o haga clic en el botón:
<br>**ClearCollect( Spaces, [ "&nbsp;&nbsp;&nbsp;Jane&nbsp;&nbsp;&nbsp;Doe&nbsp;&nbsp;&nbsp;", "&nbsp;&nbsp;&nbsp;&nbsp;Jack&nbsp;&nbsp;&nbsp;and&nbsp;&nbsp;&nbsp;Jill", "Already&nbsp;trimmed", "&nbsp;&nbsp;&nbsp;Venus,&nbsp;&nbsp;&nbsp;Earth,&nbsp;&nbsp;&nbsp;Mars&nbsp;&nbsp;", "Oil&nbsp;and&nbsp;Water&nbsp;&nbsp;&nbsp;" ] )**

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Trim(&nbsp;Spaces&nbsp;)** |Quita todos los espacios del principio y del final de una cadena, y los espacios adicionales de dentro de cada cadena de la colección **Spaces**. |<style> img { max-width: none } </style> ![](media/function-trim/output-trim.png) |
| **TrimEnds(&nbsp;Spaces&nbsp;)** |Quita todos los espacios del principio y del final de cada cadena de la colección **Spaces**. |<style> img { max-width: none } </style> ![](media/function-trim/output-trimends.png) |

> [!NOTE]
> Si pulsa o hace clic en **Colecciones** en el menú **Archivo** para mostrar una colección, no aparecen espacios adicionales. Para comprobar la longitud de la cadena, use la función **[Len](function-len.md)** .

