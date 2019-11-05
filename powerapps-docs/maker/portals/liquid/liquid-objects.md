---
title: Usar objetos Liquid para un portal | MicrosoftDocs
description: Obtenga información sobre los objetos Liquid disponibles en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 857c65097800420662aafe825f61333037b4e31c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543167"
---
# <a name="available-liquid-objects"></a>Objetos de Liquid disponibles

Los objetos Liquid contienen atributos para generar contenido dinámico en la página. Por ejemplo, el objeto Page tiene un atributo denominado title que se puede usar para generar el título de la página actual.

Para tener acceso a un atributo de objeto por nombre, use un punto. Para representar el atributo de un objeto en una plantilla, inclúyalo en {{y}}.

```
{{ page.title }}
```
También se puede tener acceso a los atributos de un objeto mediante un nombre de cadena y \[\]. Esto resulta útil en los casos en que el atributo deseado se determina de forma dinámica, o el nombre de atributo contiene caracteres, espacios, caracteres especiales, etc. que no serían válidos al utilizar. sintáctica.

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

Los objetos siguientes se pueden usar y se puede acceder a ellos desde cualquier parte, en cualquier plantilla.


|   Objeto    |                                                                                                                                                                                          Descripción                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  jurídica   |                                                                                                 Permite cargar cualquier entidad de PowerApps por identificador. [entidades](#entities) [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)]                                                                                                 |
|     estará     |                                          Objeto de fecha y hora que hace referencia a la hora UTC actual en el momento en que se representa la plantilla.<br>**Nota**: este valor se almacena en la memoria caché de la aplicación web del portal y no se actualiza cada vez. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [filtros de fecha](liquid-filters.md#date-filters)                                          |
|    del     | Hace referencia a la página de solicitud del portal actual. El objeto de página proporciona acceso a elementos como las rutas de navegación de la página actual, el título o la dirección URL de la página actual y cualquier otro atributo o entidad relacionada del registro de PowerApps subyacente. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Página](#page) |
|   params    |                                                                                                                             Un acceso directo adecuado para request. params. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [solicitud](#request)                                                                                                                              |
|   Solicite   |                                                                                                                        Contiene información sobre la solicitud HTTP actual. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [solicitud](#request)                                                                                                                        |
|  Configuración   |                                                                                                            Permite cargar cualquier valor de [configuración del sitio](../configure/configure-site-settings.md) por nombre. [configuración](#settings) de [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)]                                                                                                            |
|   mapas   |                                                                                                                               Permite el acceso al mapa del sitio del portal. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [mapa del sitio](#sitemap)                                                                                                                                |
| sitemarkers |                                                                                                                        Permite cargar marcadores de sitio por nombre. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [sitemarkers](#sitemarkers)                                                                                                                        |
|  fragmentos   |                                                                                                         Permite cargar cualquier fragmento de [contenido](../configure/customize-content-snippets.md) por nombre. [fragmentos](#snippets) de [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)]                                                                                                         |
|    Usuario     |                             Hace referencia al usuario del portal actual, lo que permite el acceso a todos los atributos del registro de contacto de PowerApps subyacente. Si ningún usuario ha iniciado sesión, esta variable será [null](liquid-types.md#null). [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [usuario](#user)                              |
|  weblinks   |                                                                                                                        Permite cargar cualquier vínculo Web establecido por nombre o identificador. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [weblinks](#weblinks)                                                                                                                        |
|   Bsitio   |                                                      Hace referencia al registro del sitio web del portal, que permite el acceso a todos los atributos del sitio web de PowerApps (sitio web de ADX\_) para el portal. [sitio web](#website) [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)]                                                       |

## <a name="ads"></a>anuncios


Proporciona la capacidad de obtener acceso a un anuncio y de representarlo.

El objeto ADS permite seleccionar una ubicación de ad o ad específica:

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>Atributos de ADS

|Atribui   |Descripción   |
|---|---|
| ubicaciones        | Devuelve el objeto adplacements.    |
| nombre o identificador de \[ad\] | Puede tener acceso a cualquier ad por sus propiedades name o ID. <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>Atributos de ubicaciones de anuncios

|Atribui   |Descripción   |
|---|---|
| \[el identificador o el nombre de la ubicación de ad\] | Puede tener acceso a cualquier adplacement por sus propiedades name o ID.<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>Atributos de colocación de ad

Una ubicación de ad es un objeto entidad, con todos los mismos atributos, además de los que se enumeran a continuación.

|Atribui   |Descripción   |
|---|---|
| anuncios            | Devuelve la colección de objetos de ad asociada a la ubicación.  Las [etiquetas de iteración](iteration-tags.md) y los [filtros de matriz](liquid-filters.md#array-filters) se pueden usar con esta colección.  |  
| Nombre           | Devuelve el campo de nombre de la ubicación de ad.                                                                |
| Dirección URL de\_de ubicación | La dirección URL que se puede usar para recuperar la ubicación de ad totalmente representada por una plantilla.                         |
| URL de\_aleatorio    | La dirección URL que se puede usar para recuperar un anuncio aleatorio de la ubicación representada completamente por una plantilla.           |

### <a name="ad-attributes"></a>Atributos de ad

> [!Note]
> Un anuncio es un objeto entidad, con todos los mismos atributos además de los que se enumeran a continuación.

|Atribui   |Descripción   |
|---|---|
| URL de ad\_ |  La dirección URL que se puede usar para recuperar el anuncio totalmente representado por una plantilla.   |
| Copiar| Devuelve el campo de copia para el anuncio.|
| Impresión| Devuelve el objeto de imagen (si existe) para el anuncio.|
| Nombre| Devuelve el campo de nombre para el anuncio.|
| abrir\_en\_ventana nuevo\_ | Devuelve true si la dirección URL especificada por Redirect\_dirección URL debe abrirse en una nueva ventana. |
| URL de\_de redireccionamiento| La dirección URL a la que se dirigirá al usuario seleccionando ad.|

### <a name="ad-image-attributes"></a>Atributos de imagen de ad

|Atribui   |Descripción   |
|---|---|
| texto alternativo de\_ | Devuelve el texto que se va a mostrar en el atributo ALT de la etiqueta. |
| alto          | Devuelve el alto en píxeles de la imagen.                             |
| Dirección             | Devuelve el origen de la dirección URL de la imagen.                                  |
| ancho           | Devuelve el ancho en píxeles de la imagen.                              |


## <a name="blogs"></a>Blogs

Proporciona la capacidad de obtener acceso a blogs y entradas de blog y presentarlos.

El objeto blogs permite seleccionar un blog específico o entradas de blog.

```
{% assign posts = blogs.posts | paginate: 0,4 %}

<div class=content-panel panel panel-default>

<div class=panel-heading>

{% assign sitemarker = sitemarkers[Blog Home] %}

{% assign snippet = snippets[Home Blog Activity Heading] %}

<a class=pull-right href={{sitemarker.url}}> All Blogs </a>

<h4>

<a class=feed-icon fa fa-rss-square href={{ blogs.feedpath }} />

{{ snippet.adx_value }}

</h4>

</div>

<ul class=list-group>

{% for post in posts.all %}

<li class=list-group-item >

<a class=user-avatar href={{ post.author_url }}>

<img src={{ post.user_image_url }} />

</a>

<h4 class=list-group-item-heading>

<a href={{ post.app_relative_path }}>{{ post.title }}</a>

</h4>

<div class=content-metadata>

<abbr class=timeago>{{ post.publish_date }}</abbr>

&ndash;

<a href={{ post.author_url }}> {{ post.author_name }} </a>

&ndash;

<a href={{ post.application_path }}#comments>

<span class=fa fa-comment aria-hidden=true></span> {{ post.comment_count }}

</a>

</div>

</li>

{% endfor %}

</ul>

</div>
```

### <a name="blogs-object"></a>blog (objeto)

El objeto blogs permite acceder a cualquier blog específico en el portal o acceder a todas las entradas de blog en el portal (independientemente del blog).

En la tabla siguiente se explican los atributos asociados al objeto blogs.

|Atribui   |Descripción   |
|---|---|
| publique               | Devuelve un objeto Blogposts que contiene todas las entradas de blog en el portal.     |
| nombre o identificador de \[blog\] | Puede tener acceso a cualquier blog mediante sus propiedades nombre o ID.                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>Objeto de blog

El objeto de blog permite trabajar con un solo blog, lo que permite acceder a las publicaciones de dicho blog.

En la tabla siguiente se explican los distintos atributos asociados al objeto de blog.

|Atribui   |Descripción   |
|---|---|
| publique | Devuelve un objeto Blogposts que contiene todas las entradas de blog del blog. |
| Nombre  | Nombre del blog.                                              |
| Titulo | Título del blog.                                             |
| Dirección   | La dirección URL del blog.                                               |

### <a name="blogposts-object"></a>Objeto Blogposts

El objeto Blogposts permite acceder a una colección de objetos de entrada de blog. Puede ordenar las entradas de blog y lograr la paginación además de usar filtros líquidos:

{% Assign Blogposts = blogs. posts | Order\_por "ADX\_name", "DESC" | Paginate: 0, 4 | All%} Tenga en cuenta que blogs. posts. All también es una manera válida de obtener todas las entradas de blog blogs. posts | de\_índice: 0 | Take: 2 también es posible

En la tabla siguiente se explican los distintos atributos asociados al objeto Blogposts.

|Atribui   |Descripción   |
|---|---|
| Todos | Devuelve todos los objetos blog de la colección. |

### <a name="blogpost-object"></a>Objeto blog

Hace referencia a una sola entrada de blog.

En la tabla siguiente se explican los distintos atributos asociados al objeto blog.

|Atribui   |Descripción   |
|---|---|
| Dirección            | Dirección URL de la publicación.                                                                |
| Content        | Devuelve el campo de contenido para la publicación.                                             |
| Content        | Devuelve el campo de contenido para la publicación.                                             |
| frente         | Devuelve el authorf para la publicación (que es simplemente un objeto de entidad contact.          |
| Titulo          | Título de la publicación.                                                              |
| recuento de\_de comentarios | Devuelve el valor entero del recuento de cuántos comentarios hay para un post determinado. |
| fecha de\_de publicación  | Fecha en la que se publicó la publicación.                                           |

## <a name="entities"></a>jurídica

Permite cargar cualquier entidad de PowerApps por identificador. Si la entidad existe, se devolverá un objeto entidad. Si no se encuentra una entidad con el identificador especificado, se devolverá [null](liquid-types.md#null) .  

```
{% assign account = entities.account['936DA01F-9ABD-4d9d-80C7-02AF85C822A8'] %}

{% if account %}

{{ account.name }} ({{ account.statecode.label }})

{% endif %}

{% assign entity_logical_name = 'contact' %}

{% assign contact = entities[entity_logical_name][request.params.contactid] %}

{% if contact %}

{{ contact.fullname }} ({{ contact.parentcustomerid.name }})

{% endif %}
```

### <a name="entity"></a>ID

Un objeto entidad proporciona acceso a los atributos de un registro de entidad de PowerApps.


|             Atribui              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 Identificador                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    IDENTIFICADOR GUID de la entidad, como una cadena. Por ejemplo, 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           nombre del\_lógico            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   El nombre lógico de PowerApps de la entidad.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               Notas                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Carga las notas (anotación) asociadas a la entidad, ordenadas de más antiguo a más reciente (creado). Las notas se devuelven como objetos de nota.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            Los             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Carga los resultados de aserción de permisos de entidad para la entidad. Los resultados se devuelven como un objeto de permisos.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                Dirección                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Devuelve la ruta de acceso de la dirección URL del sistema de administración de contenido del portal de PowerApps para la entidad. Si la entidad no tiene una dirección URL válida en el sitio web actual, devuelve NULL. Por lo general, esto solo devolverá un valor para determinados tipos de entidad que se han integrado en el CMS del portal, a menos que haya personalizado el proveedor de direcciones URL en la aplicación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[nombre de relación o atributo\] | Puede tener acceso a cualquier atributo de la entidad de PowerApps por nombre lógico. `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>Los valores de la mayoría de los atributos de entidad se asignan directamente a los [tipos de líquido](liquid-types.md): dos campos de opciones se asignan a valores booleanos, campos de texto a cadenas, campos numéricos/moneda a números, campos de fecha y hora hasta objetos de fecha. Pero algunos tipos de atributos se devuelven como objetos:<ul><li>Los campos Lookup (referencia de entidad) se devuelven como objetos de referencia de entidad.</li><li>Los campos conjunto de opciones/lista desplegable se devuelven como objetos de valor de conjunto de opciones.</li><li>También puede cargar cualquier entidad relacionada por nombre de esquema de relación.</li>`{{ page.adx_webpage_entitylist.adx_name }}`en el caso de que una relación sea reflexiva (es decir, autoreferencial), se devolverá un objeto de relación reflexiva. (De lo contrario, el resultado sería ambiguo).`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Nota**: la carga de un gran número de entidades relacionadas, o el acceso a un gran número de relaciones en una sola plantilla, puede tener un impacto negativo en el rendimiento de la representación de la plantilla. Evite la carga de entidades relacionadas para cada elemento de una matriz, dentro de un bucle. Siempre que sea posible, use [etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md) para cargar colecciones de entidades. |

### <a name="entity-reference"></a>Referencia de entidad

Los valores de atributo de búsqueda se devuelven como objetos de referencia de entidad, con los siguientes atributos.


|   Atribui   |                                                Descripción                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      Identificador       | IDENTIFICADOR GUID de la entidad a la que se hace referencia, como una cadena. <br> Por ejemplo, 936DA01F-9ABD-4d9d-80C7-02AF85C822A8 |
| nombre del\_lógico |  El nombre lógico de PowerApps de la entidad a la que se hace referencia.   |
|     Nombre      |                           Atributo de nombre principal de la entidad a la que se hace referencia.                            |

### <a name="note"></a>Nota

Una nota es un objeto entidad que proporciona acceso a los atributos y las relaciones de un registro de anotaciones. Además de todos los atributos de un objeto entidad, una nota tiene los siguientes atributos adicionales.


|  Atribui   |                                                                                                                                                                                                                                  Descripción                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | Carga el atributo documentbody del registro de anotaciones de nota, como una cadena codificada en Base64. Dado que el contenido de este atributo puede ser grande, no se carga con el resto de los atributos de nota, solo se carga a petición. <br> **Nota**: el uso del atributo documentbody puede tener un impacto negativo en el rendimiento de la representación de la plantilla y debe hacerse con precaución.<br>En su lugar, use el atributo URL para proporcionar un vínculo a los datos adjuntos de la nota, si es posible. |
|     Dirección      |                                                                                                                                   Devuelve la ruta de acceso de la dirección URL del controlador de datos adjuntos de anotación del portal integrado. Si el usuario tiene permiso y la nota tiene un archivo adjunto, una solicitud a esta dirección URL descargará los datos adjuntos del archivo de notas.                                                                                                                                    |

>[!Note]
> [Filtros adicionales](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>Valor del conjunto de opciones

Los valores de atributo de conjunto de opciones/lista desplegable se devuelven como objetos de referencia de entidad, con los siguientes atributos.

| Atribui | Descripción                                                     |
|-----------|-----------------------------------------------------------------|
| Etiquetas     | Etiqueta localizada del valor del atributo conjunto de opciones/lista desplegable. Por ejemplo, Active|
| Value     | Valor entero del valor del atributo conjunto de opciones/lista desplegable. Por ejemplo, 0                                                           |

### <a name="entity-permissions"></a>Permisos de entidad

El objeto Entity Permissions proporciona acceso a los resultados de aserción de permisos agregados para una entidad.

| Atribui       | Descripción                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \_puede anexar     | Devuelve true si el usuario actual tiene permiso para anexar registros a las relaciones de este registro. Devuelve false en caso contrario.                                                                                              |
| \_puede anexar\_a | Devuelve true si el usuario actual tiene permiso para anexar este registro a una relación de otra entidad. Devuelve false en caso contrario.                                                                                      |
| \_puede crear     | Devuelve true si el usuario actual tiene permiso para crear nuevos registros de este tipo de entidad. Devuelve false en caso contrario.                                                                                                      |
| \_se puede eliminar     | Devuelve true si el usuario actual tiene permiso para eliminar este registro. Devuelve false en caso contrario.                                                                                                                          |
| \_puede leer       | Devuelve true si el usuario actual tiene permiso para leer este registro. Devuelve false en caso contrario.                                                                                                                            |
| \_puede escribir      | Devuelve true si el usuario actual tiene permiso para actualizar este registro. Devuelve false en caso contrario.                                                                                                                          |
| \_existen reglas    | Devuelve true si los resultados de permiso que representa este objeto son el resultado de las reglas de permisos definidas explícitamente. Devuelve false si son los resultados predeterminados en ausencia de permisos definidos explícitamente. |

### <a name="reflexive-relationship"></a>Relación reflexiva

Los intentos de cargar relaciones reflexivas (es decir, autoreferencial) en las entidades se devuelven como objetos con los siguientes atributos.

| Atribui     | Descripción                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| es\_reflexiva | Devuelve true. Se puede utilizar para comprobar si un objeto devuelto por una relación es un objeto de relación reflexiva. |
| hace referencia    | Devuelve una matriz de entidades a las que se hace referencia para la relación especificada.                                           |
| referencia   | Devuelve una entidad de referencia para la relación especificada. Devuelve NULL si no existe ninguna entidad de referencia. Si la relación es de varios a varios (N:N), devuelve una matriz de entidades de referencia.                          

## <a name="entitylist"></a>entitylist

El objeto entitylist se usa dentro de las [etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md). Proporciona acceso a todos los atributos de una lista de entidades determinada.  

> [!Note]                                                       
> [Representar la lista de entidades asociada a la página actual](render-entity-list-current-page.md)

### <a name="attributes"></a>Atributos

> [!Note]
> [jurídica](#entities)

|               Atribui               |                                                                                                                            Descripción                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            crear\_habilitado            |                                                                                Devuelve true si la creación de nuevos registros está configurada para la lista de entidades. Devuelve false en caso contrario.                                                                                |
|              crear\_URL              |                                                                                          Devuelve la ruta de acceso de la dirección URL configurada para un vínculo o botón de creación para la lista de entidades.                                                                                          |
|            \_de detalle habilitado            |                                                                         Devuelve true si se configura una vista de detalle para registros individuales para la lista de entidades. Devuelve false en caso contrario.                                                                          |
|         parámetro\_de ID\_de detalle         |               Devuelve el nombre del parámetro de cadena de consulta que se va a usar para el ID. de registro al construir una dirección URL de vista de detalle de registro. Consulte [filtros de URL](liquid-filters.md#url-filters) para más información sobre el uso de filtros Liquid para construir direcciones URL. Por ejemplo, ID.                |
|             etiqueta de\_de detalle             |                                                                                     Devuelve la etiqueta localizada configurada para los vínculos y botones de la vista de detalles de la lista de entidades.                                                                                     |
|              URL de\_de detalle              |                                                                                       Devuelve la ruta de acceso de la dirección URL configurada para los vínculos y botones de la vista de detalles de la lista de entidades.                                                                                        |
|           \_texto en la lista de\_vacía           |                                                                                Devuelve el texto localizado configurado que se va a mostrar cuando la vista de lista de entidades no devuelve resultados.                                                                                |
|      habilitar\_Entity\_permisos      |                                                                               Devuelve true si está habilitado el filtrado de permisos de entidad para esta lista de entidades. Devuelve false en caso contrario.                                                                               |
|         nombre del\_lógico\_Entity         |                                                 Devuelve el nombre lógico de la entidad de PowerApps para los registros que se van a mostrar en esta lista de entidades. Por ejemplo, póngase en contacto con                                                 |
|   filtrar\_cuenta\_atributo\_nombre    |                                            Devuelve el nombre lógico del atributo de la búsqueda que se va a usar para filtrar los registros de resultados por la cuenta primaria del usuario del portal actual. Por ejemplo, accountID                                            |
|         filtrar\_aplicar\_etiqueta          |                                                            Devuelve la etiqueta localizada configurada que se va a usar para el vínculo o botón que aplica un filtro de atributo avanzado a los resultados de la lista de entidades.                                                            |
|          definición de\_de filtro           |                      Devuelve la definición de filtro de atributo JSON para la lista de entidades. Consulte [filtros](liquid-filters.md#entity-list-filters) de la lista de entidades para obtener más información sobre cómo usar el filtro Liquid de metafiltros para procesar esta definición.                       |
|            \_de filtro habilitado            |                                                                               Devuelve true si el filtrado de atributos avanzado está habilitado para la lista de entidades. Devuelve false en caso contrario.                                                                               |
| filtro de\_de\_de usuario\_atributo\_nombre |                                                 Devuelve el nombre lógico del atributo de la búsqueda que se va a usar para filtrar los registros de resultados por el contacto actual del usuario del portal. Por ejemplo, ContactID                                                  |
|   filtrar\_sitio web\_atributo nombre\_    |                                              Devuelve el nombre lógico del atributo para la búsqueda en ADX\_sitio web que se utilizará para filtrar los registros de resultados por el sitio web del portal actual. Por ejemplo, ADX\_websiteid                                              |
|            código de lenguaje\_             |                                               Devuelve el código de idioma del entero de PowerApps que se usará para seleccionar todas las etiquetas localizadas para esta lista de entidades.                                                |
|              tamaño de\_de página               |                                                                                                   Devuelve el tamaño de página de resultados configurado para la lista de entidades.                                                                                                    |
|          nombre\_clave del\_principal           |                                                                                  Devuelve el nombre lógico del atributo de clave principal para los registros que se van a mostrar en esta lista de entidades.                                                                                  |
|            búsqueda\_habilitada            |                                                                                         Devuelve true si la búsqueda está habilitada para esta lista de entidades. Devuelve false en caso contrario.                                                                                          |
|          marcador de posición de\_de búsqueda          |                                                                                        Devuelve el texto localizado configurado para el marcador de posición de campo de búsqueda de la lista de entidades.                                                                                        |
|            Buscar en la información sobre herramientas\_            |                                                                                             Devuelve el texto localizado configurado para la información sobre herramientas de búsqueda de la lista de entidades.                                                                                             |
|                 Vistas                 |                                                                                           Devuelve las vistas disponibles para la lista de entidades, como objetos de vista de lista de entidades.                                                                                           |
|      \[nombre lógico del atributo\]       | Puede tener acceso a cualquier atributo del registro de la lista de entidades (ADX\_entitylist) PowerApps por nombre lógico, de la misma manera que un objeto [entidad](liquid-objects.md#entity) . Por ejemplo, {{entitylist. ADX\_nombre}} |

### <a name="entity-list-view-attributes"></a>Atributos de la vista de lista de entidades

|          Atribui          |                                                                                     Descripción                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Columnas           |                                                         Devuelve las columnas de la vista como objetos de columna de la vista de lista de entidades.                                                         |
|    nombre del\_lógico\_Entity    |               Devuelve el nombre lógico de la entidad de PowerApps para los registros incluidos en la vista. Por ejemplo, póngase en contacto con                |
|             Identificador              |                                                                          Devuelve el identificador de GUID de la vista.                                                                           |
|       código de lenguaje\_        | Devuelve el código de idioma de entero de PowerApps que se usará para seleccionar todas las etiquetas localizadas (encabezados de columna, etc.) de la vista. |
|            Nombre             |                                          Devuelve el nombre para mostrar de PowerApps de la vista.                                          |
| clave de\_principal\_nombre de\_lógico |        Devuelve el nombre lógico de la clave principal de la entidad de PowerApps para los registros incluidos en la vista. Por ejemplo, ContactID         |
|      ordenar\_expresión       |                                               Devuelve la expresión de ordenación predeterminada para la vista. Por ejemplo, nombre ASC, creada DESC                                               |

### <a name="entity-list-view-column-attributes"></a>Atributos de columna de la vista de lista de entidades

|    Atribui     |                                                                                    Descripción                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| tipo de\_de atributo  | Devuelve el nombre del tipo de atributo PowerApps para la columna, como una cadena. Por ejemplo, búsqueda, lista desplegable, cadena, booleano, fecha y hora |
|  nombre del\_lógico   |                       Devuelve el nombre lógico del atributo PowerApps para la columna. Por ejemplo, creaon                       |
|       Nombre       |                      Devuelve el nombre para mostrar de PowerApps localizado para la columna. Por ejemplo, creado el                       |
| ordenar\_ascendente  |                                      Devuelve una cadena de expresión de ordenación para ordenar la columna en orden ascendente. Por ejemplo, ha creado ASC                                       |
| ordenar\_descendente |                                     Devuelve una cadena de expresión de ordenación para ordenar la columna en orden descendente. Por ejemplo, se ha creado DESC                                      |
|  ordenar\_deshabilitado  |                                                   Devuelve true si la ordenación está deshabilitada para la columna. Devuelve false en caso contrario.                                                    |
|  \_de ordenación habilitada   |                                                    Devuelve true si está habilitada la ordenación para la columna. Devuelve false en caso contrario.                                                    |
|      ancho       |                                                              Devuelve el ancho configurado para la columna, en píxeles.                                                              |

## <a name="entityview"></a>entityview

El objeto entityview se usa dentro de la etiqueta entityview y proporciona acceso a los metadatos de la vista, además de para ver los registros de resultados.

### <a name="attributes"></a>Atributos

|          Atribui          |                                                                               Descripción                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Columnas           |                         Devuelve las columnas de la vista, como [objetos de columna](liquid-objects.md#entity-list-view-column-attributes)de la vista de entidad.                          |
| \_denegado el permiso de\_de entidad  | Devuelve true si se denegó el acceso a los resultados de la vista debido a que no hay suficientes permisos de entidad para el usuario actual. Devuelve false si se ha concedido acceso de lectura a los resultados de la vista. |
|    nombre del\_lógico\_Entity    |                   El nombre lógico de la entidad de PowerApps de los registros de resultados de la vista. Por ejemplo, póngase en contacto con                   |
|         primera\_página         |                 El número de página de la primera página de resultados de la vista. Será 1 a menos que no se devuelva ningún resultado, en cuyo caso será null.                  |
|             Identificador              |                            IDENTIFICADOR de GUID de la vista de PowerApps que define este entityview.                             |
|       código de lenguaje\_        |             El código de idioma de entero de PowerApps que se usa para cargar las etiquetas localizadas de la vista actual.              |
|         última página de\_          |                                 Número de página de la última página de resultados de la vista. Si no se devolvieron resultados, será null.                                  |
|            Name             |              El nombre de la vista de PowerApps que define este entityview., por ejemplo, contactos activos.               |
|         Página de\_siguiente          |                                El número de página de la página siguiente de resultados de la vista. Si no hay ninguna página de resultados siguiente, será null.                                 |
|            del             |                                                           Número de página de la página actual de resultados de la vista.                                                           |
|            Páginas            |                                          Devuelve una matriz de números de página que contiene todas las páginas de resultados de la vista actual.                                          |
|         tamaño de\_de página          |                                                      Número de resultados devueltos por página para la vista actual.                                                       |
|       Página de\_anterior        |                              El número de página de la página siguiente de resultados de la vista. Si no hay ninguna página anterior de resultados, será null.                               |
| clave de\_principal\_nombre de\_lógico |  El nombre lógico de PowerApps del atributo de clave principal de la entidad de resultado para esta vista. Por ejemplo, ContactID.   |
|           Informes           |                                                   La página actual de registros de resultados de la vista, como objetos entidad.                                                    |
|      ordenar\_expresión       |                                             Expresión de ordenación predeterminada para la vista. Por ejemplo, nameASC, crease DESC.                                              |
|        total de páginas\_         |                                                              Número total de páginas de resultados de la vista.                                                              |
|       total de registros de\_        |                                                       Número total de resultados de la vista (en todas las páginas).                                                       |

## <a name="events"></a>Ceso

Proporciona la capacidad de obtener acceso y representar eventos. El objeto Events le permite seleccionar un evento específico o todos los eventos.

### <a name="events-object"></a>Events (objeto)

El objeto Events le permite tener acceso a cualquier evento específico en el portal o tener acceso a todos los eventos del portal (independientemente del evento).

El objeto Events tiene los siguientes atributos:

|Atribui   |Descripción   |
|---|---|
|peticiones |Devuelve un eventoccurancessobject que contiene todas las repeticiones del evento en el portal. |
|[nombre o ID. de evento] |Puede tener acceso a cualquier evento por sus propiedades name o ID.<br>{% Assign Event = Events [&quot;nombre del evento&quot;]%}<br>{% Assign Event = Events [&quot;da8b8a92-2ee6-476f-8A21-782b047ff460&quot;]%} |

### <a name="event-object"></a>Objeto de evento

El objeto de evento le permite trabajar con un solo evento, lo que le permite tener acceso a las programaciones y las repeticiones de ese evento.

El objeto de evento tiene los siguientes atributos:

|Atribui   |Descripción   |
|---|---|
| Apariciones | Devuelve un eventoccurrencesobject que contiene todas las repeticiones del evento. |
| Name       | Nombre del evento.                                                     |
| Dirección        | Dirección URL del evento.                                                      |

### <a name="eventoccurences-object"></a>Objeto eventoccurences

El objeto eventoccurrences permite obtener acceso a una colección de objetos de repeticiones de eventos. Puede ordenar las repeticiones del evento y especificar un intervalo de fechas para las repeticiones que se van a recuperar y para lograr la paginación también mediante filtros líquidos.

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

Tenga en cuenta que

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

también es posible.

Los atributos siguientes están asociados al objeto eventoccurrences

|Atribui   |Descripción   |
|---|---|
| Todos | Devuelve todos los objetos eventoccurance de la colección. |

### <a name="eventoccurence-object"></a>Objeto eventoccurence

Representa una única repetición del evento. A continuación se indican los atributos asociados:

|Atribui   |Descripción   |
|---|---|
| Dirección                 | Dirección URL de la repetición.    |
| es\_\_día\_evento | ¿Se trata de un evento de día completo?     |
| iniciar hora de\_         | La hora de inicio del evento. |
| finalizar\_hora           | La hora de finalización del evento.   |


## <a name="forloop"></a>forloop

Contiene propiedades útiles dentro de un bloque de bucles [for](iteration-tags.md#for) .  

> [!Note]
> forloop solo se puede usar dentro de una etiqueta [for](iteration-tags.md#for) .

**Codifica**

```
{% for child in page.children %}

{% if forloop.first %}

This is the first child page!

{% else %}

This is child page number {{ forloop.index }}.

{% endif %}

{% endfor %}
```

**Genere**

```
This is the first child page!

This is child page number 2.

This is child page number 3.
```

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| Lugar   | Devuelve true si es la primera iteración del bucle. Devuelve false si no es la primera iteración.       |
| Ajustar   | La posición del elemento actual en la colección, donde el primer elemento tiene una posición de 1.                   |
| index0  | La posición del elemento actual en la colección, donde el primer elemento tiene una posición de 0.                   |
| Last    | Devuelve true si es la última iteración del bucle. Devuelve false si no es la última iteración.         |
| longitud  | Devuelve el número de iteraciones para el bucle ߝ el número de elementos de la colección que se recorren en iteración. |
| rindex  | Número de elementos restantes en el bucle (length-index), donde 1 es el índice del último elemento.              |
| rindex0 | Número de elementos restantes en el bucle (length-index), donde 0 es el índice del último elemento.              |


## <a name="forums"></a>foros

Proporciona la capacidad de obtener acceso y representar foros y subprocesos del foro. Tenga en cuenta que la capacidad de usar Liquid para representar los datos del Foro se extiende a las publicaciones, pero para crear un nuevo envío o subproceso, debe usar una plantilla de página de formularios Web Forms de ASP.NET con la funcionalidad integrada (como las plantillas predeterminadas de la página de blog del foro y el subproceso del foro).

El objeto forums le permite seleccionar un foro o conversaciones de foros:

```
<div class=content-panel panel panel-default>

<div class=panel-heading>

<h4>

<span class=fa fa-comments aria-hidden=true></span>

{{ snippets[Home Forum Activity Heading] | default: Forum Activity | h }}

</h4>

</div>

{% for forum in website.forums %}

<ul class=list-group>

<li class=list-group-item>

<div class=row>

<div class=col-sm-6>

<h4 class=list-group-item-heading><a href="{{ forum.url | h }}"> {{ forum.name | h }}</a></h4>

<div class=list-group-item-text content-metadata>{{ forum.adx_description | h }}</div>

</div>

<div class=col-sm-3 content-metadata>{{ forum.thread_count }} threads</div>

<div class=col-sm-3 content-metadata>{{ forum.post_count }} posts</div>

</div>

</li>

</ul>

{% endfor %}

</div>
```

### <a name="forums-object"></a>Objeto forums

El objeto forums le permite acceder a cualquier foro específico en el portal o acceder a todos los subprocesos del foro en el portal (independientemente del foro).

El objeto Forum le permite trabajar con un solo foro, permitiéndole tener acceso a los subprocesos de ese foro.

El objeto forumthreads permite acceder a una colección de objetos forumthread. Puede ordenar los subprocesos del foro y obtener la paginación también con filtros líquidos.

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

Un solo subproceso de foro

El objeto forumposts permite acceder a una colección de objetos forumpost.

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| ThreadPool              | Devuelve un objeto forumthreads que contiene todos los objetos forumthread del portal.             |
| Todos                  | Devuelve todos los objetos del foro en el portal. Tenga en cuenta que sitio Web. foros también es equivalente.    |
| recuento de\_de subprocesos        | Devuelve el valor entero del recuento de número de subprocesos que hay en todo el sitio Web. |
| recuento de\_posteriores          | Devuelve el valor entero del número total de publicaciones en el portal.                       |
| \[el nombre o el identificador del Foro\] | Puede tener acceso a cualquier foro mediante sus propiedades de nombre o ID. <br>' {% Assign Forum = Forums [nombre del Foro]%}<br>{% Assign Forum = Forums [da8b8a92-2ee6-476f-8A21-782b047ff460]%} 

### <a name="forum-object"></a>Objeto Forum

### <a name="attributes"></a>Atributos

> [!Note]
> [jurídica](#entities)

|Atribui   |Descripción   |
|---|---|
| ThreadPool       | Devuelve un objeto forumthreads que contiene todos los subprocesos del foro para el foro.               |
| Nombre          | Nombre del foro.                                                                  |
| recuento de\_de subprocesos | Devuelve el valor entero del recuento de número de subprocesos que hay en el foro.      |
| recuento de\_posteriores   | Devuelve el valor entero del recuento del número de entradas que hay en el foro completo. |

### <a name="forumthreads-object"></a>Objeto forumthreads

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| Todos | Devuelve todos los objetos forumthread de la colección. |

### <a name="forumthread-object"></a>Objeto forumthread

### <a name="attributes"></a>Atributos

> [!Note]
> [jurídica](#entities)

|Atribui   |Descripción   |
|---|---|
| publique        | Devuelve un objeto forumposts que contiene todas las entradas del Foro del subproceso.            |
| frente       | Devuelve el autor del subproceso (que es simplemente un objeto de entidad de contacto).      |
| última\_post | Devuelve la última entrada del subproceso.                                            |
| primera\_post  | Devuelve el primer envío del subproceso.                                             |
| recuento de\_posteriores  | Devuelve el valor entero del recuento del número de entradas que hay en el subproceso. |
| \_responde | ¿El subproceso responde o no?                                                    |
| es\_permanente   | ¿El subproceso es un subproceso permanente?                                                    |

### <a name="forumposts-object"></a>Objeto forumposts

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| Todos | Devuelve todos los objetos forumthread de la colección. |

Una sola entrada de foro

### <a name="attributes"></a>Atributos

> [!Note] 
> [jurídica](#entities)

|Atribui   |Descripción   |
|---|---|
| frente     | Devuelve el autor de la publicación (que es simplemente un objeto de entidad de contacto). |
| Content    | Contenido de la publicación.                                                   |
| es\_respuesta | ¿Esta publicación es una respuesta al subproceso?                                      |


## <a name="knowledge"></a>conocen

Proporciona acceso a los registros de entidades knowledgearticle y Category de PowerApps para representar artículos y categorías en un portal.

### <a name="attributes"></a>Atributos

|Atribui|Descripción|
|---|---|
|consultar|Devuelve un objeto articles que contiene objetos de artículo para los registros de entidad knowledgearticle disponibles en el portal.|
|categorías|Devuelve un objeto de categorías que contiene objetos de categoría para los registros de entidad de categoría disponibles en el portal.|
|||

### <a name="articles-object"></a>articles (objeto)

El objeto articles le permite tener acceso a una colección de objetos article. Puede ordenar los artículos y obtener la paginación también con filtros líquidos.

```
{% assign count = count | default: 3 %}
{% assign languagecode = website.selected_language.code %}
{% assign popular_articles = knowledge.articles | popular: count,languagecode  %}
{% if popular_articles %}
    <div class=list-group>
    {% for article in popular_articles %}
      <div class=list-group-item clearfix>
        <a class=title href={{ article.url | escape }}>{{ article.title | escape }}</a>
        <p class=description>{{ article.description | escape }}</p>
      </div>
    {% endfor %}
    </div>
{% endif %}
```

### <a name="attributes"></a>Atributos

|Atribui|Descripción|
|---|---|
|utilizada |Devuelve una colección de objetos de artículo que contienen la mayoría de las vistas. `{% assign popular_articles = knowledge.articles.popular %}` |
|último |Devuelve una colección de objetos article que contiene la última fecha modificada. `{% assign recent_articles = knowledge.articles.recent %}` |
|top |Devuelve una colección de objetos de artículo que contienen la clasificación más alta. `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>complementa

Los filtros siguientes pueden aceptar parámetros opcionales para el tamaño de página y el idioma. El primer parámetro es el número o los registros que se van a recuperar. El tamaño de página predeterminado es 5. El segundo parámetro es el código de un lenguaje para recuperar artículos para un idioma determinado. Los filtros se pueden combinar con otros [filtros Liquid](liquid-filters.md).

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|Atribui|Descripción|
|---|---|
|utilizada |Devuelve una colección de objetos de artículo que contienen la mayoría de las vistas. `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|último |Devuelve una colección de objetos article que contiene la última fecha modificada. `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|top |Devuelve una colección de objetos de artículo que contienen la clasificación más alta. `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>Categories (objeto)

El objeto Categories permite tener acceso a una colección de objetos Category. Puede ordenar las categorías y obtener la paginación también con filtros líquidos.

```
{% assign category_url = sitemarkers['Category'].url %}
  {% assign count = count | default: 0 %}  
  {% assign categories = knowledge.categories | top_level: count %}
  {% if categories %}
    <div class=list-group unstyled>
    {% for category in categories %}
      <a href={{ category_url | add_query: 'id', category.categorynumber }} class=list-group-item>
        {{ category.title }}
      </a>
    {% endfor %}
    </div>
  {% endif %}
```

### <a name="attributes"></a>Atributos

|Atribui|Descripción|
|---|---|
|último |Devuelve una colección de objetos Category que contiene la última fecha modificada. |
|top_level |Devuelve una colección de objetos de categoría que no tienen una categoría primaria. |
|||

### <a name="filters"></a>complementa

Los filtros siguientes pueden aceptar un parámetro opcional que indica el tamaño de página. El tamaño de página predeterminado es 5. Los filtros se pueden combinar con otros [filtros Liquid](liquid-filters.md).

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|Atribui|Descripción|
|---|---|
|último |Devuelve una colección de objetos Category que contiene la última fecha modificada. Puede proporcionar parámetros `{% assign recent_categories = knowledge.categories \| recent: 10 %}` |
|top_level |Devuelve una colección de objetos de categoría que no tienen una categoría primaria. `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>Objeto Article

El objeto Article le permite trabajar con un solo knowledgearticle para mostrar los detalles de ese artículo en el portal.

### <a name="attributes"></a>Atributos

el artículo es un objeto [entidad](#entity) , con todos los mismos atributos, además de los que se enumeran a continuación.

|Atribui|Descripción|
|---|---|
|article_public_number| El artículo número público del artículo.|
|comment_count| Valor entero del recuento de la cantidad de comentarios que hay en un artículo determinado.|
|Content|Contenido del artículo.|
|current_user_can_comment|Devuelve un valor booleano que indica si el usuario actual puede agregar comentarios en el artículo.|
|is_rating_enabled|Devuelve un valor booleano que indica si está habilitada la clasificación en un artículo.|
|palabra|Palabras clave del artículo.|
|Name|Un alias alternativo para el título del artículo.|
|Clasific|Valor de clasificación decimal del artículo.|
|Titulo|Título del artículo.|
|view_count|Valor entero del número de veces que se ha visto el artículo.|
|||

### <a name="category-object"></a>Objeto de categoría

El objeto de categoría permite trabajar con una única categoría para mostrar sus detalles en el portal.

### <a name="attributes"></a>Atributos

Category es un objeto [entidad](#entity) , con todos los mismos atributos, además de los que se enumeran a continuación.

|Atribui|Descripción|
|---|---|
|categorynumber|El número de categoría de la categoría.|
|Name|Un alias alternativo para el título de la categoría.|
|Titulo|Título de la categoría.|
|||

## <a name="page"></a>del

Hace referencia a la página de solicitud del portal actual. Este objeto combina los atributos del [mapa del sitio](#sitemap) y las [entidades](#entities) de solicitud actuales (normalmente una página web).  

El objeto de página proporciona acceso a elementos como las rutas de navegación de la página actual, el título o la dirección URL de la página actual y cualquier otro atributo o entidad relacionada del registro de PowerApps subyacente.

```
<ul class=breadcrumb>

{% for crumb in page.breadcrumbs %}

<li><a href={{ crumb.url | escape }}>{{ crumb.title | escape }}</a></li>

{% endfor %}

<li class=active>{{ page.title | escape }}</li>

</ul>

<div class=page-header>

<h1>{{ page.title | escape }}</h1>

</div>

<div class=page-copy>

{{ page.adx_copy }}

</div>

<div class=list-group>

{% for child in page.children %}

<a class=list-group-item href={{ child.url | escape }}>

{{ child.title | escape }}

</a>

{% endfor %}

</div>

<!-- Page {{ page.id }} was last modified on {{ page.modifiedon }}. -->
```

### <a name="page-attributes"></a>Atributos de página

> [!Note]  
> [jurídica](#entities)

|             Atribui              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Exploración             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Devuelve los objetos de nodo del mapa del sitio de la ruta de navegación para la página, empezando por el nodo raíz del mapa del sitio y finalizando en el elemento primario.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              Dominios              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Devuelve los objetos de nodo del mapa del sitio secundario de la página.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               aérea               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Devuelve el nodo del mapa del sitio primario de la página. Si la página es la Página principal, Parent será null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               Titulo                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Título de la página.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                Dirección                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Dirección URL de la página.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[nombre de relación o atributo\] | Puede tener acceso a cualquier atributo del registro de PowerApps subyacente de la página por nombre lógico.<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>Los valores de la mayoría de los atributos de entidad se asignan directamente a los [tipos de líquido](liquid-types.md): dos campos de opciones se asignan a valores booleanos, campos de texto a cadenas, campos numéricos/moneda a números, campos de fecha y hora hasta objetos de fecha. Pero algunos tipos de atributos se devuelven como objetos:<ul><li>Los campos Lookup (referencia de entidad) se devuelven como [objetos de referencia de entidad](#entity-reference).</li><li>Los campos conjunto de opciones/lista desplegable se devuelven como [objetos de valor de conjunto de opciones](#option-set-value).</li> También puede cargar cualquier entidad relacionada por nombre de esquema de relación. <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>En el caso de que una relación sea reflexiva (es decir, autoreferencial), se devolverá un objeto de [entidades](#entities) . (De lo contrario, el resultado sería ambiguo).`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Nota**: la carga de un gran número de entidades relacionadas, o el acceso a un gran número de relaciones en una sola plantilla, puede tener un impacto negativo en el rendimiento de la representación de la plantilla. Evite la carga de entidades relacionadas para cada elemento de una matriz, dentro de un bucle. Siempre que sea posible, se prefiere el uso de las [etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md) para cargar colecciones de entidades. |

## <a name="polls"></a>sondea

Proporciona la capacidad de obtener acceso y representar un sondeo.

El objeto Polls le permite seleccionar una ubicación de sondeo o sondeo específico:

```
<div>

{% assign poll = polls[Poll Name] %}

<h4>{{ poll.question }}</h4>

{% for option in poll.options %}

<div>

<input type=radio name={{ poll.name }} id={{ option.id }} />

<label for={{ option.id }}>{{ option.answer }}</label>

</div>

{% endfor %}

<button type=button>{{ poll.submit_button_label }}</button>

</div>
```

### <a name="polls-attributes"></a>Sondear atributos

|Atribui   |Descripción   |
|---|---|
| ubicaciones          | Devuelve el objeto pollplacements.                                      |
| \[el identificador o el nombre del sondeo\] | Puede tener acceso a cualquier sondeo por sus propiedades name o ID. `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>Atributos de las ubicaciones de sondeo

|Atribui   |Descripción   |
|---|---|
| \[el identificador o el nombre de selección de sondeo\] | Puede tener acceso a cualquier selección de ubicación de sondeo por sus propiedades de nombre o ID.`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>Atributos de selección de ubicación de sondeo

> [!Note] 
> [jurídica](#entities)                                       

|Atribui   |Descripción   |
|---|---|
| Nombre           | Devuelve el campo de nombre para la selección de ubicación del sondeo.                            
| Dirección URL de\_de ubicación | La dirección URL que se puede utilizar para recuperar la ubicación del sondeo totalmente representada por una plantilla.                       |
| sondea          | Devuelve la colección de objetos de sondeo asociados a la colocación. Las [etiquetas de iteración](iteration-tags.md) y los [filtros de matriz](liquid-filters.md#array-filters) se pueden usar con esta colección.  |  
| URL de\_aleatorio    | La dirección URL que se puede utilizar para recuperar un sondeo aleatorio de la ubicación representada por una plantilla.         |
| enviar dirección URL de\_    | Dirección URL a la que se envía un sondeo completado.                                                             |

### <a name="poll-attributes"></a>Atributos de sondeo

> [!Note] 
> [jurídica](#entities)                                          

|Atribui   |Descripción   |
|---|---|
| tiene\_usuario\_votó       | Devuelve true si el usuario actual (con sesión iniciada o anónima) ya ha votado en este sondeo.         |
| Nombre                   | Devuelve el campo de nombre del sondeo.                                                              |
| Opciones                | Devuelve la colección de objetos de opción de sondeo asociados al sondeo. Las [etiquetas de iteración](iteration-tags.md) y las [entidades](#entities) se pueden usar con esta colección.  |  
| Dirección URL de\_de sondeo              | La dirección URL que se puede usar para recuperar el sondeo completo representado por una plantilla.                       |
| correspondiente               | Devuelve el campo de pregunta para el sondeo.                                                          |
| botón Enviar\_\_etiqueta  | Devuelve una cadena que se puede usar para invalidar la etiqueta del botón de envío para el sondeo.               |
| enviar dirección URL de\_            | Dirección URL a la que se envía un sondeo completado.                                                   |
| opción de\_de usuario\_seleccionada | Devuelve el objeto polloption seleccionado por el usuario (si ya ha votado).                  |
| votos                  | Devuelve el número de votos que se han tabulado para el sondeo.                                |

### <a name="poll-option-attributes"></a>Atributos de opción de sondeo

>[!Note]
> [jurídica](#entities)                                         

|Atribui   |Descripción   |
|---|---|
| Respuesta     | Devuelve el campo de respuesta para el sondeo. |
| proporción | Devuelve el porcentaje de votos en el sondeo de la opción como un número decimal comprendido entre 0 y 100. |
| votos      | Devuelve el número de votos que se han tabulado para la opción.                              |


## <a name="request"></a>Solicite

Contiene información sobre la solicitud HTTP actual.

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> Puede compilar las direcciones URL dinámicamente en Liquid mediante filtros de URL. 

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| params           | Valores de parámetro con nombre para la solicitud actual. params es una combinación de parámetros de cadena de consulta de dirección URL, parámetros de envío de formulario y cookies.  |
| Camino             | Ruta de acceso de la dirección URL de la solicitud actual. <br> /Profile|
| \_de ruta de acceso y\_consulta | La ruta de acceso y la consulta de la dirección URL de la solicitud actual.<br> /Profile/? foo = 1 & Bar = algo|
| query            | La parte de la consulta de la dirección URL de la solicitud actual. <br> ? foo = 1 & Bar = algo |
| Dirección              | Dirección URL completa de la solicitud actual.<br>  https://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>searchindex

El objeto searchindex se usa dentro de las [etiquetas de entidad de servicio de datos común de PowerApps](portals-entity-tags.md)y proporciona acceso a los resultados de una consulta.  

```
{% searchindex query: 'support', page: params.page, page_size: 10 %}

{% if searchindex.results.size > 0 %}

<p>Found about {{ searchindex.approximate_total_hits }} matches:</p>

<ul>

{% for result in searchindex.results %}

<li>

<h3><a href={{ result.url | escape }}>{{ result.title | escape }}</a></h3>

<p>{{ result.fragment }}</p>

</li>

{% endfor %}

</ul>

{% else %}

<p>Your query returned no results.</p>

{% endif %}

{% endsearchindex %}
```

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| \_aproximado de\_total | Devuelve un recuento aproximado de aciertos totales que coinciden con la consulta del índice. Tenga en cuenta que, debido a la forma en que el índice de búsqueda funciona con respecto al filtrado de seguridad y otros factores de diseño, este número es solo una aproximación y puede que no coincida exactamente con el número total de resultados disponibles para el usuario actual en algunas situaciones.  |
| del                     | Devuelve el número de página de la consulta actual.                                                                                                                                                                                                           |
| tamaño de\_de página               | Devuelve el tamaño de página máximo de la consulta actual. Tenga en cuenta que si desea que se devuelva el número real de resultados para la página actual (porque puede ser menor que el tamaño de página máximo especificado), use Results. size.                                                                                           |
| Resultados                  | Devuelve la página de resultados de la consulta, como objetos de resultado del índice de búsqueda.                                                                                                                                                                                          |

### <a name="search-index-results"></a>Resultados del índice de búsqueda

|   Atribui   |                                                                                                                                                Descripción                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    ID     |                                                                                                                            [Entidades](#entities) subyacentes para el resultado.                                                                                                                            |
|   Fragment    | Un fragmento de texto corto pertinente para el resultado, con términos que coinciden con la consulta especificada resaltada mediante la etiqueta HTML &lt;em&gt;. Tenga en cuenta que determinados tipos de consultas no admiten fragmentos resaltados, como consultas aproximadas (~) y consultas con caracteres comodín (\*). Esta propiedad será null en esos casos. |
|      Identificador       |                                                             El identificador de entidad de PowerApps del registro subyacente para el resultado, como una cadena. Por ejemplo, 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                              |
| nombre del\_lógico |                                                                           El nombre lógico de la entidad de PowerApps del registro subyacente para el resultado. Por ejemplo, ADX\_Página Web                                                                           |
|    number     |                                                            Número del resultado, en todas las páginas de resultados, a partir de 1. Por ejemplo, para el primer resultado de la segunda página de resultados, con un tamaño de página de 10, este valor será 11.                                                             |
|     carácter     |                                                                                                 La puntuación de Lucene del resultado, como un valor de punto flotante. Los resultados se devolverán ordenados por este valor.                                                                                                 |
|     Titulo     |                                                                                                                                          Título del resultado.                                                                                                                                          |
|      Dirección      |                                                            Dirección URL del resultado. Normalmente&mdash;, pero no necesariamente&mdash;ser una ruta de acceso absoluta para la aplicación actual, en lugar de una dirección URL completa. Por ejemplo:/articles/article1/                                                             |

## <a name="settings"></a>Configuración

Permite cargar cualquier valor de [configuración del sitio](../configure/configure-site-settings.md) por nombre. Si no se encuentra un valor con el nombre especificado, se devolverá [null](liquid-types.md#null) .  

> [!Note]
> Los valores se devuelven como [cadenas](liquid-types.md#string), pero puede usar [filtros de tipo](liquid-filters.md#type-filters) para convertirlos en otros tipos.

```
{{ settings[My Setting] }}

{% assign search_enabled = settings[Search/Enabled] | boolean %}

{% if search_enabled %}

Search is enabled.

{% endif %}

{% assign pagesize = settings['page size'] | integer | default: 10 %}

{% if pagesize > 10 %}

Page size is greater than 10.

{% endif %}
```

> [!Note]
> [Representar un encabezado de sitio web y una barra de navegación principal](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>mapas

Permite el acceso al mapa del sitio del portal.

```
<h1>{{ sitemap.root.title }}</h1>

<ul class=breadcrumb>

{% for crumb in sitemap.current.breadcrumbs %}

<li><a href={{ crumb.title }}>{{ crumb.title }}</a></li>

{% endfor %}

<li class=active>{{ sitemap.current.title }}</li>

</ul>

{% for child in sitemap.current.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

It's also possible to load a site map node by URL path:

{% assign node = sitemap[/content/page1/] %}

{% if node %}

{% for child in node.children %}

<a href={{ child.url }}>{{ child.title }}</a>

{% endfor %}

{% endif %}
```

### <a name="site-map-attributes"></a>Atributos del mapa del sitio

|Atribui   |Descripción   |
|---|---|
| Corrientes | Devuelve el objeto de nodo del mapa del sitio para la página actual.                    |
| Raíces    | Devuelve el objeto de nodo del mapa del sitio para la página raíz (Inicio) del sitio Web. |

### <a name="site-map-node-attributes"></a>Atributos de nodo del mapa del sitio

|Atribui   |Descripción   |
|-------|-------|
| Exploración           | Devuelve los objetos de nodo de mapa del sitio de ruta de navegación para el nodo, empezando por el nodo raíz del mapa del sitio y finalizando en el elemento primario. |
| Dominios              | Devuelve los objetos de nodo del mapa del sitio secundario del nodo.                                                                  |
| Descripción           | La descripción o el contenido de resumen para el nodo. (Este campo puede contener HTML).                                          |
| ID                | Devuelve las [entidades](#entities) subyacentes del nodo. Si el nodo no tiene ninguna entidad subyacente, este valor será null.                                                         |
| es\_Sitemap\_antecesor | Devuelve true si el nodo Sitemap es un antecesor del nodo actual; de lo contrario, es false.                                                                                                         |
| es\_mapa del sitio\_actual  | Devuelve true si el nodo Sitemap es el nodo actual; en caso contrario, false.                                                                                                         |
| aérea                | Devuelve el nodo del mapa del sitio primario del nodo. Si el nodo es el nodo raíz, Parent será null.                                                                     |
| Título                 | Título del nodo.                                                                                                |
| Dirección                   | Dirección URL del nodo.                                                                                                  |


## <a name="sitemarkers"></a>sitemarkers

Permite cargar cualquier marcador de sitio por nombre. Si el sitemarker existe, se devolverá un objeto sitemarker. Si no se encuentra un sitemarker con el nombre especificado, se devolverá [null](liquid-types.md#null) .  

```
{{ sitemarkers[Login].url }}

{% assign my_sitemarker = sitemarkers[My Site Marker] %}

{% if my_sitemarker %}

<a href={{ my_sitemarker.url }}>{{ my_sitemarker.adx_name }}</a>

{% else %}

Site marker My Site Marker does not exist.

{% endif %}
```

> [!Note]
> [Representar un encabezado de sitio web y una barra de navegación principal](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>Atributos Sitemarker

|         Atribui          |                                                                                    Descripción                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Dirección             |                                                                         Dirección URL del destino sitemarker.                                                                         |
| \[nombre lógico del atributo\] | Puede tener acceso a cualquier atributo del registro PowerApps de destino de sitemarker por nombre lógico. Por ejemplo, {{sitemarker. ADX\_nombre}} |

## <a name="snippets"></a>fragmentos

Permite cargar fragmentos de contenido por nombre. Si no se encuentra un fragmento de código con el nombre especificado, se devolverá [null](liquid-types.md#null) .  

```
{{ snippets[Header] }}

{% assign footer = snippets[Footer] %}

{% if footer %}

{{ footer }}

{% else %}

No footer snippet was found.

{% endif %}
```


## <a name="tablerowloop"></a>tablerowloop

Contiene propiedades útiles dentro de un bloque de bucle de [etiquetas de iteración](iteration-tags.md) .  

> [!Note] 
> tablerowloop solo se puede usar dentro de una etiqueta de [etiquetas de iteración](iteration-tags.md) .

### <a name="attributes"></a>Atributos

|Atribui   |Descripción   |
|---|---|
| Col        | Devuelve el índice de la fila actual, a partir de 1.                                                       |
| col0       | Devuelve el índice de la fila actual, empezando por 0.                                                       |
| col\_First | Devuelve true si la columna actual es la primera columna de una fila; de lo contrario, devuelve false.               |
| col\_Last  | Devuelve true si la columna actual es la última columna de una fila; de lo contrario, devuelve false.                |
| First      | Devuelve true si es la primera iteración del bucle. Devuelve false si no es la primera iteración.       |
| Ajustar      | La posición del elemento actual en la colección, donde el primer elemento tiene una posición de 1.                   |
| index0     | La posición del elemento actual en la colección, donde el primer elemento tiene una posición de 0.                   |
| Last       | Devuelve true si es la última iteración del bucle. Devuelve false si no es la última iteración.         |
| longitud     | Devuelve el número de iteraciones para el bucle ߝ el número de elementos de la colección que se recorren en iteración. |
| rindex     | Número de elementos restantes en el bucle (length-index), donde 1 es el índice del último elemento.              |
| rindex0    | Número de elementos restantes en el bucle (length-index), donde 0 es el índice del último elemento.              |



## <a name="user"></a>Usuario

Hace referencia al usuario del portal actual, lo que permite el acceso a todos los atributos del registro de contacto de PowerApps subyacente. Si ningún usuario ha iniciado sesión, esta variable será [null](liquid-types.md#null).  

el usuario es un objeto [entidad](#entity) .  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>Atributos

Además de tener todos los atributos de un objeto [entidad](#entity) , el usuario tiene los atributos siguientes.


|    Atribui     |                                                                                                                                                                                     Descripción                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      roles       |                                                      Devuelve los roles a los que pertenece el usuario, como una [matriz](liquid-types.md#array).<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**Nota**: también puede usar el filtro `has_role` para probar la pertenencia a roles individuales.                                                       |
| basic_badges_url | Devuelve la dirección URL del servicio para recuperar los distintivos de un usuario.<br>Para representar las notificaciones de un usuario, debe incluir una etiqueta con los atributos "Data-badge" y "Data-URI". Para representar los distintivos del usuario actual:<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>Para representar los distintivos de un usuario por identificador (ID. de la variable):<br>\`< datos de distintivo de datos div-URI = ' {{user. basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>weblinks

Permite cargar weblinks por nombre o identificador.  

Si el conjunto de vínculos Web existe, se devolverá un [objeto de conjunto de vínculos Web](#web-link-set-attributes) . Si no se encuentra un conjunto de vínculos Web con el nombre o el identificador especificados, se devolverá [null](liquid-types.md#null) .


```
<!-- Load web link set by ID -->

{{ weblinks[page.adx_navigation.id].name }}

<!-- Load web link set by name -->

{% assign nav = weblinks[Primary Navigation] %}

{% if nav %}

<h1>{{ nav.title | escape }}</h1>

<ul>

{% for link in nav.weblinks %}

<li>

<a href={{ link.url | escape }} title={{ link.tooltip | escape }}>

{% if link.image %}

<img src={{ link.image.url | escape }} alt={{ link.image.alternate_text | escape }} />

{% endif %}

{{ link.name | escape }}

</a>

</li>

{% endfor %}

</ul>

{% endif %}
```

> [!Note]
> [Representar un encabezado de sitio web y una barra de navegación principal](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>Atributos de conjunto de vínculos Web

> [!Note]
> Un conjunto de vínculos Web es un objeto [entidad](#entity) , con todos los mismos atributos, además de los que se enumeran a continuación.                                         

|         Atribui          |                                                                                 Descripción                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Copiar            |                                                                      Copia HTML del conjunto de vínculos Web.                                                                      |
|            Nombre            |                                                                        Nombre del conjunto de vínculos Web.                                                                         |
|           Título            |                                                                        Título del conjunto de vínculos Web.                                                                        |
|          weblinks          |                                                       Matriz de objetos de vínculo Web asociados al conjunto de vínculos Web.                                                        |
| \[nombre lógico del atributo\] | Puede tener acceso a cualquier atributo del conjunto de vínculos Web para el registro de PowerApps por nombre lógico. Por ejemplo, {{weblinkset. Created}} |

### <a name="web-link-attributes"></a>Atributos de vínculo Web

> [!Note]
> Un vínculo Web es un objeto [entidad](#entity) , con todos los mismos atributos, además de los que se enumeran a continuación.

|          Atribui          |                                                                              Descripción                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Descripción         |                                                                 La descripción HTML del vínculo Web.                                                                 |
|    Mostrar solo\_de imagen de\_     |                              Atributo booleano que indica si el vínculo Web se debe mostrar solo como imagen, sin texto de vínculo.                               |
| Mostrar\_página\_vínculos secundarios\_ |            Atributo booleano que indica si el vínculo Web debe mostrar vínculos a las páginas secundarias del [*mapa del sitio*](#sitemap) de la página vinculada, como subvínculos.             |
|            Imagen            |                                     Objeto de imagen de vínculo Web para este vínculo. Este atributo será NULL si no hay ninguna imagen presente.                                      |
|        es\_externo         |                 Atributo booleano que indica si la dirección URL de destino del vínculo Web es a un sitio externo (en lugar de a una página interna del portal).                  |
|    es\_Sitemap\_antecesor    |                                Devuelve true si la dirección URL de WebLink hace referencia a un antecesor del nodo del mapa del sitio actual; de lo contrario, es false.                                 |
|    es\_mapa del sitio\_actual     |                                        Devuelve true si la dirección URL del WebLink hace referencia al nodo del mapa del sitio actual; de lo contrario, es false.                                        |
|            Nombre             |                                                                    Nombre/título del vínculo Web.                                                                    |
|          Nofollow           |                                         Atributo booleano que indica si el vínculo Web se debe marcar como rel = nofollow.                                         |
|    abrir\_en\_ventana nuevo\_    |                             Atributo booleano que indica si el vínculo Web se debe abrir en una nueva ventana o pestaña del explorador cuando se selecciona.                             |
|           Herramienta           |                                                                    Texto de información sobre herramientas para el vínculo Web.                                                                     |
|             Dirección             |                                                                       Dirección URL del vínculo Web.                                                                        |
|          weblinks           |                                                   Matriz de objetos de vínculo Web secundarios asociados al vínculo Web.                                                   |
| \[nombre lógico del atributo\]  | Puede tener acceso a cualquier atributo del registro de PowerApps del vínculo Web por nombre lógico. Por ejemplo, {{WebLink. Created}} |

### <a name="web-link-image-attributes"></a>Atributos de imagen de vínculo Web

| texto alternativo de\_ | Texto alternativo para la imagen.                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| Alto          | Entero que contiene el alto especificado de la imagen. Si no se proporcionó ningún valor de alto, este atributo será null. |
| Dirección             | Dirección URL de la imagen.                                                                                               |
| Ancho           | Entero que contiene el ancho especificado de la imagen. Si no se proporcionó ningún valor de ancho, este atributo será null.   |


## <a name="website"></a>Bsitio

Hace referencia al sitio web del portal, que permite el acceso a todos los atributos del registro del sitio web de PowerApps (ADX\_website) para el portal.  

> [!Note]
> El sitio web es un objeto [entidad](#entity) , con todos los mismos atributos.

**Codifica**

```
{{ website.adx_name }} ({{ website.id }})
```

**Genere**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>Vea también

[Tipos de líquido](liquid-types.md)  
[Etiquetas líquidas](liquid-tags.md)  
[Filtros líquidos](liquid-filters.md)  
