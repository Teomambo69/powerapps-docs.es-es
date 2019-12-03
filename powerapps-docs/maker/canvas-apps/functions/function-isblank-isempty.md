---
title: Funciones Blank, Coalesce, IsBlank e IsEmpty | Microsoft Docs
description: Información de referencia de las funciones Blank, Coalesce, IsBlank e IsEmpty de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.component: canvas
ms.date: 08/27/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a026d801a6bda6ae82884f5fab94f09b4fdde571
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680383"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-powerapps"></a>Funciones Blank, Coalesce, IsBlank e IsEmpty en PowerApps
Comprueba si un valor está en blanco o una [tabla](../working-with-tables.md) no contiene [registros](../working-with-tables.md#records), y proporciona una manera de crear valores *blank*.

## <a name="overview"></a>Información general
*Blank* es un marcador de posición para "sin valor" o "valor desconocido".  Por ejemplo, la propiedad **seleccionada** de un control de **[cuadro combinado](../controls/control-combo-box.md)** está *en blanco* si el usuario no ha realizado una selección. Muchos orígenes de datos pueden almacenar y devolver valores NULL, que se representan en las aplicaciones de energía como *en blanco*.

Cualquier propiedad o valor calculado en Power apps puede estar *en blanco*.  Por ejemplo, un valor booleano normalmente tiene uno de dos valores: **true** o **false**.  Pero además de estos dos, también puede estar *en blanco* , lo que indica que no se conoce el estado.  Esto es similar a Microsoft Excel, donde una celda de hoja de cálculo empieza en blanco sin contenido, pero puede contener los valores **true** o **false** (entre otros). En cualquier momento, se puede volver a borrar el contenido de la celda y devolverlo a un estado *en blanco* .

Una *cadena vacía* hace referencia a una cadena que no contiene ningún carácter.  La [función **Len** ](function-len.md) devuelve cero para este tipo de cadena y se puede escribir en una fórmula como dos comillas dobles sin nada entre `""`.  Algunos controles y orígenes de datos usan una cadena vacía para indicar una condición de "sin valor".  Para simplificar **la creación de aplicaciones** , las funciones esblanco y **Coalesce** comprueban si hay valores *en blanco* o cadenas vacías.    

En el contexto de la función **IsEmpty** , *Empty* es específico de las tablas que no contienen registros. La estructura de tabla puede estar intacta, con nombres de [columna](../working-with-tables.md#columns), pero ningún dato en la tabla. Una tabla puede comenzar como vacía, obtener registros y ya no estar vacía y luego quitarse los registros y estar de nuevo vacía.

> [!NOTE]
> Estamos en un período de transición.  Hasta ahora, el *espacio en blanco* también se ha utilizado para notificar los errores, lo que impide que se diferencie un "valor" no válido de un error.  Por esta razón, en este momento, solo se admite el almacenamiento de valores *en blanco* para las colecciones locales.  Puede almacenar valores en *blanco* en otros orígenes de datos si activa la característica experimental "administración de errores de nivel de fórmulas" en el menú Archivo, configuración de la aplicación, configuración avanzada, características experimentales.  Estamos trabajando activamente para finalizar esta característica y completar la separación adecuada de los valores *en blanco* de los errores.

## <a name="description"></a>Descripción
La función **Blank** devuelve un valor *blank*. Use esta función para almacenar un valor NULL en un origen de datos que admita estos valores, de forma que se quiten en la práctica todos los valores del campo.

La **función esblanco comprueba** un valor *en blanco* o una cadena vacía.  La prueba incluye cadenas vacías para facilitar la creación de aplicaciones, ya que algunos orígenes de datos y controles usan una cadena vacía cuando no hay ningún valor.  Para probar específicamente si hay un valor *en blanco* , use `if( Value = Blank(), ...` en lugar de **esblanco**.

La función **Coalesce** evalúa sus argumentos en orden y devuelve el primer valor que no está *en blanco* ni una cadena vacía.  Utilice esta función para reemplazar un valor *en blanco* o una cadena vacía con un valor diferente, pero sin modificar los valores de cadena que no estén*en blanco* y que no estén vacíos.  Si todos los argumentos están *en blanco* o cadenas vacías, la función devuelve un valor *en*blanco, lo que permite que la **combinación** sea una buena manera de convertir cadenas vacías en valores *en blanco* .  Todos los argumentos de **Coalesce** debe ser del mismo tipo; por ejemplo, no puede combinar números con cadenas de texto.  

`Coalesce( value1, value2 )` es el equivalente más conciso de `If( Not IsBlank( value1 ), value1, Not IsBlank( value2 ), value2 )` y no requiere que **value1** y **value2** se evalúen dos veces.  La [función **If** ](function-if.md) devuelve un valor *en blanco* si no hay ninguna fórmula "Else", como es el caso.

La función **IsEmpty** comprueba si una tabla contiene registros. Es equivalente a usar la función **[CountRows](function-table-counts.md)** y la comprobación de cero. Puede usar **IsEmpty** para comprobar errores de origen de datos en combinación con la función **[Errors](function-errors.md)** .

El valor devuelto para **IsBlank** e **IsEmpty** es un valor booleano **true** o **false**.

## <a name="syntax"></a>Sintaxis
**Blank**()

**Coalesce**( *Valor1* [, *Valor2*, ... ] )

* *Valores*: requerido. Valores que se van a comprobar.  Cada valor se evalúa en orden hasta que se encuentra un valor que no está *en blanco* y no es una cadena vacía.  Los valores después de este punto no se evalúan.  

**IsBlank**( *Value* )

* *Value*: requerido. Valor que se va a comprobar para un valor *en blanco* o una cadena vacía.

**IsEmpty**( *Table* )

* *Table*: requerido. Tabla en la que se van a comprobar registros.

## <a name="examples"></a>Ejemplos
### <a name="blank"></a>Blank
> [!NOTE]
> Actualmente, el siguiente ejemplo solo funciona en colecciones locales.  Puede almacenar valores en *blanco* en otros orígenes de datos si activa la característica experimental "administración de errores de nivel de fórmulas" en el menú Archivo, configuración de la aplicación, configuración avanzada, características experimentales.  Estamos trabajando activamente para finalizar esta característica y completar la separación de los valores *en blanco* de los errores.

1. Cree una aplicación desde el principio y agregue un control **Botón**.
2. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón en esta fórmula:

    ```powerapps-dot
    ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )
    ```
3. Obtenga una vista previa de la aplicación, haga clic o pulse en el botón que agregó y luego cierre la vista previa.  
4. En el menú **Archivo**, haga clic o pulse en **Colecciones**.

     Aparece la colección **Cities**, que muestra un registro con "Seattle" y "Rainy":

    ![Colección que muestra Seattle con tiempo lluvioso](./media/function-isblank-isempty/seattle-rainy.png)
5. Haga clic o pulse en la flecha Atrás para volver al área de trabajo predeterminada.
6. Agregue un control **Label** y establezca su propiedad **Text** en esta fórmula:

    ```powerapps-dot
    IsBlank( First( Cities ).Weather )
    ```

    La etiqueta muestra **false** porque el campo **Weather** contiene un valor ("Rainy").
7. Agregue un segundo botón y establezca su propiedad **OnSelect** en esta fórmula:

    ```powerapps-dot
    Patch( Cities, First( Cities ), { Weather: Blank() } )
    ```
8. Obtenga una vista previa de la aplicación, haga clic o pulse en el botón que agregó y luego cierre la vista previa.  

    El campo **Weather** del primer registro de **Cities** se sustituye por un valor *blank*, de forma que se reemplaza el valor inicial "Rainy" que estaba ahí anteriormente.

    ![Colección que muestra Seattle con un campo Weather en blanco](./media/function-isblank-isempty/seattle-blank.png)

    La etiqueta muestra **true** porque el campo **Weather** ya no contiene ningún valor.

### <a name="coalesce"></a>Coalesce

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Coalesce (&nbsp;en blanco (),&nbsp;1&nbsp;)** |Comprueba el valor devuelto por la función **Blank**, que siempre devuelve un valor *blank*. Dado que el primer argumento está *en blanco*, la evaluación continúa con el argumento siguiente hasta que se encuentre un valor que no esté*en blanco* y una cadena que no esté vacía. |**1** |
| **Coalesce ("", 2)** |Comprueba el primer argumento, que es una cadena vacía. Dado que el primer argumento es una cadena vacía, la evaluación continúa con el argumento siguiente hasta que se encuentre un valor que no esté*en blanco* y una cadena que no esté vacía. |**2** |
| **Coalesce (Blank (), "", Blank (), "", 3, 4)** |**Coalesce** comienza al principio de la lista de argumentos y evalúa cada argumento a su vez hasta que se encuentra un valor que no está*en blanco* y una cadena no vacía.  En este caso, los cuatro primeros argumentos devuelven un valor *en blanco* o una cadena vacía, por lo que la evaluación continúa hasta el quinto argumento. El quinto argumento es una cadena que no está*en blanco* y no está vacía, por lo que la evaluación se detiene aquí. Se devuelve el valor del quinto argumento y no se evalúa el sexto argumento. |**3** |
| **Coalesce ("")** | Comprueba el primer argumento, que es una cadena vacía. Dado que el primer argumento es una cadena vacía y no hay más argumentos, la función devuelve *Blank*.   |*blank* |

### <a name="isblank"></a>EsBlanco
1. Cree una aplicación desde el principio, agregue un control de entrada de texto y llámelo **FirstName**.
2. Agregue una etiqueta y establezca su propiedad **[Text](../controls/properties-core.md)** en esta fórmula:

    ```powerapps-dot
    If( IsBlank( FirstName.Text ), "First Name is a required field." )
    ```

    De forma predeterminada, la propiedad **[Text](../controls/properties-core.md)** de un control de entrada de texto se establece en **"Entrada de texto"** . Como la propiedad contiene un valor, no está en blanco, y la etiqueta no muestra ningún mensaje.
3. Quite todos los caracteres del control de entrada de texto, espacios incluidos.

    Dado que la propiedad **[Text](../controls/properties-core.md)** ya no contiene ningún carácter, es una cadena vacía y **esblanco (FirstName. Text)** será **true**. Se muestra el mensaje de campo requerido.

Para más información sobre cómo realizar la validación mediante otras herramientas, consulte la función **[Validate](function-validate.md)** y el [uso de orígenes de datos](../working-with-data-sources.md).  

Otros ejemplos:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Esblanco (&nbsp;en blanco ()&nbsp;)** |Comprueba el valor devuelto por la función **Blank**, que siempre devuelve un valor *blank*. |**true** |
| **IsBlank( "" )** |Una cadena que no contiene ningún carácter. |**true** |
| **IsBlank( "Hello" )** |Una cadena que contiene uno o más caracteres. |**false** |
| **IsBlank( *AnyCollection* )** |Como la [colección](../working-with-data-sources.md#collections) existe, no está en blanco, incluso si no contiene ningún registro. Para comprobar si existe una colección vacía, use **IsEmpty** en su lugar. |**false** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |El carácter inicial de **[Mid](function-left-mid-right.md)** está más allá del final de la cadena.  El resultado es una cadena vacía. |**true** |
| **IsBlank( If( false, false ) )** |Una función **[If](function-if.md)** sin *ElseResult*.  Como la condición es siempre **false**, esta función **[If](function-if.md)** siempre devuelve *blank*. |**true** |

### <a name="isempty"></a>IsEmpty
1. Cree una aplicación desde el principio y agregue un control **Botón**.
2. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón en esta fórmula:

    **Collect( IceCream, { Flavor: "Strawberry", Quantity: 300 }, { Flavor: "Chocolate", Quantity: 100 } )**
3. Obtenga una vista previa de la aplicación, haga clic o pulse en el botón que agregó y luego cierre la vista previa.  

    Se crea una colección denominada **IceCream** con estos datos:

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    Esta colección tiene dos registros y no está vacía. **IsEmpty( IceCream )** devuelve **false** y **CountRows( IceCream )** devuelve **2**.
4. Agregue un segundo botón y establezca su propiedad **[OnSelect](../controls/properties-core.md)** en esta fórmula:

    **Clear( IceCream )**
5. Obtener una vista previa de la aplicación, haga clic o pulse en el segundo botón y luego cierre la vista previa.  

    Ahora, la colección está vacía:

    ![](media/function-isblank-isempty/icecream-clear.png)

    La función **[Clear](function-clear-collect-clearcollect.md)** quita todos los registros de una colección, lo que da lugar a una colección vacía. **IsEmpty( IceCream )** devuelve **true** y **CountRows( IceCream )** devuelve **0**.

También puede usar **IsEmpty** para comprobar si una tabla calculada está vacía, como muestran estos ejemplos:

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |La tabla de una columna contiene tres registros y, por lo tanto, no está vacía. |**false** |
| **IsEmpty( [&nbsp;] )** |La tabla de una columna no contiene registros y está vacía. |**true** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |La tabla de una columna no contiene valores que sean mayores que 5.  El resultado del filtro no contiene ningún registro y está vacío. |**true** |

