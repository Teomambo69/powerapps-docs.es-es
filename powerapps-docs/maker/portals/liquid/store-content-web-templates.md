---
title: Almacenar contenido de origen utilizando plantillas web en un portal | MicrosoftDocs
description: Instrucciones para almacenar contenido mediante las plantillas web en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: d75a8afd6b269078a4be3c0c7cc9b370cb9fe9f5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866466"
---
# <a name="store-source-content-by-using-web-templates"></a>Almacenar contenido de origen con plantillas web

La plantilla web es una entidad de Power Apps (adx\_webtemplate), que se incluye con los portales de Power Apps, que se usa para almacenar contenido de origen de la plantilla. Una plantilla web contendrá normalmente Liquid para representación de contenido dinámico, y es la entidad central usada para integrar plantillas de Liquid con el resto del sistema de portales de Power Apps.

Las plantillas web se pueden incluir en otro contenido o combinar con otras mediante etiquetas de plantilla, y se hace referencia a ellas en estas etiquetas mediante el atributo **Nombre**. También se pueden usar para crear plantillas de página personalizadas completas, o para crear encabezados o pies de página personalizados para el sitio web del portal.

## <a name="web-template-attributes"></a>Atributos de plantilla de web

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Nombre    |                                                                         Nombre de la plantilla. Usado para hacer referencia a esta plantilla cuando se incluye en otro contenido, o es ampliado por otras plantillas.                                                                         |
|  Origen   |                                  El contenido de origen de la plantilla. En Power Apps, un editor de código de origen con resalto de sintaxis y otras funciones de edición de código se proporciona para este campo.                                  |
| Tipo MIME | Opcionalmente proporciona un tipo MIME para el contenido de la plantilla. Si no se ofrece ninguno, se da por hecho un tipo de texto/html. Esta valor se usará solo en casos en que la plantilla esté asociada a una plantilla de página, y controla la representación de todo el contenido de esa plantilla. |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>Plantillas web como plantillas de página

Las plantillas web pueden usarse junto con plantillas de página para crear nuevas plantillas para el sistema de administración de contenido de los portales de Power Apps. Esto se puede hacer completamente desde Power Apps, sin necesidad de escribir código .NET o de volver a implementar la aplicación de portal.

Para crear una nueva plantilla de página a partir de una plantilla web, seleccione el **Tipo** de Plantilla web cuando cree un nuevo registro de plantilla de página. Luego seleccione una **Plantilla web**.

Observe la opción **Usar encabezado y el pie de página del sitio web** (que está activada de forma predeterminada). Si esta opción está activada, la plantilla web controlará la representación de todo el contenido de página entre el encabezado y pie de página del sitio web global. Si se desactiva esta opción, la plantilla web será el responsable de representar la respuesta completa ߝ en caso de que esté representando HTML, lo que implica todo desde el doctype hasta las etiquetas &lt;html&gt; raíz, y todo lo que hay en medio.

