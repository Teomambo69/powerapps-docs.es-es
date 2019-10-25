---
title: Función JSON | Microsoft Docs
description: Información de referencia de la función JSON en PowerApps, incluida la sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba852093da05c3fa69cc47b219a0bef65908c170
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "71992622"
ms.PowerAppsDecimalTransform: true
---
# <a name="json-function-in-powerapps"></a>Función JSON en PowerApps

Genera una cadena de texto JSON para una tabla, un registro o un valor.

## <a name="description"></a>Descripción

La función **JSON** devuelve la representación notación de objetos JavaScript (JSON) de una estructura de datos como texto para que sea adecuada para el almacenamiento o la transmisión a través de una red. [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) y [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) describen el formato, que es ampliamente utilizado por JavaScript y otros lenguajes de programación.

Las aplicaciones de lienzo admiten los [tipos de datos](data-types.md) que esta tabla muestra con detalles sobre su representación de texto:

| Tipo de datos | Descripción | Ejemplo de resultado |
|-----------|-------------|---------|
| **Booleano** | *true* o *false*. | `true` |
| **Color** | Cadena que contiene la representación hexadecimal de 8 dígitos del color. Esta representación adopta el formato #*RRGGBBAA*, donde *RR* es el componente rojo, *GG* es verde, *BB* es azul y *AA* es el canal alfa. Para el canal alfa, **00** es totalmente transparente y **FF** es totalmente opaco. Puede pasar la cadena a la función [**ColorValue**](function-colors.md) .  | `"#102030ff"` |
| **Moneda** | Número que usa el separador decimal adecuado para el idioma del usuario. Si es necesario, se usa la notación científica. | `1,345` |
| **Posteriormente** | Cadena que contiene la fecha en formato ISO 8601 **AAAA-MM-DD** . | `"2019-03-31"` |
| **DateTime** | Cadena que contiene una fecha y hora ISO 8601. Los valores de fecha y hora están en formato UTC, como indica el "Z" final.  | `"2019-03-31T22:32:06.822Z"`  |
| **VOLUMEN** | Cadena que contiene el valor de GUID. Las letras están en minúsculas. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **Imagen, medios** | Si se especifica **IncludeBinaryData** , los archivos multimedia se codifican en una cadena. Las referencias Web que usan el esquema http: o https: URL no se modifican. Las referencias a los datos binarios en memoria se codifican con el formato ["Data:*Mimetype*; Base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme) . Los datos en memoria incluyen imágenes que los usuarios capturan mediante el control de [**cámara**](../controls/control-camera.md) y cualquier otra referencia con los esquemas appres: y BLOB: URL.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **Números** | Número que usa el separador decimal adecuado para el idioma del usuario. Si es necesario, se usa la notación científica. | `1,345` |
| **@No__t_1set de opciones** | Valor numérico del conjunto de opciones, no la etiqueta que se usa para la presentación. El valor numérico se usa porque es independiente del lenguaje.  | `1001` |
| **Tiempo** | Cadena que contiene el formato ISO 8601 *HH: mm: SS. FFF* .  | `"23:12:49.000"` |
| **Record** | Lista delimitada por comas, entre **{** y **}** , de los campos y sus valores. Esta notación es similar a la de los registros de las aplicaciones de lienzo, pero el nombre siempre está entre comillas dobles. Este formato no admite registros basados en relaciones de varios a uno.  | `{ "First Name": "Fred"; "Age": 21 }` |
| **Cuadro** | Lista delimitada por comas, entre **[** y **]** , de registros. Este formato no admite tablas basadas en relaciones uno a varios.  | `[ { "First Name": "Fred"; "Age": 21 }; { "First Name": "Jean"; "Age": 20 } ]` |
| **Dos &nbsp;option** | Valor booleano de la opción dos, *true* o *false*, no la etiqueta que se usa para la presentación. El valor booleano se usa porque es independiente del lenguaje. | `false` |
| **Hipervínculo, texto** | Cadena entre comillas dobles. La función convierte las comillas dobles incrustadas en una barra diagonal inversa, reemplaza las líneas nuevas por "\n" y realiza otros reemplazos de JavaScript estándar. | `"This is a string."` |

Especifique el argumento de *formato* opcional para controlar la legibilidad del resultado y el modo en que se administran los tipos de datos binarios y no compatibles. De forma predeterminada, la salida es lo más compacta posible sin espacios ni líneas nuevas innecesarias, y no se permiten tipos de datos no admitidos ni datos binarios. Puede combinar varios formatos si especifica el operador **&** .

| Enumeración JSONFormat | Descripción |
|-----------------|-------------|
| **Unidad** | Predeterminado.  La salida es lo más compacta posible sin espacios ni líneas nuevas. |
| **IndentFour** | Para mejorar la legibilidad, la salida contiene una línea nueva para cada columna y el nivel de anidamiento, y usa cuatro espacios para cada nivel de sangría. |
| **IncludeBinaryData** | El resultado incluye las columnas Image, video y audio-clip. Este formato puede aumentar drásticamente el tamaño del resultado y degradar el rendimiento de la aplicación. |
| **IgnoreBinaryData** | El resultado no incluye las columnas Image, video o audio-clip. Si no especifica **IncludeBinaryData** ni **IgnoreBinaryData**, la función genera un error si encuentra datos binarios. |
| **IgnoreUnsupportedTypes** | Se permiten los tipos de datos no admitidos, pero el resultado no los incluirá. De forma predeterminada, los tipos de datos no admitidos generan un error. |

Use las funciones [ **Mostrarcolumnas** y **DropColumns** ](function-table-shaping.md) para controlar los datos que incluye el resultado y para quitar los tipos de datos no admitidos.

Dado que **JSON** puede ser de memoria y de proceso intensivo, solo puede usar esta función en [funciones de comportamiento](../working-with-formulas-in-depth.md). Puede capturar el resultado de **JSON** en una [variable](../working-with-variables.md), que puede usar en el flujo de datos.

Si una columna tiene un nombre para mostrar y un nombre lógico, el resultado contiene el nombre lógico. Los nombres para mostrar reflejan el idioma del usuario de la aplicación y, por lo tanto, son inadecuados para la transferencia de datos a un servicio común.

## <a name="syntax"></a>Sintaxis

**JSON**( *Structure* [; *Format* ])

* *Structure* : requerido. La estructura de datos que se va a convertir en JSON.  Se admiten tablas, registros y valores primitivos, anidados arbitrariamente.
* *Format* : opcional.  Valor de enumeración **JSONFormat** . El valor predeterminado es **Compact**, que no agrega líneas nuevas ni espacios y bloquea los datos binarios y las columnas no admitidas.

## <a name="examples"></a>Ejemplos

### <a name="hierarchical-data"></a>Datos jerárquicos

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
    ClearCollect( CitiesByCountry; GroupBy( CityPopulations; "Country"; "Cities" ) )
    ```

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

    La colección **CitiesByCountry** se crea con esta estructura de datos, que puede mostrar seleccionando **colecciones** en el menú **archivo** y, a continuación, seleccionando el nombre de la colección.

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry colección ](media/function-json/cities-grouped.png)

    También puede mostrar esta colección seleccionando **archivo**  >  configuración de la**aplicación**  > **Configuración avanzada**  >  la vista de resultado de la**barra de fórmulas**, seleccionando el nombre de la colección en la barra de fórmulas y seleccionando el flecha abajo situada junto al nombre de la colección en la barra de fórmulas.

    > [!div class="mx-imgBorder"]
    > ![Collection en la vista de resultados de la barra de fórmulas ](media/function-json/cities-grouped-resultview.png)

1. Inserte otro botón y establezca su propiedad **alseleccionar** en esta fórmula:

    ```powerapps-comma
    Set( CitiesByCountryJSON; JSON( CitiesByCountry ) )
    ```

    Esta fórmula establece la variable global **CitiesByCountryJSON** en la representación JSON de **CitiesByCountry**.

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

1. Inserte un control [**etiqueta**](../controls/control-text-box.md) y establezca su propiedad **texto** en esta variable.

    ```powerapps-comma
    CitiesByCountryJSON
    ```

    La etiqueta muestra este resultado, todo en una sola línea sin espacios, adecuada para la transmisión a través de una red:

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. Cambie la fórmula del segundo botón para que la salida sea más legible.

    ```powerapps-comma
    Set( CitiesByCountryJSON; JSON(CitiesByCountry; JSONFormat.IndentFour ))
    ```

1. Seleccione el segundo botón mientras mantiene presionada la tecla Alt.

    La etiqueta muestra el resultado más legible.

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>Imágenes y elementos multimedia en Base64

1. Agregue un control [**imagen**](../controls/control-image.md) .

    Este control pone **SampleImage** en él.

1. Agregue un control [**botón**](../controls/control-button.md) y establezca su propiedad **alseleccionar** en esta fórmula.

    ```powerapps-comma
    Set( ImageJSON; JSON( SampleImage; JSONFormat.IncludeBinaryData ) )
    ```

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

1. Agregue una etiqueta y establezca su propiedad **Text** en esta variable.

    ```powerapps-comma
    ImageJSON
    ```

1. Cambie el tamaño del control y reduzca el tamaño de fuente según sea necesario para mostrar la mayor parte del resultado.

    La etiqueta muestra la cadena de texto que la función **JSON** capturó.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
