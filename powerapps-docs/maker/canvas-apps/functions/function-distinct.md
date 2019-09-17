---
title: Función Distinct | Microsoft Docs
description: Información de referencia sobre la función Distinct de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 98fd1b67d4835969ac01b1ce63155bc81ed36630
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038123"
ms.PowerAppsDecimalTransform: true
---
# <a name="distinct-function-in-powerapps"></a>Función Distinct de PowerApps
Resume los [registros](../working-with-tables.md#records) de una [tabla](../working-with-tables.md), quitando los duplicados.

## <a name="description"></a>DESCRIPCIÓN
La función **DISTINCT** evalúa una fórmula en cada registro de una tabla y devuelve una tabla de una columna de los resultados con valores duplicados quitados.  El nombre de la columna es **result**.  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>Sintaxis
**Distinct**( *Table*; *Formula* )

* *Table*: requerido.  Tabla en la cual se realizará la evaluación.
* *Formula*: requerido.  La fórmula que se evalúa en cada registro.

## <a name="example"></a>Ejemplo

1. Inserte un control de [**botón**](../controls/control-button.md) y establezca su propiedad **alseleccionar** en esta fórmula.

    ```powerapps-comma
    ClearCollect( CityPopulations;
        { City: "London";    Country: "United Kingdom"; Population: 8615000 };
        { City: "Berlin";    Country: "Germany";        Population: 3562000 };
        { City: "Madrid";    Country: "Spain";          Population: 3165000 };
        { City: "Hamburg";   Country: "Germany";        Population: 1760000 };
        { City: "Barcelona"; Country: "Spain";          Population: 1602000 };
        { City: "Munich";    Country: "Germany";        Population: 1494000 }
    );;
    ```

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

    La fórmula se evaluará y se creará la colección **CityPopulations** , que se puede mostrar seleccionando **CityPopulations** en la barra de fórmulas:

    > [!div class="mx-imgBorder"]
    > ![Colección CityPopulations mostrada en la vista de resultados](media/function-distinct/citypopulations-create.png)

1. Inserte un control [**tabla de datos**](../controls/control-data-table.md) y establezca su propiedad **elementos** en esta fórmula:

    ```powerapps-comma
    Distinct( CityPopulations; Country )
    ```

    Para ver el resultado de esta fórmula en la barra de fórmulas, seleccione toda la fórmula:

    > [!div class="mx-imgBorder"]
    > ![Salida de la función DISTINCT mostrada en la vista de resultados](media/function-distinct/citypopulations-distinct.png)

1. Use el vínculo **Editar campos** en el panel de propiedades de la tabla de datos para agregar la columna de **resultados** :

    > [!div class="mx-imgBorder"]
    > ![Salida de la función DISTINCT mostrada en la tabla de datos](media/function-distinct/citypopulations-datatable.png)

1. Inserte un control [**etiqueta**](../controls/control-text-box.md) y establezca su propiedad **texto** en la fórmula:

    ```powerapps-comma
    First( Sort( Distinct( CityPopulations; Country ); Result ) ).Result
    ```

    Esta fórmula ordena los resultados de **DISTINCT** con la función de [**ordenación**](function-sort.md) , toma el primer registro de la tabla resultante con la [**primera**](function-first-last.md) función y extrae el campo de **resultados** para obtener solo el nombre del país.

    > [!div class="mx-imgBorder"]
    > ![Salida de la función DISTINCT que muestra el primer país por nombre](media/function-distinct/citypopulations-first.png)

     
