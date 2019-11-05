---
title: Búsqueda global en portales de PowerApps | MicrosoftDocs
description: Obtenga información sobre cómo funciona la búsqueda global en un portal.
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551632"
---
# <a name="search"></a>Search

En los portales de PowerApps, puede buscar registros en varias entidades mediante la funcionalidad de búsqueda global del portal. También puede buscar en los registros de las listas de entidades mediante la funcionalidad de búsqueda de la lista de entidades. 

La funcionalidad de búsqueda de la lista de entidades en el portal usa FetchXML en el back-end para buscar las columnas definidas en la lista de entidades y, a continuación, mostrar los resultados. 

La búsqueda global utiliza un índice de búsqueda externa que se basa en Lucene.Net y se usa para buscar en varias entidades y campos a la vez.

## <a name="global-search"></a>Búsqueda global

La búsqueda global de portales permite buscar registros en varias entidades. También permite buscar en varias columnas y configurar las columnas de una entidad que se pueden buscar.

Entre las ventajas de la búsqueda global se encuentran su capacidad para:
- Buscar coincidencias con cualquier palabra del término de búsqueda en cualquier campo de la entidad. Las coincidencias pueden incluir palabras con inflexión como Stream, streaming o streaming.
- Devuelve los resultados de todas las entidades que se pueden buscar en una única lista ordenada por relevancia, en función de factores como el número de palabras coincidentes o su proximidad entre sí en el texto.
- Resaltar coincidencias en los resultados de la búsqueda.
- Proporcionar opciones de faceta que se pueden usar para filtrar más los resultados de la búsqueda.

En la búsqueda global, cuanto mejor sea la coincidencia, más alta aparecerá en los resultados. Una coincidencia tiene una mayor relevancia si se encuentran más palabras del término de búsqueda en estrecha proximidad entre sí. Cuanto menor sea la cantidad de texto donde se encuentren las palabras de búsqueda, mayor será la relevancia. Por ejemplo, si encuentra las palabras de búsqueda en el nombre y la dirección de la empresa, podría ser una mejor coincidencia que las mismas palabras que se encuentran en un artículo grande, separadas entre sí. Dado que los resultados se devuelven en una sola lista, puede ver una combinación de registros mostrados uno después de otro, con los trabajos coincidentes resaltados. 

En las secciones siguientes se detalla cómo funciona la búsqueda global en portales de PowerApps y se describen las distintas opciones de configuración disponibles.

## <a name="entities-searchable-in-portal-global-search"></a>Entidades que se pueden buscar en la búsqueda global del portal

Se puede buscar en las siguientes entidades en un sitio web del portal siempre que se hayan instalado los paquetes de solución adecuados y se haya agregado la búsqueda a un portal. Las columnas que se indexan se componen de las columnas que se encuentran en la vista de búsqueda, que se pueden personalizar.  Cada entidad de la lista tiene su conjunto predeterminado de atributos indizados, como se muestra aquí:
- Artículo de conocimientos
    - También se pueden realizar búsquedas en las notas y los datos adjuntos de un artículo de conocimientos. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)
    - Los artículos solo se pueden buscar si se publican y su campo solo interno está establecido en false.
- Blog 
- Entrada de blog 
- Comentario de entrada de blog 
- Enhance 
- Publicación en el foro 
- Subproceso del Foro 
- Recomendable 
- Comentario de idea 
- Foro de ideas 
- Archivo Web 
    - También se pueden realizar búsquedas en el contenido de los datos adjuntos de archivos Web. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)
- Página Web 
- Incidente 

> [!NOTE]
> Aparte de las entidades que se enumeran aquí, no se puede habilitar ninguna otra entidad para la búsqueda global en un portal.

## <a name="fields-searchable-in-global-search"></a>Campos que se pueden buscar en la búsqueda global

Todos los campos disponibles en la vista definida por la configuración del sitio Search/IndexQueryName para cualquier entidad se indexan en la búsqueda global y se pueden buscar. 

El valor predeterminado de Search/IndexQueryName es "búsqueda del portal".

