---
title: "Función Idioma | Microsoft Docs"
description: "Información de referencia para la función Language en PowerApps, incluidos ejemplos y sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2016
ms.author: gregli
ms.openlocfilehash: 35f6b462a57a29e6989d6a635425c981b705eaaf
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="language-function-in-powerapps"></a>Función Language en PowerApps
Devuelve la etiqueta de idioma del usuario actual.

## <a name="description"></a>Descripción
La función **Language** devuelve el idioma, el alfabeto y la región del usuario actual como una etiqueta de idioma.

Use la información de idioma para adaptar la aplicación a las configuraciones regionales.  Por ejemplo, si va a crear una aplicación que se usará en Italia y Francia, puede usar **Language** para mostrar automáticamente cadenas en italiano y francés a los usuarios que se encuentren estas ubicaciones diferentes. 

### <a name="language-tags"></a>Etiquetas Language
Las *etiquetas de idioma* pueden presentar uno de estos tres formatos:

| Valor devuelto | Descripción |
| --- | --- |
| **"*lg&#8209;RE*"** |*lg* es la abreviatura de dos caracteres para el idioma y *RE* es la abreviatura de dos caracteres para la región.  Se trata del tipo de valor devuelto más común.  Por ejemplo, se devuelve "en-GB" para Gran Bretaña. |
| **"*lg*"** |*lg* es la abreviatura de dos caracteres para el idioma.  Este es el formato que se usa cuando PowerApps tiene información sobre el idioma, pero no sobre la región específica. |
| **"*lg&#8209;scrp&#8209;RE*"** |*lg* es la abreviatura de dos caracteres para el idioma, *scrp* es la abreviatura de cuatro caracteres para el alfabeto y *RE* es la abreviatura de dos caracteres para la región. |

PowerApps usa el formato de [etiqueta de idioma IETF BCP-47](https://tools.ietf.org/html/bcp47).  

Para ver la lista de etiquetas de idioma compatibles, escriba **Value( "1", )** en la barra de fórmulas o en la vista avanzada, y desplácese por la lista de configuraciones regionales sugeridas para el segundo argumento.  

Las funciones **[Text](function-text.md)** y **[Value](function-value.md)** también usan etiquetas de idioma.  Use estas funciones para traducir desde y hacia cadenas de texto teniendo en cuenta el contexto global.  Cuando pasar una etiqueta de idioma a estas funciones y la región no suponga una diferencia, puede usar solo la porción de idioma de la etiqueta.

## <a name="syntax"></a>Sintaxis
**Language**()

## <a name="examples"></a>Ejemplos
### <a name="users-locale"></a>Configuración regional del usuario
Se supone que el sistema operativo host o el explorador usan la configuración regional predeterminada para la ubicación.

| Fórmula | Ubicación | Valor devuelto |
| --- | --- | --- |
| **Language()** |Lisboa, Portugal |"pt-PT" |
| **Language()** |Río de Janeiro, Brasil |"pt-BR" |
| **Language()** |Atlanta, Estados Unidos |"en-US" |
| **Language()** |Mánchester, Reino Unido |"en-GB" |
| **Language()** |París, Francia |"fr-FR" |
| **Language()** |Roseau, Dominica |"en" |
| **Language()** |Belgrado, Serbia |"sr-cyrl-RS" o "sr-latn-RS", según la configuración del sistema del usuario |

### <a name="localization-table"></a>Tabla de localización
Un enfoque sencillo para la localización consiste en crear una hoja de cálculo de Excel en la que se asigne un **TextID** definido por el autor a un texto traducido para el idioma del usuario.  Aunque podría utilizar una colección o cualquier otro origen de datos para esta tabla, hemos elegido Excel porque a los traductores les resulta fácil de editar y administrar fuera de la aplicación.

1. Cree la siguiente tabla en Excel: 
   
    ![](media/function-language/loc-table.png)
   
    La entrada con *blank* para la columna **Language** se usará como el valor predeterminado si no hay ninguna cadena de texto específica para un idioma determinado. Esta entrada debe aparecer después de todas las demás entradas para un determinado **TextID**.
   
    Para nuestros propósitos, solo necesitamos consultar el idioma de la configuración regional, no la región.  Si consideraciones regionales fueran importantes, podríamos haber incluido el valor completo de la etiqueta de idioma en la tabla anterior. 
2. Use la cinta de opciones **Insertar** y el comando **Tabla** para convertirla en una tabla de Excel apropiada.  De forma predeterminada, se denominará **Table1**, pero puede asignarle el nombre quiera con la cinta de opciones **Herramientas de tabla/Diseño** y el cuadro de texto **Nombre de la tabla** del extremo izquierdo.
3. Guarde el archivo de Excel en el sistema de archivos local.   
4. En PowerApps, en el panel derecho, pulse o haga clic en la pestaña **Orígenes de datos** y, después, pulse o haga clic en **Agregar origen de datos**.
5. Pulse o haga clic en **Agregar datos estáticos a la aplicación**, pulse o haga clic en el archivo de Excel que ha guardado y, luego, en **Abrir**.
6. Seleccione la tabla que ha creado y, después, pulse o haga clic en **Conectar**.

En la aplicación, en los casos en los que antes habría usado el texto **"Hello"**, use la siguiente fórmula en su lugar:

* **LookUp( Table1, TextID = "Hello" && (LanguageTag = Left( Language(), 2 ) || IsBlank( LanguageTag ))).LocalizedText**  

Esta fórmula buscará el valor adecuado de **LocalizedText** para el idioma del usuario y, si no lo encuentra, recurrirá a la versión predeterminada *blank*. 

Tenga en cuenta que las cadenas traducidas a otros idiomas podrían ocupar más espacio que las que están en su idioma.  En muchos casos, las etiquetas y otros elementos que muestran las cadenas en la interfaz de usuario necesitarán ser más anchos para dar cabida a esas cadenas.

### <a name="translation-service"></a>Servicio de traducción
Puede traducir texto a petición con un servicio de traducción, como el servicio Microsoft Translator:  

1. En PowerApps, en el panel derecho, pulse o haga clic en la pestaña **Orígenes de datos** y, después, pulse o haga clic en **Agregar origen de datos**.
2. Pulse o haga clic en **Microsoft Translator**.

En la aplicación, en los casos en los que antes habría usado el texto **"Hello"**, use la siguiente fórmula en su lugar:

* **MicrosoftTranslator.Translate( "Hello", Language() )**

El servicio Microsoft Translator usa las mismas etiquetas de idioma que devuelve la función **Language**.

Este enfoque tiene algunas desventajas en comparación con el ejemplo anterior, en el que se usaba una tabla de cadenas de texto traducida previamente:

* La traducción tardará en completarse, ya que requiere llamar a un servicio a través de la red.  Esto implica que transcurrirá un tiempo hasta que pueda ver el texto traducido en la aplicación. 
* La traducción será mecánica y es posible que los resultados no sean los esperados ni la mejor opción para el contexto de su aplicación.

