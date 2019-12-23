---
title: Usar objetos de Liquid para un portal | MicrosoftDocs
description: Obtenga información acerca de los objetos de Liquid disponibles en un portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8d7dff4588b2f026c8cf4583775177e5ce687ded
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866419"
---
# <a name="available-liquid-objects"></a>Objetos de Liquid disponibles

Los objetos de Liquid contienen atributos para emitir contenido dinámico a la página. Por ejemplo, el objeto Page tiene un atributo llamado Title que se puede usar para emitir el título de la página actual.

Para obtener acceso a un atributo de objeto por nombre, use un punto . Para generar el atributo de un objeto en una plantilla, inclúyalo entre {{ y }}.

```
{{ page.title }}
```
También se puede acceder a los atributos de un objeto con un nombre de cadena y "\[\]". Esto es útil en casos en que el atributo deseado se determine dinámicamente, o el nombre de atributo contenga caracteres, espacios, caracteres especiales, etc. que invalidarían el uso de la  sintaxis.

```
{{ page[title] }}

{% assign attribute_name = Name with spaces %}

{{ object[attribute_name] }}
```

Los siguientes objetos se pueden usar y acceder a ellos en cualquier lugar de cualquier plantilla.


|   Objeto    |                                                                                                                                                                                          Descripción                                                                                                                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  entities   |                                                                                                 Permite cargar cualquier entidad Power Apps por Id. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [entidades](#entities)                                                                                                 |
|     now     |                                          Un objeto de fecha/hora que hace referencia a la hora UTC actual, en el momento que se representa la plantilla.<br>**Nota**: este valor es almacenado en la memoria caché de la aplicación web del portal y no siempre se actualiza. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Filtros por fecha](liquid-filters.md#date-filters)                                          |
|    página     | Hace referencia a la página de solicitud del portal actual. El objeto page proporciona acceso a los aspectos como rutas de navegación para la página actual, el título o la dirección URL de la página actual, y cualquier otro atributo o entidad relacionada de registro de Power Apps subyacente. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [página](#page) |
|   params    |                                                                                                                             Un acceso directo adecuado para request.params. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [solicitud](#request)                                                                                                                              |
|   solicitud   |                                                                                                                        Contiene información acerca de la solicitud HTTP actual. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [solicitud](#request)                                                                                                                        |
|  configuración   |                                                                                                            Permite cargar cualquier [configuración de sitio](../configure/configure-site-settings.md) por nombre. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [configuración](#settings)                                                                                                            |
|   sitemap   |                                                                                                                               Permite el acceso al mapa del sitio del portal. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [mapa del sitio](#sitemap)                                                                                                                                |
| marcadores de sitio |                                                                                                                        Permite cargar cualquier marcador de sitio por nombre. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [marcadores de sitio](#sitemarkers)                                                                                                                        |
|  fragmentos   |                                                                                                         Permite cargar cualquier [fragmento de contenido](../configure/customize-content-snippets.md) por nombre. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [snippets](#snippets)                                                                                                         |
|    Usuario     |                             Hace referencia al usuario del portal actual, que permite el acceso a todos los atributos del registro de contacto de Power Apps subyacente. Si ningún usuario ha iniciado sesión, esta variable será [null](liquid-types.md#null). [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [usuario](#user)                              |
|  weblinks   |                                                                                                                        Permite cargar cualquier Conjunto de vínculos web por nombre o Id. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [weblinks](#weblinks)                                                                                                                        |
|   sitio web   |                                                      Hace referencia al registro de sitio web del portal, que permite el acceso a todos los atributos del registro del sitio web de Power Apps (adx\_website) para el portal. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [sitio web](#website)                                                       |

## <a name="ads"></a>ads


Proporciona la capacidad de acceder y representar un anuncio.

El objeto ads permite seleccionar un anuncio o ubicación de anuncio específico:

```
<div>

{% assign ad = ads[Ad Name] %}

<h4>{{ ad.title }}</h4>

<a href={{ ad.redirect_url }}>

<img src={{ ad.image.url }} alt={{ ad.image.alternate_text }} />

</a>

</div>
```

### <a name="ads-attributes"></a>Atributos de ads

|Atributo   |Descripción   |
|---|---|
| placements        | Devuelve el objeto de ubicaciones de anuncios.    |
| \[nombre o id de anuncio\] | Puede obtener acceso a cualquier anuncio por sus propiedades de nombre o id. <br> `{% assign ad = ads[Ad Name] %}`<br>`{% assign ad = ads["da8b8a92-2ee6-476f-8a21-782b047ff460"] %}`  |


### <a name="ad-placements-attributes"></a>Atributos de Ad Placements

|Atributo   |Descripción   |
|---|---|
| \[nombre o identificador de colocación de anuncio\] | Puede obtener acceso a cualquier ubicación de anuncios por sus propiedades de nombre o id.<br>`{% assign placement = ads.placements[Placement Name or Id] %}`<br>`{% assign placement = ads.placements[2423d713-abb3-44c3-8a7d-c445e16fccad] %}`  |

### <a name="ad-placement-attributes"></a>Atributos de Ad Placement

Un ad placement es un objeto de entidad con los mismos atributos, además de los que se muestran a continuación.

|Atributo   |Descripción   |
|---|---|
| Anuncios            | Devuelve la colección de objetos de anuncio asociados con la ubicación.  [Las etiquetas de iteración](iteration-tags.md) y los [filtros de matriz](liquid-filters.md#array-filters) se pueden usar con esta colección.  |  
| Nombre           | Devuelve el campo Nombre para la ubicación del anuncio.                                                                |
| placement\_url | La dirección URL que puede usarse para recuperar la ubicación del anuncio representada completamente por una plantilla.                         |
| random\_url    | La dirección URL que puede usarse para recuperar un anuncio aleatorio de la ubicación representada completamente por una plantilla.           |

### <a name="ad-attributes"></a>Atributos de anuncios

> [!Note]
> Un anuncio es un objeto de entidad con los mismos atributos, además de los que se muestran a continuación.

|Atributo   |Descripción   |
|---|---|
| ad\_url |  La dirección URL que puede usarse para recuperar el anuncio representada completamente por una plantilla.   |
| Texto| Devuelve el campo Texto del anuncio.|
| image| Devuelve el objeto de imagen (si la hay) para el anuncio.|
| Nombre| Devuelve el campo Nombre del anuncio.|
| open\_in\_new\_window | Devuelve true si la dirección URL especificada por redirect\_url debe abrirse en una nueva ventana. |
| redirect\_url| La dirección URL a la que se reenviará al usuario al hacer clic en el anuncio.|

### <a name="ad-image-attributes"></a>Atributos de Ad Image

|Atributo   |Descripción   |
|---|---|
| alternate\_text | Devuelva el texto que está diseñado para que aparezca en el atributo alt de la etiqueta. |
| height          | Devuelve el alto en píxeles para la imagen                             |
| dirección url             | Devuelve el origen de la dirección URL de la imagen.                                  |
| width           | Devuelve el ancho en píxeles para la imagen                              |


## <a name="blogs"></a>blogs

Proporciona la capacidad de acceder y representar blogs y entradas de blog.

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

### <a name="blogs-object"></a>Objeto blogs

El objeto blogs permite tener acceso a cualquier blog específico en el portal, o tener acceso a todas las entradas de blog en el portal (independientemente del blog).

En la tabla siguiente se explican los atributos asociados con el objeto blogs.

|Atributo   |Descripción   |
|---|---|
| posts               | Devuelve un objeto blogposts que contiene todas las entradas de blog en el portal.     |
| \[nombre o identificador de blog\] | Puede obtener acceso a cualquier blog por sus propiedades de nombre o id.                   

```
{% assign blog = blogs[Blog Name] %}                             

{% assign blog = blogs[da8b8a92-2ee6-476f-8a21-782b047ff460] %}  |
```

### <a name="blog-object"></a>Objeto blog

El objeto blog permite trabajar con un solo blog, lo que permite obtener acceso a las entradas de ese blog.

En la tabla siguiente se explican los distintos atributos asociados con el objeto blog.

|Atributo   |Descripción   |
|---|---|
| posts | Devuelve un objeto blogposts que contiene todas las entradas de ese blog. |
| Nombre  | El nombre del blog.                                              |
| title | El título del blog.                                             |
| dirección url   | La dirección URL del blog.                                               |

### <a name="blogposts-object"></a>Objeto blogposts

El objeto blogposts permite tener acceso a una colección de objetos de entradas de blog. Puede ordenar las entradas de blog y realizar la paginación además de utilizar filtros de Liquid:

{% assign blogposts = blogs.posts | order\_by “adx\_name”, “desc” | paginate: 0,4 | all %} Tenga en cuenta que blogs.posts.all también es una forma válida de obtener todas las publicaciones de blogs blogs.posts | de\_index: 0 | take: 2 también es posible

En la tabla siguiente se explican los distintos atributos asociados con el objeto blogposts.

|Atributo   |Descripción   |
|---|---|
| Todas | Devuelve todos los objetos blogposts en la colección. |

### <a name="blogpost-object"></a>Objeto blogpost

Hace referencia a una sola entrada de blog.

En la tabla siguiente se explican los distintos atributos asociados con el objeto blogpost.

|Atributo   |Descripción   |
|---|---|
| dirección url            | URL de la entrada.                                                                |
| content        | Devuelve el campo de contenido de la entrada.                                             |
| content        | Devuelve el campo Contenido de la entrada.                                             |
| author         | Devuelve el autor de la publicación (que es simplemente un objeto de entidad de contacto).          |
| title          | El título de la entrada.                                                              |
| comment\_count | Devuelve el valor entero del recuento del número de comentarios para una entrada determinada. |
| publish\_date  | La fecha en la que la publicación se publicó.                                           |

## <a name="entities"></a>entities

Permite cargar cualquier entidad Power Apps por Id. Si la entidad existe, se devolverá un objeto de entidad. Si no se encuentra una entidad con el Id. dado, se devolverá [null](liquid-types.md#null).  

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

### <a name="entity"></a>Entity

Un objeto de entidad proporciona acceso a los atributos de un registro de entidad de Power Apps.


|             Atributo              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                 Id.                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    El Id. de GUID de la entidad, como cadena. Por ejemplo, 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|           logical\_name            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   El nombre lógico de Power Apps de la entidad.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|               Notas                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Carga cualquier nota (anotación) asociada a la entidad, ordenada de la más antigua a la más nueva (createdon). Las notas se devuelven como objetos de nota.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            permisos             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Carga resultados de la aserción de permiso de carga para la entidad. Se devuelven los resultados como un objeto de permisos.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                dirección url                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Devuelve la ruta de la dirección URL del sistema de administración del contenido de los portales de Power Apps para la entidad. Si la entidad no tiene una dirección URL válida en el sitio web actual, devuelve null. Normalmente, esto devolverá solo un valor para determinados tipos de entidad que se han integrado en la  CMS del portal, a menos que haya  personalizado el proveedor de la dirección URL en la aplicación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| \[nombre de atributo o relación\] | Puede obtener acceso a cualquier atributo de la entidad de Power Apps por nombre lógico. `{{ entity.createdon }}{% assign attribute_name = 'name' %}{{ entity[attribute_name] }}` <br>Los valores de la mayoría de los atributos de entidad se asignan directamente a los [tipos de Liquid](liquid-types.md): los campos de dos opciones se asignan a booleanos, los campos de texto a cadenas, los campos numérico o divisa a números, los campos de fecha y hora a objetos de fecha. Pero algunos tipos de atributos se devuelven como objetos:<ul><li>Los campos de búsqueda (referencia de entidad) se devuelven como objetos de referencia de entidad.</li><li>Los campos de conjunto de opciones o de lista desplegable se devuelven como objetos de valor del conjunto de opciones.</li><li>También puede cargar cualquier entidad relacionada por nombre de esquema de la relación.</li>`{{ page.adx_webpage_entitylist.adx_name }}`En caso de que una relación sea reflexiva (es decir, que se haga referencia a sí misma), se devolverá un objeto de relación reflexiva. (Si no, el resultado sería ambiguo.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Nota**: Cargar un gran número de entidades relacionadas, o acceder a un gran número de relaciones en una sola plantilla, puede tener un impacto negativo en el rendimiento de la representación de plantilla. Evite cargar entidades relacionadas para cada elemento de una matriz, en un bucle. Cuando sea posible, use [etiquetas de entidad de Power Apps common data service](portals-entity-tags.md) para cargar colecciones de entidades. |

### <a name="entity-reference"></a>Referencia de entidad

Los valores de atributo de búsqueda se devuelven como objetos de referencia de la entidad, con los siguientes atributos.


|   Atributo   |                                                Descripción                                                |
|---------------|-----------------------------------------------------------------------------------------------------------|
|      Id.       | El Id. de GUID de la entidad referenciada, como cadena. <br> Por ejemplo, 936DA01F-9ABD-4d9d-80C7-02AF85C822A8 |
| logical\_name |  El nombre lógico de Power Apps de la entidad referenciada.   |
|     Nombre      |                           El atributo de nombre principal de la entidad referenciada.                            |

### <a name="note"></a>Nota

Una nota es un objeto de entidad que proporciona acceso a los atributos y relaciones de un registro de anotación. Además de todos los atributos de un objeto de entidad, una nota tiene los siguientes atributos adicionales.


|  Atributo   |                                                                                                                                                                                                                                  Descripción                                                                                                                                                                                                                                  |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| documentbody | Carga el atributo documentbody del registro anotación de nota, como cadena codificada en Base64. Como el contenido de este atributo puede ser grande, no se carga con el resto de los atributos de nota y se carga solo según petición. <br> **Nota**: El uso del atributo documentbody podría tener un impacto negativo en rendimiento de representación de la plantilla, y se debe hacer con precaución.<br>Use el atributo url para proporcionar un vínculo con los datos adjuntos de nota en su lugar, si es posible. |
|     dirección url      |                                                                                                                                   Devuelve la dirección URL del controlador de datos adjuntos de la anotación del portal integrado. Si el usuario tiene permiso, y la nota tiene un archivo adjunto, una solicitud a esta dirección URL descargará el archivo adjunto de la nota.                                                                                                                                    |

>[!Note]
> [Filtros adicionales](liquid-filters.md#additional-filters)                     

### <a name="option-set-value"></a>Valor del conjunto de opciones

Los valores de atributo de conjunto de opciones/lista desplegable se devuelven como objetos de referencia de la entidad, con los siguientes atributos.

| Atributo | Descripción                                                     |
|-----------|-----------------------------------------------------------------|
| Etiqueta     | La etiqueta localizada del valor de atributo del conjunto de opciones/lista desplegable. Por ejemplo, "Activo"|
| Valor     | El valor entero del valor de atributo del conjunto de opciones/lista desplegable. Por ejemplo, 0                                                           |

### <a name="entity-permissions"></a>Permisos de entidad

El objeto Permisos de entidad proporciona acceso a los resultados agregados de aserción de permisos para una entidad.

| Atributo       | Descripción                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| can\_append     | Devuelve true si el usuario actual tiene permiso para anexar registros a relaciones de este registro. De lo contrario, devuelve false.                                                                                              |
| can\_append\_to | Devuelve true si el usuario actual tiene permiso para anexar este registro a una relación de otra entidad. De lo contrario, devuelve false.                                                                                      |
| can\_create     | Devuelve true si el usuario actual tiene permiso para crear nuevos registros de este tipo de entidad. De lo contrario, devuelve false.                                                                                                      |
| can\_delete     | Devuelve true si el usuario actual tiene permiso para eliminar este registro. De lo contrario, devuelve false.                                                                                                                          |
| can\_read       | Devuelve true si el usuario actual tiene permiso para leer este registro. De lo contrario, devuelve false.                                                                                                                            |
| can\_write      | Devuelve true si el usuario actual tiene permiso para actualizar este registro. De lo contrario, devuelve false.                                                                                                                          |
| rules\_exist    | Devuelve true si los resultados de permisos representados por este objeto son resultado de las reglas de permiso definidas explícitamente. Devuelve false si son los resultados predeterminados en ausencia de permisos definidos explícitamente. |

### <a name="reflexive-relationship"></a>Relación reflexiva

Los intentos de cargar relaciones reflexivas (es decir, que se hacen referencia a sí mismas) en entidades se devuelven como objetos con los siguientes atributos.

| Atributo     | Descripción                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------------|
| is\_reflexive | Devuelve true. Se puede usar para comprobar si un objeto devuelto por una relación es un objeto de relación reflexiva. |
| referenced    | Devuelve una matriz de entidades referenciadas para la relación determinada.                                           |
| referencing   | Devuelve una entidad de referencia para la relación determinada. Devuelve null si no existe una entidad de referencia. Si la relación es de varios a varios (N:N), devuelve una matriz de entidades de referencia.                          

## <a name="entitylist"></a>entitylist

El objeto entitylist se usa dentro de [etiquetas de entidad de Power Apps common data service](portals-entity-tags.md). Proporciona acceso a todos los atributos de una determinada lista de entidades.  

> [!Note]                                                       
> [Representar la lista de entidades asociada a la página actual](render-entity-list-current-page.md)

### <a name="attributes"></a>Atributos

> [!Note]
> [entities](#entities)

|               Atributo               |                                                                                                                            Descripción                                                                                                                            |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            create\_enabled            |                                                                                Devuelve true si la creación de nuevos registros se configura para la lista de entidades. De lo contrario, devuelve false.                                                                                |
|              create\_url              |                                                                                          Devuelve la ruta URL configurada para un vínculo o un botón de creación para la lista de entidades.                                                                                          |
|            detail\_enabled            |                                                                         Devuelve true si una vista de detalle para registros individuales se configura para la lista de entidades. De lo contrario, devuelve false.                                                                          |
|         detail\_id\_parameter         |               Devuelve el nombre de parámetro de cadena de consulta que usará para el Id. de registro al crear una dirección URL de vista de detalle de registro. Vea [Filtros de direcciones URL](liquid-filters.md#url-filters) para obtener detalles sobre el uso de filtros de Liquid para generar URL. Por ejemplo, id.                |
|             detail\_label             |                                                                                     Devuelve la etiqueta localizada configurada para vínculos o botones de vista de detalle para la lista de entidades.                                                                                     |
|              detail\_url              |                                                                                       Devuelve la ruta URL configurada para vínculos o botones de vista de detalle para la lista de entidades.                                                                                        |
|           empty\_list\_text           |                                                                                Devuelve el texto localizado configurado que se mostrará cuando la vista en lista de entidades no devuelva ningún resultado.                                                                                |
|      enable\_entity\_permissions      |                                                                               Devuelve true si el filtro de permisos de entidad está habilitado para esta lista de entidades. De lo contrario, devuelve false.                                                                               |
|         entity\_logical\_name         |                                                 Devuelve el nombre lógico de la entidad de Power Apps para los registros que mostrará esta lista de entidades. Por ejemplo, contact                                                 |
|   filter\_account\_attribute\_name    |                                            Devuelve el nombre lógico de atributo para la búsqueda a cuenta que usará para filtrar los registros de resultado la cuenta primaria del usuario del portal actual. Por ejemplo, accountid                                            |
|         filter\_apply\_label          |                                                            Devuelve la etiqueta localizada configurada que se usará para el vínculo/botón que aplica un filtro de atributo avanzado a los resultados de la lista de entidades.                                                            |
|          filter\_definition           |                      Devuelve la definición de filtro de atributo JSON para la lista de entidades. Vea [Filtros de lista de entidades](liquid-filters.md#entity-list-filters) para obtener información sobre cómo usar el filtro de Liquid de metafiltros para procesar esta definición.                       |
|            filter\_enabled            |                                                                               Devuelve true si el filtro de atributo avanzado está habilitada para la lista de entidades. De lo contrario, devuelve false.                                                                               |
| filter\_portal\_user\_attribute\_name |                                                 Devuelve el nombre lógico de atributo para la búsqueda a contacto que se usará para filtrar los registros de resultado el contacto del usuario del portal actual. Por ejemplo, contactid                                                  |
|   filter\_website\_attribute\_name    |                                              Devuelve el nombre lógico de atributo para la búsqueda a adx\_website que usará para filtrar los registros de resultado el sitio web del portal actual. Por ejemplo, adx\_websiteid                                              |
|            language\_code             |                                               Devuelve el código de idioma entero de Power Apps que se usará para seleccionar todas las etiquetas localizadas para esta lista de entidades.                                                |
|              page\_size               |                                                                                                   Devuelve el tamaño de página de resultados configurada para la lista de entidades.                                                                                                    |
|          primary\_key\_name           |                                                                                  Devuelve el nombre lógico de atributo de clave principal para los registros que mostrará esta lista de entidades.                                                                                  |
|            search\_enabled            |                                                                                         Devuelve true si la búsqueda está habilitada para esta lista de entidades. De lo contrario, devuelve false.                                                                                          |
|          search\_placeholder          |                                                                                        Devuelve el texto localizado configurado para el marcador de posición del campo de búsqueda en la lista de entidades.                                                                                        |
|            search\_tooltip            |                                                                                             Devuelve el texto localizado configurado para la información sobre herramientas de búsqueda en la lista de entidades.                                                                                             |
|                 vistas                 |                                                                                           Devuelve las vistas disponibles para la lista de entidades, como objetos de vista de lista de entidades.                                                                                           |
|      \[nombre lógico del atributo\]       | Puede obtener acceso a cualquier atributo del registro de Power Apps de la lista de entidades (adx\_entitylist) por nombre lógico, de la misma forma que un objeto de [entidad](liquid-objects.md#entity). Por ejemplo, {{ entitylist.adx\_name }} |

### <a name="entity-list-view-attributes"></a>Atributos de vista de listas de entidades

|          Atributo          |                                                                                     Descripción                                                                                     |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                                                         Devuelve las columnas de la vista como objetos de columna de vista de la lista de entidades.                                                         |
|    entity\_logical\_name    |               Devuelve el nombre lógico de la entidad de Power Apps para los registros incluidos en la vista. Por ejemplo, contact                |
|             Id.              |                                                                          Devuelve el identificador de GUID de la vista.                                                                           |
|       language\_code        | Devuelve el código de idioma entero de Power Apps que se usará para seleccionar todas las etiquetas localizadas (encabezados de columna, etc.) para la vista. |
|            Nombre             |                                          Devuelve el nombre para mostrar de Power Apps de la vista.                                          |
| primary\_key\_logical\_name |        Devuelve el nombre lógico de clave principal de la entidad de Power Apps para los registros incluidos en la vista. Por ejemplo, contactid         |
|      sort\_expression       |                                               Devuelve la expresión de ordenación predeterminada para la vista. Por ejemplo, name ASC, createdon DESC                                               |

### <a name="entity-list-view-column-attributes"></a>Atributos de columna de vista de lista de entidades

|    Atributo     |                                                                                    Descripción                                                                                    |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| attribute\_type  | Devuelve el nombre del tipo de atributo de Power Apps para la columna, como cadena. Por ejemplo, Lookup, Picklist, String, Boolean, DateTime |
|  logical\_name   |                       Devuelve el nombre lógico de atributo de Power Apps para la columna. Por ejemplo, createdon                       |
|       Nombre       |                      Devuelve el nombre para mostrar de Power Apps localizado para la columna. Por ejemplo, Created On                       |
| sort\_ascending  |                                      Devuelve una cadena de expresión de orden para ordenar la columna en orden ascendente. Por ejemplo, createdon ASC                                       |
| sort\_descending |                                     Devuelve una cadena de expresión de orden para ordenar la columna en orden descendente. Por ejemplo, createdon DESC                                      |
|  sort\_disabled  |                                                   Devuelve true si el orden está deshabilitado para la columna. De lo contrario, devuelve false.                                                    |
|  sort\_enabled   |                                                    Devuelve true si el orden está habilitado para la columna. De lo contrario, devuelve false.                                                    |
|      width       |                                                              Devuelve el ancho configurado para la columna, en píxeles.                                                              |

## <a name="entityview"></a>entityview

El objeto entityview se usa dentro de la etiqueta entityview y proporciona acceso a los metadatos de la vista, así como registros de los resultados de la vista.

### <a name="attributes"></a>Atributos

|          Atributo          |                                                                               Descripción                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           columns           |                         Devuelve las columnas de la vista, como [objetos de columna de vista de entidad](liquid-objects.md#entity-list-view-column-attributes).                          |
| entity\_permission\_denied  | Devuelve true si el acceso a los resultados de la vista se ha denegado debido a permisos de entidad insuficientes para el usuario actual. Devuelve false si se ha concedido acceso de lectura a los resultados de la vista. |
|    entity\_logical\_name    |                   El nombre lógico de la entidad de Power Apps de los registros de resultados de la vista. Por ejemplo, contact                   |
|         first\_page         |                 El número de página de la primera página de los resultados de vista. Será 1 a menos que no hubiera resultados devueltos, en cuyo caso será null.                  |
|             Id.              |                            El Identificador GUID de la vista de Power Apps que define esta entityview.                             |
|       language\_code        |             El código de idioma entero de Power Apps que se usa para cargar etiquetas localizadas para la vista actual.              |
|         last\_page          |                                 El número de página de la última página de los resultados de vista. Si no hay resultados devueltos, será null.                                  |
|            nombre             |              El nombre de la vista de Power Apps que define esta entityview., por ejemplo, Contactos activos.               |
|         next\_page          |                                El número de página de la siguiente página de los resultados de vista. Si no hay siguiente página de resultados, será null.                                 |
|            Página             |                                                           El número de página de la página actual de los resultados de vista.                                                           |
|            pages            |                                          Devuelve una matriz de números de página que contiene todas las páginas de resultados de la vista actual.                                          |
|         page\_size          |                                                      El número de resultados devueltos por página para la vista actual.                                                       |
|       previous\_page        |                              El número de página de la siguiente página de los resultados de vista. Si no hay página anterior de resultados, será null.                               |
| primary\_key\_logical\_name |  El nombre lógico de Power Apps del atributo de clave principal de la entidad de resultado para esta vista. Por ejemplo, contactid.   |
|           Registros           |                                                   La página actual de los registros de resultado de la vista, como objetos de entidad.                                                    |
|      sort\_expression       |                                             Expresión de ordenación predeterminada para la vista. Por ejemplo, nameASC, createdon DESC.                                              |
|        total\_pages         |                                                              El número total de páginas de resultados para la vista.                                                              |
|       total\_records        |                                                       El número total de resultados para la vista (en todas las páginas).                                                       |

## <a name="events"></a>eventos

Proporciona la capacidad de acceder y representar eventos. El objeto events permite seleccionar un evento específico o todos los eventos.

### <a name="events-object"></a>Objeto events

El objeto events permite tener acceso a cualquier evento específico del portal, o tener acceso a todos los eventos del portal (independientemente del evento).

El objeto events tiene los siguientes atributos:

|Atributo   |Descripción   |
|---|---|
|occurences |Devuelve un objeto eventoccurancess que contiene todas las instancias del evento en el portal |
|[event name or id] |Puede obtener acceso a cualquier evento por sus propiedades de nombre o id.<br>{% assign event = events[&quot;Event Name&quot;] %}<br>{% assign event = events[&quot;da8b8a92-2ee6-476f-8a21-782b047ff460&quot;] %} |

### <a name="event-object"></a>Objeto event

El objeto event permite trabajar con un solo evento, lo que permite obtener acceso a las programaciones e instancias de ese evento.

El objeto event tiene los siguientes atributos:

|Atributo   |Descripción   |
|---|---|
| repeticiones | Devuelve un objeto eventoccurrences que contiene todas las instancias del evento. |
| nombre       | El nombre del evento.                                                     |
| dirección url        | Dirección URL del evento.                                                      |

### <a name="eventoccurences-object"></a>Objeto eventoccurences

El objeto eventoccurrences permite tener acceso a una colección de objetos de instancias del evento. Puede ordenar las instancias del evento y especificar un intervalo de fechas para las instancias a recuperar, y realizar paginación así como utilizar filtros de Liquid.

```
{% assign occurances = event.occurrences.from[today].to[advance_date] %}
```

tenga en cuenta que

```
{% assign occurances = event.occurrences.min[today].max[advance_date] %}
```

también es posible.

Los siguientes atributos se asocian con el objeto eventoccurrences

|Atributo   |Descripción   |
|---|---|
| Todas | Devuelve todos los objetos eventoccurrence en la colección. |

### <a name="eventoccurence-object"></a>Objeto eventoccurence

Representa una sola instancia del evento. Los atributos asociados se indican a continuación:

|Atributo   |Descripción   |
|---|---|
| dirección url                 | Dirección URL de la instancia.    |
| is\_all\_day\_event | ¿Se trata de un evento de todo el día?     |
| start\_time         | Las horas de inicio del evento. |
| end\_time           | Las horas de finalización del evento.   |


## <a name="forloop"></a>forloop

Contiene propiedades útiles en un bloque de bucle [para](iteration-tags.md#for).  

> [!Note]
> forloop solo se puede usar dentro de una etiqueta [para](iteration-tags.md#for).

**Código**

```
{% for child in page.children %}

{% if forloop.first %}

This is the first child page!

{% else %}

This is child page number {{ forloop.index }}.

{% endif %}

{% endfor %}
```

**Salida**

```
This is the first child page!

This is child page number 2.

This is child page number 3.
```

### <a name="attributes"></a>Atributos

|Atributo   |Descripción   |
|---|---|
| primero   | Devuelve true si es la primera iteración del bucle. Devuelve false si no es la primera iteración.       |
| index   | La ubicación del elemento actual en la colección, donde el primer artículo tiene una posición de 1.                   |
| index0  | La ubicación del elemento actual en la colección, donde el primer artículo tiene una posición de 0.                   |
| Última    | Devuelve true si es la última iteración del bucle. Devuelve false si no es la última iteración.         |
| length  | Devuelve el número de iteraciones para el de bucle ߝ el número de elementos en la colección que se está iterando. |
| rindex  | Número de elementos que permanecen en el bucle (duración - índice) donde 1 es el índice del último elemento.              |
| rindex0 | Número de elementos que permanecen en el bucle (duración - índice) donde 0 es el índice del último elemento.              |


## <a name="forums"></a>foros

Proporciona la capacidad de acceder y representar foros e hilos de foros. Tenga en cuenta que la posibilidad de usar Liquid para representar datos de foros se amplía a las entradas, pero para crear una nueva entrada o hilo, debe usar una plantilla de página de formularios web ASP.NET con dicha funcionalidad integrada (por ejemplo, las plantillas predeterminadas de página de hilos y entradas de foro).

El objeto de foros permite seleccionar un foro o hilos de foro:

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

### <a name="forums-object"></a>Objetos foros

El objeto foros permite tener acceso a cualquier foro específico en el portal, o tener acceso a todos hilos de foro en el portal (independientemente del foro).

El objeto forum permite trabajar con un solo foro, lo que permite obtener acceso a los hilos del foro.

El objeto forumthreads permite tener acceso a una colección de objetos de hilos de foro. Puede ordenar los hilos de foro y realizar paginación además de utilizar filtros de Liquid.

```
{% assign threads = forum.threads | order_by adx_name, desc | paginate: 0,4 | all %}
```

Un único hilo del foro

El objeto forumposts permite tener acceso a una colección de objetos de entrada de foro.

### <a name="attributes"></a>Atributos

|Atributo   |Descripción   |
|---|---|
| threads              | Devuelve un objeto forumthreads que contiene todos los objetos forumthread en el portal.             |
| Todas                  | Devuelve todos los objetos forum del portal. Tenga en cuenta que website.forums es también un equivalente.    |
| thread\_count        | Devuelve el valor de entero del recuento del número de hilos que hay en el sitio web completo. |
| post\_count          | Devuelve el valor de entero del número total de publicaciones del portal.                       |
| \[nombre o identificador del foro\] | Puede obtener acceso a cualquier foro por sus propiedades de nombre o id. <br>`{% assign forum = forums[Forum Name] %}<br>{% assign forum = forums[da8b8a92-2ee6-476f-8a21-782b047ff460] %} 

### <a name="forum-object"></a>Objeto forum

### <a name="attributes"></a>Atributos

> [!Note]
> [entities](#entities)

|Atributo   |Descripción   |
|---|---|
| threads       | Devuelve un objeto forumthreads que contiene todos hilos del foro.               |
| Nombre          | El nombre del foro.                                                                  |
| thread\_count | Devuelve el valor entero del recuento del número de hilos que hay en el foro.      |
| post\_count   | Devuelve el valor entero del recuento del número de entradas que hay en todo el foro. |

### <a name="forumthreads-object"></a>Objeto forumthreads

### <a name="attributes"></a>Atributos

|Atributo   |Descripción   |
|---|---|
| Todas | Devuelve todos los objetos forumthread en la colección. |

### <a name="forumthread-object"></a>Objeto forumthread

### <a name="attributes"></a>Atributos

> [!Note]
> [entities](#entities)

|Atributo   |Descripción   |
|---|---|
| posts        | Devuelve un objeto forumposts que contiene todas las entradas de foro del hilo.            |
| author       | Devuelve el autor del hilo (que es simplemente un objeto de entidad de contacto).      |
| latest\_post | Devuelve la última entrada del hilo.                                            |
| first\_post  | Devuelve la primera entrada del hilo.                                             |
| post\_count  | Devuelve el valor de entero del recuento del número de entradas que hay en el hilo. |
| is\_answered | ¿Se ha respondido al hilo o no?                                                    |
| is\_sticky   | ¿Es el hilo un hilo pegajoso?                                                    |

### <a name="forumposts-object"></a>Objeto forumposts

### <a name="attributes"></a>Atributos

|Atributo   |Descripción   |
|---|---|
| Todas | Devuelve todos los objetos forumthread en la colección. |

Una sola entrada del foro

### <a name="attributes"></a>Atributos

> [!Note] 
> [entities](#entities)

|Atributo   |Descripción   |
|---|---|
| author     | Devuelve el autor de la publicación (que es simplemente un objeto de entidad de contacto). |
| content    | Contenido de la entrada.                                                   |
| is\_answer | ¿Es esta entrada una respuesta al hilo?                                      |


## <a name="knowledge"></a>Conocimiento

Proporciona acceso al artículo de conocimiento Power Apps y a los registros de entidad de categoría para representar los artículos y las categorías en un portal.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---|---|
|artículos|Devuelve un objeto de artículo que contiene los objetos de artículo para los registros de entidad de los artículos de conocimiento disponibles en el portal.|
|categorías|Devuelve un objeto de categoría que contiene los objetos de categoría para los registros de entidad de las categorías disponibles en el portal.|
|||

### <a name="articles-object"></a>objeto de artículos

El objeto de artículos permite tener acceso a una colección de objetos de artículo. Puede ordenar los artículos y realizar paginación además de utilizar filtros de Liquid.

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

|Atributo|Descripción|
|---|---|
|Popular |Devuelve una recopilación de objetos del artículo que contiene los más vistos. `{% assign popular_articles = knowledge.articles.popular %}` |
|reciente |Devuelve una recopilación de objetos del artículo que contiene los últimos modificados. `{% assign recent_articles = knowledge.articles.recent %}` |
|superior |Devuelve una recopilación de objetos del artículo que contiene los de mayor interés. `{% assign top_articles = knowledge.articles.top  %}` |
| | |

### <a name="filters"></a>Filtros

Los filtros siguientes pueden admitir parámetros opcionales para el tamaño de página y el idioma. El primer parámetro es el número o los registros a recuperar. El tamaño de página predeterminado es 5. El segundo parámetro es el código de un idioma para recuperar los artículos de un idioma determinado. Los filtros se pueden combinar con otros [Filtros Liquid](liquid-filters.md).

```
{% assign page_size = 5 %}
{% assign language_code = website.selected_language.code %}
{% assign recent_articles = knowledge.articles | recent: page_size, language_code %}
```

|Atributo|Descripción|
|---|---|
|Popular |Devuelve una recopilación de objetos del artículo que contiene los más vistos. `{% assign popular_articles = knowledge.articles \| popular: 10, en-US %}` |
|reciente |Devuelve una recopilación de objetos del artículo que contiene los últimos modificados. `{% assign recent_articles = knowledge.articles \| recent: 5 %}` |
|superior |Devuelve una recopilación de objetos del artículo que contiene los de mayor interés. `{% assign top_articles = knowledge.articles \| top: 3, en-US %}` |
| | |

### <a name="categories-object"></a>objeto de categorías

El objeto categorías permite tener acceso a una colección de objetos de categorías. Puede ordenar las categorías y realizar paginación además de utilizar filtros de Liquid.

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

|Atributo|Descripción|
|---|---|
|reciente |Devuelve una recopilación de objetos de categorías que contiene los últimos modificados. |
|top_level |Devuelve una recopilación de objetos de categorías que no tiene una categoría principal. |
|||

### <a name="filters"></a>Filtros

Los filtros siguientes pueden admitir un parámetro opcional que indique el tamaño de página. El tamaño de página predeterminado es 5. Los filtros se pueden combinar con otros [Filtros Liquid](liquid-filters.md).

```
{% assign page_size = 5 %}
{% assign recent_categories = knowledge.categories | recent: page_size %}
```

|Atributo|Descripción|
|---|---|
|reciente |Devuelve una recopilación de objetos de categorías que contiene los últimos modificados. Puede proporcionar parámetros `{% assign recent_categories = knowledge.categories \| recent: 10 %}` |
|top_level |Devuelve una recopilación de objetos de categorías que no tiene una categoría principal. `{% assign root_categories = knowledge.categories \| top_level %}` |
|||

### <a name="article-object"></a>objeto de artículos

El objeto de artículo permite trabajar con un solo artículo de conocimiento para mostrar los detalles del artículo en el portal.

### <a name="attributes"></a>Atributos

el artículo es un objeto de [entidad](#entity), con todos los mismos atributos, además de los que se muestran a continuación.

|Atributo|Descripción|
|---|---|
|article_public_number| El número público de artículo del artículo.|
|comment_count| El valor entero del recuento del número de comentarios de un artículo determinado.|
|content|El contenido del artículo.|
|current_user_can_comment|Devuelve un valor booleano que indica si el usuario actual puede agregar comentarios en el artículo.|
|is_rating_enabled|Devuelve un valor booleano que indica si está habilitado el nivel de interés en un artículo.|
|palabras clave|Las palabras clave del artículo.|
|nombre|Un alias alternativo para el título del artículo.|
|nivel de interés|El valor decimal del nivel de interés en el artículo.|
|title|Título del artículo.|
|view_count|El valor entero del número de veces que el artículo se ha visto.|
|||

### <a name="category-object"></a>objeto de categorías

El objeto de categoría permite trabajar con una sola categoría para mostrar los detalles en el portal.

### <a name="attributes"></a>Atributos

la categoría es un objeto de [entidad](#entity), con todos los mismos atributos, además de los que se muestran a continuación.

|Atributo|Descripción|
|---|---|
|número de categoría|El número de categoría de la categoría.|
|nombre|Un alias alternativo para el título de la categoría.|
|title|El título de la categoría.|
|||

## <a name="page"></a>página

Hace referencia a la página de solicitud del portal actual. Este objeto combina los atributos del [mapa del sitio](#sitemap) y la solicitud actual [entidades](#entities) (generalmente, una página web).  

El objeto page proporciona acceso a los aspectos como rutas de navegación para la página actual, el título o la dirección URL de la página actual, y cualquier otro atributo o entidad relacionada de registro de Power Apps subyacente.

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
> [entities](#entities)

|             Atributo              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            breadcrumbs             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Devuelve los objetos de nodo del mapa del sitio de ruta de navegación para la página, empezando desde el nodo raíz del mapa del sitio y terminando en el principal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|              children              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Devuelve objetos de nodo de mapa del sitio secundario de la página.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|               parent               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Devuelve el nodo de mapa del sitio principal de la página. Si la página es la página principal, el principal será nulo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|               title                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                El título de la página.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                dirección url                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Dirección URL de la página.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| \[nombre de atributo o relación\] | Puede obtener acceso a cualquier atributo del registro de Power Apps subyacente de la página por nombre lógico.<br>`{{ page.createdon }}`<br>`{% assign attribute_name = 'name' %}`<br>`{{ page[attribute_name] }}`<br>Los valores de la mayoría de los atributos de entidad se asignan directamente a los [tipos de Liquid](liquid-types.md): los campos de dos opciones se asignan a booleanos, los campos de texto a cadenas, los campos numérico o divisa a números, los campos de fecha y hora a objetos de fecha. Pero algunos tipos de atributos se devuelven como objetos:<ul><li>Los campos de búsqueda (referencia de entidad) se devuelven como [objetos de referencia de entidad](#entity-reference).</li><li>Los campos de conjunto de opciones o de lista desplegable se devuelven como [objetos de valor del conjunto de opciones](#option-set-value).</li> También puede cargar cualquier entidad relacionada por nombre de esquema de la relación. <br> `{{ page.adx_webpage_entitylist.adx_name }}`<br>En caso de que una relación sea reflexiva (es decir que haga referencia a sí misma), se devolverá un objeto [entidades](#entities). (Si no, el resultado sería ambiguo.)`{{ page.adx_webpage_webpage.referencing.adx_name }}` <br>**Nota**: Cargar un gran número de entidades relacionadas, o acceder a un gran número de relaciones en una sola plantilla, puede tener un impacto negativo en el rendimiento de la representación de plantilla. Evite cargar entidades relacionadas para cada elemento de una matriz, en un bucle. Cuando es posible, es preferible utilizar las [etiquetas de entidad de Power Apps common data service](portals-entity-tags.md) para cargar colecciones de entidades. |

## <a name="polls"></a>sondeos

Proporciona la capacidad de acceder y representar un sondeo.

El objeto polls permite seleccionar un sondeo o ubicación de sondeo específico:

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

### <a name="polls-attributes"></a>Atributos de sondeos

|Atributo   |Descripción   |
|---|---|
| placements          | Devuelve el objeto pollplacements.                                      |
| \[nombre o identificador del sondeo\] | Puede obtener acceso a cualquier sondeo por sus propiedades de nombre o id. `{% assign poll = polls[Poll Name] %}`<br>`{% assign poll = polls["41827a5c-33de-49b8-a0c7-439e6a02eb98"] %}`  |

### <a name="poll-placements-attributes"></a>Atributos de ubicaciones de sondeos

|Atributo   |Descripción   |
|---|---|
| \[nombre o identificación de ubicación de sondeo\] | Puede obtener acceso a cualquier ubicación de sondeo por sus propiedades de nombre o id.`{% assign placement = polls.placements[Placement Name or Id] %}`<br>`{% assign placement = polls.placements[7677c5d4-406e-4b6c-907c-916ac17dba0f] %} `|

### <a name="poll-placement-attributes"></a>Atributos de ubicación de sondeos

> [!Note] 
> [entities](#entities)                                       

|Atributo   |Descripción   |
|---|---|
| Nombre           | Devuelve el campo Nombre para la ubicación del sondeo.                            
| placement\_url | La dirección URL que puede usarse para recuperar la ubicación del sondeo representada completamente por una plantilla.                       |
| sondeos          | Devuelve la colección de objetos de sondeo asociados con la ubicación. [Las etiquetas de iteración](iteration-tags.md) y los [filtros de matriz](liquid-filters.md#array-filters) se pueden usar con esta colección.  |  
| random\_url    | La dirección URL que puede usarse para recuperar un sondeo aleatorio de la ubicación representada completamente por una plantilla.         |
| submit\_url    | La dirección URL a la que se envía un sondeo completado.                                                             |

### <a name="poll-attributes"></a>Atributos de sondeo

> [!Note] 
> [entities](#entities)                                          

|Atributo   |Descripción   |
|---|---|
| has\_user\_voted       | Devuelve true si el usuario actual (que ha iniciado sesión o anónimo) ya ha votado en este sondeo.         |
| Nombre                   | Devuelve el campo Nombre para el sondeo.                                                              |
| opciones                | Devuelve la colección de objetos poll option asociados con el sondeo. Las [etiquetas de la iteración](iteration-tags.md) y las [entidades](#entities) se puede usar con esta colección.  |  
| poll\_url              | La dirección URL que puede usarse para recuperar el sondeo representada completamente por una plantilla.                       |
| Pregunta de                | Devuelve el campo Pregunta para el sondeo.                                                          |
| submit\_button\_label  | Devuelve una cadena que se puede usar para reemplazar la etiqueta del botón enviar para el sondeo.               |
| submit\_url            | La dirección URL a la que se envía un sondeo completado.                                                   |
| user\_selected\_option | Devuelve el objeto polloption seleccionado por el usuario (si ya ha votado).                  |
| votes                  | Devuelve el número de votos que se han tabulado para el sondeo.                                |

### <a name="poll-option-attributes"></a>Atributos de la opción de sondeo

>[!Note]
> [entities](#entities)                                         

|Atributo   |Descripción   |
|---|---|
| answer     | Devuelve el campo Respuesta para el sondeo. |
| percentage | Devuelve el porcentaje de votos en el sondeo para la opción como número decimal entre 0 y 100. |
| votes      | Devuelve el número de votos que se han tabulado para la opción.                              |


## <a name="request"></a>solicitud

Contiene información acerca de la solicitud HTTP actual.

```
{% assign id = request.params['id'] %}

<a href={{ request.url | add_query: 'foo', 1 }}>Link</a>
```

> [!Note]
> Puede crear direcciones URL dinámicamente en Liquid utilizando filtros de dirección URL. 

### <a name="attributes"></a>Atributos

|Atributo   |Descripción   |
|---|---|
| params           | Valores de parámetros con nombre para la solicitud actual. params es una combinación de parámetros de cadena de consulta de la dirección URL, parámetros de entrada de formulario, y cookies.  |
| Ruta             | La ruta de dirección URL de la solicitud actual. <br> /profile/|
| path\_and\_query | La ruta y consulta de la dirección URL de la solicitud actual.<br> /profile/?foo=1&bar=something|
| query            | La parte de consulta de la dirección URL de la solicitud actual. <br> ?foo=1&bar=something |
| dirección url              | La dirección URL completa de la solicitud actual.<br>  https://www.example.com/profile/?foo=1&bar=something  |


## <a name="searchindex"></a>searchindex

El objeto searchindex se usa dentro de las [etiquetas de entidad de Power Apps common data service](portals-entity-tags.md), y proporciona acceso a los resultados de una consulta.  

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

|Atributo   |Descripción   |
|---|---|
| approximate\_total\_hits | Devuelve un recuento aproximado de los aciertos generales que coinciden con la consulta de índice. Tenga en cuenta que debido a la forma de funcionar del índice de búsqueda en relación con el filtrado de seguridad y otros factores de diseño, este número sólo es una aproximación, puede no coincidir exactamente con el número total de resultados disponibles al usuario actual en algunos casos.  |
| Página                     | Devuelve el número de página de la consulta actual.                                                                                                                                                                                                           |
| page\_size               | Devuelve el tamaño de página máximo de la consulta actual. Tenga en cuenta que si desea que el número real de resultados devueltos para la página actual (ya que puede ser inferior al tamaño máximo de página especificado), debe usar results.size.                                                                                           |
| Resultados                  | Devuelve la página de resultados de la consulta, como objetos de resultados de índice de búsqueda.                                                                                                                                                                                          |

### <a name="search-index-results"></a>Resultados de índice de búsqueda

|   Atributo   |                                                                                                                                                Descripción                                                                                                                                                 |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    entidad     |                                                                                                                            Las [entidades](#entities) subyacentes para el resultado.                                                                                                                            |
|   fragment    | Un fragmento de texto corto relevante para el resultado, con los términos que coinciden con la consulta especificada resaltada utilizando la etiqueta HTML &lt;em&gt;. Tenga en cuenta que determinados tipos de consultas no admiten fragmentados resaltados, como las consultas aproximadas (~) y consultas comodín (\*). Esta propiedad será nula en esos casos. |
|      Id.       |                                                             El Id. de entidad de Power Apps del registro subyacente para el resultado, como cadena. Por ejemplo, 936DA01F-9ABD-4d9d-80C7-02AF85C822A8                                                              |
| logical\_name |                                                                           El nombre lógico de entidad de Power Apps del registro subyacente para el resultado. Por ejemplo, adx\_webpage                                                                           |
|    Número     |                                                            El número del resultado, a través de todas las páginas de resultado, empezando por 1. Por ejemplo, para el primer resultado de la segunda página de resultados, con un tamaño de página de 10, este valor será 11.                                                             |
|     score     |                                                                                                 La puntuación Lucene del resultado, como un valor de coma flotante. Los resultados serán devueltos ordenados por este valor.                                                                                                 |
|     title     |                                                                                                                                          El título del resultado.                                                                                                                                          |
|      dirección url      |                                                            La dirección URL para el resultado. Esta será normalmente &mdash;pero no necesariamente&mdash; una ruta de acceso absoluta de la aplicación actual, en lugar de la dirección URL completa. Por ejemplo: /articles/article1/                                                             |

## <a name="settings"></a>configuración

Permite cargar cualquier [configuración de sitio](../configure/configure-site-settings.md) por nombre. Si no se encuentra un valor con un nombre dado, se devolverá [null](liquid-types.md#null).  

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
> [Represente un encabezado y una barra de navegación principal de página web](render-site-header-primary-navigation.md)


## <a name="sitemap"></a>mapa del sitio

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

|Atributo   |Descripción   |
|---|---|
| Actuales | Devuelve el objeto del nodo de mapa del sitio para la página actual.                    |
| Raíz    | Devuelve el objeto del nodo de mapa del sitio de la página raíz (principal) del sitio web. |

### <a name="site-map-node-attributes"></a>Atributos del nodo del mapa del sitio

|Atributo   |Descripción   |
|-------|-------|
| Rutas de navegación           | Devuelve los objetos de nodo del mapa del sitio de ruta de navegación para el nodo, empezando desde el nodo raíz del mapa del sitio y terminando en el principal. |
| Secundarios              | Devuelve objetos de nodo de mapa del sitio secundario del nodo.                                                                  |
| Descripción           | El contenido de descripción/resumen para el nodo. (Este campo puede contener HTML).                                          |
| Entidad                | Devuelve las [entidades](#entities) subyacentes del nodo. Si el nodo no tiene una entidad subyacente, este valor será null.                                                         |
| is\_sitemap\_ancestor | Devuelve true si el nodo del mapa del sitio es un antecesor del nodo actual, de lo contrario false.                                                                                                         |
| is\_sitemap\_current  | Devuelve true si el nodo del mapa del sitio es el nodo actual, de lo contrario false.                                                                                                         |
| Principal                | Devuelve el nodo de mapa del sitio principal del nodo. Si el nodo es el nodo raíz, principal será null.                                                                     |
| Cargo                 | El título del nodo.                                                                                                |
| dirección url                   | La dirección URL del nodo.                                                                                                  |


## <a name="sitemarkers"></a>marcadores de sitio

Permite cargar cualquier marcador de sitio por nombre. Si el marcador de sitio existe, se devolverá un objeto de marcador de sitio. Si no se encuentra un marcador de sitio con un nombre determinado, se devolverá [null](liquid-types.md#null).  

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
> [Represente un encabezado y una barra de navegación principal de página web](render-site-header-primary-navigation.md)  

### <a name="sitemarker-attributes"></a>Atributos de marcador de sitio

|         Atributo          |                                                                                    Descripción                                                                                    |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            dirección url             |                                                                         La dirección URL del destino del marcador de sitio.                                                                         |
| \[nombre lógico del atributo\] | Puede obtener acceso a cualquier atributo del registro de Power Apps de destino del marcador de sitio por nombre lógico. Por ejemplo, {{ sitemarker.adx\_name }} |

## <a name="snippets"></a>fragmentos

Permite cargar cualquier fragmento de contenido por nombre. Si no se encuentra un fragmento con un nombre dado, se devolverá [null](liquid-types.md#null).  

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

Contiene propiedades útiles en un bloque de bucle [Etiquetas de iteración](iteration-tags.md).  

> [!Note] 
> tablerowloop solo se puede usar dentro de una [etiqueta de iteración](iteration-tags.md).

### <a name="attributes"></a>Atributos

|Atributo   |Descripción   |
|---|---|
| Col        | Devuelve el índice de la fila actual, empezando en 1.                                                       |
| col0       | Devuelve el índice de la fila actual, empezando en 0.                                                       |
| col\_first | Devuelve true si la columna actual es la primera columna de una fila, devuelve false si no lo es.               |
| col\_last  | Devuelve true si la columna actual es la última columna de una fila, devuelve false si no lo es.                |
| Primera      | Devuelve true si es la primera iteración del bucle. Devuelve false si no es la primera iteración.       |
| Índice      | La ubicación del elemento actual en la colección, donde el primer artículo tiene una posición de 1.                   |
| index0     | La ubicación del elemento actual en la colección, donde el primer artículo tiene una posición de 0.                   |
| Última       | Devuelve true si es la última iteración del bucle. Devuelve false si no es la última iteración.         |
| Duración     | Devuelve el número de iteraciones para el de bucle ߝ el número de elementos en la colección que se está iterando. |
| Rindex     | Número de elementos que permanecen en el bucle (duración - índice) donde 1 es el índice del último elemento.              |
| rindex0    | Número de elementos que permanecen en el bucle (duración - índice) donde 0 es el índice del último elemento.              |



## <a name="user"></a>Usuario

Hace referencia al usuario del portal actual, que permite el acceso a todos los atributos del registro de contacto de Power Apps subyacente. Si ningún usuario ha iniciado sesión, esta variable será [null](liquid-types.md#null).  

El usuario es un objeto de [entidad](#entity).  

```
{% if user %}

Hello, {{ user.fullname }}!

{% else %}

Hello, anonymous user!

{% endif %}
```

### <a name="attributes"></a>Atributos

Además de tener todos los atributos de un objeto de [entidad](#entity), el usuario tiene los siguientes atributos.


|    Atributo     |                                                                                                                                                                                     Descripción                                                                                                                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      roles       |                                                      Devuelve los roles a los que pertenece el usuario como una [matriz](liquid-types.md#array).<br>`{% if user.roles contains 'Administrators' %} User is an administrator. {% endif %}`<br>**Nota**: También puede usar el filtro `has_role` para probar las suscripciones de roles individuales.                                                       |
| basic_badges_url | Devuelve la dirección URL del servicio para recuperar las insignias de un usuario.<br>Para que se muestren las insignias para un usuario, debe incluir una etiqueta con los atributos "data-badge" y "data-uri". Para mostrar las insignias del usuario actual:<br>`<div data-badge data-uri='{{user.basic_badges_url }}'></div>`<br>Para mostrar las insignias de un usuario por Id. (Id. de usuario variable):<br>\`<div data-badge data-uri='{{user.basic_badges_url |
|                  |                                                                                                                                                                                                                                                                                                                                                                                     |

## <a name="weblinks"></a>weblinks

Permite cargar cualquier weblinks por nombre o Id.  

Si existe el conjunto de vínculos web, se devolverá un [objeto de conjunto de vínculos web](#web-link-set-attributes). Si no se encuentra un conjunto de vínculos web con el nombre o el Id. dado, se devolverá [null](liquid-types.md#null).


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
> [Represente un encabezado y una barra de navegación principal de página web](render-site-header-primary-navigation.md) |  

### <a name="web-link-set-attributes"></a>Atributos de conjunto de vínculos web

> [!Note]
> Un conjunto de vínculos web es un objeto de [entidad](#entity), con todos los mismos atributos, además de los que se muestran a continuación.                                         

|         Atributo          |                                                                                 Descripción                                                                                  |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            Copia            |                                                                      Texto HTML del conjunto de vínculos web.                                                                      |
|            Nombre            |                                                                        Nombre del conjunto de vínculos web.                                                                         |
|           Cargo            |                                                                        Título del conjunto de vínculos web.                                                                        |
|          Weblinks          |                                                       La matriz de objetos de vínculo web asociada con el conjunto de vínculos web.                                                        |
| \[nombre lógico del atributo\] | Puede obtener acceso a cualquier atributo del registro de Power Apps del conjunto de vínculos web por nombre lógico. Por ejemplo, {{ weblinkset.createdon }} |

### <a name="web-link-attributes"></a>Atributos de vínculo web

> [!Note]
> Un vínculo web es un objeto de [entidad](#entity), con todos los mismos atributos, además de los que se muestran a continuación.

|          Atributo          |                                                                              Descripción                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Descripción         |                                                                 Descripción HTML del vínculo web.                                                                 |
|    display\_image\_only     |                              Atributo booleano que indica si el vínculo web debe mostrarse solo como imagen, sin el texto del vínculo.                               |
| display\_page\_child\_links |            Atributo booleano que indica si el vínculo web debe mostrar vínculos a páginas secundarias del [*mapa del sitio*](#sitemap) de la página vinculada, como vínculos secundarios.             |
|            Imagen            |                                     El objeto de imagen de vínculo web para este vínculo. Este atributo será nulo si no hay imagen presente.                                      |
|        is\_external         |                 Atributo booleano que indica si la dirección URL de destino del vínculo web es a un sitio externo (en lugar de una página del portal interno).                  |
|    is\_sitemap\_ancestor    |                                Devuelve true si la dirección URL del vínculo web hace referencia a un antepasado del nodo del mapa del sitio actual, de lo contrario false.                                 |
|    is\_sitemap\_current     |                                        Devuelve true si la dirección URL del vínculo web hace referencia a un nodo del mapa del sitio actual, de lo contrario false.                                        |
|            Nombre             |                                                                    Nombre/título del vínculo web.                                                                    |
|          Nofollow           |                                         Atributo booleano que indica si el vínculo web se debe marcar como rel=nofollow.                                         |
|    open\_in\_new\_window    |                             Atributo booleano que indica si el vínculo web se debe abrir en una nueva ventana/pestaña del explorador cuando se selecciona.                             |
|           Información sobre herramientas           |                                                                    Texto de información sobre herramientas para el vínculo web.                                                                     |
|             dirección url             |                                                                       Dirección URL del vínculo web.                                                                        |
|          Weblinks           |                                                   La matriz de objetos de vínculo web secundarios asociada con el vínculo web.                                                   |
| \[nombre lógico del atributo\]  | Puede obtener acceso a cualquier atributo del registro de Power Apps del vínculo web por nombre lógico. Por ejemplo, {{ weblink.createdon }} |

### <a name="web-link-image-attributes"></a>Atributos de imagen de vínculos web

| alternate\_text | Texto alternativo para la imagen.                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
| Alto          | Entero que contiene el alto especificado de la imagen. Si no se proporcionó ningún valor de alto, este atributo será nulo. |
| dirección url             | Dirección URL de la imagen.                                                                                               |
| Ancho           | Entero que contiene el ancho especificado de la imagen. Si no se proporcionó ningún valor de ancho, este atributo será nulo.   |


## <a name="website"></a>sitio web

Hace referencia al sitio web del portal, que permite el acceso a todos los atributos del registro del sitio web de Power Apps (adx\_website) para el portal.  

> [!Note]
> El sitio web es un objeto de [entidad](#entity), con todos los mismos atributos.

**Código**

```
{{ website.adx_name }} ({{ website.id }})
```

**Salida**

```
Community Portal (936DA01F-9ABD-4d9d-80C7-02AF85C822A8)
```


### <a name="see-also"></a>Vea también

[Tipos Liquid](liquid-types.md)  
[Etiquetas de Liquid](liquid-tags.md)  
[Filtros de Liquid](liquid-filters.md)  
