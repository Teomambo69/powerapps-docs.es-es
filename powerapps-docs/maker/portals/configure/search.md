---
title: Búsqueda global en portales de PowerApps | MicrosoftDocs
description: Aprenda cómo funciona la búsqueda global en un portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da142a452e903b890b1b395262771228e245140c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761092"
---
# <a name="search"></a>Search

En portales de PowerApps, puede buscar los registros a través de varias entidades mediante búsqueda por relevancia o búsqueda categorizada. También puede buscar en los registros de listas de la entidad con funcionalidad de búsqueda de la lista de entidades. 

La funcionalidad de búsqueda de lista de entidades en el portal usa FetchXML en el backend para buscar las columnas definidas en la lista de entidades y luego mostrar los resultados. 

La búsqueda global usa un índice de búsqueda externo que se base en Lucene.Net y se usa para buscar en las entidades y en varios campos de forma inmediata.

## <a name="global-search"></a>Búsqueda global

La búsqueda global de portales le permite buscar los registros a través de varias entidades. También le permite buscar en múltiples columnas y configurar qué columnas de una entidad se pueden buscar.

Entre las ventajas de la búsqueda global está su capacidad para:
- Encontrar coincidencias con cualquier palabra en el término de búsqueda en cualquier campo de la entidad. Las coincidencias pueden incluir palabras de inflexión como secuencia, secuenciando, o secuenciado.
- Devolver resultados de todas las entidades que permiten búsquedas en una sola lista ordenada por relevancia, en función de factores como número de palabras que coinciden o su proximidad mutua en el texto.
- Resaltar coincidencias en la lista de resultados.
- Proporcionar opciones de faceta que se pueden utilizar para filtrar los resultados de búsqueda aún más.

En Búsqueda por relevancia, cuanto mejor sea la correspondencia, más alta aparecerá en los resultados. Una coincidencia tiene una relevancia mayor si se encuentran más palabras del término de búsqueda en gran proximidad mutua. Cuanto más pequeña sea la cantidad de texto donde se encuentran las palabras de búsqueda, más alta será la relevancia. Por ejemplo, si encuentra las palabras de búsqueda en un nombre de compañía y una dirección, podría ser una coincidencia mejor que las mismas palabras se encuentren en un artículo grande, muy alejadas entre sí. Como los resultados se devuelven en una sola lista, puede ver una combinación de registros mostrados uno tras otro, con los trabajos coincidentes resaltados. 

Las secciones siguientes detallan cómo funciona la búsqueda global en portales de PowerApps y describen varias opciones de configuración disponibles.

## <a name="entities-searchable-in-portal-global-search"></a>Entidades de búsqueda en búsqueda global de portal

Las siguientes entidades se pueden buscar en un sitio web del portal siempre que se hayan instalado los paquetes de solución adecuados y se haya agregado la búsqueda a un portal. Las columnas que están indexadas consistirán en las columnas que se encuentran en la vista búsqueda, que se pueden personalizar.  Cada entidad en la lista tiene su conjunto predeterminado de atributos indexados como se detalla aquí:
- Artículo de conocimientos
    - También se pueden buscar notas y adjuntos de un artículo de conocimiento. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)
    - Solo se pueden realizar búsquedas en los artículos si están publicados y su campo Internal Only se establece en false.
- Blog 
- Entrada de blog 
- Publicar comentario 
- Foro 
- Entrada de foro 
- Hilo de foro 
- Idea 
- Comentarios de ideas 
- Foro de ideas 
- Archivo web 
    - También se pueden realizar búsquedas en el contenido de datos adjuntos de archivos web. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)
- Página web 
- Incidente 

> [!NOTE]
> Aparte de las entidades incluidas aquí, ninguna otra entidad puede estar habilitada para la búsqueda global en un portal.

## <a name="fields-searchable-in-global-search"></a>Campos que se pueden buscar en la búsqueda global

Todos los campos disponibles en la vista definida por la configuración del sitio Search / IndexQueryName para cualquier entidad se indexan en la búsqueda global y se pueden buscar. 

