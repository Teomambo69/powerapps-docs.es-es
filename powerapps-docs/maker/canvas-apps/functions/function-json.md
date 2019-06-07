---
title: Función JSON | Microsoft Docs
description: Información de referencia, incluida la sintaxis de la función JSON en PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 74e10a5b073e16ba9f35139441c94e9911446a0f
ms.sourcegitcommit: 2084789802fc5134dbeb888e759cced46019a017
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66736408"
---
# <a name="json-function-in-powerapps"></a>Función JSON en PowerApps

Genera una cadena de texto JSON para una tabla, un registro o un valor.

## <a name="description"></a>Descripción

El **JSON** función devuelve la representación de JavaScript Object Notation (JSON) de una estructura de datos como texto para que sea adecuado para almacenar o transmitir a través de una red. [ECMA 404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) y [IETF RFC 8259](https://tools.ietf.org/html/rfc8259) describir el formato, que se utiliza ampliamente en JavaScript y otros lenguajes de programación.

Compatibilidad de aplicaciones de lienzo el [tipos de datos](data-types.md) que esta tabla se enumeran con detalles acerca de su representación de texto:

| Tipo de datos | Descripción | Ejemplo de resultado |
|-----------|-------------|---------|
| **Boolean** | *True* o *false*. | `true` |
| **Color** | Cadena que contiene la representación hexadecimal de 8 dígitos para el color. Esta representación toma el formato #*rrggbbaa*, donde *rr* es el componente rojo, *gg* es verde, *bb* es azul y *aa* es el canal alfa. Para el canal alfa, **00** es completamente transparente, y **ff** es completamente opaco. Puede pasar la cadena a la [ **ColorValue** ](function-colors.md) función.  | `"#102030ff"` |
| **Moneda** | Número que usa el separador decimal adecuado para el idioma del usuario. Si es necesario, se usa la notación científica. | `1.345` |
| **Fecha** | Cadena que contiene la fecha en ISO 8601 **aaaa-mm-dd** formato. | `"2019-03-31"` |
| **DateTime** | Cadena que contiene una imagen ISO 8601 fecha y hora. Fecha y hora son valores en UTC, tal como indica el final "Z".  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | Cadena que contiene el valor de GUID. Letras estén en minúsculas. | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **Imagen de medios** | Si **IncludeBinaryData** se especifica, se codifican los archivos multimedia en una cadena. Referencias que usan http Web: o https: No se modifican el esquema de dirección URL. Las referencias a los datos binarios en memoria se codifican con el ["datos:*mimetype*; base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme) formato. Datos en memoria incluyen imágenes que los usuarios capturar mediante el [ **cámara** ](../controls/control-camera.md) control y cualquier otra referencia con el appres: y blob: Esquemas de dirección URL.| `"data:image/jpeg;base64,/9j/4AA..."` |
| **Número** | Número que usa el separador decimal adecuado para el idioma del usuario. Si es necesario, se usa la notación científica. | `1.345` |
| **Opción&nbsp;establecido** | Valor numérico de la opción de conjunto, no la etiqueta que se usa para mostrarlo. El valor numérico se usa porque es independiente del lenguaje.  | `1001` |
| **Tiempo** | Cadena que contiene un ISO 8601 *ss. fff* formato.  | `"23:12:49.000"` |
| **Record** | Delimitado por comas de lista, entre **{** y **}** , de los campos y sus valores. Esta notación es similar para los registros de aplicaciones de lienzo, pero siempre es el nombre entre comillas dobles. Este formato no admite registros que se basan en relaciones de varios a uno.  | `{ "First Name": "Fred", "Age": 21 }` |
| **Table** | Delimitado por comas de lista, entre **[** y **]** , de registros. Este formato no admite las tablas que se basan en las relaciones uno a varios.  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **Dos&nbsp;opción** | Valor booleano de la opción dos, *true* o *false*, no la etiqueta que se usa para mostrarlo. El valor booleano se utiliza porque es independiente del lenguaje. | `false` |
| **Hyperlink, Text** | Cadena entre comillas dobles. La función convierte las comillas dobles incrustadas con una barra diagonal inversa, reemplaza las nuevas líneas por "\n" y realiza otras sustituciones de JavaScript estándares. | `"This is a string."` |

Especifique el valor opcional *formato* se controlan el argumento para controlar cómo se puede leer el resultado es y los tipos de datos binarios y de cómo no admitido. De forma predeterminada, la salida es lo más compacta posible sin espacios innecesarios o nuevas líneas y no se permiten los tipos de datos no admitidos y los datos binarios. Puede combinar varios formatos si especifica la **&** operador.

| Enumeración de JSONFormat | Descripción |
|-----------------|-------------|
| **Compacto** | Predeterminado.  La salida es lo más compacta posible sin espacios se ha agregado o nuevas líneas. |
| **IndentFour** | Para mejorar la legibilidad, la salida contiene una línea nueva para cada columna y el nivel de anidamiento y usa cuatro espacios para cada nivel de sangría. |
| **IncludeBinaryData** | El resultado incluye columnas de imagen, vídeo y clips de audio. Este formato drásticamente puede aumentar el tamaño del resultado y reducir el rendimiento de la aplicación. |
| **IgnoreBinaryData** | El resultado no incluye columnas de imagen, vídeo o un clip de audio. Si se especifica ninguno **IncludeBinaryData** ni **IgnoreBinaryData**, la función genera un error si encuentra datos binarios. |
| **IgnoreUnsupportedTypes** | Se permiten los tipos de datos no admitido, pero el resultado no los incluirá. De forma predeterminada, los tipos de datos no admitido generan un error. |

Use la [ **Mostrarcolumnas** y **DropColumns** ](function-table-shaping.md) funciones para controlar qué datos se incluye el resultado y quitar tipos de datos no admitido.

Dado que **JSON** puede ser memoria y a de proceso intensivo, puede usar esta función solo en [funciones comportamiento](../working-with-formulas-in-depth.md). Puede capturar el resultado de **JSON** en un [variable](../working-with-variables.md), que, a continuación, puede usar en el flujo de datos.

Si una columna tiene un nombre para mostrar y un nombre lógico, el resultado contiene el nombre lógico. Los nombres para mostrar reflejan el idioma del usuario de la aplicación y son, por lo tanto, inadecuado para la transferencia de datos a un servicio común.

## <a name="syntax"></a>Sintaxis

**JSON**( *DataStructure* [, *Format* ] )

* *DataStructure* : requerido. La estructura de datos para convertir en JSON.  Se admiten las tablas, los registros y los valores primitivos, arbitrariamente anidados.
* *Formato* : opcional.  **JSONFormat** valor enum. El valor predeterminado es **Compact**, que no se agregarán nuevas líneas o los espacios y bloquea los datos binarios y columnas no admitidas.

## <a name="examples"></a>Ejemplos

### <a name="hierarchical-data"></a>Datos jerárquicos

1. Insertar un [ **botón** ](../controls/control-button.md) y establezca su **OnSelect** fórmula para la propiedad.

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

    El **CitiesByCountry** colección se crea con esta estructura de datos, puede mostrar seleccionando **colecciones** en el **archivo** menú y, a continuación, seleccione el nombre de la colección.

    > [!div class="mx-imgBorder"]
    > ![Colección de CitiesByCountry](media/function-json/cities-grouped.png)

    También puede mostrar esta colección seleccionando **archivo** > **configuración de la aplicación** > **configuración avanzada**  >   **Habilitar la barra de vista de resultados de fórmulas**, seleccionando el nombre de la colección en la barra de fórmulas y, a continuación, seleccione la flecha abajo situada junto al nombre de la recopilación en la barra de fórmulas.

    > [!div class="mx-imgBorder"]
    > ![Colección en la vista de resultado de la barra de fórmulas](media/function-json/cities-grouped-resultview.png)

1. Inserte otro botón y establezca su **OnSelect** propiedad en esta fórmula:

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    Esta fórmula establece la variable global **CitiesByCountryJSON** a la representación JSON de **CitiesByCountry**.

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

1. Insertar un [ **etiqueta** ](../controls/control-text-box.md) y establezca su **texto** propiedad a esta variable.

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    La etiqueta muestra este resultado, todo en una sola línea sin espacios en blanco, adecuado para la transmisión a través de una red:

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. Cambiar la fórmula del segundo botón para que la salida sea más legible.

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. Seleccione el segundo botón mientras mantiene presionada la tecla Alt.

    La etiqueta muestra el resultado sea más legible.

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

### <a name="images-and-media-in-base64"></a>Las imágenes y medios en base64

1. Agregar un [ **imagen** ](../controls/control-image.md) control.

    Este control aporta **SampleImage** con él.

1. Agregar un [ **botón** ](../controls/control-button.md) y establezca su **OnSelect** fórmula para la propiedad.

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. Seleccione el botón mientras mantiene presionada la tecla Alt.

1. Agregue una etiqueta y establezca su **texto** propiedad a esta variable.

    ```powerapps-dot
    ImageJSON
    ```

1. El tamaño del control y reducir el tamaño de fuente según sea necesario para mostrar la mayor parte del resultado.

    La etiqueta muestra la cadena de texto que el **JSON** función capturado.

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
