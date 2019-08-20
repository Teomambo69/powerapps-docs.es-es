---
title: With (función) | Microsoft Docs
description: Información de referencia de la función with en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4dff9fa391fcecd19b3cc3195d8353e342ef46b8
ms.sourcegitcommit: 9163abbe9a24298f216f15139f977adfd2c3f2ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559247"
ms.PowerAppsDecimalTransform: true
---
# <a name="with-function-in-powerapps"></a>Función with en PowerApps
Calcula valores y realiza acciones para un único [registro](../working-with-tables.md#records), incluidos los registros insertados de valores con nombre.

## <a name="description"></a>DESCRIPCIÓN

La función **with** evalúa una fórmula para un único registro.  La fórmula puede calcular un valor o realizar acciones, como modificar datos o trabajar con una conexión.  Utilice la [ función forall](function-with.md) para evaluar una fórmula para todos los registros de una tabla de registros.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Use **con** para mejorar la legibilidad de las fórmulas complejas dividiéndolo en subfórmulas con nombre más pequeñas.  Estos valores con nombre actúan como variables locales simples que se limitan al ámbito de **con**.  La misma sintaxis de registro en línea que se usa con la [función **UpdateContext** ](function-updatecontext.md) se puede utilizar con **con**.  El uso **de con** es preferible a las variables globales o de contexto, ya que son independientes, fáciles de entender y se pueden usar en cualquier contexto de fórmula declarativo.  

Use **con** para tener acceso a los campos del registro devueltos por funciones como, por ejemplo, [**patch**](function-patch.md) o [**Match**](function-ismatch.md).  **With** contiene el valor de estas funciones lo suficientemente largo para usarse en cálculos o acciones adicionales.  

Si el argumento de *registro* en **with** es un error, la función devolverá ese error y no se evaluará la *fórmula* .

## <a name="syntax"></a>Sintaxis
**Con** ( *Registro*, *fórmula* )

* *Registro* : requerido. Registro sobre el que se va a actuar.  Para los valores de names, use la sintaxis en línea`{ name1: value1; name2: value2; ... }`
* *Fórmula* : requerido.  Fórmula que se va a evaluar para el *registro*.  La fórmula puede hacer referencia a cualquiera de los campos de *registro* directamente como un ámbito de registro.

## <a name="examples"></a>Ejemplos

### <a name="simple-named-values"></a>Valores con nombre simples

```powerapps-comma
With( { radius: 10; 
        height: 15 };
    Pi() * (radius*radius) * height
)
// Result: 4712,38898038 (as shown in a label control)
```

En este ejemplo se usa un registro de valores con nombre para calcular el volumen de un cilindro.  **With** se usa para capturar todos los valores de entrada de forma conjunta, lo que facilita su separación del propio cálculo.  

### <a name="nested-with"></a>Anidado con

![](media/function-with/interest-calculator.gif)

```powerapps-comma
With( { AnnualRate: RateSlider/8/100;        // slider moves in 1/8th increments and convert to decimal
        Amount: AmountSlider*10000;          // slider moves by 10;000 increment
        Years: YearsSlider;                  // slider moves in single year increments; no adjustment required
        AnnualPayments: 12 };                // number of payments per year
      With( { r: AnnualRate/AnnualPayments;  // interest rate
              P: Amount;                     // loan amount
              n: Years*AnnualPayments };     // number of payments
            r*P / (1 - (1+r)^-n)             // standard interest calculation
      )
)  
```

Este ejemplo se anida **con** funciones para crear un cálculo de dos niveles para los [pagos mensuales](https://en.wikipedia.org/wiki/Mortgage_calculator#Monthly_payment_formula)de hipotecas.  Siempre que no haya ningún conflicto, todos los externos **con** valores con nombre están disponibles dentro del interior **con**.

Dado que los controles deslizantes solo pueden moverse en incrementos de 1, los controles deslizantes se dividen o multiplican para crear eficazmente un incremento personalizado.  En el caso de la tasa de interés, **RateSlider** tiene su propiedad **Max** establecida en **48**, dividida entre 8 para un incremento del punto de porcentaje 1/8 y dividida entre 100 para que se describa de un porcentaje a un decimal, cubriendo el intervalo del 0,125% al 6%.  En el caso de la cantidad de préstamo, **AmountSlider** tiene la propiedad **Max** establecida en **60** y se multiplica por 10.000, cubriendo el intervalo de 10.000 a 600.000.

La **con** se vuelve a calcular automáticamente a medida que se mueven los controles deslizantes y se muestra el nuevo pago de préstamo.  No se usa ninguna variable y no es necesario usar la propiedad **onchange** de los controles deslizantes.

Estas son las instrucciones detalladas para crear esta aplicación:
1. Cree una nueva aplicación.
2. Agregue un [ control deslizante](../controls/control-slider.md) y asígnele el nombre **RateSlider**.  Establezca su propiedad **Max** en 48.
3. Agregue un [control **etiqueta** ](../controls/control-text-box.md) a la izquierda del control deslizante.  Establezca su propiedad **texto** en **"tasa de interés:"** .
3. Agregue un control **etiqueta** a la derecha del control deslizante.  Establezca su propiedad **texto** en la fórmula **RateSlider/8 & "&nbsp;%"** .
3. Agregue otro control deslizante y asígnele el nombre **AmountSlider**.  Establezca su propiedad **Max** en 60.
3. Agregue un control **etiqueta** a la izquierda de este control deslizante.  Establezca su propiedad **texto** en **"importe de préstamo:"** . 
3. Agregue un control **etiqueta** a la derecha de este control deslizante.  Establezca su propiedad **texto** en la fórmula **AmountSlider/8 * 10000**
4. Agregue otro control deslizante y asígnele el nombre **YearsSlider**.  Establezca su propiedad **Max** en 40.
3. Agregue un control **etiqueta** a la izquierda de este control deslizante.  Establezca su propiedad **Text** en **"Number of years:"** . 
3. Agregue un control **etiqueta** a la derecha de este control deslizante.  Establezca su propiedad **texto** en la fórmula **YearsSlider**.
5. Agregue un control **etiqueta** y establezca su propiedad **texto** en la fórmula mostrada anteriormente.
3. Agregue un control **etiqueta** a la izquierda del último control etiqueta.  Establezca su propiedad **texto** en **"periódico monthly payment:"** .  

### <a name="primary-key-returned-from-patch"></a>Clave principal devuelta por la revisión

```powerapps-comma
With( Patch( Orders; Defaults( Orders ); { OrderStatus: "New" } );
      ForAll( NewOrderDetails; 
              Patch( OrderDetails; Defaults( OrderDetails ); 
                     { Order: OrderID;          // from With's first argument; primary key of Patch result
                       Quantity: Quantity;      // from ForAll's NewOrderDetails table
                       ProductID: ProductID }   // from ForAll's NewOrderDetails table
              )
      )
)
```

En este ejemplo se agrega un registro a la tabla **Order** de SQL Server.  A continuación, usa la clave principal devuelta para el pedido, devuelta por la función **patch** en el campo **OrderID** , para crear registros relacionados en la tabla **OrderDetails** .  

### <a name="extracted-values-with-a-regular-expression"></a>Valores extraídos con una expresión regular

```powerapps-comma
With( 
    Match( "PT2H1M39S"; "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" );
    Time( Value( hours ); Value( minutes ); Value( seconds ) )
)
// Result: 2:01 AM (as shown in a label control; use the Text function to see the seconds)
```

En este ejemplo se extraen las horas, los minutos y los segundos de un valor de duración ISO 8601 y, a continuación, se usan estas subcoincidencias para crear un valor de fecha y hora. 

Tenga en cuenta que, aunque las subcoincidencias contienen números, siguen en una cadena de texto.  Utilice la función [**Value**](function-value.md) para convertir en un número antes de realizar operaciones matemáticas.  

