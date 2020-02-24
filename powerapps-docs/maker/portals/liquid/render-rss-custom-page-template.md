---
title: Representar una fuente RSS a través de la plantilla de página personalizada para un portal | MicrosoftDocs
description: Instrucciones para crear una plantilla de página personalizada y usarla para representar una fuente de RSS.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d2c4956bd6d5e1a15e6308b4e40442ef15502178
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2981029"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>Crear una plantilla de página personalizada para representar una fuente RSS
En este ejemplo, crearemos una plantilla de página personalizada para representar una [fuente RSS](https://en.wikipedia.org/wiki/RSS) de artículos de noticias, utilizando Liquid y una plantilla de página web. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][Almacenar contenido de origen con plantillas web](store-content-web-templates.md).  

## <a name="step-1-create-a-new-power-apps-view"></a>Paso 1: Crear nueva vista de Power Apps

Primero, crearemos una nueva vista de Power Apps que utilizaremos para cargar los datos para nuestra fuente. En este ejemplo, la convertiremos en una vista de páginas web, y usaremos esta entidad para almacenar nuestros artículos. Podemos usar esta vista para configurar la ordenación y el filtrado de resultados, e incluir como columnas los atributos de entidad que deseamos disponibles en nuestra plantilla de Liquid.

![Edición una plantilla de página](../media/edit-page-template.png "Edición una plantilla de página")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>Paso 2: Crear una plantilla web para la fuente RSS

En este paso, crearemos una plantilla web para nuestra fuente RSS. Esta plantilla será aplicada a una página web particular en nuestro sitio web, por lo que usaremos el título y el resumen de esa página como título y descripción de la fuente. A continuación usaremos la etiqueta entityview para cargar nuestra vista Artículos de noticias recién creada. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [Etiquetas de entidad de Power Apps common data service](portals-entity-tags.md). Tenga en cuenta que también establecemos el campo **Tipo MIME** de la plantilla web como application/rss+xml. Esto indica qué tipo de contenido de respuesta podría ser cuando se representa nuestra plantilla.  

![Configurar una plantilla web para una fuente RSS](../media/web-template-rss-feed.png "Configurar una plantilla web para una fuente RSS")  

### <a name="rss-feed-web-template"></a>Fuente RSS (plantilla web)

```xml
<?xml version=1.0 encoding=UTF-8 ?>
<rss version=2.0>
  <channel>
    <title>{{ page.title | xml_escape }}</title>
    <description>{{ page.description | strip_html | xml_escape }}</description>
    <link>{{ request.url | xml_escape }}</link>
    {% entityview logical_name:'adx_webpage', name:'News Articles', page_size:20 -%}
      {% for item in entityview.records %}
        <item>
          <title>{{ item.adx_name | xml_escape }}</title>
          <description>{{ item.adx_copy | escape }}</description>
          <link>{{ request.url | base | xml_escape }}{{ item.url | xml_escape }}</link>
          <guid>{{ item.id | xml_escape }}</guid>
          <pubDate>{{ item.createdon | date_to_rfc822 }}</pubDate>
        </item>
      {% endfor -%}
    {% endentityview %}
  </channel>
</rss>
```

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>Paso 3: Crear una plantilla de página para asignar la plantilla de fuente RSS

Ahora, crearemos una nueva plantilla de página, lo que nos permitirá asignar nuestra plantilla de fuente RSS a cualquier página web en nuestro sitio web. Tenga en cuenta que anulamos la selección de **Usar encabezado y el pie de página del sitio web**, ya que deseamos establecer la representación de la respuesta de la página completa a nuestra fuente.

![Configurar una plantilla de página para una fuente RSS](../media/page-template-rss-feed.png "Configurar una plantilla de página para una fuente RSS")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>Paso 4: Crear una página web para hospedar fuente RSS

Ahora lo único que queda es crear una nueva página web a través de la plantilla de fuente RSS para hospedar nuestra fuente. Cuando solicitamos esta nueva página web, recibiremos nuestro XML de fuente RSS:

![Ejemplo de fuente RSS](../media/rss-feed-example.png "Ejemplo de fuente RSS")  

En este ejemplo, hemos visto cómo podemos agrupar características de administración de contenido de Liquid, plantillas web, vistas de Power Apps, y los portales para crear una fuente RSS personalizada. La combinación de estas características agrega eficaces capacidades de personalización a cualquier aplicación de portal.

### <a name="see-also"></a>Vea también

[Crear una plantilla de página personalizada con Liquid y una plantilla de página de plantilla web](create-custom-template.md)  
[Representar la lista de entidades asociada a la página actual](render-entity-list-current-page.md)  
[Represente un encabezado y una barra de navegación principal de página web](render-site-header-primary-navigation.md)  
[Represente hasta tres niveles de jerarquía de páginas mediante la navegación híbrida](hybrid-navigation-render-page-hierachy.md)  

