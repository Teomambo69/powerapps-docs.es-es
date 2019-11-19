---
title: Tipos de datos | Microsoft Docs
description: Tipos de datos en aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/19/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3147308c52439f250f8f65a81d91d99f30ae1481
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540300"
---
# <a name="data-types-in-canvas-apps"></a>Tipos de datos en aplicaciones de lienzo

La información fluye a través de una aplicación en pequeños valores discretos, muy parecidos a las celdas de una hoja de cálculo. Por ejemplo, los datos de un campo de **cumpleaños** y un campo de **aniversario** fluyen como un valor de **fecha** que incluye el año, el mes y el día. La aplicación sabe cómo dar formato a estos valores, restringir la entrada a lo apropiado para cada uno y compartir los valores con una base de datos. Los cumpleaños difieren de los aniversarios a los usuarios, pero el sistema los controla exactamente de la misma manera. En este caso, **Date** es un ejemplo de un [tipo de datos](https://en.wikipedia.org/wiki/Data_type).

En este artículo se proporcionan detalles sobre los tipos de datos que admiten las aplicaciones de canvas. Cuando una aplicación se conecta a un origen de datos externo, cada tipo de datos de ese origen se asigna a un tipo de datos para las aplicaciones de canvas.

| Tipo de datos | Descripción | Ejemplos |
|-----------|-------------|---------|
| **Booleano** | Valor *true* o *false* .  Se puede usar directamente en **si**, **filtrar** y otras funciones sin una comparación.  | *true* |
| **Color** | Especificación de color, incluido un canal alfa. | **Color.Red**<br>**ColorValue ("#102030")**<br>**RGBA (255, 128, 0, 0,5)** |
| **Moneda** | Valor de moneda que se almacena en un número de punto flotante. Los valores de moneda son los mismos que los valores numéricos con opciones de formato de moneda.  | **123**<br>**4,56** |
| **Posteriormente** | Una fecha sin una hora, en la zona horaria del usuario de la aplicación. | **Fecha (2019, 5, 16)** |
| **DateTime** | Una fecha con una hora, en la zona horaria del usuario de la aplicación. | **Fechahoranumero ("May 16, 2019 1:23:09 PM")** |
| **VOLUMEN** | [Identificador único global](https://en.wikipedia.org/wiki/Universally_unique_identifier). | **GUID ()**<br>**GUID ("123e4567-e89b-12d3-A456-426655440000")** |
| **Hipervínculo** | Cadena de texto que contiene un hipervínculo. | **"https://powerapps.microsoft.com"** |
| **Imagen** | Una cadena de texto de [identificador de recursos universal (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) a una imagen de. JPEG,. png,. SVG,. gif u otro formato de imagen web común. | Mi **imagen** se ha agregado como un recurso de la aplicación<br>**"https://northwindtraders.com/logo.jpg"**<br>**"appres://blobmanager/7b12ffa2..."** |
| **Multimedia** | Una cadena de texto de URI en una grabación de vídeo o audio. | El **vídeo** se ha agregado como un recurso de la aplicación<br>**"https://northwindtraders.com/intro.mp4"**<br>**"appres://blobmanager/3ba411c..."** |
| **Números** | Número de punto flotante. | **123**<br>**-4,567**<br>**8.903e121** |
| **Conjunto de opciones** | Una opción de un conjunto de opciones, respaldado por un número. Este tipo de datos combina una etiqueta de texto traducible con un valor numérico. La etiqueta aparece en la aplicación y el valor numérico se almacena y se usa para las comparaciones. | **ThisItem. OrderStatus** |
| **Record** | Un registro de valores de datos. Este tipo de datos compuesto contiene instancias de otros tipos de datos que se enumeran en este tema. Más información: [trabajar con tablas](../working-with-tables.md). | **{Company: "Northwind Traders",<br>personal: 35, <br>sin ánimo de lucro: false}** |
| **Referencia de registro** | Referencia a un registro de una entidad. Estas referencias se suelen usar con búsquedas polimórficas. Más información: [trabajar con referencias](../working-with-references.md).| **Primero (cuentas). Propietario** |
| **Cuadro** | Una tabla de registros.  Todos los registros deben tener los mismos nombres para sus campos con los mismos tipos de datos y los campos omitidos se tratan como *en blanco*. Este tipo de datos compuesto contiene instancias de otros tipos de datos que se enumeran en este tema. Más información: [trabajar con tablas](../working-with-tables.md). | **Tabla ({FirstName: "Sidney",<br>LastName: "Higa"}, <br>{FirstName: "Nancy",<br>LastName: "Anderson"})**
| **Texto** | Cadena de texto Unicode. | **"Hello, World"** |
| **Tiempo** | Una hora sin fecha, en la zona horaria del usuario de la aplicación. | **Hora (11, 23, 45)** |
| **Dos opciones** | Una opción de un conjunto de dos opciones, respaldada por un valor booleano. Este tipo de datos combina una etiqueta de texto traducible con un valor booleano. La etiqueta aparece en la aplicación y el valor booleano se almacena y se usa para las comparaciones. | **ThisItem. gravable** |

Muchos de estos tipos de datos son similares y tienen la misma representación subyacente, como un campo de **hipervínculo** que se trata como **texto**.  Los tipos de datos adicionales proporcionan mejores experiencias predeterminadas en formularios y otros controles.

## <a name="blank"></a>En blanco

Todos los tipos de datos pueden tener un valor *en blanco* (es decir, ningún valor). El término "null" se usa a menudo en las bases de datos para este concepto.  

Utilice la función **Blank** con la función **set** o **patch** para establecer una variable o un campo en *blanco*. Por ejemplo, **set (x, Blank ())** quita cualquier valor de la variable global **x**.  

Compruebe si hay un valor *en blanco* mediante [**la función esblanco.** ](function-isblank-isempty.md) Reemplace los valores *en blanco* posibles por valores que no estén*en blanco* mediante la función [**Coalesce**](function-isblank-isempty.md) .

Dado que todos los tipos de datos admiten valores *en blanco*, los tipos de datos **booleanos** y **dos opciones** tienen eficazmente tres valores posibles.

## <a name="text-hyperlink-image-and-media"></a>Texto, hipervínculo, imagen y multimedia

Los cuatro tipos de datos se basan en una cadena de texto [Unicode](https://en.wikipedia.org/wiki/Unicode) .

### <a name="image-and-media-resources"></a>Recursos multimedia y de imagen

Mediante el menú **archivo** , puede Agregar archivos de imagen, vídeo y audio como recursos de la aplicación. El nombre del archivo importado se convierte en el nombre del recurso en la aplicación. En este gráfico, el logotipo de Northwind Traders, denominado **nwindlogo**, se ha agregado a una aplicación:

![](media/data-types/nwind-resource.png)

Para usar este recurso en una aplicación, especifíquelo en la propiedad **imagen** de un control [**imagen**](../controls/control-image.md) :

![](media/data-types/nwind-image.png)

### <a name="uris-for-images-and-other-media"></a>URI para imágenes y otros medios

Puede profundizar un poco más en ese último ejemplo si establece la propiedad **texto** de un control [**etiqueta**](../controls/control-text-box.md) en **nwindlogo**. La etiqueta muestra una cadena de texto:

![](media/data-types/nwind-text.png)

Las aplicaciones de lienzo hacen referencia a cada imagen u otro archivo multimedia, ya sea en la nube o se agregan como un recurso de la aplicación, mediante una cadena de texto de URI.

Por ejemplo, la propiedad **imagen** de un control imagen acepta no solo los recursos de la aplicación, sino también los vínculos a las imágenes en la web, como "https://northwindtraders.com/logo.jpg". La propiedad también acepta imágenes insertadas que usan el [esquema de URI de datos](https://en.wikipedia.org/wiki/Data_URI_scheme), como en este ejemplo:

```powerapps-dot
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAkAAAAFAQMAAACtnVQoAAAABlBMVEUAAAB0J3UMNU6VAAAAAXRSTlMAQObYZgAAABRJREFUCNdjUGJgCGVg6GgAkkA2AA8/AffqCEBsAAAAAElFTkSuQmCC"
```

Ese URI muestra una versión escalada de dos diamantes púrpura:

![](media/data-types/double-diamonds.png)

Puede mostrar la imagen más reciente capturada en un control de [**cámara**](../controls/control-camera.md) si establece la propiedad **imagen** de un control imagen en la propiedad **foto** del control cámara. La aplicación contiene la imagen en memoria y la propiedad **Photo** del control de cámara devuelve una referencia de URI a la imagen. Por ejemplo, puede tomar una foto y la propiedad **Photo** de la cámara podría devolver **"appres://blobmanager/7b12ffa2ea4547e5b3812cb1c7b0a2a0/1"** .

El URI se usa para hacer referencia a una imagen u otro archivo multimedia almacenado en una base de datos. De este modo, la aplicación no recupera los datos reales hasta que realmente se necesita. Por ejemplo, los datos adjuntos de una entidad Common Data Service podrían devolver **"appres://datasources/Contacts/Table/..."** como en el ejemplo de cámara, puede mostrar esta imagen estableciendo la propiedad **imagen** de un control imagen en esta referencia, que recupera los datos binarios.

Al guardar un tipo de datos multimedia, como una imagen, en una base de datos, la aplicación envía la imagen o los datos multimedia reales, no la referencia de URI.

### <a name="size-limits"></a>Límites de tamaño

Como cadenas de texto y URI, estos tipos de datos no tienen ningún límite preestablecido para su longitud.

Los datos binarios a los que hacen referencia estos tipos de datos tampoco tienen un límite preestablecido en el tamaño. Por ejemplo, una imagen capturada a través del control de la cámara a la que se hace referencia ahora como **"appres://..."** puede ser tan grande y alta como para la cámara del dispositivo. La resolución, la velocidad de fotogramas y otros atributos de archivos multimedia no están limitados por el tipo de datos, pero los controles específicos para reproducir y capturar medios pueden tener sus propias limitaciones.

Sin embargo, todos los tamaños de datos están sujetos a la cantidad de memoria disponible en la aplicación. Los exploradores que se ejecutan en un equipo de escritorio suelen admitir más de 100 megabytes de datos. Sin embargo, la cantidad de memoria disponible en un dispositivo, como un teléfono, puede ser mucho menor, normalmente en el intervalo de 30-70 megabytes. Para determinar si la aplicación se ejecutará dentro de estos límites, pruebe los escenarios comunes en todos los dispositivos en los que se debe ejecutar.

Como procedimiento recomendado, conserve los datos en la memoria solo cuando sea necesario. Cargar imágenes en una base de datos tan pronto como pueda; Descargue imágenes solo cuando el usuario de la aplicación las solicite.

## <a name="number-and-currency"></a>Número y moneda

Los tipos de datos **Number** y **Currency** usan el [estándar de punto flotante de doble precisión IEEE 754](https://en.wikipedia.org/wiki/IEEE_754). Este estándar proporciona un gran número de números en los que trabajar, desde – 1,79769 x 10<sup>308</sup> hasta 1,79769 x 10<sup>308</sup>. El valor más pequeño que se puede representar es 5 x 10<sup>– 324</sup>.

Las aplicaciones de lienzo pueden representar exactamente números enteros (o enteros) entre – 9.007.199.254.740.991 (– (2<sup>53</sup> – 1)) y 9.007.199.254.740.991 (2<sup>53</sup> – 1), ambos incluidos. Este intervalo es mayor que los tipos de datos enteros de 32 bits (o 4 bytes) que usan habitualmente las bases de datos. Sin embargo, las aplicaciones de canvas no pueden representar tipos de datos enteros de 64 bits (o 8 bytes). Es posible que quiera almacenar el número en un campo de texto o usar una columna calculada para crear una copia del número en un campo de texto, de modo que se asigne a un tipo de datos de **texto** en la aplicación Canvas. De esta manera, puede mantener, mostrar y escribir estos valores, así como compararlos para determinar si son iguales; sin embargo, en este formulario no se pueden realizar cálculos numéricos.

La aritmética de punto flotante es aproximada, por lo que a veces puede proporcionar resultados inesperados con muchos ejemplos documentados. Podría esperar que la fórmula **55/100 * 100** devuelva exactamente 55 y **(55/100 * 100)-55** para que se devuelva exactamente cero. Sin embargo, la última fórmula devuelve 7,1054 x 10<sup>– 15</sup>, que es muy pequeño pero no cero. Esta pequeña diferencia no provoca normalmente un problema y la aplicación la redondea al mostrar el resultado. Sin embargo, las pequeñas diferencias pueden componerse en cálculos posteriores y parecen dar la respuesta equivocada.

Los sistemas de base de datos suelen almacenar monedas y realizar cálculos mediante el uso de matemáticas decimales, que ofrece un intervalo menor pero mayor control sobre la precisión. De forma predeterminada, las aplicaciones de canvas asignan divisas dentro y fuera de los valores de punto flotante; por consiguiente, el resultado podría diferir de los cálculos que se realizan en un tipo de datos decimal nativo. Si este tipo de discrepancia causa problemas, puede que desee trabajar con estos valores como **texto**, del mismo modo que con los enteros grandes descritos anteriormente en esta sección.

## <a name="date-time-and-datetime"></a>Fecha, hora y fecha y hora

### <a name="time-zones"></a>Zonas horarias

Los valores de fecha y hora se encuentran en estas categorías:

- **Local del usuario**: estos valores se almacenan en [UTC (hora universal coordinada)](https://en.wikipedia.org/wiki/Coordinated_Universal_Time), pero la zona horaria del usuario de la aplicación afecta a cómo la aplicación muestra estos valores y cómo los especifica el usuario de la aplicación. Por ejemplo, el mismo momento aparece de manera diferente para un usuario en Canadá que para un usuario de Japón.
- **Independiente de la zona horaria**: la aplicación muestra estos valores de la misma manera y el usuario de la aplicación los especifica de la misma manera, independientemente de la zona horaria. El mismo momento aparece de la misma manera para un usuario en Canadá que para un usuario de Japón. Los autores de aplicaciones que no esperan que sus aplicaciones se ejecuten en distintas zonas horarias usan estos valores, ya que son más sencillos.

En esta tabla se muestran algunos ejemplos:

| Tipo de fecha y hora | Valor almacenado en la base de datos | Valor que se muestra y se especifican 7 horas oeste de UTC | Valor que se muestra y se escribe 4 horas este de UTC |
|--------------------------|------------------------------|------------------------------|
| **Usuario local** | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM | Sábado,&nbsp;puede&nbsp;18&nbsp;2019<br>9:00 PM | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>8:00 AM |
| **Independiente de la zona horaria** | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM | 

En el caso de la fecha y hora **locales del usuario** , las aplicaciones de lienzo usan la zona horaria del explorador o el dispositivo, pero las aplicaciones controladas por modelos usan la configuración del usuario en Common Data Service. Estos valores suelen coincidir, pero los resultados variarán si esta configuración es diferente.

Utilice las funciones [**DateAdd**](function-dateadd-datediff.md) y [**TimeZoneInformation**](function-dateadd-datediff.md) para volver a convertir la hora local a UTC y viceversa.  Vea los ejemplos al final de la documentación de estas funciones.

### <a name="numeric-equivalents"></a>Equivalentes numéricos

Las aplicaciones de lienzo contienen y calculan todos los valores de fecha y hora, ya sean **locales** o de **zona horaria independientes** de la hora UTC. La aplicación traduce los valores en función de la zona horaria del usuario de la aplicación cuando los muestra y cuando el usuario de la aplicación los especifica.

Cuando una aplicación de lienzo Lee un valor independiente de la **zona horaria** de un origen de datos o escribe este valor en un origen de datos, la aplicación ajusta automáticamente el valor para compensar la zona horaria del usuario de la aplicación. A continuación, la aplicación trata el valor como un valor UTC, coherente con todos los demás valores de fecha y hora de la aplicación. Debido a esta compensación, el valor **independiente de la zona horaria** original aparece cuando la aplicación ajusta el valor UTC de la zona horaria del usuario de la aplicación.

Puede observar este comportamiento más detenidamente mediante el uso de la función [**Value**](function-value.md) para tener acceso al valor numérico subyacente de un valor de fecha y hora. Esta función devuelve el valor de fecha y hora como el número de milisegundos transcurridos desde el 1 de enero de 1970 00:00:00.000 UTC.

Dado que cada valor de fecha y hora se mantiene en UTC, el valor de la fórmula **(fecha (1970, 1, 1))** no devolverá cero en la mayoría de las partes del mundo porque la función **Date** devuelve una fecha en formato UTC. Por ejemplo, la fórmula devolverá 28,8 millones en una zona horaria en la que se desplace la hora UTC en ocho horas. Ese número refleja el número de milisegundos en ocho horas.

Volviendo al ejemplo anterior:

| Tipo de fecha y hora | Valor almacenado en la base de datos | Valor que se muestra y se especifican 7 horas oeste de UTC | La función **Value** devuelve |
|--------------------------|------------------------------|------------------------------|
| **Usuario local** | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM | Sábado,&nbsp;puede&nbsp;18&nbsp;2019<br>9:00 PM | 1\.558.238.400.000<br> (Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM UTC) |
| **Independiente de la zona horaria** | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM | Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>4:00 AM |1\.558.263.600.000<br> (Domingo,&nbsp;puede&nbsp;19&nbsp;2019<br>11:00 AM UTC) |

### <a name="converting-unix-times"></a>Convertir horas UNIX

Los tiempos UNIX reflejan el número de segundos transcurridos desde el 1 de enero de 1970 00:00:00 UTC. Dado que las aplicaciones de canvas usan milisegundos en lugar de segundos, puede convertir entre los dos multiplicando o dividiendo por 1.000.

Por ejemplo, la hora de UNIX muestra el 9 de septiembre de 2001, a las 01:46:40 UTC como 1 mil millones. Para mostrar ese valor de fecha y hora en una aplicación de lienzo, multiplique ese número por 1.000 para convertirlo en milisegundos y usarlo en una función de [**texto**](function-text.md) . El texto de la fórmula **(1 mil millones * 1000, DateTimeFormat. UTC)** devuelve la cadena **2001-09-09T01:46:40.000 z**.

Sin embargo, esa función devuelve el **sábado, 8 de septiembre de 2001 18:46:40** si usa el formato **DateTimeFormat. LongDateTime24** en una zona horaria con una diferencia de 7 horas con respecto a la hora UTC (7 horas oeste de UTC). Este resultado muestra el valor **DateTime** correctamente basado en la zona horaria local.

Para convertir a una hora de UNIX, divida el resultado de **Value** por 1.000:
<br>**Redondear (valor (UnixTime)/1000, 0)**

Si necesita la hora de UNIX en un valor de **fecha** para obtener más cálculos o Mostrar en PowerApps, use esta fórmula:
<br>**DateAdd (fecha (1970, 1, 1), UnixTime, segundos)**

### <a name="sql-server"></a>SQL Server

SQL Server tiene [ **DateTime**, **Datetime2**y otros tipos de datos de fecha y hora](https://docs.microsoft.com/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql?view=sql-server-2017) que no incluyen un desplazamiento de zona horaria y no indican la zona horaria en la que se encuentran. Las aplicaciones de canvas suponen que estos valores se almacenan en UTC y los tratan como **usuario local**. Si los valores están diseñados para ser independientes de la zona horaria, corrija las traducciones UTC mediante la función [**TimeZoneOffset**](function-dateadd-datediff.md#converting-to-utc) .

Las aplicaciones de lienzo usan la información de zona horaria incluida en campos **DateTimeOffset** al convertir un valor en la representación UTC interna de la aplicación. Las aplicaciones siempre usan la hora UTC como zona horaria (cero desplazamiento de zona horaria) cuando escriben datos.

Las aplicaciones de lienzo leen y escriben los valores del tipo de datos [**Time**](https://docs.microsoft.com/sql/t-sql/data-types/time-transact-sql) en SQL Server como cadenas de texto en el [formato de duración ISO 8601](https://en.wikipedia.org/wiki/ISO_8601#Durations). Por ejemplo, debe analizar este formato de cadena y usar la función [**Time**](function-date-time.md) para convertir la cadena de texto **"PT2H1M39S"** en un valor de **hora** :

```powerapps-dot
First(
    ForAll(
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

### <a name="mixing-date-and-time-information"></a>Mezclar información de fecha y hora

**Date**, **Time**y **DateTime** tienen nombres diferentes, pero todos contienen la misma información sobre las fechas y horas. 

Un valor de **fecha** puede incluir información de hora con él, que normalmente es la medianoche. Un valor de **hora** puede contener información de fecha, que suele ser el 1 de enero de 1970. Common Data Service también almacena información de hora con un campo de **fecha solo** , pero muestra solo la información de fecha de forma predeterminada. Del mismo modo, las aplicaciones de canvas distinguen a veces estos tipos de datos para determinar los formatos y controles predeterminados.

No se recomienda agregar y restar los valores de fecha y hora directamente porque la zona horaria y otras conversiones podrían producir resultados confusos. Use la función **Value** para convertir los valores de fecha y hora en milisegundos en primer lugar y tener en cuenta la zona horaria del usuario de la aplicación, o use las funciones [**DateAdd**](function-dateadd-datediff.md) y [**DateDiff**](function-dateadd-datediff.md) para sumar o restar de uno de estos valores.

## <a name="option-sets-and-two-options"></a>Conjuntos de opciones y dos opciones

Los conjuntos de opciones y los tipos de datos de dos opciones proporcionan dos o más opciones para que un usuario de la aplicación seleccione. Por ejemplo, un conjunto de opciones de **Estado de pedido** podría ofrecer las opciones **nuevas**, **enviadas**, **facturadas**y **cerradas**. El tipo de datos de dos opciones solo ofrece dos opciones.

Ambos tipos de datos muestran sus etiquetas en un contexto de cadena de texto. Por ejemplo, un control etiqueta muestra una de las opciones de estado de orden si la propiedad **texto** del control se establece en una fórmula que hace referencia a ese conjunto de opciones. Las etiquetas de opción se pueden localizar para los usuarios de aplicaciones en ubicaciones diferentes.

Cuando un usuario de la aplicación selecciona una opción y guarda ese cambio, la aplicación transmite los datos a la base de datos, que almacena esos datos en una representación independiente del lenguaje. Una opción en un conjunto de opciones se transmite y almacena como un número, y una opción en un tipo de datos de dos opciones se transmite y se almacena como un valor booleano.

Las etiquetas solo son para fines de presentación. No se pueden realizar comparaciones directas con las etiquetas porque son específicas de un idioma. En su lugar, cada conjunto de opciones tiene una enumeración que funciona con el número o valor booleano subyacente. Por ejemplo, no puede usar esta fórmula:

`If( ThisItem.OrderStatus = "Active", ...`

Pero puede usar esta fórmula:

`If( ThisItem.OrderStatus = OrderStatus.Active, ...`

En el caso de los conjuntos de opciones globales (que comparten las entidades), el nombre de la enumeración de conjuntos de opciones coincide con el nombre del conjunto de opciones global. En el caso de los conjuntos de opciones locales (cuyo ámbito es una entidad), el nombre puede contener el nombre de la entidad. Este comportamiento evita conflictos si varias entidades tienen conjuntos de opciones con el mismo nombre. Por ejemplo, la entidad **accounts** puede tener una opción **OrderStatus** establecida y su nombre podría ser **OrderStatus (accounts)** . Ese nombre contiene uno o varios espacios y paréntesis, por lo que debe encerrarlo con comillas simples si hace referencia a él en una fórmula.

Además, los valores de dos opciones también pueden comportarse como valores booleanos. Por ejemplo, un valor de dos opciones denominado **TaxStatus** podría tener las etiquetas **gravable** y **No gravable**, que corresponden a *true* y *false* respectivamente. Para mostrarlo, puede usar esta fórmula:

`If( ThisItem.Taxable = TaxStatus.Taxable, ...`

También puede usar esta fórmula equivalente:

`If( ThisItem.Taxable, ...`