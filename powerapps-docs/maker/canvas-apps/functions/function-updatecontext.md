---
title: Función UpdateContext | Microsoft Docs
description: Información de referencia para la función UpdateContext de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/08/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 646a5de203c713d59965f7787dabe087c0a33f51
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678175"
---
# <a name="updatecontext-function-in-powerapps"></a>Función UpdateContext de PowerApps
Crea o actualiza [variables de contexto](../working-with-variables.md#use-a-context-variable) de la pantalla actual.

## <a name="overview"></a>Información general
Use la función **UpdateContext** para crear una variable de contexto, que guarda temporalmente un fragmento de información, como el número de veces que el usuario ha seleccionado un botón o el resultado de una operación de datos.

El ámbito de las variables de contexto es una pantalla, lo que significa que no se puede generar una fórmula que haga referencia a una variable de contexto de otra pantalla. Si usó otra herramienta de programación, se puede pensar en una variable de contexto como en una variable local.  Use la función [**Set** ](function-set.md) para trabajar con variables globales que estén disponibles en toda la aplicación.  

Las aplicaciones de energía se basan en fórmulas que se recalculan automáticamente a medida que el usuario interactúa con una aplicación.  Las variables de contexto no tienen esta ventaja y pueden hacer que la aplicación sea más difícil de crear y comprender.  Antes de utilizar una variable de contexto, repase cómo [trabajar con variables](../working-with-variables.md).

## <a name="description"></a>Descripción
Para crear o actualizar una variable de contexto, pase un solo [registro](../working-with-tables.md#records) a la función **UpdateContext**. En cada registro, especifique el nombre de un [columna](../working-with-tables.md#columns), que defina o coincida con el nombre de la variable, y el valor en el que va a establece esa variable.

* Si especifica el nombre de una variable que ha definido previamente, **UpdateContext** establece el valor de la variable en el valor que especifique.
* Si especifica el nombre de una variable que no existe todavía, **UpdateContext** crea una variable con ese nombre y establece el valor de esa variable en el valor que especifique.
* Si previamente se ha definido una variable pero no se especifica en esta fórmula de **UpdateContext** específica, su valor sigue siendo el mismo.

Se pueden crear implícitamente variables de contexto mediante la función **UpdateContext** o [**Navigate**](function-navigate.md).  No es necesaria ninguna declaración explícita.  Si quita todas las referencias de **UpdateContext** y **Navigate** a una variable de contexto, posteriormente, esa variable de contexto dejará de existir.  Para borrar una variable, establezca su valor en el resultado de la función [**Blank**](function-isblank-isempty.md).

Puede ver los valores de las variables, las definiciones y los usos con la vista Variables del menú Archivo en el entorno de creación.

Para hacer referencia a una variable de contexto en una fórmula, se usa el nombre de columna de la variable. Por ejemplo, **UpdateContext ({ShowLogo: true})** crea una variable de contexto llamada **ShowLogo** y establece su valor en **true**. Después, puede usar el valor de esta variable de contexto con el nombre **ShowLogo** en una fórmula.  Puede escribir **ShowLogo** como fórmula para la propiedad **Visible** de un control de imagen, y mostrar u ocultar ese control en función de si el valor de la variable de contexto es **true** o **false**.

Tal y como se muestra en los ejemplos más adelante en este tema, las variables de contexto pueden contener distintos tipos de información, incluidos los siguientes:

* un valor único
* un registro
* una tabla
* una referencia de objeto
* el resultado de una fórmula

Una variable de contexto guarda su valor hasta que se cierra la aplicación.  Si define una variable de contexto y establece su valor en una pantalla concreta, esa información permanece intacta aunque el usuario cambie a otra pantalla.  Una vez que se cierre la aplicación, el valor de la variable de contexto se perderá y deberá volver a crearlo al cargar la aplicación de nuevo.  

El ámbito de una variable de contexto se limita a una pantalla. Si desea definir una variable de contexto en una pantalla y modificarla desde otra pantalla, debe crear una fórmula que se basa en la función **[Navigate](function-navigate.md)** .  O bien, use una variable global.

**UpdateContext** no devuelve ningún valor y solo se puede usar en una [fórmula de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**UpdateContext**( *UpdateRecord* )

* *UpdateRecord*: requerido. Registro que contiene el nombre de al menos una columna y un valor para esa columna. Se crea o se actualiza una variable de contexto para cada columna y valor que especifique.

**UpdateContext**( { *ContextVariable1*: *Value1* [, *ContextVariable2*: *Value2* [, ... ] ] } )

* *ContextVariable1*: requerido.  Nombre de la variable de contexto que se va a crear o actualizar.
* *Value1*: requerido.  Valor que se asigna a la variable de contexto.
* *ContextVariable2*: *Value2*, ...: opcional. Variables de contexto adicionales que se van a crear o actualizar, y sus valores.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **UpdateContext( {&nbsp;Counter:&nbsp;1&nbsp;} )** |Crea o modifica la variable de contexto **Counter** y establece su valor en **1**. |**Counter** tiene el valor **1**. Puede hacer referencia a esa variable con el nombre **Counter** en una fórmula. |
| **UpdateContext( {&nbsp;Counter:&nbsp;2&nbsp;} )** |Establece el valor de la variable de contexto **Counter** del ejemplo anterior en **2**. |**Counter** tiene el valor **2**. |
| **UpdateContext( {&nbsp;Name:&nbsp;"Lily",&nbsp;Score:&nbsp;10&nbsp;} )** |Crea o modifica las variables de contexto **Name** y **Score**, y establece sus valores en **Lily** y **10**, respectivamente. |**Name** tiene el valor **Lily**, y **Score** tiene el valor **10**. |
| **UpdateContext( {&nbsp;Person:&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;} )** |Crea o modifica la variable de contexto **Person** y establece su valor en un registro. El registro contiene dos columnas, llamadas **Name** y **Address**. El valor de la columna **Name** es **Milton**, y el valor de la columna **Address** es **1 Main St**. |**Person** tiene el valor del registro **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}** .<br><br>Haga referencia a este registro como un todo con el nombre **Person**, o haga referencia a una columna individual de este registro con **Person.Name** o **Person.Address**. |
| **UpdateContext( {&nbsp;Person: Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;) }&nbsp;)** |Trabaja con la función **[Patch](function-patch.md)** para actualizar la variable de contexto **Person** y establece el valor de la columna **Address** en **2 Main St**. |**Person** ahora tiene el valor del registro **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}** . |

