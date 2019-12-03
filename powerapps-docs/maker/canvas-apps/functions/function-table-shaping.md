---
title: Funciones AddColumns, DropColumns, RenameColumns y ShowColumns | Microsoft Docs
description: Información de referencia de las funciones AddColumns, DropColumns, Cambiarnombrecolumnas y Mostrarcolumnas en Power Apps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c60017202c398d7a7e73ea9ff3ccee2bd8835b42
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730040"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-power-apps"></a>Funciones AddColumns, DropColumns, Cambiarnombrecolumnas y Mostrarcolumnas en Power apps
Forma una [tabla](../working-with-tables.md) agregando, quitando, cambiando el nombre y seleccionando sus [columnas](../working-with-tables.md#columns).

## <a name="overview"></a>Información general
Estas funciones dan forma a una tabla mediante el ajuste de sus columnas:

* Reducción de una tabla que contiene varias columnas a una sola columna para su uso con las funciones de columna única, como **[Lower](function-lower-upper-proper.md)** o  **[Abs](function-numericals.md)** .  
* Incorporación de una columna calculada a una tabla (por ejemplo, una columna **Total Price** que muestre el resultado de multiplicar **Quantity** por **Unit Price**).
* Cambio del nombre de una columna a algo más significativo, para mostrarla a los usuarios o para su uso en las fórmulas.

Una tabla es un valor de Power Apps, al igual que una cadena o un número.  Puede especificar una tabla como un argumento en una fórmula, y las funciones pueden devolver una tabla como resultado.

> [!NOTE]
> Las funciones que se describen en este tema no modifican la tabla original. En su lugar, toman esa tabla como argumento y devuelven una nueva tabla con una transformación aplicada. Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.  

No se pueden modificar las columnas de un [origen de datos](../working-with-data-sources.md) mediante el uso de estas funciones. Tiene que modificar los datos en su origen. Puede agregar columnas a una [colección](../working-with-data-sources.md#collections) con la función **[Collect](function-clear-collect-clearcollect.md)** . Consulte cómo [trabajar con fuentes de datos](../working-with-data-sources.md) para más detalles.  

## <a name="description"></a>Descripción
La función **AddColumns** agrega una columna a una tabla y una fórmula define los valores de esa columna. Las columnas existentes permanecen sin modificar.

La fórmula se evalúa para cada registro de la tabla.
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

La función **DropColumns** excluye las columnas de una tabla.  El resto de las columnas permanece sin modificar. **DropColumns** excluye las columnas y **ShowColumns** las incluye.

Use la función **RenameColumns** para cambiar el nombre de una o varias columnas de una tabla al proporcionar al menos un par de argumentos que especifiquen el nombre de una columna que contiene la tabla (el nombre antiguo, que se quiere reemplazar) y el nombre de una columna que la tabla no contiene (el nombre nuevo, que se quiere usar). El nombre antiguo ya debe existir en la tabla y el nuevo nombre no. Cada nombre de columna puede aparecer solo una vez en la lista de argumentos como un nombre de columna antiguo o nuevo. Para cambiar el nombre de una columna por un nombre de columna existente, primero quite la columna existente con **DropColumns** o cambie el nombre de la columna existente al anidar una función **RenameColumns** dentro de otra.

La función **ShowColumns** incluye columnas de una tabla y quita todas las demás columnas. Puede usar **ShowColumns** para crear una tabla de una sola columna a partir de una tabla de varias columnas.  **ShowColumns** incluye columnas y **DropColumns** las excluye.  

Para todas estas funciones, el resultado es una nueva tabla con la transformación aplicada. La tabla original no se modifica. No se puede modificar una tabla existente con una fórmula. SharePoint, Common Data Service, SQL Server y otros orígenes de datos proporcionan herramientas para modificar las columnas de listas, entidades y tablas, a las que se suele hacer referencia como esquema. Las funciones de este tema solo transforman una tabla de entrada, sin modificar la original, en una tabla de salida para su uso posterior.

Los argumentos de estas funciones admiten la delegación. Por ejemplo, una función de **filtro** que se usa como argumento para extraer los registros relacionados realiza búsquedas en todas las listas, incluso si el **' [dbo]. [ AllListings] '** el origen de datos contiene un millón de filas:

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

Sin embargo, el resultado de estas funciones está sujeto al [límite de registros que no son de delegación](../delegation-overview.md#non-delegable-limits).  En este ejemplo, solo se devuelven los registros 500, incluso si el origen de datos **RealEstateAgents** tiene 501 o más registros.

Si utiliza **AddColumns** de esta manera, el **filtro** debe realizar llamadas independientes en el origen de datos para cada uno de esos primeros registros en **RealEstateAgents**, lo que provoca una gran cantidad de chatter de red. Si **[dbo]. [ AllListings]** es lo suficientemente pequeño y no cambia con frecuencia, puede llamar a la función **Collect** en [**OnStart**](signals.md#app) para almacenar en caché el origen de datos en la aplicación cuando se inicia. Como alternativa, puede reestructurar la aplicación para que extraiga los registros relacionados solo cuando el usuario los solicite.  

## <a name="syntax"></a>Sintaxis
**AddColumns**( *Table*, *ColumnName1*, *Formula1* [, *ColumnName2*, *Formula2*, ... ] )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *ColumnName(s)* : requerido. Nombres de las columnas para agregar.  Tiene que especificar una cadena (por ejemplo, **"Name"** entre comillas dobles incluidas) para este argumento.
* *Formula(s)* : requerido.  La fórmula o fórmulas para evaluar para cada registro. Se agregará el resultado como el valor de la nueva columna correspondiente. Puede hacer referencia a otras columnas de la tabla en esta fórmula.

**DropColumns**( *Table*, *ColumnName1* [, *ColumnName2*, ... ] )

* *Table*: requerido.  La tabla sobre la cual se opera.
* *ColumnName(s)* : requerido. Nombres de las columnas para excluir. Tiene que especificar una cadena (por ejemplo, **"Name"** entre comillas dobles incluidas) para este argumento.

**Cambiarnombrecolumnas**( *TABLE*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*, *NewColumnName2*,...])

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
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |Cambia el nombre de la columna **UnitPrice** en el resultado. |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |Cambia el nombre de las columnas **UnitPrice** y **QuantitySold** en el resultado. |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |Realiza las siguientes transformaciones de tabla en orden, comenzando desde el interior de la fórmula: <ol><li>Agrega una columna **Revenue** basada en el cálculo por registro de **UnitPrice * Quantity**.<li>Cambia el nombre de **UnitPrice** a **Price**.<li>Excluye la columna **Quantity**.</ol>  Tenga en cuenta que el orden es importante. Por ejemplo, no se puede calcular con **UnitPrice** después de que se le haya cambiado el nombre. |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>Paso a paso

Vamos a probar algunos de los ejemplos anteriores de este tema.  

1. Cree una colección agregando un control de **[botón](../controls/control-button.md)** y estableciendo su propiedad **alseleccionar** en esta fórmula:

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. Ejecute la fórmula seleccionando el botón mientras mantiene presionada la tecla Alt.

1. Agregue un segundo control **botón** , establezca su propiedad **alseleccionar** en esta fórmula y, a continuación, ejecútelo:

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. En el menú **archivo** , seleccione **colecciones**y, a continuación, seleccione **IceCreamSales** para mostrar esa recopilación.
 
    Como se muestra en este gráfico, la segunda fórmula no modificó esta colección. La función **AddColumns** usó **IceCreamSales** como argumento de solo lectura; la función no modificó la tabla a la que hace referencia ese argumento.
    
    ![Visor de recopilación que muestra tres registros de la colección de ventas de helado que no incluye una columna de ingresos](media/function-table-shaping/ice-cream-sales-collection.png)

1. Seleccione **FirstExample**.

    Como se muestra en este gráfico, la segunda fórmula devolvió una nueva tabla con la columna agregada. La función **ClearCollect** capturó la nueva tabla en la colección **FirstExample** , agregando algo a la tabla original a medida que fluye a través de la función sin modificar el origen:

    ![Visor de recopilación que muestra tres registros de la primera colección de ejemplo que incluye una nueva columna Revenue](media/function-table-shaping/first-example-collection.png)
