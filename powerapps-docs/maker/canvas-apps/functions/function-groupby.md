---
title: Funciones GroupBy y Ungroup | Microsoft Docs
description: Información de referencia para las funciones GroupBy y Ungroup en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/26/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c5b5ddf05201743a5ea4848793fcd05aea7def24
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680176"
---
# <a name="groupby-and-ungroup-functions-in-powerapps"></a>Funciones GroupBy y Ungroup en PowerApps
Agrupa y desagrupa [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **GroupBy** devuelve una tabla con registros agrupados en función de los valores de una o varias [columnas](../working-with-tables.md#columns). Los registros del mismo grupo se colocan en un único registro, con una columna agregada que contiene una tabla anidada de las columnas restantes.   

La función **Ungroup** invierte el proceso realizado por **GroupBy**. Esta función devuelve una tabla y divide en registros individuales todos los registros que estaban agrupados.

Puede agrupar los registros mediante **GroupBy**, modificar la tabla que devuelve y, a continuación, desagrupar los registros de la tabla modificada mediante la función **Ungroup**. Por ejemplo, puede quitar un grupo de registros siguiendo este enfoque:

* Use la función **GroupBy**.
* Use la función **[Filter](function-filter-lookup.md)** para quitar todo el grupo de registros.
* Use la función **Ungroup**.  

También puede agregar los resultados en función de una agrupación:

* Use la función **GroupBy**.
* Use la función **[AddColumns](function-table-shaping.md)** con **[Sum](function-aggregates.md)** , **[Average](function-aggregates.md)** y otras funciones de agregado para agregar una nueva columna que sea un agregado de las tablas de grupos.
* Use la función **[DropColumns](function-table-shaping.md)** para quitar la tabla de grupo.

**Ungroup** intenta conservar el orden original de los registros que se proporcionan a **GroupBy**.  Esto no siempre es posible (por ejemplo, si la tabla original contiene registros *blank*).

Una tabla es un valor de Power Apps, al igual que una cadena o un número. Puede especificar una tabla como argumento para una función y una función puede devolver una tabla. **GroupBy** y **Ungroup** no modifican una tabla; en lugar de eso, toman una tabla como argumento y devuelven una tabla diferente. Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

## <a name="syntax"></a>Sintaxis
**GroupBy**( *Table*, *ColumnName1* [, *ColumnName2*, ... ], *GroupColumnName* )

* *Table*: requerido. Tabla que se desea agrupar.
* *ColumnName(s)* : requerido.  Los nombres de columna en *Table* mediante los que se van a agrupar los registros.  Estas columnas se convierten en columnas en la tabla resultante.
* *GroupColumnName*: requerido.  El nombre de la columna para el almacenamiento de datos de registro que no están en el *ColumnName(s)* .
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"** . Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"** .

**Ungroup**( *Table*, *GroupColumnName* )

* *Table*: requerido. Tabla que se desea desagrupar.
* *GroupColumnName*: requerido. La columna que contiene la configuración de los datos de registro con la función **GroupBy**.
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"** . Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"** .

## <a name="examples"></a>Ejemplos
### <a name="create-a-collection"></a>Crear una colección
1. Agregue un botón y establezca su propiedad **[Text](../controls/properties-core.md)** para que el botón muestre **Original**.
2. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón **Original** en esta fórmula:

```powerapps-dot   
ClearCollect( CityPopulations, 
    { City: "London",    Country: "United Kingdom", Population: 8615000}, 
    { City: "Berlin",    Country: "Germany",        Population: 3562000}, 
    { City: "Madrid",    Country: "Spain",          Population: 3165000}, 
    { City: "Rome",      Country: "Italy",          Population: 2874000}, 
    { City: "Paris",     Country: "France",         Population: 2273000}, 
    { City: "Hamburg",   Country: "Germany",        Population: 1760000}, 
    { City: "Barcelona", Country: "Spain",          Population: 1602000}, 
    { City: "Munich",    Country: "Germany",        Population: 1494000}, 
    { City: "Milan",     Country: "Italy",          Population: 1344000}
)
```

3. Mientras mantiene presionada la tecla Alt, seleccione el botón **Original**.
   
    Acaba de crear una [colección](../working-with-data-sources.md#collections), que se denomina **CityPopulations**, que contiene estos datos:
   
    ![](media/function-groupby/cities.png)
4. Para mostrar esta colección, seleccione **Colecciones** en el menú **Archivo** y, a continuación, seleccione la colección **CityPopulations**.  Aparecerán los cinco primeros registros de la colección:
   
    ![](media/function-groupby/citypopulations-collection.png)

### <a name="group-records"></a>Registros de grupo
1. Agregue otro botón y establezca su propiedad **[Text](../controls/properties-core.md)** en **"Group"** .
2. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** de este botón en esta fórmula:
   
    **ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )**
3. Mientras mantiene presionada la tecla Alt, seleccione el botón **Grupo**.
   
    Acaba de crear una recopilación denominada **CitiesByCountry**, en la que se agrupan los registros de la colección anterior mediante la columna **País**.
   
    ![](media/function-groupby/cities-grouped.png)
4. Para mostrar los primeros cinco registros de esta colección, seleccione **Colecciones** en el menú **Archivo**.
   
    ![](media/function-groupby/citiesbycountry-collection.png)
5. Para mostrar la población de las ciudades de un país o región, seleccione el icono de tabla de la columna **Ciudades** de ese país (por ejemplo, Alemania):
   
    ![](media/function-groupby/population-germany.png)

### <a name="filter-and-ungroup-records"></a>Filtrado y desagrupación de registros
1. Agregue otro botón y establezca su propiedad **[Text](../controls/properties-core.md)** para que el botón muestre **"Filtrar"** .
2. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** de este botón en esta fórmula:
   
    **ClearCollect( CitiesByCountryFiltered, Filter( CitiesByCountry, "e" in Country ) )**
3. Mientras mantiene presionada la tecla Alt, seleccione el botón que ha agregado.
   
    Acaba de crear una tercera colección denominada **CitiesByCountryFiltered**, que incluye solo aquellos países que tienen una "e" en sus nombres (es decir, no España o Italia, por ejemplo).
   
    ![](media/function-groupby/cities-grouped-hase.png)
4. Agregue un botón más y establezca su propiedad **[Text](../controls/properties-core.md)** para que el botón muestre **"Desagrupar"** .
5. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** de este botón en esta fórmula:
   
    **ClearCollect( CityPopulationsUngrouped, Ungroup( CitiesByCountryFiltered, "Cities" ) )**
   
    Que da como resultado:
   
    ![](media/function-groupby/cities-hase.png)

### <a name="aggregate-results"></a>Agregación de resultados
Otra cosa que podemos hacer con una tabla agrupada consiste en agregar los resultados.  En este ejemplo, se sumará la población de las ciudades más importantes de cada país.

1. Agregue otro botón y establezca su propiedad **[Text](../controls/properties-core.md)** para que el botón muestre **"Sum"** .
2. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón **"Sum"** en esta fórmula:
   
    **ClearCollect( CityPopulationsSum, AddColumns( CitiesByCountry, "Sum of City Populations", Sum( Cities, Population ) ) )**
   
    Que da como resultado:
   
    ![](media/function-groupby/cities-sum.png)
   
    **[AddColumns](function-table-shaping.md)** comienza con la colección básica de **CitiesByCountry** y agrega una nueva columna denominada **Sum of City Populations**.  Los valores de esta columna se calculan fila por fila según la fórmula **Sum( Cities, Population )** .  **AddColumns** proporciona el valor de la columna **Cities** (una tabla) para cada fila y **[Sum](function-aggregates.md)** el valor de **Population** de cada fila de esta subtabla.

    Ahora que tenemos la suma que queremos, podemos usar la función **[DropColumns](function-table-shaping.md)** para quitar las subtablas.
  
3. Agregue otro botón y establezca su propiedad **[Text](../controls/properties-core.md)** para que el botón muestre **"SumOnly"** .
4. Establezca la propiedad **[OnSelect](../controls/properties-core.md)** del botón **"SumOnly"** en esta fórmula:

    **ClearCollect( CityPopulationsSumOnly, DropColumns( CityPopulationsSum, "Cities" ) )**
   
    Que da como resultado:
   
    ![](media/function-groupby/cities-sum-drop-cities.png)
   
    Tenga en cuenta que no fue necesario desagrupar esta tabla.