### <a name="step-by-step-example"></a>Ejemplo paso a paso
1. Asigne un nombre a la pantalla predeterminada **Origen**, agregue otra pantalla y asígnele el nombre **Destino**.
2. En la pantalla **Origen**, agregue dos botones y establezca sus propiedades **[Text](../controls/properties-core.md)** de forma que una sea **Inglés** y la otra **Español**.
3. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón **Inglés** en esta expresión:<br>**Navigate(Target, ScreenTransition.Fade, {Language:"English"})**
4. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón **Español** en esta expresión:<br>**Navigate(Target, ScreenTransition.Fade, {Language:"Spanish"})**
5. En la pantalla **Destino**, agregue una etiqueta y establezca su propiedad **[Text](../controls/properties-core.md)** en esta expresión:<br>**If(Language="Inglés", "Hello!", "¡Hola!")**
6. En la pantalla **Destino**, seleccione **Formas** en la pestaña **Insertar** y seleccione la flecha Anterior.
7. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** de la flecha Anterior en esta fórmula:<br>**Navigate(Source, ScreenTransition.Fade)**
8. En la pantalla **Origen**, presione F5 y seleccione el botón de cualquiera de estos idiomas.

    En la pantalla **Destino**, la etiqueta aparece en el idioma correspondiente a botón que ha seleccionado.
9. Seleccione la flecha Anterior para volver a la pantalla **Origen** y seleccione el botón del otro idioma.

    En la pantalla **Destino**, la etiqueta aparece en el idioma correspondiente a botón que ha seleccionado.
10. Presione Esc para volver al área de trabajo predeterminada.

[Otro ejemplo](../add-screen-context-variables.md)