El valor predeterminado para el Search/IndexQueryName es “Portal Search”.

Si la vista no está disponible para una entidad, no se indexa, y los resultados no se muestran en búsqueda global.

> [!NOTE]
> Si cambia el valor de la configuración del sitio Search/IndexQueryName, debe desencadenar una reindexación manual de la compilación usando los pasos definidos en la sección [Reconstruir el índice de búsqueda completo](#rebuild-full-search-index).

## <a name="related-site-settings"></a>Configuración del sitio relacionada

La siguiente configuración del sitio está relacionada con la búsqueda global:

| Nombre    | Valor predeterminado     | Descripción       |
|-----------------------|--------------------|-------------|
| Búsqueda / Habilitado | Verdadero  | Un valor booleano que indica si la búsqueda está habilitada. Si establece su valor en falso, la búsqueda global en el portal se desactiva.<br>Si usa plantillas web listas para usar y desactiva esta opción, el cuadro de búsqueda no se mostrará en el encabezado ni en la página de búsqueda. Además, no se devuelven resultados incluso si se introduce la dirección URL directa de la página de búsqueda.  |
| Búsqueda/Filtros  | Contenido: adx_webpage; Eventos: adx_event, adx_eventschedule; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment; Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Ideas: adx_ideaforum, adx_idea, adx_ideacomment; Problemas: adx_issueforum, adx_issue, adx_issuecomment; Título de datos: incidente | Una recopilación de opciones de filtro del nombre lógico de búsqueda. Definir un valor aquí agregará opciones de filtro desplegable a la búsqueda global. Este valor debe tener la forma de pares nombre / valor, con nombre y valor separados por dos puntos, y pares separados por punto y coma. Por ejemplo: “Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment”.  |
| Buscar/IndexQueryName   | Búsqueda del portal  | El nombre de la vista del sistema usada por la consulta de búsqueda de portal para definir los campos de una entidad habilitada se indexan y se buscan.   |
| Búsqueda/Consulta  | +(@Query) _title:(@Query) _logicalname:adx_webpage\~0.9^0.2 -_logicalname:adx_webfile\~0.9 adx_partialurl:(@Query) _logicalname:adx_blogpost\~0.9^0.1 -_logicalname:adx_communityforumthread\~0.9   | Esta configuración agrega ponderaciones y filtros adicionales a la consulta que un usuario ingresa en el cuadro de búsqueda predeterminado que se muestra en el portal. En el valor predeterminado, @Query es el texto de la consulta escrito por un usuario.<br>Para obtener información sobre cómo modificar este valor, siga [Sintaxis de la consulta de Lucene](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html).<br>**Importante**: estas ponderaciones y filtros se aplican solo al cuadro de búsqueda que se proporciona en la página de búsqueda predeterminada del portal. Si usa una etiqueta líquida de búsqueda para crear su propia página de búsqueda, este valor no se aplica. |
| Buscar/lematizador  | Inglés    | El idioma utilizado por el algoritmo de la lematización de búsqueda de portal.   |
| Buscar/FacetedView  | True   | Habilita facetas en los resultados de la búsqueda. Cuando se establece en True, las facetas se mostrarán junto con los resultados en la página de búsqueda.  |
| Search/IndexNotesAttachments   | True    | Indica si se debe indexar el contenido de los datos adjuntos de las notas en artículos de Knowledge Base y archivos web. De forma predeterminada, se establece en Falso. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)    |
| Buscar/RecordTypeFacetsEntities  | Blogs: adx_blog, adx_blogpost; Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Ideas: adx_ideaforum, adx_idea; Downloads:annotation, adx_webfile    | Esto determina cómo se agrupan las entidades en la faceta tipo de registro en la página de búsqueda. Ésta es la configuración predeterminada. <br>“DisplayNameinRecordTypeFacet1: logicalnameofentity1, logicalnameofentity2; DisplayNameinRecordTypeFacet2: logicalnameofentity3, logicalnameofentity4” <br>El nombre para mostrar en aspecto del tipo de registro aparecerá en la interfaz de usuario. Este grupo de facetas combinará el resultado de las entidades definidas en la configuración.   |
| KnowledgeManagement/DisplayNotes | True   | Indica si indexar los datos adjuntos de los artículos de Knowledge Base. De forma predeterminada, se establece en Falso. |
|||

