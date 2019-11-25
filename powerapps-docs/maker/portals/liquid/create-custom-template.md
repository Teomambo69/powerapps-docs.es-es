---
title: Crear una plantilla de página personalizada con Liquid y una plantilla de página web para un portal | MicrosoftDocs
description: Instrucciones para crear una plantilla de página personalizada con operadores de Liquid.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757420"
---
# <a name="create-a-custom-page-template"></a>Crear una plantilla de página personalizada

En este ejemplo, crearemos una plantilla de páginas personalizada, usando Liquid y una plantilla de página que se basa en una plantilla web. [!INCLUDE[proc-more-information](../../../includes/proc-more-information.md)][Almacenar contenido de origen con plantillas web](store-content-web-templates.md). Nuestra objetivo es crear una plantilla simple de dos columnas que use un [conjunto de vínculos web](../configure/manage-web-links.md) como navegación del lado izquierdo, con el contenido de páginas a la derecha. 

## <a name="step-1-create-a-web-template-and-write-the-liquid-template-code"></a>Paso 1. Crear una plantilla web y escribir el código de plantilla de Liquid

Primero, crearemos nuestra plantilla web y escribiremos el código de plantilla de Liquid. Es probable que reutilicemos algunos elementos comunes de esta plantilla en plantillas futuras. De esta manera, crearemos una plantilla base común que ampliaremos con nuestra plantilla específica. Nuestra plantilla base proporcionará vínculos de ruta de navegación y nuestro título/encabezado de página, así como el diseño de una columna:

> [!div class=mx-imgBorder]
![Diseño de una columna de plantilla web](../media/web-template-two-column-layout.png "Diseño de una columna de plantilla web")

> [!TIP]
> Lea sobre herencia de plantilla con las etiquetas block y extends: [Etiquetas de plantilla](template-tags.md#extends)

### <a name="two-column-layout-web-template"></a>Diseño de dos columnas (plantilla web)

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

## <a name="step-2-create-a-new-web-template-that-extends-our-base-layout-template"></a>Paso 2: Crear una nueva plantilla web que amplíe nuestra plantilla de diseño base

Utilice el conjunto de vínculos web de navegación asociado con la página actual para nuestros vínculos de navegación para crear una nueva plantilla web que amplía nuestra plantilla de diseño base.

> [!div class=mx-imgBorder]
![Diseño de navegación izquierda de vínculos web de plantilla web](../media/web-template-weblinks-left-navigation-layout.png "Diseño de navegación izquierda de vínculos web de plantilla web")  

> [!TIP]
> Familiarícese sobre cómo cargar conjuntos de vínculos web mediante el objeto [weblinks](liquid-objects.md#weblinks).

### <a name="weblinks-left-navigation-web-template"></a>Navegación izquierda por weblinks (plantilla web)

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

## <a name="step-3-create-a-new-page-template-based-on-the-web-template"></a>Paso 3: Crear una nueva plantilla de página web basada en la plantilla web

En este paso, crearemos una nueva plantilla de página que se base en la plantilla web que creamos en el paso anterior.

> [!div class=mx-imgBorder]
![Diseño de navegación izquierda de vínculos web de plantilla de página](../media/page-template-weblinks-left-navigation-layout.png "Diseño de navegación izquierda de vínculos web de plantilla de página")  

## <a name="step-4-create-a-web-page-to-display-content"></a>Paso 4: Crear una página web para mostrar contenido

Ahora, todo lo que tiene que hacer es crear una página web que use nuestra plantilla de páginas y tenga un conjunto de vínculos web asociado, y obtenemos el resultado.

> [!div class=mx-imgBorder]
![Página web con navegación izquierda](../media/web-page-left-navigation.png "Página web con navegación izquierda")  

### <a name="see-also"></a>Vea también

[Crear una plantilla de página personalizada para representar una fuente RSS](render-rss-custom-page-template.md)  
[Representar la lista de entidades asociada a la página actual](render-entity-list-current-page.md)  
[Represente un encabezado y una barra de navegación principal de página web](render-site-header-primary-navigation.md)  
[Represente hasta tres niveles de jerarquía de páginas mediante la navegación híbrida](hybrid-navigation-render-page-hierachy.md)  

