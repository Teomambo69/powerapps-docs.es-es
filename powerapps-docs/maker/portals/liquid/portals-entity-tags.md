---
title: Uso de etiquetas de entidad Common Data Service de PowerApps para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas de entidad de PowerApps Common Data Service disponibles en el portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b6efc3e176602d366315b9b54b66593005051e55
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543257"
---
# <a name="powerapps-common-data-service-entity-tags"></a>Etiquetas de entidad de Common Data Service PowerApps

Las etiquetas de entidad de PowerApps se usan para cargar y Mostrar datos de PowerApps, o para usar otros servicios de marco de portal de PowerApps. Estas etiquetas son extensiones específicas de PowerApps para el lenguaje Liquid.

## <a name="chart"></a>gráfica

Agrega un gráfico de PowerApps a una página web. La etiqueta de gráfico se puede Agregar en el campo de copia de una página web o en el campo de origen de una plantilla Web. Para conocer los pasos para agregar un gráfico de PowerApps a una página web, consulte [Agregar un gráfico a una página web en el portal](../configure/add-chart.md).

```
{% chart id:"EE3C733D-5693-DE11-97D4-00155DA3B01E" viewid:"00000000-0000-0000-00AA-000010001006" %}
```

### <a name="parameters"></a>Parámetros

Hay dos parámetros que se proporcionan con la etiqueta de gráfico: ID. de gráfico y viewid.

**identificador de gráfico**

IDENTIFICADOR de visualización del gráfico. Para obtener esto, exporte el gráfico.

**viewid**

IDENTIFICADOR de la entidad cuando se abre en el editor de vistas. 

## <a name="powerbi"></a>powerbi

Agrega los paneles e informes de Power BI dentro de las páginas. La etiqueta se puede Agregar en el campo de **copia** de una página web o en el campo de **origen** de una plantilla Web. Para conocer los pasos para agregar un informe o un panel de Power BI a una página web en el portal, consulte [Agregar un informe o un panel de Power BI a una página web en el portal](../admin/add-powerbi-report.md).

> [!NOTE]
> Para que la etiqueta funcione, debe [Habilitar la integración de Power BI](../admin/set-up-power-bi-integration.md) desde el centro de administración de portales de PowerApps. Si no está habilitada la integración de Power BI, no se mostrará el panel o el informe.

### <a name="parameters"></a>Parámetros

La etiqueta powerbi acepta los parámetros siguientes:

**camino**

Ruta de acceso del informe o panel de Power BI. Si el informe o el panel de Power BI es seguro, debe proporcionar el tipo de autenticación.

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

**authentication_type**

Tipo de autenticación necesario para el informe o panel de Power BI. Los valores válidos para este parámetro son:

- **Anónimo**: permite incrustar informes de publicación en Power BI Web. El tipo de autenticación predeterminado es Anonymous.

- **AAD**: le permite compartir informes o paneles de Power BI seguros para Power BI Azure Active Directory usuarios autenticados.

- **powerbiembedded**: le permite compartir los informes o paneles de Power BI seguros con usuarios externos que no tienen Power BI licencia o Azure Active Directory la configuración de la autenticación. Para obtener información sobre la configuración del servicio de Power BI Embedded, consulte [enable Power BI Embedded Service](../admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service). 

Mientras agrega el informe o panel de Power BI seguro, asegúrese de que se comparte con los servicios de Azure Active Directory o Power BI Embedded del portal. 

> [!NOTE]
> Los valores del parámetro `authentication_type` no distinguen mayúsculas de minúsculas.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

También puede filtrar el informe en uno o varios valores. La sintaxis para filtrar un informe es la siguiente:

URL? Filter =**tabla**/**campo** EQ '**Value**'

Por ejemplo, supongamos que desea filtrar el informe para ver los datos de un contacto denominado Bert cabello. Debe agregar la dirección URL con lo siguiente:

? Filter = Ejecutivos/Executive EQ ' Bert cabello '

El código completo será:

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq 'Bert Hair'" %}
```

Más información sobre cómo filtrar un informe: [filtrar un informe con parámetros de cadena de consulta en la dirección URL](https://docs.microsoft.com/power-bi/service-url-filters)

> [!NOTE]
> El informe anónimo no admite el filtrado. 

También puede crear una ruta de acceso dinámica mediante el `capture ` variable Liquid como se indica a continuación:

```
{% capture pbi_path %}https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01?filter=Executives/Executive eq '{{user.id}}'{% endcapture %}
{% powerbi authentication_type:"AAD" path:pbi_path %}
```

Más información sobre variables líquidas: [etiquetas de variables](variable-tags.md)

**tileid**

Muestra el icono especificado del panel. Debe proporcionar el identificador del icono.

```
{% powerbi authentication_type:"AAD" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/dashboards/00000000-0000-0000-0000-000000000001" tileid:"00000000-0000-0000-0000-000000000002" %}
```

**roles**

Roles asignados al informe de Power BI. Este parámetro solo funciona cuando el parámetro **authentication_type** se establece en **powerbiembedded**.

Si ha definido roles en Power BI y los ha asignado a los informes, debe especificar los roles adecuados en la etiqueta Liquid de **powerbi** . Los roles permiten filtrar los datos que se van a mostrar en un informe. Puede especificar varios roles separados por una coma. Para obtener más información sobre cómo definir roles en Power BI, consulte [seguridad de nivel de fila (RLS) con Power BI](https://docs.microsoft.com/power-bi/service-admin-rls).

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:"Region_East,Region_West" %}
```

Si ha asignado un rol a un informe de Power BI y no ha especificado el parámetro **roles** en la etiqueta Liquid o no ha especificado un rol en el parámetro, se muestra un error.

> [!TIP]
> Si desea usar los roles web definidos en el portal como roles Power BI, puede definir una variable y asignarle roles Web. Después, puede usar la variable definida en la etiqueta Liquid.
>
> Supongamos que ha definido dos roles web como Region_East y Region_West en el portal. Puede combinarlos mediante el código: `{% assign webroles = user.roles | join: ", " %}`
>
> En el fragmento de código anterior, `webroles` es una variable y los roles web Region_East y Region_West se almacenarán en ella.
>
> Use la variable `webroles` como se indica a continuación en la etiqueta Liquid:
>
> `{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000000/ReportSection2" roles:webroles%}`

## <a name="editable"></a>edita

Representa un objeto CMS de portales de PowerApps determinado como editable en el portal, para los usuarios con permiso de edición de contenido para ese objeto. Los objetos editables incluyen [Página](liquid-objects.md#page), [fragmentos de código](liquid-objects.md#snippets)y [weblinks](liquid-objects.md#weblinks).  

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

El primer parámetro proporcionado a editable es el objeto editable. Por ejemplo, puede tratarse de un conjunto de vínculos Web, fragmentos de código o la página actual. El segundo parámetro opcional es especificar un nombre de atributo o una clave dentro de ese objeto que se va a representar y editar. Este puede ser el nombre de un atributo de entidad o un nombre de fragmento de código, por ejemplo.

Después de estos parámetros iniciales, la etiqueta admite varios parámetros con nombre opcionales.

**las**

Especifica un valor de atributo de clase para el elemento raíz representado por esta etiqueta.

**predeterminada**

Un valor predeterminado que se va a representar en caso de que el elemento editable no tenga ningún valor.

**salida**

Valor booleano que indica si un valor representado por esta etiqueta va a codificarse en HTML. De forma predeterminada, es false.

**circula**

Un valor booleano que indica si se procesará cualquier código de plantilla Liquid que se encuentre dentro del valor de texto representado por esta etiqueta. Esto es así de forma predeterminada.

**etiqueta**

El nombre de las etiquetas HTML del contenedor que se representarán mediante esta etiqueta. Esta etiqueta representará los elementos div de forma predeterminada. Por lo general, se recomienda elegir entre div o span como valor para este parámetro.

**Titulo**

Especifica una etiqueta para este elemento editable dentro de la interfaz de edición de contenido. Si no se proporciona ninguno, se generará automáticamente una etiqueta descriptiva.

**automáticamente**

Valor de cadena que indica el tipo de interfaz de edición que se va a presentar, para los valores de texto modificable. Los valores válidos para este parámetro son HTML o texto. HTML es el valor predeterminado.

## <a name="entitylist"></a>entitylist

Carga una lista de entidades determinada, por nombre o identificador. A continuación, se puede tener acceso a las propiedades de la lista de entidades mediante un [objeto entitylist](liquid-objects.md#entitylist) que estará disponible en el bloque de etiquetas. Para representar los registros de resultados reales de la lista de entidades, use la etiqueta [entityview](#entityview) en el bloque.  

Si la lista de entidades se carga correctamente, se representará el contenido del bloque. Si no se encuentra la lista de entidades, no se representará el contenido del bloque.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```
De forma predeterminada, al objeto entitylist se le asignará el nombre de variable entitylist. Opcionalmente, se puede proporcionar un nombre de variable diferente.

```
{% entitylist my_list = name:My Entity List %}

Loaded entity list {{ my_list.adx_name }}.

{% endentitylist %}
```

### <a name="parameters"></a>Parámetros

Proporcione **solo un** identificador, nombre o clave para seleccionar la lista de entidades que se va a cargar.

**sesión**

Carga una lista de entidades por identificador de [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier) . ID debe ser una cadena que se pueda analizar como un GUID.  

```
{% entitylist id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

Por lo general, no se usarán cadenas de GUID literales. En su lugar, se especificará ID mediante una propiedad GUID de otra variable.

```
{% entitylist id:page.adx_entitylist.id %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**Name**

Carga una lista de entidades por nombre.

```
{% entitylist name:My Entity List %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**clave**

Carga una lista de entidades por identificador **o** nombre. Si el valor de clave proporcionado se puede analizar como un [GUID](https://en.wikipedia.org/wiki/Globally_unique_identifier), la lista de entidades se cargará mediante el identificador. De lo contrario, se cargará por nombre.

```
<!-- key_variable can hold an ID or name -->

{% entitylist key:key_variable %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

**código de lenguaje\_**

Un código de idioma de entero de PowerApps para seleccionar las etiquetas localizadas de la lista de entidades que se van a cargar. Si no se proporciona ningún lenguaje\_código, se usará el idioma predeterminado de la conexión de PowerApps de aplicación del portal.

```
{% entitylist name:"My Entity List", language_code:1033 %}

Loaded entity list {{ entitylist.adx_name }}.

{% endentitylist %}
```

## <a name="entityview"></a>entityview

Carga una vista de PowerApps determinada, por nombre o identificador. A continuación, se puede acceder a las propiedades de la vista ߝ ver metadatos de columna, registros de resultados paginados, etc. mediante un [objeto entityview](liquid-objects.md#entityview) que estará disponible en el bloque de etiquetas.  

Si la vista se carga correctamente, se representará el contenido del bloque. Si no se encuentra la vista, el contenido del bloque no se representará.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

De forma predeterminada, al objeto entityview se le asignará el nombre de variable entityview. Opcionalmente, se puede proporcionar un nombre de variable diferente.

```
{% entityview my_view = logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ my_view.total_records }} total records.

{% endentityview %}
```

Si entityview está anidado dentro de un bloque entitylist, heredará su configuración predeterminada (tamaño de página de resultados, opciones de filtro, etc.) de la lista de entidades. Si no se proporciona ningún parámetro de nombre o identificador de vista a entityview, cargará la vista predeterminada de la entitylist envolvente.

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview %}

Loaded default view of the entity list associated with the current page, with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

### <a name="parameters"></a>Parámetros

Proporcione **el** nombre del\_lógico **o** el identificador con el nombre para seleccionar la vista de PowerApps que se va a cargar. Si no se proporciona ninguno y la etiqueta entityview está anidada dentro de una etiqueta entitylist, se cargará la vista predeterminada de la entitylist envolvente.

**sesión**

ID debe ser una cadena que se pueda analizar como un GUID.

```
{% entityview id:936DA01F-9ABD-4d9d-80C7-02AF85C822A8 %}

Loaded entity view {{ entityview.name }}.

{% endentityview %}
```

Por lo general, no se usarán cadenas de GUID literales. En su lugar, se especificará ID mediante una propiedad GUID de otra variable.

```
{% entityview id:request.params.view %}

Loaded entity view {{ entityview.name }} using view query string request parameter.

{% endentityview %}
```

**nombre del\_lógico**

Nombre lógico de la entidad de PowerApps de la vista que se va a cargar. Debe usarse en combinación con el nombre.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**Name**

Nombre de PowerApps de la vista que se va a cargar. Debe usarse en combinación con el nombre de\_lógico.

```
{% entityview logical_name:'contact', name:"Active Contacts" %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**filtro**

Especifica si se van a filtrar los resultados de la vista por usuario o cuenta. Debe tener un valor de cadena de usuario o cuenta.

```
{% entityview id:request.params.view, filter:'user' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, filter:request.params.filter %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**metafiltro**

Especifica la expresión de filtro de metadatos de la lista de entidades por la que filtrar los resultados de la vista. Este parámetro solo es válido cuando entityview se usa en combinación con entitylist. En la mayoría de los casos, este parámetro se establece en función de una [solicitud](liquid-objects.md#request).  

```
{% entitylist id:page.adx_entitylist.id %}

{% entityview id:request.params.view, metafilter:request.params.mf %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}

{% endentitylist %}
```

**orden**

Especifica una expresión de ordenación para ordenar los resultados de la vista. Una expresión de ordenación puede contener uno o más nombres lógicos de atributo de entidad, seguido de una dirección de ordenación de ASC o DESC.

```
{% entityview id:request.params.view, order:'name ASC, createdon DESC' %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, order:request.params.order %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**del**

Especifica la página de resultados de la vista que se va a cargar. Si no se especifica este parámetro, se cargará la primera página de resultados.

Este parámetro debe pasar un valor entero o una cadena que se pueda analizar como un entero. Si se proporciona un valor para este parámetro, pero el valor es null o no se puede analizar como un entero, se cargará la primera página de resultados.

```
{% entityview id:request.params.view, page:2 %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page:request.params.page %}

Loaded page {{ entityview.page }} of entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**tamaño de\_de página**

Especifica el número de resultados que se van a cargar para la página de resultados actual. Si no se proporciona ningún valor para este parámetro y entityview se usa dentro de un bloque [entitylist](#entitylist) , se usará el tamaño de página de la lista de entidades. Si no se encuentra dentro de un bloque entitylist, se usará un valor predeterminado de 10.

Este parámetro debe pasar un valor entero o una cadena que se pueda analizar como un entero. Si se proporciona un valor para este parámetro, pero el valor es null o no se puede analizar como un entero, se usará el tamaño de página predeterminado.

```
{% entityview id:request.params.view, page_size:20 %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request).  

```
{% entityview id:request.params.view, page_size:request.params.pagesize %}

Loaded entity view with {{ entityview.total_records }} total records.

{% endentityview %}
```

**buscan**

Especifica una expresión de búsqueda por la que filtrar los resultados de la vista. Las expresiones de búsqueda de palabras clave simples filtrarán por si los atributos comienzan con la palabra clave. Los caracteres comodín \* también pueden incluirse en la expresión.

```
{% entityview id:request.params.view, search:'John\*' %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request), de modo que el filtro de búsqueda se pueda establecer en función de los datos proporcionados por el usuario.  
```
{% entityview id:request.params.view, search:request.params.search %}

Loaded entity view with {{ entityview.total_records }} total matching records.

{% endentityview %}
```

**habilitar\_Entity\_permisos**

Especifica si se debe aplicar el filtrado de permisos de entidad en los resultados de la vista. De forma predeterminada, este parámetro se establece en false. Si entityview se usa dentro de un bloque entitylist, el valor de este parámetro se heredará de la configuración de la lista de entidades.

Este parámetro debe pasar un valor [booleano](liquid-types.md#boolean) o una cadena que se pueda analizar como booleano (true, false). Si se proporciona un valor para este parámetro, pero el valor es null o no se puede analizar como booleano, se usará el valor predeterminado de false.  

```
{% entityview id:request.params.view, enable_entity_permissions:true %}

Loaded entity view with {{ entityview.total_records }} total records to which the user has read permission.

{% endentityview %}
```

**código de lenguaje\_**

Un código de idioma de entero de PowerApps para seleccionar las etiquetas localizadas de la vista de entidad (etiquetas de encabezado de columna, etc.) que se van a cargar. Si no se proporciona ningún lenguaje\_código, se usará el idioma predeterminado de la conexión de PowerApps de aplicación del portal.

Si entityview se usa dentro de un bloque entitylist, entityview heredará su configuración de código de idioma de entitylist.

```
{% entityview logical_name:'contact', name:"Active Contacts", language_code:1033 %}

Loaded entity view {{ entityview.name }}.

{% endentitylist %}
```

## <a name="searchindex"></a>searchindex

Realiza una consulta en el índice de búsqueda del portal. A continuación, se puede tener acceso a los resultados de búsqueda de coincidencias mediante un [searchindex](liquid-objects.md#searchindex) que estará disponible en el bloque de etiquetas.  

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

De forma predeterminada, al objeto de índice de búsqueda se le asignará el nombre de variable searchindex. Opcionalmente, se puede proporcionar un nombre de variable diferente.

```
{% searchindex liquid_search = query: 'support', page: params.page, page_size: 10 %}

{% if liquid_search.results.size > 0 %}

...

{% endif %}

{% endsearchindex %}
```

### <a name="parameters"></a>Parámetros

La etiqueta searchindex acepta los siguientes parámetros.

**misma**

Consulta utilizada para buscar coincidencias con los resultados. Este parámetro está pensado para aceptar la parte especificada por el usuario de la consulta de índice (si existe).

```
{% searchindex query: 'support' %}

...

{% endsearchindex %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request).  

```
{% searchindex query: request.params.query %}

...

{% endsearchindex %}
```

Este parámetro es compatible con [la sintaxis del analizador de consultas de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).

**filtro**

Consulta adicional que se usa para comparar los resultados. Este parámetro está pensado para aceptar un filtro especificado por el desarrollador para los resultados, si se desea.

```
{% searchindex query: request.params.query, filter: '+statecode:0' %}

...

{% endsearchindex %}
```

Este parámetro es compatible con [la sintaxis del analizador de consultas de Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html).  

> [!Note]     
> La diferencia entre Filter y Query es que, aunque ambos aceptarán la sintaxis del analizador de consultas de Lucene, la consulta está pensada para ser más permisivo sobre cómo se analiza esta sintaxis ߝ, ya que se espera que la mayoría de los usuarios finales no conozcan esta sintaxis. Por lo tanto, en el caso de que se produzca un error en la consulta de análisis según esta sintaxis, se aplicará un carácter de escape a toda la consulta y se enviará como texto de la consulta. el filtro, por otro lado, se analizará estrictamente y devolverá un error si el caso de la sintaxis no es válida.

**nombres de\_lógicos**

Los nombres lógicos de la entidad PowerApps a los que se limitarán los resultados coincidentes, como una cadena delimitada por comas. Si no se proporciona, se devolverán todas las entidades coincidentes.

```
{% searchindex query: request.params.query, logical_names: 'kbarticle,incident' %}

...
>
{% endsearchindex %}
```
**del**

Página de resultados de la búsqueda que se va a devolver. Si no se proporciona, se devolverá la primera página (1).

```
{% searchindex query: request.params.query, page: 2 %}

...

{% endsearchindex %}
```

Un caso de uso común es establecer este parámetro en función de una [solicitud](liquid-objects.md#request).  

```
{% searchindex query: request.params.query, page: request.params.page %}

...

{% endsearchindex %}
```

**tamaño de\_de página**

Tamaño de la página de resultados que se va a devolver. Si no se proporciona, se usará un tamaño predeterminado de 10.

```
{% searchindex query: request.params.query, page_size: 20 %}

...

{% endsearchindex %}
```

## <a name="entityform"></a>entityform

Representa por completo un formulario de entidad configurado por PowerApps, por nombre o identificador.  

> [!Note]
> La etiqueta entityform solo está disponible para su uso en el contenido representado dentro de una plantilla de página basada en  <em>[plantillas web](store-content-web-templates.md)</em>. Si intenta usar la etiqueta dentro de una plantilla de página basada en reescritura, no se representará nada. Solo puede representar una sola etiqueta de entityform o WebForm por cada página. las etiquetas entityform o WebForm después de la primera no se representarán.       

`{% entityform name: 'My Entity Form' %}`

### <a name="parameters"></a>Parámetros

**Name**

Nombre del formulario de la entidad que desea cargar.

`{% entityform name:My Entity Form %}`

### <a name="webform"></a>**WebForm**

Representa por completo un formulario web configurado por PowerApps, por nombre o identificador. La etiqueta WebForm solo está disponible para su uso en el contenido representado dentro de una plantilla de página basada en [plantillas web](store-content-web-templates.md) . Si intenta usar la etiqueta dentro de una plantilla de página basada en reescritura, no se representará nada. Solo puede representar una sola etiqueta de entityform o WebForm por cada página. las etiquetas entityform o WebForm después de la primera no se representarán.                
`{% webform name: 'My Web Form' %}`

### <a name="parameters"></a>Parámetros

**Name**

Nombre del formulario web que desea cargar.

`{% webform name:My Web Form %}`

### <a name="see-also"></a>Vea también

[Etiquetas de flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas de variables](variable-tags.md)<br>
[Etiquetas de plantilla](template-tags.md)
