---
title: Almacenar contenido de origen mediante plantillas web en un portal | MicrosoftDocs
description: Instrucciones para almacenar contenido mediante plantillas web en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 76c8e525c5d5b612e055da9c43e14df55cec6e4f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543221"
---
# <a name="store-source-content-by-using-web-templates"></a>Almacenar contenido de origen mediante plantillas web

La plantilla Web es una entidad de PowerApps (ADX\_webtemplate), incluida con los portales de PowerApps, que se usa para almacenar el contenido de origen de la plantilla. Por lo general, una plantilla Web contiene Liquid para la representación dinámica de contenido y es la entidad central que se usa para integrar las plantillas líquidas con el resto del sistema de portales de PowerApps.

Las plantillas web pueden incluirse en otro contenido o combinarse con otras plantillas mediante etiquetas de plantilla, y se hace referencia a ellas en estas etiquetas por su atributo de **nombre** . También se pueden usar para crear plantillas de página personalizadas completas o para crear encabezados y pies de página personalizados para el sitio web del portal.

## <a name="web-template-attributes"></a>Atributos de plantilla Web

|           |                                                                                                                                                                                                                                                                                 |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Nombre    |                                                                         Nombre de la plantilla. Se usa para hacer referencia a esta plantilla cuando se incluye en otro contenido o se extiende por otras plantillas.                                                                         |
|  Fuentes   |                                  El contenido de origen de la plantilla. En PowerApps, se proporciona un editor de código fuente con resaltado de sintaxis y otras características de edición de código para este campo.                                  |
| Tipo MIME | Opcionalmente, proporciona un tipo MIME para el contenido de la plantilla. Si no se proporciona ninguno, se supone que se trata de un tipo de texto/HTML. Este valor solo se usará en los casos en los que la plantilla esté asociada a una plantilla de página y controla la representación de todo el contenido de esa plantilla. |
|           |                                                                                                                                                                                                                                                                                 |

## <a name="web-templates-as-page-templates"></a>Plantillas web como plantillas de página

Las plantillas web se pueden usar junto con las plantillas de página para crear nuevas plantillas para el sistema de administración de contenido de portales de PowerApps. Esto puede realizarse completamente en PowerApps, sin necesidad de escribir código .NET ni volver a implementar la aplicación del portal.

Para crear una nueva plantilla de página basada en una plantilla Web, seleccione un **tipo** de plantilla Web al crear un nuevo registro de plantilla de página. A continuación, seleccione una **plantilla Web**.

Tenga en cuenta la opción **usar encabezado y pie de página del sitio web** (que está activada de forma predeterminada). Si se activa esta opción, la plantilla Web controlará la representación del contenido de todas las páginas entre el encabezado y el pie de página del sitio web global. Si esta opción está desactivada, la plantilla Web será responsable de la representación de la respuesta completa en el caso de que se esté representando HTML, lo que significa todo lo que haya desde el DOCTYPE hasta el &lt;raíz&gt; etiquetas HTML y todo lo que hay entre ellos.