Si la vista no está disponible para ninguna entidad, no se indexa y los resultados no se muestran en la búsqueda global.

> [!NOTE]
> Si cambia el valor de la configuración del sitio de Search/IndexQueryName, debe desencadenar un reíndice manual de la compilación mediante los pasos definidos en la sección [volver a generar el índice de búsqueda completo](#rebuild-full-search-index) .

## <a name="related-site-settings"></a>Configuración del sitio relacionado

La siguiente configuración del sitio está relacionada con la búsqueda global:

| Nombre    | Valor predeterminado     | Descripción       |
|-----------------------|--------------------|-------------|
| Búsqueda/habilitado | True  | Valor booleano que indica si la búsqueda está habilitada. Si establece su valor en false, se desactivará la búsqueda global en el portal.<br>Si usa plantillas web preparadas y desactiva esta opción, el cuadro de búsqueda no se mostrará en el encabezado, ni tampoco en la página de búsqueda. Además, no se devuelven resultados aunque se alcance la dirección URL directa de la página de búsqueda.  |
| Búsqueda/filtros  | Contenido: adx_webpage; Eventos: adx_event, adx_eventschedule; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment; Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost; ideas: adx_ideaforum, adx_idea, adx_ideacomment; problemas: adx_issueforum, adx_issue, adx_issuecomment; Departamento de soporte técnico: incidente | Colección de opciones de filtro de nombre lógico de búsqueda. Al definir un valor aquí se agregarán opciones de filtro desplegables a la búsqueda global. Este valor debe tener el formato de pares nombre-valor, con el nombre y el valor separados por dos puntos, y los pares separados por un punto y coma. Por ejemplo: "forums: adx_communityforum, adx_communityforumthread, adx_communityforumpost; Blogs: adx_blog, adx_blogpost, adx_blogpostcomment ".  |
| Buscar/IndexQueryName   | Búsqueda en el portal  | El nombre de la vista del sistema utilizada por la consulta de búsqueda del portal para definir los campos de una entidad habilitada que se indexan y se buscan.   |
| Búsqueda/consulta  | \+ (@Query) _title:(@Query) _logicalname: adx_webpage\~0.9 ^ 0,2-_logicalname: adx_webfile\~0,9 adx_partialurl:(@Query) _logicalname: adx_blogpost\~0.9 ^ 0.1-_logicalname: adx_communityforumthread\~0,9   | Esta configuración agrega pesos y filtros adicionales a la consulta que un usuario escribe en el cuadro de búsqueda predeterminado que se muestra en el portal. En el valor predeterminado, @Query es el texto de la consulta escrito por un usuario.<br>Para obtener información sobre cómo modificar este valor, siga la [Sintaxis de consulta de Lucene](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html).<br>**Importante**: esta ponderación y el filtrado solo se aplican al cuadro de búsqueda que aparece en la página de búsqueda predeterminada del portal. Si usa una etiqueta de búsqueda líquida para crear su propia página de búsqueda, no se aplica esta configuración. |
| Búsqueda/analizador lingüístico  | Inglés    | El lenguaje utilizado por el algoritmo de lematización de la búsqueda del portal.   |
| Buscar/FacetedView  | True   | Esto habilita las aspectos de los resultados de la búsqueda. Cuando se establece en true, se mostrarán las caras junto con los resultados en la página de búsqueda.  |
| Buscar/IndexNotesAttachments   | True    | Indica si se debe indizar el contenido de los datos adjuntos de las notas de los artículos de Knowledge base y los archivos Web. De forma predeterminada, se establece en false. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)    |
| Buscar/RecordTypeFacetsEntities  | Blogs: adx_blog, adx_blogpost; Foros: adx_communityforum, adx_communityforumthread, adx_communityforumpost; ideas: adx_ideaforum, adx_idea; downloads: Annotation, adx_webfile    | Esto determina cómo se agrupan las entidades en la faceta de tipo de registro en la página de búsqueda. Esta opción está en el formato <br>"DisplayNameinRecordTypeFacet1:logicalnameofentity1,logicalnameofentity2; DisplayNameinRecordTypeFacet2:logicalnameofentity3,logicalnameofentity4" <br>El nombre para mostrar en la faceta tipo de registro aparecerá en la interfaz de usuario. Este grupo de facetas combinará el resultado de las entidades definidas en la configuración.   |
| KnowledgeManagement/DisplayNotes | True   | Indica si se van a indizar los datos adjuntos de los artículos de Knowledge base. De forma predeterminada, se establece en false. |
|||