## <a name="related-content-snippets"></a>Fragmento de contenido relacionado

Los siguientes fragmentos de contenido están relacionados con la búsqueda global:

| Nombre   | Valor predeterminado  | Descripción   |
|------------------|-----------------|--------------------|
| Encabezado/Búsqueda/Etiqueta| Search| Este fragmento de contenido determina el texto de la marca de agua que se muestra en el cuadro de búsqueda en el encabezado del portal.<br>![Etiqueta de búsqueda](../media/search-label.png "Etiqueta de búsqueda")    |
| Encabezado/Búsqueda/Información sobre herramientas| Search  | Este fragmento de contenido determina el texto de información sobre herramientas que se muestra al pasar el cursor sobre el icono de búsqueda en el encabezado del portal.<br>![Información sobre herramientas de búsqueda](../media/search-tooltip.png "Información sobre herramientas de búsqueda")  |
| Búsqueda/Predeterminada/Texto de filtro| Todo   | Este fragmento de contenido determina el texto predeterminado que se muestra en la lista desplegable de filtros junto al cuadro de búsqueda.<br>![Texto de filtro de búsqueda](../media/search-filter-text.png "Texto de filtro de búsqueda")  |
| Búsqueda/Faceta/Todo| Todo| Este fragmento de contenido determina el texto predeterminado que se muestra para la "faceta de todos los registros" en la faceta "Tipo de registro" de la página de resultados de búsqueda.<br>![Todos los aspectos](../media/facet-all.png "Todos los aspectos") |
| Búsqueda/Faceta/Borrar restricciones   | Borrar todo  | Este fragmento de contenido determina la etiqueta del botón que restablece todas las facetas aplicadas en la página de resultados de búsqueda.<br>![Restablecer todos los aspectos](../media/facet-clear-all.png "Restablecer todos los aspectos") |
| BuscarFacetaDescargas   | Descargas   | Este fragmento de contenido determina la etiqueta que se muestra en los resultados de búsqueda de archivos adjuntos de anotaciones y archivos web en la faceta "Tipo de registro".<br>![Faceta de descarga](../media/facet-download.png "Faceta de descarga")|
| Búsqueda/Faceta/Menos    | Mostrar menos  | Este fragmento de contenido determina la etiqueta del botón que colapsa los resultados de faceta.<br>![Mostrar menos facetas](../media/facet-show-less.png "Mostrar menos facetas") |
| Búsqueda/Faceta/Fecha de modificación  | Fecha de modificación  | Este fragmento de contenido determina la etiqueta del encabezado que se muestra para la faceta de fecha modificada.<br>![Fecha de modificación](../media/facet-modified-date.png "Faceta de fecha modificada")   |
| Búsqueda/Faceta/Más   | Mostrar más  | Este fragmento de contenido determina la etiqueta del botón que expande los resultados de las facetas.<br>![Mostrar más facetas](../media/facet-show-more.png "Mostrar más facetas")  |
| Búsqueda/Faceta/Producto  | Productos | Este fragmento de contenido determina la etiqueta de la faceta Productos.<br>![Faceta de productos](../media/facet-product.png "Faceta de productos")  |
| Búsqueda/Faceta/Valoración   | Valoración   | Este fragmento de contenido determina la etiqueta de la faceta Clasificación.<br>![Faceta de calificaciones](../media/facet-rating.png "Faceta de calificaciones")  |
| Búsqueda/Faceta/Tipo de registro   | Tipo de registro | Este fragmento de contenido determina la etiqueta de la faceta clasificación.<br>![Faceta de tipo de registro](../media/facet-record-type.png "Faceta de tipo de registro")     |
| Búsqueda/Faceta/Criterio de ordenación/Valoración media de los usuarios | Valoraciones medias de los usuarios | Este fragmento de contenido determina la etiqueta que se muestra para la opción "Ordenar por calificaciones promedio del usuario" en la lista desplegable de clasificación en la página Resultados de la búsqueda.<br>![Ordenar la calificación por promedio](../media/sort-avg-user-rating.png "Ordenar la calificación por promedio")  |
| Búsqueda/Faceta/Criterio de ordenación/Relevancia| Importancia| Este fragmento de contenido determina la etiqueta que se muestra para la opción "Ordenar por relevancia" en la lista desplegable de clasificación en la página Resultados de la búsqueda.<br>![Ordenar por relevancia](../media/sort-relevance.png "Ordenar por relevancia")|
| Búsqueda/Faceta/Criterio de ordenación/Vistas| Número de visualizaciones| Este fragmento de contenido determina la etiqueta que se muestra para la opción "Ordenar por conteo de vista" en la lista desplegable de clasificación en la página Resultados de la búsqueda.<br>![Ordenar por recuento de vistas](../media/sort-view-count.png "Ordenar por recuento de vistas")|
|||