Si bien los casos de uso más comunes para plantillas web serán representar HTML, la representación de la respuesta completa (desactivando **Usar encabezado y el pie de página del sitio web**) le ofrece la opción de representar cualquier formato basado en texto que elija. Aquí es donde el atributo **Tipo MIME** de la plantilla web pasa a ser relevante. Cuando se representa una plantilla de página que no usa el encabezado y el pie de página del sitio web, el encabezado Tipo de contenido de respuesta HTTP se establecerá con el tipo MIME de la plantilla web asociada. (texto/html se usará si no se proporciona un Tipo MIME.) Esto le da una gran variedad de opciones para representar contenido no HTML utilizando Liquid. Un caso de uso común sería representar una fuente [RSS](https://en.wikipedia.org/wiki/RSS), estableciendo un tipo MIME de application/rss+xml.  

## <a name="web-templates-as-website-headers-and-footers"></a>Plantillas web como encabezados y pies de página de página web

Las plantillas web también se pueden usar para reemplazar el encabezado y el pie de página globales usados por un portal de Power Apps. Para ello, establezca el campo **Plantilla de encabezado** o **Plantilla de pie de página** de la página web en la plantilla web de su elección. Tenga en cuenta que si reemplaza el **Encabezado del sitio web**, la plantilla seleccionada asumirá la responsabilidad de representar la navegación principal, los vínculos de inicio/cierre de sesión, la interfaz de búsqueda, etc. para los elementos de la interfaz del sitio que suele gestionar la plantilla de encabezado predeterminada.

## <a name="built-in-web-templates"></a>Plantillas web integradas

Hay un conjunto de plantillas de Liquid preelaboradas disponibles en los portales de Power Apps. Para usarlos, debe incluirlos por nombre, mediante la siguiente lista como referencia.

| Nombre                        | Descripción                                                                                                                                                                                                                             | Código                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| Anuncio                          | Esta plantilla representa un anuncio por nombre, o un anuncio aleatorio de una ubicación de anuncio.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| Blogs                       | Esta plantilla representa las entradas de blog recientes de un grupo de listas.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| Rutas de navegación                 | Esta plantilla representa vínculos de páginas antecesoras hacia la página principal desde la página actual.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| Grupo de listas de vínculos secundarios       | Esta plantilla representa vínculos a todas las página secundarias de la página actual en un grupo de listas.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| Eventos: próximos            | Esta plantilla representa vínculos a eventos que tienen lugar entre ahora y 60 días a partir de ahora.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| Foros                      | Esta plantilla representa una lista de foros del sitio web con su número respectivo de hilos y entradas.                                                                                                                                 | `{% include 'forums' %}`                                       |
| Diseño 1 columna             | Esta plantilla representa un diseño de una sola columna que contiene rutas de navegación, el título de página y el contenido del texto de la página.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| Diseño 2 columnas izquierda ancha   | Esta plantilla representa un diseño de dos columnas. La columna izquierda es más ancha que la derecha. Contiene rutas de navegación, título de página en la parte superior de la página y el contenido de texto de la página en la columna de la izquierda.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| Diseño 2 columnas derecha ancha  | Esta plantilla representa un diseño de dos columnas. La columna derecha es más ancha que la izquierda. Contiene rutas de navegación, título de página en la parte superior de la página y el contenido de texto de la página en la columna de la derecha.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| Diseño 3 columnas central ancha | Esta plantilla representa un diseño de tres columnas. La columna central es más ancha que la izquierda y la derecha. El diseño contiene rutas de navegación y el título de página en la parte superior de la página y el contenido de texto de la página se encuentra en la columna central.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| Texto de página                   | Esta plantilla representa el HTML del contenido de texto editable de la página y admite líquido insertado.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| Encabezado de página                 | Esta plantilla representa el título de página.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| Sondeo                        | Esta plantilla representa un sondeo por nombre, o un sondeo aleatorio de una ubicación de sondeo.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Búsqueda                      | Esta plantilla representa un formulario básico de búsqueda con una sola entrada de texto y un botón de búsqueda.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| Navegación lateral             | Esta plantilla representa una navegación de estilo vista de árbol vertical. Tiene vínculos a las páginas antecesoras hacia el primer nivel (o el desplazamiento de profundidad especificado), vínculos a las páginas del mismo nivel que la página actual y vínculos a las páginas secundarias de la página actual. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| Fragmento                     | Esta plantilla representa un fragmento de contenido HTML editable por nombre.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| Navegación superior              | Esta plantilla representa una barra de navegación editable con menús desplegables para el conjunto de vínculos web de navegación principal.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Grupo de listas de vínculos web          | Esta plantilla representa un grupo de listas de vínculos para un conjunto de vínculos web.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>Vea también

[Descripción de los operadores de Liquid](liquid-operators.md)  
[Tipos Liquid](liquid-types.md)  
[Condicional](liquid-conditional-operators.md)  
[Objetos de Liquid](liquid-objects.md)  
[Etiquetas de Liquid](liquid-tags.md)  
[Filtros de Liquid](liquid-filters.md)  
