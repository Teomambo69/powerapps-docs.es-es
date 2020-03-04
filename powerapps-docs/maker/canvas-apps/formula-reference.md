---
title: Funciones, señales y enumeraciones | Microsoft Docs
description: Información de referencia sobre las funciones, las señales y las enumeraciones en Power Apps.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c70d73cb2dcdd9fd1832a10c4c89029cdb5c45ad
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264922"
---
# <a name="formula-reference-for-power-apps"></a>Referencia sobre las fórmulas de Power Apps
Las fórmulas combinan numerosos elementos.  A continuación se enumera lo siguiente:

* Las **funciones** toman parámetros, realizar una operación y devuelven un valor. Por ejemplo, **Sqrt(25)** devuelve **5**. Las funciones se basan en las funciones de Microsoft Excel.  Algunas funciones tienen efectos secundarios, como **SubmitForm**, y solo son adecuadas en una [fórmula de comportamiento](working-with-formulas-in-depth.md) como **Button.OnSelect**.
* Las **señales** devuelven información sobre el entorno. Por ejemplo, **[Location](functions/signals.md)** devuelve las coordenadas GPS actuales del dispositivo. Las señales no toman parámetros ni tienen efectos secundarios.
* Las **enumeraciones** devuelven un valor constante predefinido. Por ejemplo, **[Color](functions/function-colors.md)** es una enumeración que tiene valores predefinidos para **Color.Red**, **Color.Blue**, etc.  Aquí se incluyen enumeraciones comunes; las enumeraciones específicas de funciones se describen con la función.
* Los **operadores con nombre**, como **[ThisItem](functions/operators.md#thisitem-operator)** y **[Parent](functions/operators.md#parent-operator)** , proporcionan acceso a información desde un contenedor.

Otros elementos incluyen:

* [Operadores e identificadores](functions/operators.md)
* [Controles y sus propiedades](reference-properties.md)
* [Tipos de datos](functions/data-types.md)

## <a name="a"></a>A
**[Abs](functions/function-numericals.md)** : valor absoluto de un número.  

**[Acceleration](functions/signals.md)** : lee el sensor de aceleración del dispositivo.

**[Acos](functions/function-trig.md)** : devuelve el arco coseno de un número, en radianes.

**[Acot](functions/function-trig.md)** : devuelve el arco tangente de un número, en radianes.

**[AddColumns](functions/function-table-shaping.md)** : devuelve una tabla con [columnas](working-with-tables.md#columns) agregadas.

**[And](functions/function-logicals.md)** : lógica booleana Y.  Devuelve **true** si todos los argumentos son **true**.  También puede usar el [operador **&&** ](functions/operators.md).

**[App](functions/object-app.md)** : proporciona información sobre la aplicación en ejecución y el control sobre el comportamiento de esta.

**[Asin](functions/function-trig.md)** : devuelve el arco seno de un número, en radianes.

**[Assert](functions/function-assert.md)** : se evalúa como "true" o "false" en una prueba.

**[AsType](functions/function-astype-istype.md)** : trata una referencia del registro como un tipo de entidad específico.

**[Atan](functions/function-trig.md)** : devuelve el arco tangente de un número, en radianes.

**[Atan2](functions/function-trig.md)** : devuelve el arco tangente en función de una coordenada (*x*,*y*), en radianes.

**[Average](functions/function-aggregates.md)** : calcula la media de una expresión de tabla o un conjunto de argumentos.

## <a name="b"></a>B
**[Back](functions/function-navigate.md)** : muestra la pantalla anterior.  

**[Blank](functions/function-isblank-isempty.md)** : devuelve un valor *en blanco* que puede utilizarse para insertar un valor NULL en un origen de datos.

## <a name="c"></a>C
**[Calendar](functions/function-clock-calendar.md)** : recupera información sobre el calendario para la configuración regional actual.

**[Char](functions/function-char.md)** : traduce un código de carácter en una cadena.

**[Choices](functions/function-choices.md)** : devuelve una tabla de posibles valores para una columna de búsqueda.

**[Clear](functions/function-clear-collect-clearcollect.md)** : elimina todos los datos de una [colección](working-with-data-sources.md#collections).

**[ClearCollect](functions/function-clear-collect-clearcollect.md)** : elimina todos los datos de una colección y, después, agrega un conjunto de [registros](working-with-tables.md#records).

**[Clock](functions/function-clock-calendar.md)** : recupera información sobre el reloj para la configuración regional actual.

**[Coalesce](functions/function-isblank-isempty.md)** : reemplaza valores *blank* y deja los valores que no son *blank*.

**[Collect](functions/function-clear-collect-clearcollect.md)** : crea una colección o agrega datos a un origen de datos.

**[Color](functions/function-colors.md)** : establece una propiedad en un valor de color integrado.

**[ColorFade](functions/function-colors.md)** : atenúa un valor de color.

**[ColorValue](functions/function-colors.md)** : traduce un nombre de color CSS o un código hexadecimal en un valor de color.  

**[Compass](functions/signals.md)** : devuelve el encabezado de brújula.

**[Concat](functions/function-concatenate.md)** : concatena cadenas en un origen de datos.  

**[Concatenate](functions/function-concatenate.md)** : concatena cadenas.

**[Concurrent](functions/function-concurrent.md)** : evalúa varias fórmulas simultáneamente entre sí. 

**[Connection](functions/signals.md)** : devuelve información sobre la conexión de red.

**[Count](functions/function-table-counts.md)** : cuenta los registros de la tabla que contienen números.

**[Cos](functions/function-trig.md)** : devuelve el coseno de un ángulo especificado en radianes.

**[Cot](functions/function-trig.md)** : devuelve la cotangente de un ángulo especificado en radianes.

**[CountA](functions/function-table-counts.md)** : cuenta los registros de la tabla que no están [vacíos](functions/function-isblank-isempty.md).

**[CountIf](functions/function-table-counts.md)** : cuenta los registros de la tabla que cumplen una condición.  

**[CountRows](functions/function-table-counts.md)** : cuenta los registros de la tabla.   

## <a name="d"></a>D
**[DataSourceInfo](functions/function-datasourceinfo.md)** : proporciona información sobre un origen de datos.

**[Date](functions/function-date-time.md)** : devuelve un valor de fecha y hora en función de los valores **Year**, **Month** y **Day**.  

**[DateAdd](functions/function-dateadd-datediff.md)** : agrega días, meses, trimestres o años a un valor de fecha y hora.

**[DateDiff](functions/function-dateadd-datediff.md)** : resta dos valores de fecha y muestra el resultado en días, meses, trimestres o años.

**[DateTimeValue](functions/function-datevalue-timevalue.md)** : convierte una cadena de fecha y hora en un valor de fecha y hora.

**[DateValue](functions/function-datevalue-timevalue.md)** : convierte una cadena de fecha en un valor de fecha y hora.

**[Day](functions/function-datetime-parts.md)** : recupera la parte de día de un valor de fecha y hora.  

**[Defaults](functions/function-defaults.md)** : devuelve los valores predeterminados para un origen de datos.

**[Degrees](functions/function-trig.md)** : convierte radianes en grados.

**[Disable](functions/function-enable-disable.md)** : deshabilita una señal, como **[Location](functions/signals.md)** para leer el GPS.

**[Distinct](functions/function-distinct.md)** : resume los registros de una tabla, para lo que quita los duplicados.  

**[Download](functions/function-param.md)** : descarga un archivo de la Web en el dispositivo local.

**[DropColumns](functions/function-table-shaping.md)** : devuelve una tabla a la que se han quitado una o varias columnas.

## <a name="e"></a>E
**[EditForm](functions/function-form.md)** : restablece un control de formulario para la edición de un elemento.

**[Enable](functions/function-enable-disable.md)** : habilita una señal, como **[Location](functions/signals.md)** para leer el GPS.

**[EndsWith](functions/function-startswith.md)** : comprueba si una cadena de texto termina con otra cadena de texto.

**[Errors](functions/function-errors.md)** : proporciona información de error para los cambios anteriores en un origen de datos.

**[EncodeUrl](functions/function-encode-decode.md)** : codifica caracteres especiales mediante la codificación de la dirección URL.

**[Exit](functions/function-exit.md)** : sale de la aplicación que se está ejecutando.

**[Exp](functions/function-numericals.md)** : devuelve *e* elevado a una potencia.

## <a name="f"></a>F
**[Filter](functions/function-filter-lookup.md)** : devuelve una tabla filtrada en función de uno o varios criterios.

**[Find](functions/function-find.md)** : comprueba si una cadena aparece dentro de otra y devuelve la ubicación.

**[First](functions/function-first-last.md)** : devuelve el primer registro de una tabla.

**[FirstN](functions/function-first-last.md)** : devuelve el primer conjunto de registros (registros N) de una tabla.

**[ForAll](functions/function-forall.md)** : calcula valores y realiza acciones para todos los registros de una tabla.

## <a name="g"></a>N
**[GroupBy](functions/function-groupby.md)** : devuelve una tabla con los registros agrupados.

**[GUID](functions/function-guid.md)** : convierte una cadena de GUID en un valor GUID o crea un valor GUID.

## <a name="h"></a>H
**[HashTags](functions/function-hashtags.md)** : extrae los hashtags (#cadenas) de una cadena.

**[Hour](functions/function-datetime-parts.md)** : devuelve la parte de hora de un valor de fecha y hora.

## <a name="i"></a>I
**[If](functions/function-if.md)** : devuelve un valor si una condición es true y otro valor si no lo es. 

**[IfError](functions/function-iferror.md)** : detecta errores y proporciona un valor alternativo o lleva a cabo una acción. 

**[IsBlank](functions/function-isblank-isempty.md)** : busca un valor [en blanco](functions/function-isblank-isempty.md).

**[IsEmpty](functions/function-isblank-isempty.md)** : busca una tabla vacía.

**[IsMatch](functions/function-ismatch.md)** : comprueba una cadena con un patrón.  Se pueden usar expresiones regulares.

**[IsNumeric](functions/function-isnumeric.md)** : busca un valor numérico.

**[IsToday](functions/function-now-today-istoday.md)** : comprueba si un valor de fecha y hora coincide con algún momento del día actual.

**[IsType](functions/function-astype-istype.md)** : comprueba si una referencia del registro hace referencia a un tipo de entidad específico.

## <a name="j"></a>J
**[JSON](functions/function-json.md)** : genera una cadena de texto JSON para una tabla, un registro o un valor.

## <a name="l"></a>L
**[Language](functions/function-language.md)** : devuelve la etiqueta de idioma del usuario actual.

**[Last](functions/function-first-last.md)** : devuelve el último registro de una tabla.

**[LastN](functions/function-first-last.md)** : devuelve el último conjunto de registros (registros N) de una tabla.

**[Launch](functions/function-param.md)** : inicia una dirección web o una aplicación.

**[Left](functions/function-left-mid-right.md)** : devuelve la parte del extremo izquierdo de una cadena.

**[Len](functions/function-len.md)** : devuelve la longitud de una cadena.

**[Ln](functions/function-numericals.md)** : devuelve el logaritmo natural.

**[LoadData](functions/function-savedata-loaddata.md)** : carga una recopilación desde el almacenamiento de un dispositivo local.

**[Location](functions/signals.md)** : devuelve la ubicación como una coordinada de mapa mediante el sistema de posicionamiento global (GPS) y otra información.

**[LookUp](functions/function-filter-lookup.md)** : busca un único registro en una tabla en función de uno o varios criterios.

**[Lower](functions/function-lower-upper-proper.md)** : convierte todas las letras de una cadena de texto en minúsculas.

## <a name="m"></a>M
**[Match](functions/function-ismatch.md)** : extrae una subcadena basada en un patrón.  Se pueden usar expresiones regulares.

**[MatchAll](functions/function-ismatch.md)** : extrae varias subcadenas basadas en un patrón.  Se pueden usar expresiones regulares.

**[Max](functions/function-aggregates.md)** : valor máximo de una expresión de tabla o un conjunto de argumentos.

**[Mid](functions/function-left-mid-right.md)** : devuelve la parte media de una cadena.

**[Min](functions/function-aggregates.md)** : valor mínimo de una expresión de tabla o un conjunto de argumentos.

**[Minute](functions/function-datetime-parts.md)** : recupera la parte de minuto de un valor de fecha y hora.  

**[Mod](functions/function-mod.md)** : devuelve el resto después de que un dividendo se divida entre un divisor.

**[Month](functions/function-datetime-parts.md)** : recupera la parte de mes de un valor de fecha y hora.

## <a name="n"></a>N
**[Navigate](functions/function-navigate.md)** : cambia la pantalla que se muestra.

**[NewForm](functions/function-form.md)** : restablece un control de formulario para la creación de un elemento.

**[Not](functions/function-logicals.md)** : lógica booleana NO.  Devuelve **true** si su argumento es **false** y devuelve **false** si su argumento es **true**.  También puede usar el [operador **!** ](functions/operators.md).

**[Notify](functions/function-showerror.md)** : muestra un mensaje de pancarta al usuario.

**[Now](functions/function-now-today-istoday.md)** : devuelve el valor de fecha y hora actual.

## <a name="o"></a>O
**[Or](functions/function-logicals.md)** : lógica booleana O.  Devuelve **true** si alguno de sus argumentos es **true**.  También puede usar el [operador **||** ](functions/operators.md).

## <a name="p"></a>P
**[Param](functions/function-param.md)** : proporciona acceso a los parámetros pasados a la aplicación al abrirla el usuario.

**[Parent](functions/operators.md#parent-operator)** : proporciona acceso a las propiedades de un control contenedor.

**[Patch](functions/function-patch.md)** : modifica o crea un registro en un origen de datos, o bien combina registros fuera de un origen de datos.

**[Pi](functions/function-trig.md)** : devuelve el número &pi;.

**[PlainText](functions/function-encode-decode.md)** : quita las etiquetas HTML y XML de una cadena.

**[Power](functions/function-numericals.md)** : devuelve un número elevado a una potencia.  También puede usar el [operador **^** ](functions/operators.md).

**[Proper](functions/function-lower-upper-proper.md)** : convierte la primera letra de cada palabra de una cadena en mayúsculas y el resto en minúsculas.

## <a name="r"></a>R
**[Radians](functions/function-trig.md)** : convierte grados en radianes.

**[Rand](functions/function-rand.md)** : devuelve un número pseudoaleatorio.

**[Refresh](functions/function-refresh.md)** : actualiza los registros de un origen de datos.

**[Relate](functions/function-relate-unrelate.md)** : relaciona los registros de dos entidades mediante una relación de uno a varios o de varios a varios.

**[Remove](functions/function-remove-removeif.md)** : quita uno o más registros específicos de un origen de datos.

**[RemoveIf](functions/function-remove-removeif.md)** : elimina los registros de un origen de datos en función de una condición.

**[RenameColumns](functions/function-table-shaping.md)** : cambia el nombre de las columnas de una tabla.

**[Replace](functions/function-replace-substitute.md)** : reemplaza parte de una cadena por otra cadena, por posición inicial de la cadena.

**[Reset](functions/function-reset.md)** : restablece un control de entrada al valor predeterminado, descartando cualquier modificación del usuario.

**[ResetForm](functions/function-form.md)** : restablece un control de formulario para la edición de un elemento existente.

**[Revert](functions/function-revert.md)** : recarga y borra errores para los registros de un origen de datos.

**[RGBA](functions/function-colors.md)** : devuelve un valor de color para un conjunto de componentes rojo, verde, azul y alfabético.

**[Right](functions/function-left-mid-right.md)** : devuelve la parte del extremo derecho de una cadena.

**[Round](functions/function-round.md)** : redondea al número más cercano.

**[RoundDown](functions/function-round.md)** : redondea hacia abajo al número anterior más grande.

**[RoundUp](functions/function-round.md)** : redondea hacia arriba al siguiente número más pequeño.

## <a name="s"></a>S
**[Savedata](functions/function-savedata-loaddata.md)** : guarda una colección en el almacenamiento de un dispositivo local.

**[Search](functions/function-filter-lookup.md)** : busca registros en una tabla que contengan una cadena en una de sus columnas.  

**[Second](functions/function-datetime-parts.md)** : recupera la parte de segundo de un valor de fecha y hora.

**[Select](functions/function-select.md)** : simula una acción de selección en un control, lo que provoca la evaluación de la fórmula **OnSelect**.

**[Set](functions/function-set.md)** : establece el valor de una variable global.

**[SetFocus](functions/function-setfocus.md)** : mueve el foco de entrada a un control específico.

**[SetPropertry](functions/function-setproperty.md)** : simula interacciones con controles de entrada.

**[ShowColumns](functions/function-table-shaping.md)** : devuelve una tabla exclusivamente con las columnas seleccionadas.

**[Shuffle](functions/function-shuffle.md)** : reordena aleatoriamente los registros de una tabla.

**[Sin](functions/function-trig.md)** : devuelve el seno de un ángulo especificado en radianes.

**[Sort](functions/function-sort.md)** : devuelve una tabla ordenada en función de una fórmula.

**[SortByColumns](functions/function-sort.md)** : devuelve una tabla ordenada en función de una o varias columnas.

**[Split](functions/function-split.md)** : divide una cadena de texto en una tabla de subcadenas.

**[Sqrt](functions/function-numericals.md)** : devuelve la raíz cuadrada de un número.

**[StartsWith](functions/function-startswith.md)** : comprueba si una cadena de texto comienza con otra cadena de texto.

**[StdevP](functions/function-aggregates.md)** : devuelve la desviación estándar de sus argumentos.  

**[Substitute](functions/function-replace-substitute.md)** : reemplaza parte de una cadena por otra cadena, por coincidencia de cadenas.

**[SubmitForm](functions/function-form.md)** : guarda el elemento en un control de formulario para el origen de datos.

**[Sum](functions/function-aggregates.md)** : calcula la suma de una expresión de tabla o un conjunto de argumentos.  

**[Switch](functions/function-if.md)** : busca la coincidencia con un conjunto de valores y luego evalúa una fórmula correspondiente.

## <a name="t"></a>T
**[Table](functions/function-table.md)** : crea una tabla temporal.  

**[Tan](functions/function-trig.md)** : devuelve la tangente de un ángulo especificado en radianes.

**[Text](functions/function-text.md)** : convierte cualquier valor y da formato de cadena de texto a un número o valor de fecha y hora.

**[ThisItem](functions/operators.md#thisitem-operator)** : cuando se está en una galería o un formulario, devuelve los datos para el elemento actual del contenedor.

**[Time](functions/function-date-time.md)** : devuelve un valor de fecha y hora, en función de los valores **Hour**, **Minute** y **Second**.  

**[TimeValue](functions/function-datevalue-timevalue.md)** : convierte una cadena de hora en un valor de fecha y hora.

**[TimeZoneOffset](functions/function-dateadd-datediff.md)** : devuelve la diferencia entre la hora UTC y la hora local del usuario en minutos.

**[Today](functions/function-now-today-istoday.md)** : devuelve el valor de fecha y hora actual.

**[Trace](functions/function-trace.md)** : proporciona información adicional en los resultados de las pruebas.

**[Trim](functions/function-trim.md)** : quita los espacios adicionales de los extremos y el interior de una cadena de texto.

**[TrimEnds](functions/function-trim.md)** : quita los espacios adicionales únicamente de los extremos de una cadena de texto.

## <a name="u"></a>U
**[Ungroup](functions/function-groupby.md)** : quita una agrupación.

**[Unrelate](functions/function-relate-unrelate.md)** : anula la relación de los registros de dos entidades de una relación de uno a varios o de varios a varios.

**[Update](functions/function-update-updateif.md)** : reemplaza un registro en un origen de datos.

**[UpdateContext](functions/function-updatecontext.md)** : establece el valor de una o varias [variables de contexto](working-with-variables.md#use-a-context-variable) de la pantalla actual.

**[UpdateIf](functions/function-update-updateif.md)** : modifica un conjunto de registros en un origen de datos en función de una condición.

**[Upper](functions/function-lower-upper-proper.md)** : convierte todas las letras de una cadena de texto en mayúsculas.

**[User](functions/function-user.md)** : devuelve información sobre el usuario actual.

## <a name="v"></a>V
**[Validate](functions/function-validate.md)** : comprueba si el valor de una sola columna o un registro completo es válido para un origen de datos.

**[Value](functions/function-value.md)** : convierte una cadena en un número.

**[VarP](functions/function-aggregates.md)** : devuelve la varianza de sus argumentos.  

**[ViewForm](functions/function-form.md)** : restablece un control de formulario para la visualización de un elemento existente.

## <a name="w"></a>M
**[Weekday](functions/function-datetime-parts.md)** : recupera la parte de día de la semana de un valor de fecha y hora.

**[With](functions/function-with.md)** : calcula valores y realiza acciones para un único registro, incluidos los registros insertados de valores con nombre.

## <a name="y"></a>Y
**[Year](functions/function-datetime-parts.md)** : recupera la parte de año de un valor de fecha y hora.  

