---
title: Representar una fuente RSS mediante una plantilla de página personalizada para un portal | MicrosoftDocs
description: Instrucciones para crear una plantilla de página personalizada y usarla para representar una fuente RSS.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 240af2f54e153490794358dc1598b72a16fe1c38
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543321"
---
# <a name="create-a-custom-page-template-to-render-an-rss-feed"></a>Crear una plantilla de página personalizada para representar una fuente RSS
En este ejemplo, vamos a crear una plantilla de página personalizada para representar una [fuente RSS](https://en.wikipedia.org/wiki/RSS) de artículos de noticias, mediante Liquid y una plantilla de página de plantilla Web. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [almacenar el contenido de origen mediante plantillas web](store-content-web-templates.md)  

## <a name="step-1-create-a-new-powerapps-view"></a>Paso 1: creación de una nueva vista de PowerApps

En primer lugar, crearemos una nueva vista de PowerApps que usaremos para cargar los datos de la fuente. En este ejemplo, crearemos una vista en páginas web y usaremos esta entidad para almacenar nuestros artículos. Podemos usar esta vista para configurar la ordenación y el filtrado de los resultados, e incluir como columnas los atributos de entidad que queremos que estén disponibles en nuestra plantilla Liquid.

![Editar una plantilla de página](../media/edit-page-template.png "Editar una plantilla de página")  

## <a name="step-2-create-a-web-template-for-rss-feed"></a>Paso 2: crear una plantilla Web para la fuente RSS

En este paso, vamos a crear una plantilla Web para nuestra fuente RSS. Esta plantilla se aplicará a una página web determinada en nuestro sitio web, por lo que usaremos el título y el Resumen de esa página como título y descripción de la fuente. Usaremos la etiqueta entityview para cargar la vista de artículos de noticias recién creada. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [etiquetas de entidad de Common Data Service de PowerApps](portals-entity-tags.md). Tenga en cuenta que también se establece el campo de **tipo MIME** de la plantilla Web en aplicación/RSS + XML. Esto indica cuál podría ser el tipo de contenido de respuesta cuando se representa la plantilla.  

![Configurar una plantilla Web para una fuente RSS](../media/web-template-rss-feed.png "Configurar una plantilla Web para una fuente RSS")  

### <a name="rss-feed-web-template"></a>Fuente RSS (plantilla Web)

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

## <a name="step-3-create-a-page-template-to-assign-rss-feed-template"></a>Paso 3: crear una plantilla de página para asignar la plantilla de fuente RSS

Ahora, vamos a crear una nueva plantilla de página, lo que nos permite asignar nuestra plantilla de fuente RSS a cualquier página web de nuestro sitio Web. Tenga en cuenta que se anula la selección de **usar encabezado y pie**de página del sitio web, ya que se desea tomar una representación de la respuesta de página completa de nuestra fuente.

![Configurar una plantilla de página para una fuente RSS](../media/page-template-rss-feed.png "Configurar una plantilla de página para una fuente RSS")  

## <a name="step-4-create-a-web-page-to-host-rss-feed"></a>Paso 4: crear una página web para hospedar la fuente RSS

Ahora todo lo que queda es crear una nueva página web con la plantilla de fuente RSS para hospedar la fuente. Cuando solicitemos esta nueva página web, recibiremos nuestro XML de fuente RSS:

![Ejemplo de una fuente RSS](../media/rss-feed-example.png "Ejemplo de una fuente RSS")  

En este ejemplo, hemos visto cómo se pueden combinar características de liquidez, plantillas web, vistas de PowerApps y portales de administración de contenido para crear una fuente RSS personalizada. La combinación de estas características agrega funciones de personalización eficaces a cualquier aplicación del portal.

### <a name="see-also"></a>Vea también

[Creación de una plantilla de página personalizada mediante Liquid y una plantilla de página de plantilla Web](create-custom-template.md)  
[Representar la lista de entidades asociada a la página actual](render-entity-list-current-page.md)  
[Representar un encabezado de sitio web y una barra de navegación principal](render-site-header-primary-navigation.md)  
[Representar hasta tres niveles de jerarquía de páginas mediante la navegación híbrida](hybrid-navigation-render-page-hierachy.md)  

