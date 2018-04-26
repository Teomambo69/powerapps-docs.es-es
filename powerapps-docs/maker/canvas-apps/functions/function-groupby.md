---
title: Funciones AgruparPor y Desagrupar | Microsoft Docs
description: Información de referencia para las funciones AgruparPor y Desagrupar en PowerApps, incluidos ejemplos y sintaxis
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 04/26/2016
ms.author: gregli
ms.openlocfilehash: b47e1b36ec86b2bf4ee2167b2599d583b97a0fbc
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="groupby-and-ungroup-functions-in-powerapps"></a>Funciones AgruparPor y Desagrupar en PowerApps
Agrupa y desagrupa [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md).

## <a name="description"></a>Descripción
La función **AgruparPor** devuelve una tabla con registros agrupados en función de los valores de una o varias [columnas](../working-with-tables.md#columns). Los registros del mismo grupo se colocan en un único registro, con una columna agregada que contiene una tabla anidada de las columnas restantes.   

La función **Desagrupar** invierte el proceso realizado por **Agrupar por**. Esta función devuelve una tabla y divide en registros individuales todos los registros que estaban agrupados.

Puede agrupar los registros mediante **AgruparPor**, modificar la tabla que devuelve y, a continuación, desagrupar los registros de la tabla modificada mediante la función **Desagrupar**. Por ejemplo, puede quitar un grupo de registros siguiendo este enfoque:

* Use la función **AgruparPor**.
* Use la función **[Filtrar](function-filter-lookup.md)** para quitar todo el grupo de registros.
* Use la función **Desagrupar**.  

También puede agregar los resultados en función de una agrupación:

* Use la función **AgruparPor**.
* Use la función **[AddColumns](function-table-shaping.md)** con **[Suma](function-aggregates.md)**, **[Promedio](function-aggregates.md)** y otras funciones de agregado para agregar una nueva columna que sea un agregado de las tablas de grupos.
* Use la función **[DropColumns](function-table-shaping.md)** para quitar la tabla de grupo.

**Desagrupar** intenta conservar el orden original de los registros que se proporcionan a **AgruparPor**.  Esto no siempre es posible (por ejemplo, si la tabla original contiene registros *en blanco*).

Una tabla es un valor en PowerApps, como una cadena o un número. Puede especificar una tabla como argumento para una función y una función puede devolver una tabla. **AgruparPor** y **Desagrupar** no modifican una tabla; en lugar de eso, toman una tabla como argumento y devuelven una tabla diferente. Consulte cómo [trabajar con tablas](../working-with-tables.md) para más detalles.

## <a name="syntax"></a>Sintaxis
**AgruparPor**( *Tabla*, *ColumnName1* [, *ColumnName2*, ... ], *GroupColumnName* )

* *Table*: requerido. Tabla que se desea agrupar.
* *ColumnName(s)*: requerido.  Los nombres de columna en *Tabla* mediante los que se van a agrupar los registros.  Estas columnas se convierten en columnas en la tabla resultante.
* *GroupColumnName*: requerido.  El nombre de la columna para el almacenamiento de datos de registro que no están en el *ColumnName(s)*.
  
    > [!NOTE]
> En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"**. Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"**.

**Desagrupar**( *Tabla*, *GroupColumnName* )

* *Table*: requerido. Tabla que se desea desagrupar.
* *GroupColumnName*: requerido. La columna que contiene la configuración de los datos de registro con la función **AgruparPor**.
  
    > [!NOTE]
> En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"**. Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"**.

## <a name="examples"></a>Ejemplos
### <a name="create-a-collection"></a>Crear una colección
1. Agregue un botón y establezca su propiedad **[Texto](../controls/properties-core.md)** para que el botón muestre **Original**.
2. Establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** del botón **Original** en esta fórmula:
   
    **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
3. Presione F5, seleccione el botón **Original** y presione Esc.
   
    Acaba de crear una [colección](../working-with-data-sources.md#collections), que se denomina **CityPopulations**, que contiene estos datos:
   
    ![](media/function-groupby/cities.png)
4. Para mostrar esta colección, seleccione **Colecciones** en el menú **Archivo** y, a continuación, seleccione la colección **CityPopulations**.  Aparecerán los cinco primeros registros de la colección:
   
    ![](media/function-groupby/citypopulations-collection.png)

### <a name="group-records"></a>Registros de grupo
1. Agregue otro botón y establezca su propiedad **[Texto](../controls/properties-core.md)** en **"Group"**.
2. Establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** de este botón en esta fórmula:
   
    **ClearCollect( CitiesByCountry, AgruparPor( CityPopulations, "Country", "Ciudades" ) )**
3. Presione F5, seleccione el botón **Grupo** y presione Esc.
   
    Acaba de crear una recopilación denominada **CitiesByCountry**, en la que se agrupan los registros de la colección anterior mediante la columna **País**.
   
    ![](media/function-groupby/cities-grouped.png)
4. Para mostrar los primeros cinco registros de esta colección, seleccione **Colecciones** en el menú **Archivo**.
   
    ![](media/function-groupby/citiesbycountry-collection.png)
5. Para mostrar la población de las ciudades de un país o región, seleccione el icono de tabla de la columna **Ciudades** de ese país (por ejemplo, Alemania):
   
    ![](media/function-groupby/population-germany.png)

### <a name="filter-and-ungroup-records"></a>Filtrado y desagrupación de registros
1. Agregue otro botón y establezca su propiedad **[Texto](../controls/properties-core.md)** para que el botón muestre **"Filtrar"**.
2. Establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** de este botón en esta fórmula:
   
    **ClearCollect( CitiesByCountryFiltered, Filtrar( CitiesByCountry, "e" in Country ) )**
3. Presione F5, seleccione el botón que agregó y presione Esc.
   
    Acaba de crear una tercera colección denominada **CitiesByCountryFiltered**, que incluye solo aquellos países que tienen una "e" en sus nombres (es decir, no España o Italia, por ejemplo).
   
    ![](media/function-groupby/cities-grouped-hase.png)
4. Agregue un botón más y establezca su propiedad **[Texto](../controls/properties-core.md)** para que el botón muestre **"Desagrupar"**.
5. Establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** de este botón en esta fórmula:
   
    **ClearCollect( CityPopulationsUngrouped, Desagrupar( CitiesByCountryFiltered, "Ciudades" ) )**
   
    Que da como resultado:
   
    ![](media/function-groupby/cities-hase.png)

### <a name="aggregate-results"></a>Agregación de resultados
Otra cosa que podemos hacer con una tabla agrupada consiste en agregar los resultados.  En este ejemplo, se sumará la población de las ciudades más importantes de cada país.

1. Agregue otro botón y establezca su propiedad **[Texto](../controls/properties-core.md)** para que el botón muestre **"Suma"**.
2. Establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** del botón **"Suma"** en esta fórmula:
   
    **ClearCollect( CityPopulationsSum, AddColumns( CitiesByCountry, "Suma de las poblaciones de las ciudades", Suma( Ciudades, Population ) ) )**
   
    Que da como resultado:
   
    ![](media/function-groupby/cities-sum.png)
   
    **[AddColumns](function-table-shaping.md)** comienza con la colección básica de **CitiesByCountry** y agrega una nueva columna denominada **Suma de las poblaciones de las ciudades**.  Los valores de esta columna se calculan fila por fila según la fórmula **Suma( Ciudades, Population )**.  **AddColumns** proporciona el valor de la columna **Ciudades** (una tabla) para cada fila y **[Suma](function-aggregates.md)** la **Población** de cada fila de esta subtabla.
3. Ahora que tenemos la suma que queremos, podemos usar la función **[DropColumns](function-table-shaping.md)** para quitar las subtablas.  Modifique la propiedad **[AlSeleccionar](../controls/properties-core.md)** para que use esta fórmula:
   
    **ClearCollect( CityPopulationsSumOnly, DropColumns( CityPopulationsSum, "Ciudades" ) )**
   
    Que da como resultado:
   
    ![](media/function-groupby/cities-sum-drop-cities.png)
   
    Tenga en cuenta que no fue necesario desagrupar esta tabla.