Aunque los casos de uso más comunes para las plantillas web van a representar HTML, la representación de la respuesta completa (mediante la anulación de la selección de **usar encabezado y pie**de página del sitio web) le ofrece la opción de representar cualquier formato basado en texto que elija. Aquí es donde el atributo de **tipo MIME** de la plantilla Web pasa a ser relevante. Cuando se representa una plantilla de página que no usa el encabezado y el pie de página del sitio web, el encabezado de tipo de contenido de respuesta HTTP se establecerá en el tipo MIME de la plantilla Web asociada. (se usará text/html si no se proporciona ningún tipo MIME). Esto le ofrece una amplia variedad de opciones para representar contenido no HTML mediante Liquid. Un caso de uso común sería representar una fuente [RSS](https://en.wikipedia.org/wiki/RSS) mediante la configuración de un tipo MIME de aplicación/RSS + XML.  

## <a name="web-templates-as-website-headers-and-footers"></a>Plantillas web como encabezados y pies de página del sitio web

Las plantillas web también se pueden usar para invalidar el encabezado y el pie de página globales usados por un portal de PowerApps. Para ello, establezca el campo plantilla de **encabezado** o **plantilla de pie de página** del sitio web en la plantilla Web de su elección. Tenga en cuenta que si invalida el **encabezado del sitio web**, la plantilla seleccionada asume la responsabilidad de representar la navegación principal, los vínculos de inicio y cierre de sesión, la interfaz de búsqueda, etc. para los elementos de la interfaz del sitio que normalmente se administran mediante el valor predeterminado. plantilla de encabezado.

## <a name="built-in-web-templates"></a>Plantillas web integradas

Hay un conjunto de plantillas de líquido predefinidas disponibles en los portales de PowerApps. Para usarlas, debe incluirlas por nombre, mediante la siguiente lista como referencia.

| Nombre                        | Descripción                                                                                                                                                                                                                             | Código                                                                                   |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| D.c.                          | Esta plantilla representa un anuncio por nombre o un anuncio aleatorio de una ubicación de ad.                                                                                                                                                               | `{% include 'ad' ad_name:'Name' %}{% include 'ad' ad_placement_name:'Placement Name' %}`                           |
| Blogs                       | Esta plantilla representa las entradas de blog recientes en un grupo de listas.                                                                                                                                                                                | `{% include 'blogs' %}`                                                              |
| Exploración                 | Esta plantilla representa los vínculos de las páginas antecesores de nuevo a la Página principal de la página actual.                                                                                                                                              | `{% include 'breadcrumbs' %}`                                                        |
| Grupo de lista de vínculos secundarios       | Esta plantilla representa vínculos a cualquier página secundaria de la página actual de un grupo de listas.                                                                                                                                                     | `{% include 'child_link_list_group' %}{% include 'child_link_list_group' title_only:true %}{% include 'child_link_list_group' image_width:'64px', image_height:'64px' %}`  |
| Eventos: próximos            | Esta plantilla representa los vínculos a los eventos que se producen entre Now y 60 días a partir de ahora.                                                                                                                                                      | `{% include 'events_upcoming' %}{% include 'events_upcoming' number_of_days_in_advance:60 %}`                   |
| Foros                      | Esta plantilla representa una lista de los foros del sitio web con su número respectivo de subprocesos y publicaciones.                                                                                                                                 | `{% include 'forums' %}`                                       |
| Columna diseño 1             | Esta plantilla representa un diseño de una sola columna que contiene rutas de navegación, el título de la página y el contenido de la copia de la página.                                                                                                                                 | `{% extends 'layout_1_column' %}{% block main %}...   {% endblock %}`                         |
| Diseño 2 columna ancha izquierda   | Esta plantilla representa un diseño de dos columnas. La columna izquierda es más ancha que la derecha. Contiene las rutas de navegación, el título de la página en la parte superior de la página y la página copiar contenido se encuentra en la columna izquierda.                                 | `{% extends 'layout_2_column_wide_left' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                                                      |
| Diseño 2 columna derecha ancha  | Esta plantilla representa un diseño de dos columnas. La columna de la derecha es más ancha que la izquierda. Contiene las rutas de navegación, el título de la página en la parte superior de la página y la página copiar contenido se encuentra en la columna derecha.                                | `{% extends 'layout_2_column_wide_right' %}{% block main %}...{% endblock %}{% block aside %}...{% endblock %}`                                      |
| Diseño 3 columna ancho medio | Esta plantilla representa un diseño de tres columnas. La columna central es más ancha que la izquierda y la derecha. El diseño contiene rutas de navegación y el título de la página en la parte superior de la página y la página copiar contenido se encuentra en la columna central.   | `{% extends 'layout_3_column_wide_middle' %}{% block left_aside %}...{% endblock %}{% block main %}...{% endblock %}{% block right_aside %}...{% endblock %}`                                                                      |
| Copia de página                   | Esta plantilla representa la página modificable HTML de copia de contenido con compatibilidad con Liquid insertado.                                                                                                                                             | `{% include 'page_copy' %}`                                                         |
| Encabezado de página                 | Esta plantilla representa el título de la página.                                                                                                                                                                                                   | `{% include 'page_header' %}`                                               |
| Sondeo                        | Esta plantilla representa un sondeo por nombre o un sondeo aleatorio de una ubicación de sondeo.                                                                                                                                                           | `{% include 'poll' poll_name:'Name' %}{% include 'poll' poll_placement_name:'Placement Name' %}`                         |
| Search                      | Esta plantilla representa un formulario básico de búsqueda con un solo botón de búsqueda y entrada de texto.                                                                                                                                                   | `{% include 'search' %}`                                                             |
| Navegación lateral             | Esta plantilla representa una navegación de estilo de vista de árbol vertical. Tiene vínculos a páginas antecesoras de vuelta al primer nivel (o el desplazamiento de profundidad especificado), vínculos a páginas relacionadas de la página actual y vínculos a elementos secundarios de la página actual. | `{% include 'side_navigation' %}{% include 'side_navigation' depth_offset:1 %}`                                  |
| Snippet                     | Esta plantilla representa un fragmento de código HTML modificable por nombre.                                                                                                                                                                         | `{% include 'snippet' snippet_name:'Name' %}`                                       |
| Navegación superior              | Esta plantilla representa una barra de navegación editable con menús desplegables para el conjunto de vínculos Web de navegación principal.                                                                                                                                 | `{% include 'top_navigation' %}`                                         |
| Grupo de listas de WebLink          | Esta plantilla representa un grupo de lista de vínculos para un conjunto de vínculos Web.                                                                                                                                                                         | `{% include 'weblink_list_group' weblink_set_name:'Name' %}`                     |
||

### <a name="see-also"></a>Vea también

[Descripción de los operadores Liquid](liquid-operators.md)  
[Tipos de líquido](liquid-types.md)  
[Instrucción](liquid-conditional-operators.md)  
[Objetos Liquid](liquid-objects.md)  
[Etiquetas líquidas](liquid-tags.md)  
[Filtros líquidos](liquid-filters.md)  
