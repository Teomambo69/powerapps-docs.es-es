---
title: Usar etiquetas de entidad de Power Apps Common Data Service para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas de entidad de Power Apps Common Data Service disponibles en portales.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/28/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 83247403a482f7ce980f83a5813be2fd158e1be0
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980941"
---
# <a name="power-apps-common-data-service-entity-tags"></a>Etiquetas de entidad de Power Apps Common Data Service.

Las etiquetas de entidad de Power Apps se usan para cargar y mostrar los datos de Power Apps, o usar otros servicios de marco de portales de Power Apps. Estos etiquetas son extensiones específicas de Power Apps del lenguaje Liquid.

## <a name="chart"></a>Gráfico

Agrega un gráfico Power Apps a una página web. La etiqueta del gráfico puede añadirse en el campo Copiar en una página web o en el campo Origen en una Plantilla web. Para ver los pasos para agregar un gráfico de Power Apps en una página web, consulte [Agregar un gráfico a una página web en el portal](../configure/add-chart.md).

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>Parámetros

Existen dos parámetros que se ofrecerán junto con la etiqueta del gráfico: id. de gráfico y viewid.

**Id. de gráfico**

Identificador de visualización del gráfico. Puede obtener este elemento si exporta el gráfico.

**viewid**

Identificador de la entidad cuando se abre en el editor de vistas. 

## <a name="powerbi"></a>powerbi

Agrega los paneles e informes de Power BI dentro de las páginas. La etiqueta del gráfico puede añadirse en el campo **Copiar** en una página web o en el campo **Origen** en una plantilla web. Para ver los pasos para agregar un informe o una panel de Power BI a una página web en el portal, consulte [Adición de informes o paneles de Power BI a una página web en el portal](../admin/add-powerbi-report.md).

> [!NOTE]
> Para que la etiqueta funcione, debe [habilitar la integración de Power BI](../admin/set-up-power-bi-integration.md) desde el Centro de administración de portales de Power Apps. Si la integración de Power BI no está habilitada, el panel o el informe no se mostrará.

### <a name="parameters"></a>Parámetros

La etiqueta powerbi acepta los siguientes parámetros.

**path**

Ruta del informe o el panel de Power BI. Si el informe o el panel de Power BI son seguros, debe proporcionar el tipo de autenticación.

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Tipo de autenticación necesaria para el informe o el panel de Power BI. Los valores válidos para este parámetro son:

