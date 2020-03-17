---
title: Operadores e identificadores | Microsoft Docs
description: Información de referencia de los operadores y los identificadores de Power Apps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c7f982f4d2eca1b097a312f74aff70063bf3396
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79212685"
ms.PowerAppsDecimalTransform: true
---
# <a name="operators-and-identifiers-in-power-apps"></a>Operadores e identificadores en Power apps

Algunos de estos operadores dependen del idioma del autor.  Para más información, consulte [Aplicaciones globales](../global-apps.md).


|                               Símbolo                                |                        Tipo                         |                                                                                    Sintaxis                                                                                    |                                                                                                                           Descripción                                                                                                                            |
|---------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                **.**                                |                  Selector de propiedad                  |                                                               **Slider1.Value<br>Color.Red<br>Acceleration.X**                                                               |                                               Extrae una propiedad de una [tabla](../working-with-tables.md), control, [señal](signals.md) o enumeración.  Para lograr compatibilidad con versiones anteriores, también se puede usar **!** .                                                |
| **,**<br>[[dependiente del idioma](../global-apps.md)]  |                  Separador decimal                  |                                                             **1.23**                                                           |                                                                              Separador entre las partes entera y fraccionaria de un número. El carácter depende del idioma.                                                                              |
|                               **( )**                               |                     Paréntesis                     |                                                               **Filtrar(T; A &lt; 10)**<br><br>**(1 + 2) \* 3**                                                               |                                                                                           Aplica el orden de prioridad y agrupa las subexpresiones en una expresión mayor                                                                                           |
|                                **+**                                |                Operadores aritméticos                 |                                                                                  **1 + 2**                                                                                   |                                                                                                                             Suma                                                                                                                             |
|                                **-**                                |                       &nbsp;                        |                                                                                  **2 - 1**                                                                                   |                                                                                                                       Resta y signo                                                                                                                       |
|                              *                               |                       &nbsp;                        |                                                                                  **2 \* 3**                                                                                  |                                                                                                                          Multiplicación                                                                                                                          |
|                                **/**                                |                       &nbsp;                        |                                                                                  **2 / 3**                                                                                   |                                                                                                   División (consulte también la función **[Mod](function-mod.md)**)                                                                                                    |
|                                **^**                                |                       &nbsp;                        |                                                                                  **2 ^ 3**                                                                                   |                                                                                          Exponenciación, equivalente a la función **[Power](function-numericals.md)**                                                                                          |
|                                **%**                                |                       &nbsp;                        |                                                                                   **20 %**                                                                                    |                                                                                                         Porcentaje (equivalente a &quot;\* 1/100&quot;)                                                                                                          |
|                                **=**                                |                Operadores de comparación                 |                                                                               **Precio = 100**                                                                                |                                                                                                                             Igual a                                                                                                                              |
|                              **&gt;**                               |                       &nbsp;                        |                                                                              **Precio &gt; 100**                                                                              |                                                                                                                           Mayor que                                                                                                                           |
|                              **&gt;=**                              |                       &nbsp;                        |                                                                             **Precio &gt;= 100**                                                                              |                                                                                                                     Mayor o igual que                                                                                                                     |
|                              **&lt;**                               |                       &nbsp;                        |                                                                              **Precio &lt; 100**                                                                              |                                                                                                                            Menos de                                                                                                                             |
|                              **&lt;=**                              |                       &nbsp;                        |                                                                             **Precio &lt;= 100**                                                                              |                                                                                                                      Menor o igual que                                                                                                                       |
|                            **&lt;&gt;**                             |                       &nbsp;                        |                                                                            **Precio &lt;&gt; 100**                                                                            |                                                                                                                           No igual a                                                                                                                           |
|                              **&amp;**                              |            Operador de concatenación de cadenas            |                                                      **&quot;Hello&quot; &amp; &quot; &quot; &amp; &quot;World&quot;**                                                       |                                                                                                             Hace que varias cadenas aparezcan continuas                                                                                                             |
|                      **&amp;&amp;** o **And**                      |                  Operadores lógicos                  |                                       **Precio &lt; 100 &amp;&amp; Slider1.Value = 20**<br>o **Price &lt; 100 And Slider1.Value = 20**                                       |                                                                                         Conjunción lógica, equivalente a la función **[Y](function-logicals.md)**                                                                                          |
|                     **&#124;&#124;** u **Or**                      |                       &nbsp;                        |                                        **Price &lt; 100 &#124;&#124; Slider1.Value = 20** o **Price &lt; 100 Or Slider1.Value = 20**                                        |                                                                                          Disyunción lógica, equivalente a la función **[Or](function-logicals.md)**                                                                                          |
|                          **!** o **Not**                           |                       &nbsp;                        |                                                              **!(Price &lt; 100)** o **Not (Price &lt; 100)**                                                               |                                                                                           Negación lógica, equivalente a la función **[No](function-logicals.md)**                                                                                           |
|                             **exactin**                             |  [Operadores de pertenencia](#in-and-exactin-operators)  |                                                                   **Gallery1.Selected exactin SavedItems**                                                                   |                                                                                       Perteneciente a una [colección](../working-with-data-sources.md#collections) o una tabla                                                                                        |
|                             **exactin**                             |                       &nbsp;                        |                                           **&quot;Windows&quot; exactin "Para mostrar ventanas en el sistema de operativo Windows..."**                                            |                                                                                                                 Prueba de subcadena (distingue mayúsculas de minúsculas)                                                                                                                  |
|                               **in**                                |                       &nbsp;                        |                                                                     **Gallery1.Selected in SavedItems**                                                                      |                                                                                                               Perteneciente a una colección o una tabla                                                                                                               |
|                               **in**                                |                       &nbsp;                        |                                                      **&quot;El&quot; en &quot;El teclado y el monitor...&quot;**                                                      |                                                                                                                Prueba de subcadena (no distingue mayúsculas de minúsculas)                                                                                                                 |
|                                **@**                                | [Operador de desambiguación](#disambiguation-operator) |                                                                           **MyTable[@fieldname]**                                                                            |                                                                                                                       Desambiguación de campo                                                                                                                       |
|                                **@**                                |                       &nbsp;                        |                                                                              **[@MyVariable]**                                                                               |                                                                                                                      Desambiguación global                                                                                                                       |
| **;**<br>[[dependiente del idioma](../global-apps.md)]  |                   Separador de lista                    | **If( X < 10; "Bajo"; "Bien" )**<br>**{ X: 12; Y: 32 }**<br>**[ 1; 2; 3 ]** | Separa: <ul><li>argumentos en llamadas a funciones</li><li>campos en un [registro](../working-with-tables.md#elements-of-a-table)</li><li>registros de una [tabla](../working-with-tables.md#inline-value-tables)</li></ul> Este carácter depende del idioma. |
| **;;**<br>[[dependiente del idioma](../global-apps.md)] |                  Encadenamiento de fórmulas                   |                                     **Collect(T; A);; Navigate(S1; &quot;&quot;)**                                     |                                                                          Separar invocaciones de funciones en las propiedades del comportamiento. El operador de encadenamiento depende del lenguaje.                                                                          |
|                             **Parent**                              |         [Operador Parent](#parent-operator)         |                                                                               **Parent.Fill**                                                                                |                                                                                                           Acceso a las propiedades de un contenedor de control                                                                                                            |
|                            **ThisItem**                             |       [Operador ThisItem](#thisitem-operator)       |                                                                            **ThisItem.FirstName**                                                                            |                                                                                                          Acceder a los campos de una galería o un control de formulario                                                                                                           |

## <a name="in-and-exactin-operators"></a>operadores in y exactin
Los operadores **[in](operators.md#in-and-exactin-operators)** y **[exactin](operators.md#in-and-exactin-operators)** se pueden usar para buscar una cadena en un [origen de datos](../working-with-data-sources.md), como una colección o una tabla importada. El operador **[in](operators.md#in-and-exactin-operators)** identifica coincidencias, independientemente del caso, mientras que **[exactin](operators.md#in-and-exactin-operators)** identifica coincidencias solo si coinciden las mayúsculas. Aquí se muestra un ejemplo:

1. Cree o importe una colección denominada **Inventario** y muéstrela en una galería, como describe el primer procedimiento de [Show images and text in a gallery, including gallery selection, sort, and filter](../show-images-text-gallery-sort-filter.md) (Mostrar texto e imágenes de una galería, incluidos la selección, ordenación y filtro de la galería).
2. Establezca la propiedad **[Elementos](../controls/properties-core.md)** de la galería en esta fórmula:
   <br>**Filter(Inventory; "E" in ProductName)**

    La galería muestra todos los productos, excepto Callisto, porque el nombre de ese producto es el único que no contiene la letra que ha especificado.
3. Cambie la propiedad **[Elementos](../controls/properties-core.md)** de la galería a esta fórmula:
   <br>**Filter(Inventory; "E" exactin ProductName)**

    La galería muestra solo Europa, porque es la única palabra que contiene la letra que ha especificado con el uso de mayúsculas y minúsculas que ha especificado.

## <a name="thisitem-operator"></a>Operador ThisItem
Puede mostrar datos en los controles **[Galería](../controls/control-gallery.md)**, **[Formulario de edición](../controls/control-form-detail.md)** o **[Formulario de presentación](../controls/control-form-detail.md)** enlazándolos a una tabla o una colección.  Estos controles son un contenedor para otros controles y tarjetas.  Todas las tarjetas o controles del contenedor pueden acceder a los datos enlazados a través del operador **[ThisItem](operators.md#thisitem-operator)**.   

Use el operador **[ThisItem](operators.md#thisitem-operator)** para especificar la [columna](../working-with-tables.md#columns) de datos que se va a mostrar en cada tarjeta o control del control exterior. Por ejemplo, el operador de la galería de productos de [Show images and text in a gallery, including gallery selection, sort, and filter](../show-images-text-gallery-sort-filter.md) (Mostrar texto e imágenes de una galería, incluidos la selección, ordenación y filtro de la galería) especificaba que el control de imagen mostraba el diseño del producto, la etiqueta superior mostraba el nombre del producto y la etiqueta inferior mostraba el número de unidades en existencias.

En el caso de las galerías anidadas, **[ThisItem](operators.md#thisitem-operator)** hace referencia a los elementos de la galería más interna. Suponiendo que los campos de fila de las galerías interna y externa no están en conflicto, también puede utilizar los nombres de campo (columna) no completos directamente. Este enfoque permite que las reglas de una galería interna hagan referencia a elementos de una galería externa.

## <a name="parent-operator"></a>Operador Parent
Algunos controles hospedan otros controles. Por ejemplo, los controles **[Pantalla](../controls/control-screen.md)**, **[Galería](../controls/control-gallery.md)**, **[Tarjeta](../controls/control-card.md)**, **[Formulario de edición](../controls/control-form-detail.md)** y **[Formulario de presentación](../controls/control-form-detail.md)** son contenedores de controles. Al control que hospeda se le denomina el "control primario" de los controles que contiene.

Se puede hacer referencia a cualquier control de Power apps por su nombre desde cualquier lugar dentro de la aplicación. **Screen1** puede ser el nombre de una pantalla de una aplicación. Para recuperar el color de fondo de esta pantalla, puede usar **Screen1.Fill**.

Los controles de esta pantalla tienen otra opción. Pueden utilizar una referencia relativa: **Parent.Fill**. El operador **[Parent](operators.md#parent-operator)** hace referencia al control que hospeda este control, y que hace que todas sus propiedades estén disponibles. **[Parent](operators.md#parent-operator)** resulta muy útil, ya que no depende del nombre del control. Puede copiar y pegar un control contenedor sin necesidad de ajustar ninguna de las referencia del contenedor. Este operador también hace que la relación entre los controles primarios y secundarios sea más clara al leer fórmulas.

## <a name="identifier-names"></a>Nombres de identificador

Los nombres de variables, orígenes de datos, columnas y otros objetos pueden contener cualquier [Unicode](https://en.wikipedia.org/wiki/Unicode).

Use comillas simples para un nombre que contenga un espacio u otro carácter especial.  Use dos comillas simples juntas para representar una comilla simple en el nombre.  Los nombres que no contienen caracteres especiales no requieren comillas simples.

Estos son algunos nombres de columna de ejemplo que pueden encontrarse en una tabla y cómo se representan en una fórmula:

| Nombre de columna en una base de datos   | Referencia de columna en una fórmula |
|-----------------------------|-------------------------------|
| SimpleName                  | ```SimpleName``` |
| NameWith123Numbers          | ```NameWith123Numbers``` |
| Nombre con espacios            | ```'Name with spaces'``` |
| Nombre con comillas "dobles"   | ```'Name with "double" quotes'``` |
| Nombre con comillas simples   | ```'Name with ''single'' quotes'``` |
| Nombre con un signo @ arroba      | ```'Name with an @ at sign'``` |

Las comillas dobles se utilizan para [designar cadenas de texto](data-types.md#embedded-text).  

## <a name="display-names-and-logical-names"></a>Nombres para mostrar y nombres lógicos
Algunos orígenes de datos como SharePoint y Common Data Service tienen dos nombres diferentes para hacer referencia a la misma tabla o columna de datos:

* **Nombre lógico** : un nombre que se garantiza que es único, no cambia después de su creación, normalmente no permite espacios u otros caracteres especiales y no se localiza en idiomas diferentes.  Como resultado, el nombre puede ser un poco críptico.  Estos nombres los utilizan los desarrolladores profesionales.  Por ejemplo **cra3a_customfield**.  También se puede hacer referencia a este nombre como **nombre de esquema** o simplemente **nombre**.

* **Nombre para mostrar** : un nombre que es descriptivo y está pensado para que lo vean los usuarios finales.  Este nombre puede no ser único, puede cambiar con el tiempo, puede contener espacios y cualquier carácter Unicode, y puede estar localizado en distintos idiomas.  Según el ejemplo anterior, el nombre para mostrar puede ser un **campo personalizado** con un espacio entre las palabras.
 
Dado que los nombres para mostrar son más fáciles de entender, las aplicaciones de lienzo los sugerirán como opciones y no sugerirán nombres lógicos.  Aunque no se sugieren nombres lógicos, todavía se pueden usar si se escriben directamente.

Por ejemplo, Imagine que ha agregado un **campo personalizado** a una entidad en Common Data Service.  El sistema le asignará un nombre lógico, que solo podrá modificar al crear el campo.  El resultado tendría un aspecto similar al siguiente:

> [!div class="mx-imgBorder"]  
> ![entidad accounts con el campo personalizado agregado, que muestra el nombre para mostrar "Custom Field" y el nombre lógico "cr5e3_customfield"](media/operators/customfield_portal.png)

Al crear una referencia a un campo de cuentas, se realizará la sugerencia para usar **"campo personalizado"** , ya que este es el nombre para mostrar.  Tenga en cuenta que se deben usar comillas simples porque este nombre tiene un espacio en ella:

> [!div class="mx-imgBorder"]  
> ![barra de fórmulas de Studio que muestra sugerencias para nombres de campo de cuentas con el nombre para mostrar "campo personalizado" resaltado](media/operators/customfield_suggest_display.png)

Después de seleccionar la sugerencia, se muestra "campo personalizado" en la barra de fórmulas y se recuperan los datos: 

> [!div class="mx-imgBorder"]  
> ![barra de fórmulas de Studio que muestra el uso del nombre para mostrar "campo personalizado" para el campo](media/operators/customfield_display.png)

Aunque no se recomienda, también podríamos usar el nombre lógico para este campo.  Esto hará que se recuperen los mismos datos.  Tenga en cuenta que no se requieren comillas simples ya que este nombre no contiene espacios ni caracteres especiales:

> [!div class="mx-imgBorder"]  
> ![barra de fórmulas de Studio que muestra el uso del nombre lógico cr5e3_customfield para el campo](media/operators/customfield_logical.png)

En segundo plano, se mantiene una asignación entre los nombres para mostrar que se muestran en las fórmulas y los nombres lógicos subyacentes.  Dado que los nombres lógicos deben usarse para interactuar con el origen de datos, esta asignación se usa para convertir automáticamente el nombre para mostrar actual al nombre lógico y eso es lo que se muestra en el tráfico de red.  Esta asignación también se utiliza para volver a convertir a nombres lógicos con el fin de cambiar a nuevos nombres para mostrar, por ejemplo, si un nombre para mostrar cambia o un fabricante en otro idioma edita la aplicación.

> [!NOTE] 
> Los nombres lógicos no se traducen al mover una aplicación entre entornos.  Por Common Data Service entidad del sistema y los nombres de campo, esto no debería ser un problema, ya que los nombres lógicos son coherentes en todos los entornos.  Sin embargo, los campos personalizados, como **cra3a_customfield** en este ejemplo anterior, pueden tener un prefijo de entorno diferente (en este caso,**cra3a** ).  Se prefieren los nombres para mostrar, ya que se pueden comparar con los nombres para mostrar del nuevo entorno. 

## <a name="name-disambiguation"></a>Desambiguación de nombres
Dado que los nombres para mostrar no son únicos, el mismo nombre para mostrar puede aparecer más de una vez en la misma entidad.  Cuando esto sucede, el nombre lógico se agregará al final del nombre para mostrar entre paréntesis para uno o más de los nombres en conflicto.  Al basarse en el ejemplo anterior, si había un segundo campo con el mismo nombre para mostrar del **campo personalizado** con un nombre lógico de **cra3a_customfieldalt** , se mostrarán las sugerencias siguientes:

> [!div class="mx-imgBorder"]  
> ![barra de fórmulas de Studio que muestra el uso del nombre lógico cr5e3_customfieldalt para eliminar la ambigüedad de las dos versiones de "campo personalizado"](media/operators/customfield_suggest_alt.png)

Las cadenas de desambiguación de nombres se agregan en otras situaciones en las que se producen conflictos de nombres, como los nombres de entidades, conjuntos de opciones y otros elementos de Common Data Service. 

## <a name="disambiguation-operator"></a>Operador de desambiguación
Algunas funciones crean [ámbitos de registro](../working-with-tables.md#record-scope) para acceder a los campos de la tabla mientras se procesa cada registro, como **Filter**, **AddColumns** y **Sum**.  Los nombres de campo agregados con el ámbito de registro anulan los mismos nombres de los restantes lugares de la aplicación.  Cuando esto sucede, para acceder a los valores desde fuera del ámbito de registro hay que utilizar el operador de desambiguación **@**:

* Para acceder a valores de ámbitos de registro anidados, use el operador **@** con el nombre de la tabla en la que opera mediante este modelo:<br>_Table_**[@**_FieldName_**]**
* Para acceder a valores globales, como orígenes de datos, colecciones y variables de contexto, use el modelo **[@**_ObjectName_**]** (sin designación de tabla).

Para obtener más información y ejemplos, vea los [ámbitos de registro](../working-with-tables.md#record-scope).

