---
title: Función GUID | Microsoft Docs
description: Información de referencia de la función GUID en Power Apps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/14/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88028d2dc4016d294e051ecff66b590996b57966
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730862"
ms.PowerAppsDecimalTransform: true
---
# <a name="guid-function-in-power-apps"></a>Función GUID en Power apps
Convierta una cadena de GUID ([identificador único global](https://en.wikipedia.org/wiki/Universally_unique_identifier)) en un valor GUID o cree un valor GUID.

## <a name="description"></a>Descripción
Use la función **GUID** para convertir una cadena que contiene la representación hexadecimal de un GUID a un valor GUID que se puede pasar a una base de datos. Los sistemas de base de datos, como Common Data Service y SQL Server, usan los valores GUID como claves.

La cadena que se pase puede contener letras mayúsculas o minúsculas, pero debe tener 32 dígitos hexadecimales en cualquiera de estos formatos:

- **"123e4567-e89b-12d3-a456-426655440000"** (guiones en ubicaciones estándar)
- **"123e4567e89b12d3a456426655440000"** (sin guiones)

Si no se especifica un argumento, esta función crea un GUID.

Para convertir un valor GUID en una cadena, simplemente úselo en un contexto de cadena. El valor GUID se convertirá en una cadena de representación hexadecimal con letras minúsculas y guiones. 

Al generar un nuevo GUID, esta función usa números pseudoaleatorios para crear una versión 4 del GUID de [IETF RFC 4122](https://www.ietf.org/rfc/rfc4122.txt) . Al convertir una cadena en un GUID, esta función admite cualquier versión de GUID aceptando cualquier cadena de 32 dígitos hexadecimales.

## <a name="volatile-functions"></a>Funciones volátiles
**GUID** es una función volátil cuando se usa sin argumento. Cada vez que se evalúa, la función devuelve un valor diferente.  

Cuando se usa en una fórmula de flujo de datos, una función volátil solo devuelve un valor diferente si se vuelve a evaluar la fórmula en la que aparece. Si no se realiza ningún otro cambio en la fórmula, presenta el mismo valor durante la ejecución de la aplicación.

Por ejemplo, un control de etiqueta en el que la propiedad **Text** se establece en **GUID()** no cambiará mientras la aplicación está activa. Solo se generará un valor distinto si la aplicación se cierra y se vuelve a abrir.

La función se volverá a evaluar si forma parte de una fórmula en la que haya cambiado algún otro elemento. Si, por ejemplo, la propiedad **Text** de un control **Label** se establece en esta fórmula, se genera un GUID cada vez que el usuario cambia el valor del control **Text input**:

**TextInput1.Text & " " & GUID()**

Cuando se usa en una [fórmula de comportamiento](../working-with-formulas-in-depth.md), **GUID** se evalúa cada vez que se evalúa la fórmula. Para más información, vea los ejemplos más adelante en este tema.

## <a name="syntax"></a>Sintaxis
**GUID**( [ *GUIDString* ] )

* *GUIDString* (opcional).  Cadena de texto que contiene la representación hexadecimal de un GUID. Si no se especifica ninguna cadena, se crea un GUID.

## <a name="examples"></a>Ejemplos

#### <a name="basic-usage"></a>Uso básico

Para devolver un valor GUID basado en la representación de cadena hexadecimal:

* **GUID( "0f8fad5b-d9cb-469f-a165-70867728950e" )**

También puede especificar la cadena de GUID sin guiones. Esta fórmula devuelve el mismo valor GUID:

* **GUID( "0f8fad5bd9cb469fa16570867728950e" )**

Se utiliza en contexto para establecer el campo **Estado** de un nuevo registro de la base de datos en un valor establecido:

* **Patch( Products; Default( Products ); { Status: GUID( "F9168C5E-CEB2-4faa-B6BF-329BF39FA1E4" ) } )**

Probablemente no quiera mostrar los GUID a los usuarios, pero los GUID pueden ayudarle a depurar la aplicación. Para mostrar el valor del campo **Estado** en el registro que creó en el ejemplo anterior, establezca la propiedad **Text** de un control **Label** en esta fórmula:

* **First( Products ).Status**

El control **Label** mostrará **f9168c5e-ceb2-4faa-b6bf-329bf39fa1e4**.

#### <a name="create-a-table-of-guids"></a>Creación de una tabla de valores GUID

1. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** de un control de **[botón](../controls/control-button.md)** en esta fórmula:

    **ClearCollect( NewGUIDs; ForAll( [ 1; 2; 3; 4; 5 ]; GUID() ) )**

    Con esta fórmula se crea una tabla de una sola columna que se usa para iterar cinco veces, lo que produce cinco GUID.

1. Agregue un control **[Data Table](../controls/control-data-table.md)** , establezca su propiedad **Items** en **NewGUIDs** y muestre el campo **Valor**.

1. Haga clic en el botón o púlselo para seleccionarlo, manteniendo la tecla Alt presionada.

    La tabla de datos muestra una lista de GUID:

    ![Pantalla en la que se muestra una tabla de datos con cinco valores GUID distintos](media/function-guid/guid-collection-1.png)

1. Vuelva a seleccionar el botón para mostrar otra lista de GUID:

    ![Misma pantalla en la que se muestra una tabla de datos con un nuevo conjunto de cinco valores GUID distintos](media/function-guid/guid-collection-2.png)

Para generar un GUID único en lugar de una tabla, utilice esta fórmula:

**Set( NewGUID; GUID() )**