## <a name="entity-specific-handling"></a>Manejo específico de la entidad

- **Caso**: De forma predeterminada, sólo se pueden buscar los casos que se encuentren en el estado **Resuelto** con el campo **Publicar a web** como **Verdadero**. Este comportamiento se puede modificar actualizando la vista de búsqueda del portal de la entidad del caso y eliminando los filtros disponibles en la vista de búsqueda del portal. Sin embargo, cuando se elimina esta comprobación, es importante asegurarse de que la plantilla web de Customer Service - Case se modifique de forma adecuada, ya que esta plantilla web impide que todos los usuarios vean casos que están activos y que no están publicados en la web. Si la plantilla web no se modifica, los casos serán visibles en resultados de búsqueda. Sin embargo, cuando los selecciona, la página web de detalles del caso se muestra con el error permiso denegado.

- **Knowledge Base**: Solo se pueden buscar los artículos de conocimiento que se encuentran en estado **Publicado** con el campo **Interno** establecido como **No**. Este comportamiento no puede modificarse. Los artículos de conocimientos también tienen funcionalidades especiales disponibles en los resultados de la búsqueda que son los siguientes:

    - **Facetas**: Hay dos facetas especiales disponibles solo para artículos de conocimientos y se muestran si los registros de artículos de conocimientos están disponibles en los resultados de la búsqueda.

        - **Faceta de las calificaciones**: Esta faceta permite filtrar los resultados de la búsqueda en función de la calificación promedio de los artículos de conocimientos.

        - **Faceta de las calificaciones**: Esta faceta permite filtrar los resultados de la búsqueda en función de la calificación promedio de los artículos de conocimientos.

    - **Búsqueda de los datos adjuntos**: Esta faceta permite buscar en los datos adjuntos o notas asociados a un artículo de Knowledge Base. Esto le permite busque dentro de la descripción de la nota, el título, el nombre de archivo de datos adjuntos, y el contenido de los datos adjuntos notas o de datos adjuntos que se exponen en portal. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>Caracteres especiales y sintaxis admitidos por la búsqueda

Como parte de búsqueda global de portal, se admite una variedad de caracteres especiales y de sintaxis que filtren mejor los resultados de la búsqueda. Estos caracteres especiales y sintaxis se dividen ampliamente en los siguientes grupos:

