---
title: Funciones AddColumns, DropColumns, RenameColumns y ShowColumns | Microsoft Docs
description: Información de referencia para las funciones AddColumns, DropColumns, RenameColumns y ShowColumns en PowerApps, incluidos la sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc682694bb22ecc63ecc762a735df07950ce29d3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61543840"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>Funciones AddColumns, DropColumns, RenameColumns y ShowColumns en PowerApps
Forma una [tabla](../working-with-tables.md) agregando, quitando, cambiando el nombre y seleccionando sus [columnas](../working-with-tables.md#columns).

## <a name="overview"></a>Información general
Estas funciones dan forma a una tabla mediante el ajuste de sus columnas:

* Reducción de una tabla que contiene varias columnas a una sola columna para su uso con las funciones de columna única, como **[Lower](function-lower-upper-proper.md)** o  **[Abs](function-numericals.md)** .  
* Incorporación de una columna calculada a una tabla (por ejemplo, una columna **Total Price** que muestre el resultado de multiplicar **Quantity** por **Unit Price**).
* Cambio del nombre de una columna a algo más significativo, para mostrarla a los usuarios o para su uso en las fórmulas.

Una tabla es un valor en PowerApps, como una cadena o un número.  Puede especificar una tabla como un argumento en una fórmula, y las funciones pueden devolver una tabla como resultado.

> [!NOTE]
> Las funciones que se describe en este tema no modifican la tabla original. En su lugar, se toma esa tabla como argumento y devuelven una tabla nueva con una transformación aplicada. Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.  

No se pueden modificar las columnas de un [origen de datos](../working-with-data-sources.md) mediante el uso de estas funciones. Tiene que modificar los datos en su origen. Puede agregar columnas a una [colección](../working-with-data-sources.md#collections) con la función **[Collect](function-clear-collect-clearcollect.md)** . Consulte cómo [trabajar con fuentes de datos](../working-with-data-sources.md) para más detalles.  

## <a name="description"></a>Descripción
La función **AddColumns** agrega una columna a una tabla y una fórmula define los valores de esa columna. Las columnas existentes permanecen sin modificar.

La fórmula se evalúa para cada registro de la tabla.
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

La función **DropColumns** excluye las columnas de una tabla.  El resto de las columnas permanece sin modificar. **DropColumns** excluye las columnas y **ShowColumns** las incluye.

Use la función **RenameColumns** para cambiar el nombre de una o varias columnas de una tabla al proporcionar al menos un par de argumentos que especifiquen el nombre de una columna que contiene la tabla (el nombre antiguo, que se quiere reemplazar) y el nombre de una columna que la tabla no contiene (el nombre nuevo, que se quiere usar). El nombre antiguo ya debe existir en la tabla y el nuevo nombre no. Cada nombre de columna puede aparecer solo una vez en la lista de argumentos como un nombre de columna antiguo o nuevo. Para cambiar el nombre de una columna por un nombre de columna existente, primero quite la columna existente con **DropColumns** o cambie el nombre de la columna existente al anidar una función **RenameColumns** dentro de otra.

La función **ShowColumns** incluye columnas de una tabla y quita todas las demás columnas. Puede usar **ShowColumns** para crear una tabla de una sola columna a partir de una tabla de varias columnas.  **ShowColumns** incluye columnas y **DropColumns** las excluye.  

Para todas estas funciones, el resultado es una nueva tabla con la transformación aplicada. La tabla original no se modifica. No se puede modificar una tabla existente con una fórmula. Common Data Service, SharePoint, SQL Server y otros orígenes de datos proporcionan herramientas para modificar las columnas de tablas, que a menudo se conocen como el esquema, entidades y listas. Las funciones en este tema solo transforman una tabla de entrada, sin modificar el original, en una tabla de salida para su uso posterior.

Los argumentos de estas funciones admiten la delegación. Por ejemplo, un **filtro** función que se usa como argumento para la incorporación de cambios en las búsquedas de registros relacionados a través de todos los anuncios, incluso si la **' [dbo]. [ AllListings]'** origen de datos contiene un millón de filas:

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

Sin embargo, el resultado de estas funciones está sujeto a la [límite de registros que no sean de delegación](../delegation-overview.md#non-delegable-limits).  En este ejemplo, se devuelven solo 500 registros incluso si la **RealEstateAgents** origen de datos tiene registros 501 o más.

Si usas **AddColumns** de esta manera, **filtro** debe realizar llamadas independientes al origen de datos para cada uno de los primeros registros de **RealEstateAgents**, lo que hace que una gran cantidad de chatter de red. Si **[dbo]. [ AllListings]** es lo suficientemente pequeño y no cambia con frecuencia, podría llamar a la **recopilar** funcionando en [ **OnStart** ](signals.md#app) para almacenar en caché el origen de datos en la aplicación Cuando se inicia. Como alternativa, puede reestructurar la aplicación para que extraiga en los registros relacionados solo cuando el usuario pide para ellos.  

## <a name="syntax"></a>Sintaxis
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *ColumnName(s)* : requerido. Nombres de las columnas para agregar.  Tiene que especificar una cadena (por ejemplo, **"Name"** entre comillas dobles incluidas) para este argumento.
* *Formula(s)* : requerido.  La fórmula o fórmulas para evaluar para cada registro. Se agregará el resultado como el valor de la nueva columna correspondiente. Puede hacer referencia a otras columnas de la tabla en esta fórmula.

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *ColumnName(s)* : requerido. Nombres de las columnas para excluir. Tiene que especificar una cadena (por ejemplo, **"Name"** entre comillas dobles incluidas) para este argumento.

**RenameColumns**( *Table*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*, *NewColumnName2*, ... ] )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *OldColumnName*: requerido. Nombre de una columna de la tabla original cuyo nombre se va a cambiar. Este elemento aparece en primer lugar en el par de argumentos (o en primer lugar en cada par de argumentos si la fórmula incluye más de un par). Este nombre tiene que ser una cadena (por ejemplo, **"Name"** con comillas dobles incluidas).
* *NewColumnName*: requerido. Nombre de reemplazo. Este elemento aparece por último lugar en el par de argumentos (o por último lugar en cada par de argumentos si la fórmula incluye más de un par). Tiene que especificar una cadena (por ejemplo, **"Customer Name"** con comillas dobles incluidas) para este argumento.

**ShowColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *ColumnName(s)* : requerido. Nombres de las columnas para incluir. Tiene que especificar una cadena (por ejemplo, **"Name"** entre comillas dobles incluidas) para este argumento.

## <a name="examples"></a>Ejemplos
En los ejemplos en esta sección, use el origen de datos **IceCreamSales**, que contiene los datos de esta tabla:

![](media/function-table-shaping/icecream.png)

Ninguno de estos ejemplos modificar el origen de datos **IceCreamSales**. Cada función transforma el valor del origen de datos como una tabla y devuelve ese valor como resultado.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **AddColumns (IceCreamSales, "Revenue", UnitPrice * QuantitySold)** |Agrega una columna **Revenue** al resultado.  Para cada registro, se evalúa **UnitPrice * QuantitySold**, y el resultado se coloca en la nueva columna. |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns (IceCreamSales, "UnitPrice")** |Excluye la columna **UnitPrice** del resultado. Use esta función para excluir columnas y usar **ShowColumns** para incluirlas. |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |Incluye solamente la columna **Flavor** en el resultado. Use esta función para incluir columnas y **DropColumns** para excluirlas. |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |Cambia el nombre de la **UnitPrice** columna del resultado. |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |Cambia el nombre de las columnas **UnitPrice** y **QuantitySold** en el resultado. |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |Realiza las siguientes transformaciones de tabla en orden, comenzando desde el interior de la fórmula: <ol><li>Agrega una columna **Revenue** basada en el cálculo por registro de **UnitPrice * Quantity**.<li>Cambia el nombre de **UnitPrice** a **Price**.<li>Excluye la columna **Quantity**.</ol>  Tenga en cuenta que el orden es importante. Por ejemplo, no se puede calcular con **UnitPrice** después de que se le haya cambiado el nombre. |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>Paso a paso

Vamos a probar algunos de los ejemplos de anteriormente en este tema.  

1. Crear una colección mediante la adición de un **[botón](../controls/control-button.md)** control y estableciendo su **OnSelect** propiedad en esta fórmula:

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. Ejecute la fórmula, seleccione el botón mientras mantiene presionada la tecla Alt.

1. Agregue un segundo **botón** , establezca su **OnSelect** fórmula, para la propiedad y, a continuación, ejecútelo:

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. En el **archivo** menú, seleccione **colecciones**y, a continuación, seleccione **IceCreamSales** para mostrar esa colección.
 
    Como se muestra en este gráfico, la segunda fórmula no ha modificado esta colección. El **AddColumns** función usa **IceCreamSales** como un argumento de solo lectura; la función no modifica la tabla al que hace referencia ese argumento.
    
    ![Visor de la colección que muestra los tres registros de la colección de ventas de helado que no incluya una columna de ingresos](media/function-table-shaping/ice-cream-sales-collection.png)

1. Seleccione **FirstExample**.

    Como se muestra en este gráfico, la segunda fórmula devuelve una nueva tabla con la columna agregada. El **ClearCollect** función captura la nueva tabla en la **FirstExample** colección, agregar algo a la tabla original, tal como transmita a través de la función sin modificar el origen:

    ![Visor de la colección que muestra los tres registros de la colección del primer ejemplo que incluye una nueva columna de ingresos](media/function-table-shaping/first-example-collection.png)
