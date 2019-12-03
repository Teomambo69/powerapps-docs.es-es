---
title: Función Establecer| Microsoft Docs
description: Información de referencia de la función Set de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/29/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 72adafedfe09a125fda2a48d5617b2cd8c79242a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678198"
ms.PowerAppsDecimalTransform: true
---
# <a name="set-function-in-powerapps"></a>Función Set en PowerApps
Establece el valor de una variable global.

## <a name="overview"></a>Información general
La función **Set** se usa para establecer el valor de una variable global, que guarda temporalmente un fragmento de información, como el número de veces que el usuario ha seleccionado un botón o el resultado de una operación de datos.  

Las variables globales están disponibles en todas las pantallas de la aplicación. Son las variables más simples y se pueden usar en la mayor parte de las situaciones. También hay variables de contexto cuyo ámbito es una sola pantalla y colecciones que permiten modificar tablas a nivel de fila. Para obtener más información acerca de estas otras opciones, consulte [comprender las variables](../working-with-variables.md).

Las aplicaciones de energía se basan en fórmulas que se recalculan automáticamente a medida que el usuario interactúa con una aplicación. Las fórmulas que dependan de una variable se actualizarán automáticamente cuando cambie. Sin embargo, la variable no se actualizará automáticamente si cambia el valor de la fórmula utilizada en la función **set** . Esto requiere que App Maker actualice manualmente la variable, lo que puede ser propenso a errores y más difícil de entender. Antes de usar una variable, revise [comprender las variables](../working-with-variables.md).

## <a name="description"></a>Descripción
Las variables globales se crean implícitamente mediante la función **Set**. No se requiere ninguna declaración explícita. Si quita todas las funciones de **conjunto** de una variable global, la variable global dejará de existir. Para borrar una variable, establezca su valor en el resultado de la [función **Blank** ](function-isblank-isempty.md).

Puede ver los valores de las variables, las definiciones y los usos con la vista variables en el menú **archivo** de Power apps Studio.

Tal como mostrarán los ejemplos de este mismo tema, las variables de contexto pueden contener distintos tipos de información, entre los que se incluyen:

* un valor único
* un registro
* una tabla
* una referencia de objeto
* el resultado de una fórmula

Una variable global guarda su valor hasta que se cierra la aplicación.  Una vez que se cierre, el valor de la variable global se perderá y deberá volver a crearlo al cargar la aplicación de nuevo.

Las variables globales no pueden usar el mismo nombre que una colección o un control existentes.  Sin embargo, pueden usar el mismo nombre que una variable de contexto.  Para eliminar la ambigüedad entre ambas, use el [operador de desambiguación](operators.md#disambiguation-operator).

**Set** no devuelve ningún valor y solo se puede usar en una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Set**( *VariableName*; *Value* )

* *VariableName* (se requiere).  Nombre de la variable global que se va a crear o actualizar.
* *Value* (se requiere).  Valor que se asigna a la variable de contexto.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Set(&nbsp;Counter;&nbsp;1&nbsp;)** |Crea o modifica la variable global **Counter** y establece su valor en **1**. |**Counter** tiene el valor **1**. Para hacer referencia a dicha variable, utilice el nombre **Counter** en una fórmula en cualquier pantalla. |
| **Set(&nbsp;Counter;&nbsp;2&nbsp;)** |Establece el valor de la variable global **Counter** del ejemplo anterior en **2**. |**Counter** tiene el valor **2**. |
| **Set(&nbsp;Counter;&nbsp;Counter + 1&nbsp;)** |Aumenta el valor de la variable global **Counter** del ejemplo anterior en **3**. |**Counter** tiene el valor **3**. |
| **Set(&nbsp;Name;&nbsp;"Lily" )** |Crea o modifica la variable global **Name** y establece su valor en **Lily**. |**Name** tiene el valor **Lily**. |
| **Set(&nbsp;Person;&nbsp;{&nbsp;Name:&nbsp;"Milton"; Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;} )** |Crea o modifica la variable global **Person** y establece su valor en un registro. El registro contiene dos columnas, llamadas **Name** y **Address**. El valor de la columna **Name** es **Milton**, y el valor de la columna **Address** es **1 Main St**. |**Person** tiene el valor del registro **{&nbsp;Name:&nbsp;"Milton"; Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}** }.<br><br>Haga referencia a este registro como un todo con el nombre **Person**, o haga referencia a una columna individual de este registro con **Person.Name** o **Person.Address**. |
| **Set(&nbsp;Person; Patch(&nbsp;Person;&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;)&nbsp;)** |Trabaja con la función **[Patch](function-patch.md)** para actualizar la variable global **Person** y establece el valor de la columna **Address** en **2 Main St**. |**Person** ahora tiene el valor del registro **{&nbsp;Name:&nbsp;"Milton"; Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}** }. |