## <a name="related-content-snippets"></a>Fragmentos de código de contenido relacionados

Los fragmentos de código de contenido siguientes están relacionados con la búsqueda global:

| Nombre   | Valor predeterminado  | Descripción   |
|------------------|-----------------|--------------------|
| Encabezado/búsqueda/etiqueta| Search| Este fragmento de contenido determina el texto de marca de agua que se muestra en el cuadro de búsqueda en el encabezado del portal.<br>![Etiqueta de búsqueda](../media/search-label.png "Etiqueta de búsqueda")    |
| Encabezado/búsqueda/información sobre herramientas| Search  | Este fragmento de código determina el texto de información sobre herramientas que se muestra al mantener el mouse sobre el icono de búsqueda en el encabezado del portal.<br>![Información sobre herramientas de búsqueda](../media/search-tooltip.png "Información sobre herramientas de búsqueda")  |
| Buscar/predeterminado/filtro| Todos   | Este fragmento de código determina el texto predeterminado que se muestra en la lista desplegable de filtros situada junto al cuadro de búsqueda.<br>![Texto del filtro de búsqueda](../media/search-filter-text.png "Texto del filtro de búsqueda")  |
| Buscar/faceta/todo| Todos| Este fragmento de código determina el texto predeterminado que se muestra para "faceta de todos los registros" en la faceta "tipo de registro" de la página de resultados de la búsqueda.<br>![Todas las facetas](../media/facet-all.png "Todas las facetas") |
| Búsqueda/faceta/ClearConstraints   | Borrar todo  | Este fragmento de código determina la etiqueta del botón que restablece todas las caras aplicadas en la página resultados de la búsqueda.<br>![Restablecer todas las caras](../media/facet-clear-all.png "Restablecer todas las caras") |
| Búsqueda/faceta/descargas   | Carga   | Este fragmento de código determina la etiqueta que se muestra en los resultados de búsqueda de los datos adjuntos de la anotación y los registros de archivo Web en la faceta "tipo de registro".<br>![Descargar faceta](../media/facet-download.png "Descargar faceta")|
| Búsqueda/faceta/less    | Mostrar menos  | Este fragmento de contenido determina la etiqueta del botón que contrae los resultados de la faceta.<br>![Mostrar menos faceta](../media/facet-show-less.png "Mostrar menos faceta") |
| Búsqueda/faceta/ModifiedDate  | Fecha de modificación  | Este fragmento de contenido determina la etiqueta del encabezado que se muestra para la faceta de fecha de modificación.<br>![Fecha de modificación](../media/facet-modified-date.png "Faceta de fecha modificada")   |
| Búsqueda/faceta/más   | Mostrar más  | Este fragmento de código determina la etiqueta del botón que expande los resultados de la faceta.<br>![Mostrar más faceta](../media/facet-show-more.png "Mostrar más faceta")  |
| Búsqueda/faceta/producto  | Productos | Este fragmento de contenido determina la etiqueta de la faceta Products.<br>![Faceta Products](../media/facet-product.png "Faceta Products")  |
| Búsqueda/faceta/clasificación   | Clasificación   | Este fragmento de contenido determina la etiqueta de la faceta rating.<br>![Faceta ratings](../media/facet-rating.png "Faceta ratings")  |
| Búsqueda/faceta/RecordType   | Tipo de registro | Este fragmento de contenido determina la etiqueta de la faceta de tipo de registro.<br>![Faceta de tipo de registro](../media/facet-record-type.png "Faceta de tipo de registro")     |
| Búsqueda/faceta/SortOrder/AverageUserRating | Promedio de clasificación de usuario | Este fragmento de código determina la etiqueta que se muestra para la opción "ordenar por promedio de usuarios" en la lista desplegable de ordenación de la página resultados de la búsqueda.<br>![Ordenar por promedio de clasificación de usuario](../media/sort-avg-user-rating.png "Ordenar por promedio de clasificación de usuario")  |
| Búsqueda/faceta/SortOrder/relevancia| Relación| Este fragmento de contenido determina la etiqueta que se muestra para la opción "ordenar por relevancia" en la lista desplegable de ordenación de la página resultados de la búsqueda.<br>![Ordenar por relevancia](../media/sort-relevance.png "Ordenar por relevancia")|
| Búsqueda/faceta/SortOrder/vistas| Ver recuento| Este fragmento de código determina la etiqueta que se muestra para la opción "ordenar por número de vistas" en la lista desplegable de ordenación de la página resultados de la búsqueda.<br>![Ordenar por recuento de vistas](../media/sort-view-count.png "Ordenar por recuento de vistas")|
|||