- **Término**: Cada consulta especificada por un usuario para la búsqueda se analiza en términos y operadores. Estos son los tipos de términos: 

    - **Elegir el período**: El término solo es una palabra única. Por ejemplo, una consulta {hola mundo} se analizaría en varios términos, “hola” y “mundo”. Cada período se busca de forma separada. Por tanto, en la consulta {hola mundo}, todos los registros que tienen el término “hola “o “mundo” se presentarían en resultados de búsqueda.

    - **Frases**: Una frase es un grupo de términos rodeado por comillas dobles ("). Por ejemplo, una consulta {“hola mundo”} se analizaría como usuarios de la frase “hola mundo”. Cada frase se busca completamente. Por lo tanto, en la consulta {"hola mundo"}, todos los registros con la frase completa "hola mundo" se mostrarían en los resultados de búsqueda y no se mostraría ningún registro que solo tuviese "hola" o "mundo".

    Cada consulta de búsqueda puede comprender uno o muchos términos de cualquier tipo que se combinen mediante operadores booleanos para crear consultas complejas.

- **Modificadores de período**

    - **Búsqueda con caracteres comodín**: Existen dos tipos de comodines disponibles que se va a usar dentro de varios términos de consultas de búsqueda (no dentro de consultas de la frase): Búsqueda con caracteres comodín de carácter individual y búsqueda con caracteres comodín de varios caracteres.

        - **Búsqueda con caracteres comodín de carácter individual**: Para realizar una búsqueda con caracteres comodín de carácter individual, use el símbolo del signo de interrogación (?). La búsqueda con caracteres comodín de carácter individual busca los términos que coinciden con el carácter individual reemplazado. Por ejemplo, para buscar “texto” o “pruébele” puede usar la consulta de búsqueda como “te? t”.

        - **Búsqueda de comodines de varios caracteres**: Para realizar una búsqueda de comodines de varios caracteres, use el símbolo asterisco (\*). Las búsquedas de comodines de múltiples caracteres buscan cero o más caracteres. Por ejemplo, para buscar prueba, pruebas o evaluador, puede usar la consulta de búsqueda como “t *”. También puede usar búsqueda con caracteres comodín de múltiples caracteres en medio de la consulta. Por ejemplo, “te*de prueba”.

        > [!NOTE]
        > - no puede usar un * o ? símbolo como el primer carácter de una búsqueda.
        > - La búsqueda con caracteres comodín no se puede usar en una consulta de la frase. Por ejemplo, si usa una consulta como “hell* world”, no mostrará resultados con el texto “hello world”.

    - **Búsqueda de proximidad**: La búsqueda de proximidad le permite buscar palabras que se encuentran a una distancia específica una de la otra. Por ejemplo, si desea encontrar los resultados de las palabras "Imagen" y "Borrosa" que aparecen a una distancia de 10 palabras una de la otra, puede usar la búsqueda de proximidad.
    
        Para hacer búsquedas de proximidad, use la tilde (~) como símbolo en la consulta. Por ejemplo, si desea encontrar los resultados para las palabras "Imagen" y "Borrosa" que aparecen a una distancia de 10 palabras una de la otra, entonces la consulta sería "Imagen borrosa" ~ 10.

    - **Impulso de un período**: La búsqueda global proporciona el nivel de relevancia de los documentos coincidentes según los términos encontrados. Para impulsar un término, use el símbolo de intercalación (^) con un factor de impulso (un número) al final del término que está buscando. Cuanto mayor sea el factor de impulso, más relevante será el plazo.

        El impulso le permite supervisar la importancia de un documento impulsando su período. Por ejemplo, si está buscando Smart TV y desea que el término Smart sea más relevante, aumente usando el símbolo ^ junto con el factor de impulso al lado del término. Debería escribir: Smart ^ 4 TV. Esto hará que los documentos con el término Smart parezcan más relevantes.

        También puede aumentar las condiciones de la frase como en el ejemplo: Televisión inteligente^4 nueva televisión. En este caso, la frase "Smart TV" se incrementaría en comparación con "New TV".

        Por defecto, el factor de impulso es 1. Aunque el factor de impulso debe ser un valor positivo, puede ser inferior a 1 (por ejemplo, 0,2).

- **Operadores booleanos**: Los operadores booleanos permiten a los términos combinarse mediante operadores lógicos. La búsqueda global admite OR, AND, NOT, "+" y "-" como operadores booleanos.

    > [!NOTE]
    > Los operadores booleanos deben escribirse en mayúscula.

    - **OR**: El operador OR es el operador predeterminado de la conjunción. Esto significa que si no está el operador booleano entre dos términos, use el operador OR. El operador OR vincula dos términos y busca un registro coincidente si uno de los términos existe en un registro. Esto es equivalente a una combinación mediante conjuntos. El símbolo || se debe usar en lugar de la palabra OR. Por ejemplo, la consulta de búsqueda “Smart TV” (excepto comillas) buscará para todos los registros con la palabra Smart o TV. Esta consulta también se puede escribir como “Smart OR TV”, “Smart || TV”.

    - **Y:** El operador Y combina los registros donde ambos términos existen en cualquier parte del texto de un solo documento. Esto es equivalente a una combinación mediante conjuntos. El símbolo && se debe usar en lugar de la palabra Y. Por ejemplo, la consulta de búsqueda “Smart AND TV” (excepto comillas) buscará para todos los registros con la palabra Smart y TV. Esta consulta también se puede escribir como “Smart && TV”.

    - **NO**: El operador NO excluye los registros después de los que contenga el período NO. Esto es equivalente a una diferencia usando conjuntos. El símbolo ! se puede usar en lugar de la palabra NO. Por ejemplo, la consulta de búsqueda “Smart NOT TV” (excepto comillas) buscará para todos los registros que tengan la palabra Smart pero no la palabra TV. Esta consulta también se puede escribir como “Smart ! TV"

    - **Símbolo más (+)**: El símbolo más (+), conocido también como operador requerido, requiere que el término después del símbolo “+” exista en alguna parte de un registro. Por ejemplo, la consulta de búsqueda “Smart + TV” buscará para todos los registros donde la palabra TV debe estar presente, y la palabra Smart puede estar presente también. 

    - **Símbolo menos (-)**: El símbolo menos (-), conocido también como el operador de permitir, excluye los documentos que contienen el término después del símbolo “-”. Por ejemplo, la consulta de búsqueda “Smart - TV” buscará para todos los registros donde la palabra Smart está presente, y la palabra TV no está presente.

- **Agrupar**: La búsqueda global de portal admite el uso de paréntesis para agrupar cláusulas para formar subconsultas. Puede ser muy útil si desea gestionar la lógica booleana para una consulta. Por ejemplo, si desea buscar todos los registros donde aparece alguno de los términos "HD" o "Smart", pero la palabra TV siempre está presente, la consulta puede escribirse como "(HD or Smart) AND TV" ( excluyendo las comillas).

## <a name="liquid-search-tag"></a>Etiqueta líquida de búsqueda

Puede invocar la búsqueda global del portal desde plantillas líquidas utilizando la etiqueta searchindex. Más información: [searchindex](../liquid/portals-entity-tags.md#searchindex).

> [!IMPORTANT]
> Cuando se usa la etiqueta de searchindex, las facetas no se devuelven como parte de resultados, ni puede aplicar como filtro.

## <a name="update-search-index"></a>Actualizar el índice de búsqueda

Las actualizaciones de índice de búsqueda en los portales de PowerApps se producen automáticamente como la invalidación de caché. Sin embargo, tenga en cuenta estos aspectos importantes a tener presentes:

- Todas las entidades habilitadas para la búsqueda deben tener activado el indicador de metadatos Notificación de cambios, de lo contrario, ninguno de los cambios se notificará al portal y el índice de búsqueda no se actualizará.

- Cualquier cambio puede tardar hasta 30 minutos en reflejarse en una búsqueda del portal. Sin embargo, el 95 por ciento de los cambios se actualizará en 15 minutos. En caso de que intervengan datos adjuntos puede tardar según el tamaño de los datos adjuntos.

- Se recomienda volver a crear el índice completo manualmente después de realizar la migración de datos en masa o realizar actualizaciones en masa a los registros en un breve de tiempo. Para más información consulte [Reconstruir el índice de búsqueda completo](#rebuild-full-search-index).

## <a name="rebuild-full-search-index"></a>Reconstruir el índice de búsqueda completo

Se requiere la reconstrucción del índice de búsqueda completo siempre que:

- Realiza un cambio de metadatos a las propiedades de búsqueda, como cambiar la configuración del sitio específico de una determinada consulta o cambiar la vista de búsqueda de una entidad, etc.
- Se realizan migraciones o actualizaciones masivas de datos.
- Un registro de sitio web, asociado al portal, se modifica en un entorno de Common Data Service.

También puede volver a crear un índice completo de búsqueda de un portal.
1.  Inicie sesión en el portal como administrador.
2.  Navegue a la dirección URL de la siguiente manera: `<portal_path>/_services/about`
3.  Seleccionar **Volver a generar un índice de búsqueda**.

> [!IMPORTANT]
> La reconstrucción completa del índice es una operación muy costosa y no debe realizarse durante las horas pico de uso, ya que esto puede hacer que su portal pierda impulso.

## <a name="remove-an-entity-from-global-search"></a>Quitar una entidad de búsqueda global

A veces, es posible que deba eliminar completamente determinadas entidades de búsqueda global del portal para asegurarse de que los clientes obtienen los resultados correctos rápidamente.

En el siguiente ejemplo, quitaremos la entidad Caso de la búsqueda global de portal.

### <a name="step-1-block-case-entity-from-getting-indexed"></a>Paso 1: La entidad de caso bloqueada no se indexa

Para evitar que la entidad Case se indexe, debe cambiar el nombre de la vista de la entidad Case que define el conjunto de registros a indexar por el portal (definido por la configuración del sitio Search / IndexQueryName). De manera predeterminada, el nombre de esa vista es Portal Search.

1.  Abra la aplicación [Administración del portal](configure-portal.md).

2.  Seleccione el icono **Configuración** en la barra de herramientas de la parte superior derecha de la página y después seleccione **Configuración avanzada**.

2.  Vaya a **Personalizaciones** > **Personalización** > **Personalización del sistema**.

    ![Personalizar el sistema](../media/customize-system.png "Personalizar el sistema")

3.  En el cuadro de diálogo de personalización, vaya **Componentes** > **Entidades** > **Caso** en el panel de navegación de la izquierda. 

4.  Expanda  **Caso** y selecciona **Vistas**.

5.  Seleccione el vista **Buscar portal** de la lista y abren él en editor de la vista.

    ![Vista de caso](../media/case-view.png "Vista de caso")

6.  En la vista del editor, seleccione **Ver propiedades**.

    ![Editor de vistas](../media/view-editor.png "Editor de vistas")

7.  Cambie el nombre de la vista según el requisito. Asegurarse de que el nuevo nombre no tenga el término “Portal Search".

    ![Ver propiedades](../media/view-properties.png "Ver propiedades")

8.  Guarde los cambios y cierre el editor de gráficos

9.  Seleccione **Publicar todas las personalizaciones**.

10. Reconstruya el índice completo como se describe en la sección [Reconstruya el índice completo de búsqueda](#rebuild-full-search-index).

> [!NOTE]
> En este ejemplo, vamos realizar cambios en un nivel no administrado editando directamente la vista. También puede realizar esto a través de una solución administrada.

### <a name="step-2-remove-case-entity-from-the-ui"></a>Paso 2: Quite la entidad Caso de la interfaz de usuario

Después de realizar las acciones descritas en el Paso 1, la entidad Caso no podrá ser indexada. Para eliminar la entidad de caso de las áreas de superficie de la interfaz de usuario, debe modificar la configuración del sitio asociada a la búsqueda global del portal. La siguiente configuración del sitio debe ser modificada:

búsqueda/filtros: Esto quitará la entidad Caso de filtros en la página de búsqueda así como un cuadro de búsqueda en el encabezado del sitio. De forma predeterminada, el valor es `Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

Deberá eliminar `Help Desk:incident;` del valor de esta configuración de sitio para que la entidad Incidente se elimine de los filtros que se encuentran junto al cuadro de búsqueda en la interfaz de usuario.

El valor modificado será:

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

Una vez que se modifique la configuración de este sitio, la entidad Caso se eliminará de los filtros en la página de búsqueda, así como en el encabezado.

![Buscar en la página](../media/search-on-page.png "Buscar en la página")

![Buscar en encabezado](../media/search-in-header.png "Buscar en encabezado")