- **Anónimo**: Permite insertar publicaciones en informes de Power BI web. El tipo de autenticación predeterminado es Anónimo. Cuando utilice el tipo de autenticación como Anónimo, debe obtener la dirección URL del informe de Power BI como se describe en: [Publicar en la web desde Power BI](https://docs.microsoft.com/power-bi/service-publish-to-web)

- **AAD**: Permitir compartir informes Power BI o los paneles Power BI Azure Active Directory a los usuarios autenticados.

- **powerbiembedded**: Permite compartir los informes o los paneles seguros de Power BI con usuarios externos que no tienen licencia de Power BI o configuración de autenticación Azure Active Directory. Para obtener información sobre la configuración del servicio Power BI Embedded, consulte [Habilitar el servicio Power BI Embedded](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service). 

Mientras agrega el informe o el panel seguro de Power BI, asegúrese de que se comparte con servicios Azure Active Directory o Power BI Embedded del portal. 

> [!NOTE]
> Los valores del parámetro `authentication_type` no distinguen entre mayúsculas y minúsculas.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

También puede filtrar el informe por uno o varios valores. La sintaxis para filtrar un informe es:

URL?filter=**Tabla**/**Campo** eq '**valor**'

Por ejemplo, supongamos que desea filtrar el informe para ver los datos para un contacto Bert Hair. Debe anexar la dirección URL con lo siguiente:

?filter=Executives/Executive eq 'Bert Hair'

El código completado será:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

Más información sobre cómo filtrar un informe: [Filtrar un informe usando parámetros de cadena de consulta en la dirección URL](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> El informe anónimo no admite filtros. 

También puede crear una ruta dinámica mediante la variable de Liquid `capture ` como se ve a continuación:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Más información sobre la variable de Liquid: [Etiquetas de variables](variable-tags.md)

**tileid**

Muestra la ventana especificada del panel. Debe proporcionar el Id. de la ventana.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**roles**.

Roles asignados al informe Power BI. Este parámetro funciona únicamente cuando el parámetro **authentication_type** se establece en **powerbiembedded**.

Si ha definido roles en Power BI y los ha asignado a informes, se deben especificar los roles apropiados en la etiqueta Liquid **powerbi** . Los roles le permite filtre los datos que se mostrarán en un informe. Puede especificar varios roles separados por comas. Para obtener más información sobre la definición de roles en Power BI, consulte [Seguridad de nivel de fila (RLS) con Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Si ha asignado un rol a un informe de Power BI, y no especificó el parámetro **roles** en la etiqueta Liquid ni especificó un rol del parámetro, se mostrará un error.

> [!TIP]
> Si desea usar los roles web definidos en el portal como roles Power BI, puede definir una variable y asignarla roles web. Puede usar posteriormente la variable definido en la etiqueta Liquid.
>
> Digamos que ha definido dos roles web como Region_East y Region_West en el portal. Puede unirlos con el código: `{% assign webroles = user.roles | join: ", " %}`
>
> En el fragmento de código anterior, `webroles` es una variable y los roles web de Region_East y de Region_West se almacenarán en ella.
>
> Use la variable `webroles` como sigue en la etiqueta Liquid:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>editable

Representa un objeto CMS de portales de Power Apps como editable en el portal, para usuarios con permiso de edición de contenido para ese objeto. Los objetos editables son [página](liquid-objects.md#page), [fragmentos](liquid-objects.md#snippets) y [weblinks](liquid-objects.md#weblinks).  

```
{% editable page 'adx_copy' type: 'html', title: 'Page Copy', escape: false, liquid: true %}

{% editable snippets Header type: 'html' %}

<!--

An editable web link set required a specific DOM structure, with

certain classes on the containing element, as demonstrated here.

-->

{% assign primary_nav = weblinks[Primary Navigation] %}

{% if primary_nav %}

<div {% if primary_nav.editable %}class=xrm-entity xrm-editable-adx_weblinkset{% endif %}>

<ul>

<!-- Render weblinks... -->

</ul>

{% editable primary_nav %}

</div>

{% endif %}
```

### <a name="parameters"></a>Parámetros

El primer parámetro proporcionado a editable es el objeto editable. Por ejemplo, esto puede ser un conjunto de vínculos web, fragmentos o la página actual. El segundo parámetro opcional es para especificar un nombre de atributo o una clave dentro de ese objeto que se debe representar y editar. Esto puede ser el nombre de un atributo de entidad, o un nombre de fragmento, por ejemplo.

Después de estos parámetros iniciales, la etiqueta admite varios parámetros opcionales con nombre.

**clase**

Especifica un valor de atributo class para el elemento raíz representado por esta etiqueta.

**default**

Un valor predeterminado que se representará en caso de que el elemento editable no tenga ningún valor.

**escape**

Un valor booleano que indica si un valor generado por esta etiqueta se codificará como HTML. De forma predeterminada, es false.

**liquid**

Un valor booleano que indica si se procesará algún código de plantilla Liquid encontrado dentro del valor de texto representado por esta etiqueta. De forma predeterminada, es true.

**tag**

El nombre de las etiquetas HTML contenedoras que representará esta etiqueta. Esta etiqueta representará elementos div de forma predeterminada. Se recomienda generalmente elegir entre div o span como valor de este parámetro.

**title**

Especifica una etiqueta para este elemento editable en la interfaz de edición de contenido. Si no se ofrece ninguna, una etiqueta descriptiva se generará automáticamente.

**type**

Un valor de cadena que indica el tipo de interfaz de edición que se mostrará, para valores del texto modificables. Los valores válidos para este parámetro son html o texto. html es la opción predeterminada.

## <a name="entitylist"></a>entitylist

Carga una determinada lista de entidades, por nombre o Id. Puede obtener acceso a las propiedades de la lista de entidades utilizando un [objeto entitylist](liquid-objects.md#entitylist) que esté disponible en el bloque de etiqueta. Para representar los registros de resultados reales de la lista de entidades, use la etiqueta [entityview](#entityview) en el bloque.  

Si la lista de entidades se carga correctamente, el contenido del bloque se representará. Si la lista de entidades no se encuentra, el contenido del bloque no se representará.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
De forma predeterminada, el objeto entitylist recibirá el nombre de variable entitylist. Opcionalmente, puede proporcionar otro nombre de variable.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>Parámetros

Proporcione **solo uno**: id, name o key para seleccionar la lista de entidades que desea cargar.

**id**

Carga una lista de entidades por Id. [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier). id debe ser una cadena que se puede analizar como GUID.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Normalmente, las cadenas GUID literales no se usarán. En su lugar, se especificará id mediante una propiedad GUID de otra variable.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**name**

Carga una lista de entidades por nombre.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**key**

Carga una lista de entidades por ID **o** nombre. Si el valor de clave proporcionado se puede analizar como [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier), la lista de entidades se cargará por Id. De lo contrario, se cargará por nombre.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**language\_code**

Un código de idioma entero de Power Apps para seleccionar las etiquetas localizadas de la lista de entidades que se cargarán. Si no se proporciona un language\_code, el idioma predeterminado de la conexión de Power Apps de la aplicación del portal se usará.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

Carga una vista de Power Apps dada, por nombre o Id. A continuación se puede acceder a las propiedades de la vista ߝ de metadatos de columna de la vista, registros paginados de resultados, etc. utilizando un [objeto entityview](liquid-objects.md#entityview) que estará disponible en el bloque de etiquetas.  

Si la vista se carga correctamente, el contenido del bloque se representará. Si la vista no se encuentra, el contenido del bloque no se representará.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

De forma predeterminada, el objeto entityview recibirá el nombre de variable entityview. Opcionalmente, puede proporcionar otro nombre de variable.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Si entityview se anida en un bloque de entitylist, heredará su configuración predeterminada (tamaño de la página de resultados, opciones de filtrado, etc.) de la lista de entidades. Si no se proporcionan parámetros id o name de vista a entityview, cargará la vista predeterminada desde la entitylist asociada.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>Parámetros

Proporcione **bien** id**o bien** logical\_name con el nombre para seleccionar la vista de Power Apps para cargar. Si no se proporciona ninguna, y la etiqueta entityview está anidada en una etiqueta entitylist, se cargará la vista predeterminada de la entitylist asociada.

**id**

id debe ser una cadena que se puede analizar como GUID.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Normalmente, las cadenas GUID literales no se usarán. En su lugar, se especificará id mediante una propiedad GUID de otra variable.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**logical\_name**

Nombre lógico de la entidad de Power Apps de la vista que se va a cargar. Deben usarse junto con name.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**name**

El nombre de Power Apps de la vista que se cargará. Deben usarse junto con logical\_name.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filter**

Especifica si filtrar los resultados de la vista por usuario o cuenta. Debe tener un valor de cadena de usuario o cuenta.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro basado en una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafilter**

Especifica la expresión del filtro de metadatos de la lista de entidades por la que se filtrarán los resultados de la vista. Este parámetro solo es válido cuando entityview se utiliza junto con entitylist. En la mayoría de los casos, este parámetro se basa en una [solicitud](liquid-objects.md#request).  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**order**

Especifica una expresión de ordenación para ordenar los resultados de la vista. Una expresión de ordenación puede contener uno o varios nombres lógicos del atributo de entidad, seguido de una dirección de orden de ASC o DESC.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro basado en una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page**

Especifica la página de resultados de la vista para cargar. Si no se especifica este parámetro, la primera página de resultados se cargará.

Este parámetro se debe pasar como un valor entero, o una cadena que se pueda analizar como un entero. Si se proporciona un valor para este parámetro, pero el valor es nulo o no se puede analizar de otro modo como entero, la primera página de resultados se cargará.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro basado en una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**page\_size**

Especifica el número de resultados para cargar para la página de resultados actual. Si no se proporciona un valor para este parámetro, y entityview se usa en un bloque [entitylist](#entitylist), se usará el tamaño de página de la lista de entidades. Si no se encuentra en un bloque de entitylist, se usará un valor predeterminado de 10.

Este parámetro se debe pasar como un valor entero, o una cadena que se pueda analizar como un entero. Si se proporciona un valor para este parámetro, pero el valor es nulo o no se puede analizar de otro modo como entero, se usará el tamaño de página predeterminado.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro basado en una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**search**

Especifica una expresión de búsqueda por la que filtrar los resultados de la vista. Expresiones simples de búsqueda de palabras clave filtrarán en función de si los atributos empiezan por la palabra clave. Los comodines \* también se pueden incluir en la expresión.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

Un caso de uso compartido es establecer este parámetro basado en una [solicitud](liquid-objects.md#request), para poder establecer el filtro de búsqueda basado en la entrada del usuario.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**enable\_entity\_permissions**

Especifica si se va a aplicar filtrado de permisos de entidad a los resultados de la vista. Este parámetro se establece como false de manera predeterminada. Si entityview se usa en un bloque de entitylist, el valor de este parámetro se heredará de la configuración de la lista de entidades.

Este parámetro se debe pasar como un valor [booleano](liquid-types.md#boolean) o una cadena que se pueda analizar como un booleana (true, false). Si se proporciona un valor para este parámetro, pero el valor es nulo o no se puede analizar de otro modo como booleano, se usará false de forma predeterminada.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**language\_code**

Un código de idioma entero de Power Apps para seleccionar las etiquetas localizadas de vista de la entidad (etiquetas de encabezado de columna, etc.) para cargar. Si no se proporciona un language\_code, el idioma predeterminado de la conexión de Power Apps de la aplicación del portal se usará.

Si entityview se usa dentro de un bloque entitylist, entityview heredará su configuración de código de idioma de entitylist.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

Realiza una consulta en el índice de búsqueda del portal. Puede obtener acceso a los resultados que coincidan utilizando un [searchindex](liquid-objects.md#searchindex) que esté disponible en el bloque de etiqueta.  

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

De forma predeterminada, el objeto de índice de búsqueda recibirá el nombre de variable searchindex. Opcionalmente, puede proporcionar otro nombre de variable.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>Parámetros

La etiqueta searchindex acepta los siguientes parámetros.

**query**

La consulta usada para que coincidan los resultados. Este parámetro se usa para aceptar la parte especificada por el usuario de la consulta de índice (si la hay).

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

Un caso de uso común es establecer este parámetro basado en una [solicitud](liquid-objects.md#request).  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

Este parámetro admite la [sintaxis de analizador de consultas de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**filter**

Consulta adicional usada para que coincidan los resultados. Este parámetro se usa para aceptar un filtro especificado por el desarrollador para los resultados, si lo desea.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

Este parámetro admite la [sintaxis de analizador de consultas de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> La diferencia entre filter y query es aunque ambos aceptarán la sintaxis de analizador de consultas de Lucene, query está pensada para ser más indulgente sobre la sintaxis es ߝ analizada, pues se espera que la mayoría de los usuarios finales no conozcan esta sintaxis. Por lo tanto, en caso de que el análisis de query según la sintaxis genere un error, la consulta completa se incluirá con caracteres de escape y enviará como texto de la consulta. filter, por otro lado, se analizará estrictamente y devolverá un error en el caso de sintaxis no válida.

**logical\_names**

Los nombres lógicos de entidad de Power Apps a los que los resultados coincidentes estarán restringidos, como una cadena delimitada por comas. Si no se proporcionan, se devolverán todas las entidades que coincidan.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**page**

La página de resultados de búsqueda que se devolverá. Si no se proporciona, la primera página (1) será devuelta.

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

Un caso de uso común es establecer este parámetro basado en una [solicitud](liquid-objects.md#request).  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**page\_size**

El tamaño de la página de resultados que se devolverá. Si no se proporciona, se usará un tamaño predeterminado de 10.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

Representa completamente formularios de entidad configurados por Power Apps, por nombre o Id.  

> [!Note]
> La etiqueta entityform sólo está disponible para su uso en el contenido representado en una plantilla de página basada en <em>[plantilla web](store-content-web-templates.md)–</em>. Intentar usar la etiqueta en una plantilla de página basada en reescritura no representará nada. Solo puede representar una sola etiqueta entityform o webform por página. Las etiquetas entityform o webform después de la primera no se representarán.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>Parámetros

**name**

El nombre del formulario de entidad que desea cargar.

`{% entityform name:My Entity Form %}`

## <a name="webform"></a>webform

Representa completamente un formulario web configurado por Power Apps, por nombre o Id. La etiqueta webform solo está disponible para su uso en el contenido representado en una plantilla de página basada en [plantilla web](store-content-web-templates.md). Intentar usar la etiqueta en una plantilla de página basada en reescritura no representará nada. Solo puede representar una sola etiqueta entityform o webform por página. Las etiquetas entityform o webform después de la primera no se representarán.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>Parámetros

**name**

El nombre del formulario web que desea cargar.

`{% webform name:My Web Form %}`


### <a name="see-also"></a>Vea también

[Etiquetas del flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas variables](variable-tags.md)<br>
[Etiquetas de plantilla](template-tags.md)