## <a name="entity-specific-handling"></a>Control específico de la entidad

- **Caso**: de forma predeterminada, los únicos casos en los que se pueden realizar búsquedas se encuentran en el estado **resuelto** con el campo **publicar en Web** establecido en **true**. Este comportamiento puede modificarse mediante la actualización de la vista de búsqueda del portal de la entidad Case y la eliminación de los filtros disponibles en la vista de búsqueda del portal. Sin embargo, cuando se quita esta comprobación, es importante asegurarse de que la plantilla Web servicio al cliente-caso se modifique correctamente, ya que esta plantilla impide que todos los usuarios vean los casos que están activos y no se publican en la Web. Si la plantilla Web no se modifica, los casos estarán visibles en los resultados de la búsqueda. Sin embargo, cuando se selecciona, se muestra la Página Web de detalles de casos con el error de Permiso denegado.

- Knowledge **base**: solo se pueden buscar artículos de conocimientos si están en el estado **publicado** con el campo **interno** establecido en **no**. Este comportamiento no se puede modificar. Los artículos de conocimientos también tienen una funcionalidad especial disponible en los resultados de la búsqueda, como se indica a continuación:

    - **Aspectos**: dos caras especiales solo están disponibles para los artículos de conocimientos y se muestran si los registros de artículos de conocimientos están disponibles en los resultados de la búsqueda.

        - **Faceta ratings**: esta faceta le permite filtrar los resultados de la búsqueda en función de la clasificación media de los artículos de conocimientos.

        - **Faceta de producto**: esta faceta le permite filtrar los resultados de la búsqueda en función del producto asociado a los artículos de conocimientos.

    - **Búsqueda de datos adjuntos**: esta funcionalidad le permite buscar en los datos adjuntos o notas asociados a un artículo de conocimientos. Esto le permite buscar en la descripción de la nota, el título, el nombre del archivo adjunto y el contenido de los datos adjuntos de notas o datos adjuntos que se exponen en el portal. Más información: [Buscar en el contenido de los archivos adjuntos](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>Caracteres especiales y sintaxis admitidos por la búsqueda

Como parte de la búsqueda global del portal, se admiten una variedad de caracteres especiales y sintaxis para filtrar mejor los resultados de la búsqueda. Estos caracteres especiales y las sintaxis se dividen en los siguientes grupos:

- **Término**: cada consulta escrita por un usuario para la búsqueda se analiza en términos y operadores. A continuación se indican los tipos de términos: 

    - **Único término**: un único término es una sola palabra. Por ejemplo, una consulta {Hello World} se analizaría en dos términos individuales: "Hello" y "World". Cada término se busca por separado. Por lo tanto, en la consulta {Hello World}, se mostrarán todos los registros que tengan el término "Hello" o "World" en los resultados de la búsqueda.

    - **Frases**: una frase es un grupo de términos entre comillas dobles (""). Por ejemplo, una consulta {"Hello World"} se analizaría como una frase "Hello World". Cada frase se busca por completo. Por lo tanto, en la consulta {"Hello World"}, todos los registros que tengan la frase completa "Hello World" se mostrarán en los resultados de la búsqueda y cualquier registro que solo tenga "Hello" o "World" no se mostraría.

    Cada consulta de búsqueda puede constar de uno o varios de estos términos de cualquier tipo que se combinan mediante operadores booleanos para crear consultas complejas.

- **Modificadores de términos**

    - **Búsqueda con caracteres comodín**: hay dos tipos de caracteres comodín disponibles que se pueden usar dentro de los únicos términos de consultas de búsqueda (no en las consultas de frases): búsqueda con caracteres comodín de un solo carácter y búsqueda con caracteres comodín de varios caracteres.

        - Búsqueda con caracteres comodín de un **solo carácter**: para realizar una búsqueda con caracteres comodín de un solo carácter, use el signo de interrogación (?). La búsqueda con caracteres comodín de un solo carácter busca los términos que coinciden con el carácter único reemplazado. Por ejemplo, para buscar "texto" o "prueba" puede usar la consulta de búsqueda como "te? t".

        - **Búsqueda con caracteres comodín de varios caracteres**: para realizar una búsqueda con caracteres comodín de varios caracteres, utilice el símbolo de asterisco (\*). Las búsquedas con caracteres comodín de varios caracteres buscan cero o más caracteres. Por ejemplo, para buscar pruebas, pruebas o evaluadores, puede usar la consulta de búsqueda como "prueba *". También puede usar la búsqueda con caracteres comodín de varios caracteres en el medio de la consulta. Por ejemplo, "te*t".

        > [!NOTE]
        > - No puede usar un * o? símbolo como primer carácter de una búsqueda.
        > - No se puede usar la búsqueda con caracteres comodín en una consulta de frases. Por ejemplo, si usa la consulta como "Hell * World", no se mostrarán los resultados con el texto "Hello World".

    - **Búsqueda de proximidad**: la búsqueda de proximidad le permite buscar palabras que se encuentran dentro de una distancia específica entre sí. Por ejemplo, si desea que los resultados de las palabras "imagen" y "Desenfoque" aparezcan entre las 10 palabras, puede usar la búsqueda de proximidad.
    
        Para realizar búsquedas de proximidad, use el símbolo de tilde (~) al final de la consulta. Por ejemplo, si desea que los resultados de las palabras "imagen" y "Desenfoque" aparezcan entre las 10 palabras, la consulta sería "imagen borrosa" ~ 10.

    - **Aumento de un término**: la búsqueda global proporciona el nivel de relevancia de los documentos coincidentes en función de los términos encontrados. Para aumentar un término, use el símbolo de intercalación (^) con un factor de aumento (un número) al final del término que está buscando. Cuanto mayor sea el factor de aumento, más relevante será el término.

        El aumento le permite controlar la relevancia de un documento aumentando su plazo. Por ejemplo, si va a buscar Smart TV y desea que el término inteligente sea más relevante, aumente el tamaño con el símbolo ^ junto con el factor de aumento junto al término. Debe escribir: TV Smart ^ 4. Esto hará que los documentos con el término Smart aparezcan más relevantes.

        También puede aumentar los términos de la frase como en el ejemplo: TV inteligente ^ 4 nueva TV. En este caso, la frase "Smart TV" se incrementaría en comparación con "New TV".

        De forma predeterminada, el factor de aumento es 1. Aunque el factor de aumento debe ser positivo, puede ser menor que 1 (por ejemplo, 0,2).

- **Operadores booleanos**: los operadores booleanos permiten combinar términos mediante operadores lógicos. La búsqueda global admite o, AND, NOT, "+" y "-" como operadores booleanos.

    > [!NOTE]
    > Los operadores booleanos deben escribirse en mayúsculas.

    - **O bien**: el operador Or es el operador de combinación predeterminado. Esto significa que, si no hay ningún operador booleano entre dos términos, se utiliza el operador o. El operador OR vincula dos términos y encuentra un registro coincidente si alguno de los términos existe en un registro. Esto es equivalente a una Unión mediante conjuntos. El símbolo | | se puede usar en lugar de la palabra o. Por ejemplo, la consulta de búsqueda "Smart TV" (sin incluir las comillas) buscará todos los registros que contengan la palabra Smart o TV. Esta consulta también se puede escribir como "Smart o TV", "Smart | | TV ".

    - **Y:** El operador AND coincide con los registros en los que existen ambos términos en cualquier parte del texto de un documento único. Esto es equivalente a una intersección mediante conjuntos. El símbolo & & puede usarse en lugar de la palabra y. Por ejemplo, la consulta de búsqueda "Smart AND TV" (sin incluir las comillas) buscará todos los registros con las palabras Smart y TV en ellos. Esta consulta también se puede escribir como "& inteligente & TV".

    - **No**: el operador not excluye los registros que contienen el término después de no. Esto es equivalente a una diferencia mediante conjuntos. El símbolo! se puede usar en lugar de la palabra NOT. Por ejemplo, la consulta de búsqueda "Smart NOT TV" (sin incluir comillas) buscará todos los registros que tengan la palabra Smart, pero que no tengan la palabra TV. Esta consulta también se puede escribir como "inteligente! TV ".

    - **Signo más (+)** : el símbolo más (+), también conocido como operador obligatorio, requiere que el término que hay después del símbolo "+" exista en algún lugar de un registro. Por ejemplo, la consulta de búsqueda "Smart + TV" buscará todos los registros en los que la palabra TV debe estar presente y la palabra Smart también puede estar presente. 

    - **Signo menos (–)** : el símbolo menos (-), también conocido como operador de prohibición, excluye los documentos que contienen el término después del símbolo "-". Por ejemplo, la consulta de búsqueda "Smart-TV" buscará todos los registros en los que la palabra Smart esté presente y la palabra TV no debe estar presente.

- **Agrupación**: la búsqueda global del portal admite el uso de paréntesis para agrupar las cláusulas para formar subconsultas. Esto puede ser muy útil si desea controlar la lógica booleana de una consulta. Por ejemplo, si desea buscar todos los registros en los que uno de los términos "HD" o "Smart" está presente, pero la palabra TV siempre está presente, la consulta se puede escribir como "(HD o inteligente) y TV" (sin incluir las comillas).

## <a name="liquid-search-tag"></a>Etiqueta de búsqueda líquida

Puede invocar la búsqueda global del portal desde plantillas líquidas mediante la etiqueta searchindex. Más información: [searchindex](../liquid/portals-entity-tags.md#searchindex)

> [!IMPORTANT]
> Cuando se usa la etiqueta searchindex, no se devuelven las caras como parte de los resultados ni se pueden aplicar como filtro.

## <a name="update-search-index"></a>Actualizar índice de búsqueda

Las actualizaciones del índice de búsqueda en portales de PowerApps se producen automáticamente como la invalidación de la memoria caché. Tenga en cuenta estos aspectos importantes, sin embargo:

- Todas las entidades habilitadas para la búsqueda deben tener habilitada la marca de metadatos de notificación de cambios; de lo contrario, no se notificará al portal los cambios y no se actualizará el índice de búsqueda.

- Cualquier cambio puede tardar hasta 30 minutos en reflejarse en una búsqueda del portal. Sin embargo, el 95 por ciento de los cambios se actualizará en un plazo de 15 minutos. Si hay datos adjuntos, pueden tardar más en función del tamaño de los datos adjuntos.

- Es aconsejable volver a generar manualmente el índice completo después de realizar una migración de datos masiva o realizar actualizaciones masivas en los registros en un breve intervalo de tiempo. Para obtener más información, consulte [rebuild Full Search index](#rebuild-full-search-index).

## <a name="rebuild-full-search-index"></a>Volver a generar el índice de búsqueda completo

Es necesario volver a generar el índice de búsqueda completo siempre que:

- Realice un cambio en los metadatos para buscar propiedades, como cambiar determinados valores de configuración del sitio específicos de la consulta o cambiar la vista de búsqueda de una entidad, etc.
- Se realiza la migración de datos masiva o las actualizaciones.
- Un registro de sitio web, asociado a su portal, se cambia en un entorno de Common Data Service.

También puede volver a generar un índice de búsqueda completo desde un portal.
1.  Inicie sesión en el portal como administrador.
2.  Vaya a la dirección URL de la siguiente manera: `<portal_path>/_services/about`
3.  Seleccione **volver a generar índice de búsqueda**.

> [!IMPORTANT]
> Una recompilación de índice completa es una operación muy costosa y no debe realizarse durante las horas punta de uso, ya que esto puede reducir el portal.

## <a name="remove-an-entity-from-global-search"></a>Quitar una entidad de la búsqueda global

En ocasiones, es posible que deba quitar completamente ciertas entidades de la búsqueda global del portal para asegurarse de que los clientes obtienen los resultados correctos rápidamente.

En el ejemplo siguiente, se quitará la entidad case de la búsqueda global del portal.

### <a name="step-1-block-case-entity-from-getting-indexed"></a>Paso 1: bloquear la entidad case de la indización

Para bloquear la entidad Case para que no se pueda indizar, debe cambiar el nombre de la vista de la entidad case que define el conjunto de registros que se va a indexar en el portal (definido por la configuración del sitio Search/IndexQueryName). De forma predeterminada, el nombre de la vista es búsqueda en el portal.

1.  Abra la [aplicación administración del portal](configure-portal.md).

2.  Seleccione el icono de **configuración** en la barra de herramientas de la parte superior de la página y, a continuación, seleccione **Configuración avanzada**.

2.  Vaya a **configuración** > **Personalización** > **personalizar el sistema**.

    ![Personalizar el sistema](../media/customize-system.png "Personalizar el sistema")

3.  En el cuadro de diálogo personalización, vaya a **componentes** > **entidades** > **caso** en el panel de navegación izquierdo. 

4.  Expanda la entidad **Case** y seleccione **vistas**.

5.  Seleccione la vista de **búsqueda del portal** en la lista y ábrala en el editor de vistas.

    ![Vista de casos](../media/case-view.png "Vista de casos")

6.  En el editor de vistas, seleccione **Ver propiedades**.

    ![Editor de vistas](../media/view-editor.png "Editor de vistas")

7.  Cambie el nombre de la vista según el requisito. Asegúrese de que el nuevo nombre no tiene el término "Buscar en el portal" en él.

    ![Ver propiedades](../media/view-properties.png "Ver propiedades")

8.  Guarde los cambios y cierre el editor de vistas.

9.  Seleccione **Publicar todas las personalizaciones**.

10. Vuelva a generar el índice completo tal como se describe en la sección [volver a generar el índice de búsqueda completo](#rebuild-full-search-index) .

> [!NOTE]
> En este ejemplo, vamos a realizar cambios en una capa no administrada editando directamente la vista. También puede hacerlo a través de una solución administrada.

### <a name="step-2-remove-case-entity-from-the-ui"></a>Paso 2: quitar la entidad case de la interfaz de usuario

Después de realizar las acciones descritas en el paso 1, la entidad Case se detendría de la indización. Para quitar la entidad case de las áreas de la superficie de la interfaz de usuario, debe modificar la configuración del sitio asociada a la búsqueda global del portal. Se debe modificar la siguiente configuración del sitio:

búsqueda/filtros: se quitará la entidad case de los filtros de la página de búsqueda, así como el cuadro de búsqueda en el encabezado del sitio. De forma predeterminada, el valor es: `Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

Debe eliminar `Help Desk:incident;` del valor de esta configuración de sitio para que la entidad incidente se quite de los filtros que aparecen junto al cuadro de búsqueda en la interfaz de usuario.

El valor modificado será:

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

Una vez que se cambia la configuración de este sitio, la entidad Case se quitará de los filtros de la página de búsqueda, así como del encabezado.

![Buscar en la página](../media/search-on-page.png "Buscar en la página")

![Buscar en el encabezado](../media/search-in-header.png "Buscar en el encabezado")
