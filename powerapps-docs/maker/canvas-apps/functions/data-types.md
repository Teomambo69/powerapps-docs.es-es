---
title: Tipos de datos | Microsoft Docs
description: Tipos de datos en aplicaciones de lienzo
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/19/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f9acc04a9159349075647ca4e318f15939a230f7
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216646"
ms.PowerAppsDecimalTransform: true
---
# <a name="data-types-in-canvas-apps"></a>Tipos de datos en aplicaciones de lienzo

Flujos de información a través de una aplicación en los valores pequeños y discretos, de forma muy similar a las celdas de una hoja de cálculo. Por ejemplo, los datos de un **cumpleaños** campo y un **aniversario** campo podría ambos fluir a través de como un **fecha** valor que incluya la año, mes y día. La aplicación sabe cómo dar formato a estos valores, restringir la entrada a lo que sea adecuado para cada uno y compartir los valores con una base de datos. Cumpleaños diferencian aniversarios a personas, pero el sistema controla exactamente del mismo modo. En este caso, **fecha** es un ejemplo de un [tipo de datos](https://en.wikipedia.org/wiki/Data_type).

En este artículo proporciona detalles para los tipos de datos que la compatibilidad de aplicaciones de lienzo. Cuando una aplicación se conecta a un origen de datos externo, cada tipo de ese origen de datos se asigna a un tipo de datos para las aplicaciones de lienzo.

| Tipo de datos | Descripción | Ejemplos |
|-----------|-------------|---------|
| **Boolean** | Un *true* o *false* valor.  Se pueden usar directamente en **si**, **filtro** y otras funciones sin una comparación.  | *true* |
| **Hyperlink** | Una cadena de texto que contiene un hipervínculo. | **"http://powerapps.microsoft.com"** |
| **Moneda** | Un valor de moneda que se almacena en un número de punto flotante. Los valores de moneda son los mismos que los valores number con opciones de formato de moneda.  | **123**<br>**4.56** |
| **Imagen** | Un [identificador Universal de recursos (URI)](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) formatos de cadena de texto a una imagen en .jpeg, .png, .svg, .gif y otra imagen de web comunes. | **MyImage** agregado como un recurso de aplicación<br>**"https://northwindtraders.com/logo.jpg"**<br>**"appres://blobmanager/7b12ffa2..."** |
| **Color** | Una especificación de color, incluido un canal alfa. | **Color.Red**<br>**ColorValue( "#102030" )**<br>**RGBA( 255; 128; 0; 0,5 )** |
| **Fecha** | Una fecha sin un tiempo, en la zona horaria del usuario de la aplicación. | **Fecha (2019, 5, 16)** |
| **DateTime** | Una fecha con un tiempo, en la zona horaria del usuario de la aplicación. | **Fechahoranumero ("16 de mayo de 2019 1:23:09 PM")** |
| **GUID** | Un [identificador único global](https://en.wikipedia.org/wiki/Universally_unique_identifier). | **GUID()**<br>**GUID( "123e4567-e89b-12d3-a456-426655440000" )** |
| **Multimedia** | Una cadena de texto URI para una grabación de audio o vídeo. | **Mi vídeo** agregado como un recurso de aplicación<br>**"https://northwindtraders.com/intro.mp4"**<br>**"appres://blobmanager/3ba411c..."** |
| **Número** | Número de punto flotante. | **123**<br>**-4.567**<br>**8.903e121** |
| **Conjunto de opciones** | Una opción de un conjunto de opciones, respaldado por un número. Este tipo de datos combina una etiqueta de texto localizable con un valor numérico. La etiqueta aparece en la aplicación y se almacena el valor numérico y se usa para las comparaciones. | **ThisItem.OrderStatus** |
| **Record** | Registro de los valores de datos. Este tipo de datos compuesta contiene instancias de otros tipos de datos que aparecen en este tema. Más información: [Trabajar con tablas](../working-with-tables.md). | **{La empresa: "Northwind Traders";<br>personal: 35; <br>NonProfit: false }** |
| **Referencia de registro** | Una referencia a un registro en una entidad. Estas referencias se suelen usar con las búsquedas polimórficas. Más información: [Trabajar con referencias](../working-with-references.md).| **First(Accounts).Owner** |
| **Table** | Una tabla de registros.  Todos los registros deben tener los mismos nombres para sus campos con los mismos tipos de datos y los campos omitidos se tratan como *en blanco*. Este tipo de datos compuesta contiene instancias de otros tipos de datos que aparecen en este tema. Más información: [Trabajar con tablas](../working-with-tables.md). | **Tabla ({FirstName: "Sidney";<br>LastName: "Higa"}; <br>{FirstName: "Nancy,"<br>LastName: "Anderson" } )**
| **Texto** | Una cadena de texto Unicode. | **"Hello, World"** |
| **Tiempo** | Una vez sin una fecha, en la zona horaria del usuario de la aplicación. | **Tiempo (11, 23, 45)** |
| **Opción dos** | Una opción de un conjunto de dos opciones, respaldado por un valor booleano. Este tipo de datos combina una etiqueta de texto localizable con un valor booleano. La etiqueta aparece en la aplicación y se almacena el valor booleano y se usa para las comparaciones. | **ThisItem.Taxable** |

Muchos de estos tipos de datos son similares y tienen la misma representación subyacente, como un **hipervínculo** campo que se tratan como **texto**.  Los tipos de datos adicionales proporcionan predeterminada mejor experiencias en formularios y otros controles.

## <a name="blank"></a>Blank

Todos los tipos de datos pueden tener un valor de *en blanco* (es decir, ningún valor). El término "null" se usa a menudo en las bases de datos de este concepto.  

Use la **en blanco** funcionando con el **establecer** o **Patch** función para establecer una variable o campo para *en blanco*. Por ejemplo, **conjunto (x; Blank())** quita cualquier valor en la variable global **x**.  

Probar un *en blanco* valor mediante el uso de la [ **IsBlank** ](function-isblank-isempty.md) función. Reemplace posible *en blanco* valores con los que no sean de*en blanco* valores usando el [ **Coalesce** ](function-isblank-isempty.md) función.

Dado que todos los tipos de datos admiten *en blanco*, el **booleano** y **opción dos** eficazmente, tipos de datos tienen tres valores posibles.

## <a name="text-hyperlink-image-and-media"></a>Texto, hipervínculo, imágenes y multimedia

Cuatro de estos tipos de datos se basa en un [Unicode](https://en.wikipedia.org/wiki/Unicode) cadena de texto.

### <a name="image-and-media-resources"></a>Recursos de imágenes y multimedia

A través de la **archivo** menú, puede agregar archivos de imagen, audio y vídeo como recursos de la aplicación. El nombre del archivo importado se convierte en el nombre del recurso en la aplicación. En este gráfico, el logotipo de Northwind Traders, que se denomina **nwindlogo**, se ha agregado a una aplicación:

![](media/data-types/nwind-resource.png)

Para utilizar este recurso en una aplicación, especifíquela en el **imagen** propiedad de un [ **imagen** ](../controls/control-image.md) control:

![](media/data-types/nwind-image.png)

### <a name="uris-for-images-and-other-media"></a>URI para las imágenes y otros medios

Puede profundizar un poco más en el último ejemplo estableciendo el **texto** propiedad de un [ **etiqueta** ](../controls/control-text-box.md) control **nwindlogo**. La etiqueta muestra una cadena de texto:

![](media/data-types/nwind-text.png)

Las aplicaciones de lienzo hacen referencia a cada imagen u otro archivo de medios, ya sea en la nube o como un recurso de aplicación, agregando una cadena de texto identificador URI.

Por ejemplo, el **imagen** propiedad de un control image acepta no sólo los recursos de la aplicación, sino también vínculos a imágenes en la web, como "https://northwindtraders.com/logo.jpg". La propiedad también admite imágenes en línea que usan el [esquema de URI de datos](https://en.wikipedia.org/wiki/Data_URI_scheme), como en este ejemplo:

```powerapps-comma
"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAkAAAAFAQMAAACtnVQoAAAABlBMVEUAAAB0J3UMNU6VAAAAAXRSTlMAQObYZgAAABRJREFUCNdjUGJgCGVg6GgAkkA2AA8/AffqCEBsAAAAAElFTkSuQmCC"
```

Ese URI muestra una versión escalada de diamantes púrpuras dos:

![](media/data-types/double-diamonds.png)

Puede mostrar la imagen más reciente que se capturan en un [ **cámara** ](../controls/control-camera.md) controlar si establece la **imagen** propiedad de un control de imagen para el **Photo** propiedad del control de cámara. La aplicación guarda la imagen en la memoria y el **Photo** propiedad del control de cámara devuelve una referencia de URI a la imagen. Por ejemplo, puede tardar una imagen y la cámara **Photo** propiedad podría devolver **"appres://blobmanager/7b12ffa2ea4547e5b3812cb1c7b0a2a0/1"** .

Use un URI para hacer referencia a una imagen u otro archivo de medios que se almacenan en una base de datos. De este modo, la aplicación no recupera los datos reales hasta que sea realmente necesario. Por ejemplo, podrían devolver los datos adjuntos en una entidad de Common Data Service **"appres://datasources/Contacts/table/..."** Como se muestra en el ejemplo de la cámara, puede mostrar esta imagen estableciendo el **imagen** propiedad de un control de imagen para esta referencia, que recupera los datos binarios.

Al guardar un tipo de datos de medios, como una imagen, en una base de datos, la aplicación envía la imagen real o los datos de medios, no la referencia URI.

### <a name="size-limits"></a>Límites de tamaño

Como las cadenas de texto y los URI, estos tipos de datos no tienen ningún límite preestablecido en su longitud.

Los datos binarios que también hacen referencia a estos tipos de datos no tienen ningún límite preestablecido en tamaño. Por ejemplo, una imagen capturada a través del control de cámara que ahora se hace referencia como **"appres: / /..."** puede ser como grande y de alta resolución que logre reunir la cámara del dispositivo. La resolución, velocidad de fotogramas y otros atributos de archivos multimedia no están limitados por el tipo de datos, pero los controles específicos para reproducir y medios de captura pueden tener sus propias limitaciones.

Sin embargo, todos los tamaños de datos están sujetos a la cantidad de memoria disponible en la aplicación. Los exploradores que se ejecutan en un equipo de escritorio normalmente admiten más de 100 megabytes de datos. Sin embargo, la cantidad de memoria disponible en un dispositivo como un teléfono podría ser mucho menor, normalmente en el intervalo 30-70 megabytes. Para determinar si la aplicación se ejecutará dentro de estos límites, probar escenarios comunes en todos los dispositivos en los que se debe ejecutar.

Como práctica recomendada, almacenar datos en memoria solo mientras según sea necesario. Cargar imágenes en una base de datos tan pronto como pueda; Descargar imágenes solo cuando el usuario de la aplicación las solicita.

## <a name="number-and-currency"></a>Número y moneda

**Número** y **moneda** tipos de datos se usa el [estándar de punto flotante de precisión doble IEEE 754](https://en.wikipedia.org/wiki/IEEE_754). Este estándar proporciona un intervalo muy grande de números en el que se va a trabajar desde –1.79769 x 10<sup>308</sup> y 1.79769 x 10<sup>308</sup>. El valor más pequeño que se puede representar es 5 x 10<sup>–324</sup>.

Las aplicaciones de lienzo exactamente pueden representar números enteros (o enteros) entre –9,007,199,254,740,991 (– (2<sup>53</sup> – 1)) y 9,007,199,254,740,991 (2<sup>53</sup> – 1), ambos inclusive. Este intervalo es mayor que los tipos de datos entero de 32 bits (o 4 bytes) que normalmente utilizan las bases de datos. Sin embargo, las aplicaciones de lienzo no pueden representar tipos de datos enteros de 64 bits (o de 8 bytes). Es posible que desee almacenar el número en un campo de texto o usar una columna calculada para hacer una copia del número en un campo de texto, por lo que se asigna a un **texto** tipo de datos en la aplicación de lienzo. De esta manera, puede contener, mostrar y escribir estos valores, así como compararlos para determinar si son iguales; Sin embargo, no puede realizar cálculos numéricos en ellos en este formulario.

Aritmética de punto flotante es aproximado, por lo que a veces puede provocar resultados inesperados con muchos ejemplos documentados. Es de esperar la fórmula **55 / 100 * 100** para devolver exactamente 55 y **(55 / 100 * 100): 55** para devolver exactamente en cero. Sin embargo, la fórmula de este última devuelve 7.1054 x 10<sup>– 15</sup>, que es muy pequeño, pero no en cero. Esa pequeña diferencia normalmente no causa un problema y la aplicación redondea inmediatamente cuando se muestre el resultado. Sin embargo, pequeñas diferencias pueden compuesta en los cálculos posteriores y parece que asigne a la respuesta incorrecta.

A menudo, los sistemas de base de datos almacenan monedas y realizan cálculos utilizando math decimal, que ofrece un intervalo menor pero mayor control sobre la precisión. De forma predeterminada, el lienzo monedas de asignación de aplicaciones dentro y fuera de los valores de punto flotante; por lo tanto, los resultados pueden diferir de los cálculos que se realizan en un tipo de datos decimal nativo. Si este tipo de discrepancia causará problemas, es posible que desea trabajar con estos valores como **texto**, al igual que lo haría con enteros grandes se ha descrito anteriormente en esta sección.

## <a name="date-time-and-datetime"></a>Fecha, hora y fecha y hora

### <a name="time-zones"></a>Zonas horarias

Fecha/hora disminución de los valores de estas categorías:

- **Usuario local**: Estos valores se almacenan en [UTC (Coordinated Universal Time)](https://en.wikipedia.org/wiki/Coordinated_Universal_Time), pero la zona horaria del usuario de la aplicación afecta a cómo muestra estos valores de la aplicación y el modo en que especifica el usuario de la aplicación. Por ejemplo, el mismo momento muestra distinto para un usuario de Canadá de lo que un usuario en Japón.
- **Zona horaria independiente**: La aplicación muestra estos valores del mismo modo y el usuario de la aplicación especifica la misma manera, independientemente de la zona horaria. El mismo momento aparece la misma manera a un usuario en Canadá, tal como hace con un usuario en Japón. Los autores de la aplicación que no esperan que sus aplicaciones se ejecuten en diferentes zonas horarias usan estos valores porque son más sencillas en general.

Esta tabla muestra algunos ejemplos:

| Tipo de fecha y hora | Valor almacenado en la base de datos | Valor de muestra y escrito 7 horas al oeste UTC | Muestra y especifica 4 horas al este de UTC |
|--------------------------|------------------------------|------------------------------|
| **Usuario local** | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. | El sábado,&nbsp;puede&nbsp;18,&nbsp;2019<br>9:00 P. M. | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>8:00 A. M. |
| **Zona horaria independiente** | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. | 

Para **usuario local** la fecha y hora, las aplicaciones de lienzo usan la zona horaria del explorador o dispositivo, pero las aplicaciones controladas por modelos usan el usuario en común configurar el servicio de datos. Suelen coincidir con esta configuración, pero los resultados variarán si estos valores son diferentes.

### <a name="numeric-equivalents"></a>Equivalentes numéricos

Las aplicaciones de lienzo mantenga y calcular todos los valores de fecha/hora, si **usuario local** o **independientes de zona horaria** en UTC. La aplicación traduce los valores basándose en la zona de horaria del usuario de la aplicación cuando mostrarles y cuando el usuario especifica.

Cuando una aplicación de lienzo lee un **independientes de zona horaria** valor desde un origen de datos o escribe un valor de este tipo a un origen de datos, la aplicación ajusta automáticamente el valor para compensar la zona horaria del usuario de la aplicación. La aplicación, a continuación, trata el valor como un valor de hora UTC, coherente con todos los demás valores de fecha y hora en la aplicación. Debido a esta compensación, original **independientes de zona horaria** valor aparece cuando la aplicación ajusta el valor de hora UTC para la zona horaria del usuario de la aplicación.

Puede observar este comportamiento mediante el uso de más detenidamente el [ **valor** ](function-value.md) función para acceder al valor numérico subyacente de un valor de fecha y hora. Esta función devuelve el valor de fecha y hora como el número de milisegundos desde el 1 de enero de 1970 UTC 00:00:00.000.

Dado que cada valor de fecha y hora se guarda en formato UTC, la fórmula **valor (fecha (1970, 1, 1))** no devuelven cero en muchas partes del mundo, porque el **fecha** función devuelve una fecha en formato UTC. Por ejemplo, la fórmula devolvería 28,800,000 en una zona horaria que se desplaza a la hora UTC en ocho horas. Ese número refleja el número de milisegundos en ocho horas.

Volviendo a nuestro ejemplo anterior:

| Tipo de fecha y hora | Valor almacenado en la base de datos | Valor de muestra y escrito 7 horas al oeste UTC | **Valor** función devuelve |
|--------------------------|------------------------------|------------------------------|
| **Usuario local** | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. | El sábado,&nbsp;puede&nbsp;18,&nbsp;2019<br>9:00 P. M. | 1,558,238,400,000<br> (El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. UTC) |
| **Zona horaria independiente** | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. | El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>4:00 A.M. |1,558,263,600,000<br> (El domingo,&nbsp;puede&nbsp;19,&nbsp;2019<br>11:00 A.M. UTC) |

### <a name="converting-unix-times"></a>Conversión de horas de Unix

UNIX reflejan el número de segundos desde el 1 de enero de 1970 00:00:00 UTC. Dado que las aplicaciones de lienzo utiliza milisegundos en lugar de segundos, puede convertir entre los dos multiplicando o dividiendo por 1.000.

Por ejemplo, tiempo de Unix muestra 9 de septiembre de 2001, de 01:46:40 UTC como 1.000.000.000. Para mostrar que el valor en una aplicación de lienzo de fecha y hora, multiplicar ese número por 1000 para poder convertirlo en milisegundos y, a continuación, utilizarlo en un [ **texto** ](function-text.md) función. La fórmula **texto (1000000000 * 1000, DateTimeFormat.UTC)** devuelve la cadena **2001-09-09T01:46:40.000Z**.

Sin embargo, esa función devuelve **el sábado, 8 de septiembre de 2001 18:46:40** si usas el **DateTimeFormat.LongDateTime24** formato en una zona horaria que es menos 7 horas de desplazamiento a la hora UTC (7 horas al oeste UTC). Este resultado muestra el **DateTime** valor correctamente según la zona horaria local.

Para convertir en una hora Unix, divida el resultado de **valor** por 1.000:
<br>**RoundDown( Value( UnixTime ) / 1000; 0 )**

Si necesita la hora de Unix en un **fecha** valor para cálculos o mostrar dentro de PowerApps, use la siguiente fórmula:
<br>**DateAdd( Date( 1970;1;1 ); UnixTime; Seconds )**

### <a name="sql-server"></a>SQL Server

SQL Server tiene [ **Datetime**, **Datetime2**y otros tipos de datos de fecha y hora](https://docs.microsoft.com/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql?view=sql-server-2017) que no incluya un desplazamiento de zona horaria y no indican qué zona horaria que se encuentren en. Las aplicaciones de lienzo suponen estos valores se almacenan en formato UTC y tratan como **usuario local**. Si los valores están diseñados para ser independiente de la zona horaria, corregir las traducciones de hora UTC utilizando la [ **TimeZoneOffset** ](function-dateadd-datediff.md#converting-to-utc) función.

Las aplicaciones de lienzo usan la información de zona horaria incluida en **Datetimeoffset** campos al convertir un valor a la representación interna de UTC de la aplicación. Las aplicaciones siempre usan UTC como la zona horaria (cero ajuste de zona horaria) cuando escriben datos.

Las aplicaciones de lienzo, leer y escribir valores de la [ **tiempo** ](https://docs.microsoft.com/en-us/sql/t-sql/data-types/time-transact-sql) tipo de datos en SQL Server como cadenas de texto en el [formato de duración ISO 8601](https://en.wikipedia.org/wiki/ISO_8601#Durations). Por ejemplo, debe analizar este formato de cadena y usar el [ **tiempo** ](function-date-time.md) función para convertir la cadena de texto **"PT2H1M39S"** a un **tiempo** valor:

```powerapps-comma
First(
    ForAll(
        MatchAll( "PT2H1M39S"; "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" );
        Time( Value( hours ); Value( minutes ); Value( seconds ) )
    )
).Value
```

### <a name="mixing-date-and-time-information"></a>Combinar información de fecha y hora

**Fecha**, **tiempo**, y **DateTime** tienen nombres diferentes, pero contienen la misma información acerca de las fechas y horas. 

Un **fecha** valor puede incluir información de tiempo con él, que normalmente es medianoche. Un **tiempo** valor puede llevar la información de fecha, que normalmente es el 1 de enero de 1970. Common Data Service también almacena información de tiempo con un **sólo fecha** campo, pero muestra sólo la información de fecha de forma predeterminada. De forma similar, las aplicaciones de lienzo a veces se distinguen entre estos tipos de datos para determinar los formatos predeterminados y los controles.

Sumar y restar directamente los valores de fecha y hora no se recomiendan porque podrían provocar que las conversiones de zona horaria y otras resultados confusos. Usar el **valor** función para convertir los valores de fecha y hora en milisegundos en primer lugar y tener en cuenta la zona de horaria del usuario de la aplicación, o usar el [ **DateAdd** ](function-dateadd-datediff.md) y [ **DateDiff** ](function-dateadd-datediff.md) funciones para agregar o restar uno de estos valores.

## <a name="option-sets-and-two-options"></a>Conjuntos de opciones y las dos opciones

Conjuntos de opciones y los tipos de datos de la opción de dos proporcionan una dos o más opciones para seleccionar un usuario de la aplicación. Por ejemplo, un **estado del pedido** conjunto de opciones puede ofrecer las opciones **New**, **Shipped**, **facturado**, y **cerrado** . El tipo de datos de la opción de dos ofrece solo dos opciones.

Ambos de estos tipos de datos muestran sus etiquetas en un contexto de la cadena de texto. Por ejemplo, un control de etiqueta muestra una de las opciones de estado del pedido si el control **texto** propiedad está establecida en una fórmula que hace referencia a ese conjunto de opciones. Las etiquetas de la opción se pueden localizar para usuarios de la aplicación en diferentes ubicaciones.

Cuando un usuario de la aplicación selecciona una opción y guarda ese cambio, la aplicación transmite los datos a la base de datos que almacena los datos en una representación que es independiente del idioma. Una opción en un conjunto de opciones se transmite y almacena como un número y una opción en un tipo de datos de la opción de dos se transmite y almacena como un valor booleano.

Las etiquetas son solo con fines de visualización. No se puede realizar las comparaciones directas con las etiquetas debido a que son específicos de un idioma. En su lugar, cada conjunto de opciones tiene una enumeración que funciona con el número de subyacente o un valor booleano. Por ejemplo, no puede usar esta fórmula:

`If( ThisItem.OrderStatus = "Active"; ...`

Pero puede usar esta fórmula:

`If( ThisItem.OrderStatus = OrderStatus.Active; ...`

Para conjuntos de opciones globales (las entidades que comparten), el nombre de la enumeración de conjunto de opciones coincide con el nombre del conjunto de opciones globales. Para conjuntos de opciones locales (cuyo ámbito es una entidad), el nombre puede contener el nombre de la entidad. Este comportamiento evita conflictos si varias entidades tienen conjuntos de opciones que tienen el mismo nombre. Por ejemplo, el **cuentas** entidad podría tener un **OrderStatus** opción establecida, y su nombre podría ser **OrderStatus (cuentas)** . Ese nombre contiene uno o más espacios y paréntesis, por lo que debe delimitar con comillas simples si se hace referencia en una fórmula.

Además, los valores de las dos opciones también pueden comportarse como valores booleanos. Por ejemplo, un valor de opción de dos denominado **TaxStatus** podría tener las etiquetas **sujetos** y **no sujeto**, que corresponden a *true* y *false* respectivamente. Para mostrar, puede usar esta fórmula:

`If( ThisItem.Taxable = TaxStatus.Taxable; ...`

También puede usar esta fórmula equivalente:

`If( ThisItem.Taxable; ...`