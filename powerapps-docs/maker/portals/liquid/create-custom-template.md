---
title: Crear una plantilla de página personalizada mediante Liquid y una plantilla de página de plantilla Web para un portal | MicrosoftDocs
description: Instrucciones para crear una plantilla de página personalizada mediante operadores Liquid.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8fe2d6f6496c609a9811ddb4ca28c3df47d8e04d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542458"
---
# <a name="create-a-custom-page-template"></a>Crear una plantilla de página personalizada

En este ejemplo, vamos a crear una plantilla de página personalizada mediante Liquid y una plantilla de página que se basa en una plantilla Web. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)] [almacenar el contenido de origen mediante plantillas web](store-content-web-templates.md). Nuestro objetivo es crear una plantilla de dos columnas simple que use un [conjunto de vínculos Web](../configure/manage-web-links.md) como navegación en el lado izquierdo, con el contenido de la página a la derecha. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>Paso 1: crear una plantilla Web y escribir el código de plantilla Liquid

En primer lugar, crearemos la plantilla Web y escribiremos el código de plantilla Liquid. Es probable que vuelvan a usar algunos elementos comunes de esta plantilla en plantillas futuras. Por lo tanto, vamos a crear una plantilla base común que se extenderá con nuestra plantilla específica. Nuestra plantilla base proporcionará vínculos de ruta de navegación y nuestro título o encabezado de página, así como definir el diseño de una columna:

> [!div class=mx-imgBorder]
![Diseño de una columna de plantilla Web](../media/web-template-two-column-layout.png "Diseño de una columna de plantilla Web")

> [!TIP]
> Más información sobre la herencia de plantillas con las etiquetas Block y extends: [etiquetas de plantilla](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>Diseño de dos columnas (plantilla Web)

```xml
<div class=container>
  <div class=page-heading>
    <ul class=breadcrumb>
      {% for crumb in page.breadcrumbs -%}
        <li>
          <a href={{ crumb.url }}>{{ crumb.title }}</a>
        </li>
      {% endfor -%}
      <li class=active>{{ page.title }}</li>
    </ul>
    <div class=page-header>
      <h1>{{ page.title }}</h1>
    </div>
  </div>
  <div class=row>
    <div class=col-sm-4 col-lg-3>
      {% block sidebar %}{% endblock %}
    </div>
    <div class=col-sm-8 col-lg-9>
      {% block content %}{% endblock %}
    </div>
  </div>
</div>
```

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>Paso 2: crear una nueva plantilla Web que extienda nuestra plantilla de diseño base

Use el conjunto de vínculos Web de navegación asociado a la página actual de los vínculos de navegación para crear una nueva plantilla Web que extienda nuestra plantilla de diseño base.

> [!div class=mx-imgBorder]
![Diseño Web de la plantilla Web diseño de navegación izquierda](../media/web-template-weblinks-left-navigation-layout.png "Diseño Web de la plantilla Web diseño de navegación izquierda")  

> [!TIP]
> Familiarícese en cómo cargar conjuntos de vínculos Web mediante el objeto [weblinks](liquid-objects.md#weblinks) .

### <a name="weblinks-left-navigation-web-template"></a>Navegación izquierda de weblinks (plantilla Web)

```xml
{% extends 'Two Column Layout' %}

{% block sidebar %}
  {% assign weblinkset_id = page.adx_navigation.id %}
  {% if weblinkset_id %}
    {% assign nav = weblinks[page.adx_navigation.id] %}
    {% if nav %}
      <div class=list-group>
        {% for link in nav.weblinks %}
          <a class=list-group-item href={{ link.url }}>
            {{ link.name }}
          </a>
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
{% endblock %}

{% block content %}
  <div class=page-copy>
    {{ page.adx_copy }}
  </div>
{% endblock %}
```

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>Paso 3: crear una nueva plantilla de página basada en la plantilla Web

En este paso, vamos a crear una nueva plantilla de página que se basa en la plantilla Web que creamos en el paso anterior.

> [!div class=mx-imgBorder]
![Diseño de la plantilla de página weblinks de navegación izquierda](../media/page-template-weblinks-left-navigation-layout.png "Diseño de la plantilla de página weblinks de navegación izquierda")  

## <a name="step-4-create-a-web-page-to-display-content"></a>Paso 4: crear una página web para mostrar contenido

Ahora, lo único que queda por hacer es crear una página web que use nuestra plantilla de página y tener un conjunto de vínculos Web asociado, y tenemos el resultado.

> [!div class=mx-imgBorder]
![Página Web con navegación izquierda](../media/web-page-left-navigation.png "Página Web con navegación izquierda")  

### <a name="see-also"></a>Vea también

[Crear una plantilla de página personalizada para representar una fuente RSS](render-rss-custom-page-template.md)  
[Representar la lista de entidades asociada a la página actual](render-entity-list-current-page.md)  
[Representar un encabezado de sitio web y una barra de navegación principal](render-site-header-primary-navigation.md)  
[Representar hasta tres niveles de jerarquía de páginas mediante la navegación híbrida](hybrid-navigation-render-page-hierachy.md)  

