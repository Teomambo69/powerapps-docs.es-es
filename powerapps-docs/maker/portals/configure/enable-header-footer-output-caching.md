---
title: Habilitar el almacenamiento en caché de resultados del encabezado y el pie de página en un portal | MicrosoftDocs
description: Instrucciones para habilitar el almacenamiento en caché de resultados del encabezado y el pie de página en un portal de usuarios existentes.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e7a112c722e284f9060696d0fac5a3389b47b0d3
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977113"
---
# <a name="enable-header-and-footer-output-caching-on-a-portal"></a>Habilitar el almacenamiento en caché de resultados del encabezado y el pie de página en un portal

Para mejorar el rendimiento de procesamiento con plantillas web de encabezado y el pie de página en un portal, habilite el almacenamiento en caché de los resultados de encabezado y pie de página. Se analizan y representan las plantillas web de encabezado y el pie de página cada vez que una página se carga. El almacenando en memoria caché del encabezado y el pie de página reduce significativamente el tiempo de procesamiento de la página.

Para un nuevo usuario, el almacenamiento de resultados en caché está habilitado de forma predeterminada. Los siguientes valores del sitio están disponibles y fijados en verdadero de forma predeterminada para admitir esta funcionalidad:
- Header/OutputCache/Enabled: Establezca el valor en verdadero para habilitar el almacenamiento de resultados en caché para el encabezado.
- Footer/OutputCache/Enabled: Establezca el valor en verdadero para habilitar el almacenamiento de resultados en caché para el pie de página.

En un usuario que actualizó a una nueva versión de los portales, el almacenamiento de resultados en caché está deshabilitado de manera predeterminada&mdash;es decir, las plantillas web de encabezado y el pie de página se analizan y representan en cada carga de la página. Para habilitar almacenamiento de resultados en caché, debe actualizar las plantillas web de encabezado, pie de página y menú desplegable de idiomas y crear los valores necesarios del sitio.

> [!Note]
> Si habilita almacenamiento de resultados en caché solo creando la configuración del sitio, las partes del encabezado y el pie de página no se generarán correctamente y se mostrarán mensajes de error.

### <a name="enable-header-and-footer-output-caching-for-an-existing-user"></a>Habilitar el almacenamiento de resultados en caché de encabezado y pie de página para un usuario existente

**Paso 1: Actualizar la plantilla web de encabezado**

1. Abra la aplicación [Administración del portal](configure-portal.md).
2. Vaya a **Portales** > **Plantillas web**.
3. Abra la plantilla web de encabezado.
4. En el campo **Origen**, haga lo siguiente:
    - Busque el siguiente código y actualícelo:
    
        **Código existente**

        ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/Account/Login/LogOff?returnUrl={{ request.raw_url_encode | escape }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}/SignIn?returnUrl={{ request.raw_url_encode }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
        
        **Código actualizado**

         ```
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_out_url_substitution }} title={{ snippets[links/logout] | default:resx[Sign_Out] | escape }}>
            {{ snippets[links/logout] | default:resx[Sign_Out] | escape }}
            </a>
        </li>
        </ul>
        </li>
        {% else %}
        <li>
            <a href={% if homeurl%}/{{ homeurl }}{% endif %}{{ website.sign_in_url_substitution }}>
            {{ snippets[links/login] | default:resx[Sign_In] }}
            </a>
        </li>
        ```
    - Busque el siguiente código y actualícelo:

        **Código existente**
        ```
        {% assign current_page = page.adx_partialurl %}
        {% assign sr_page = sitemarkers[Search].url | remove: '/' %}
        {% assign forum_page = sitemarkers[Forums].url | remove: '/' %}
        {% if current_page == sr_page or current_page == forum_page %}
          <section class=page_section section-landing-{{ current_page }} color-inverse>
            <div class=container>
              <div class=row >
                <div class=col-md-12 text-center>
                  {% if current_page == sr_page %}
                    <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                    {% include 'Search' %}
                  {% endif %}
                </div>
              </div>
            </div>
          </section>
        {% endif %}
        ```

        **Código actualizado**

        ```
        {% substitution %}
          {% assign current_page = page.id %}
          {% assign sr_page = sitemarkers[Search].id %}
          {% assign forum_page = sitemarkers[Forums].id %}
          {% if current_page == sr_page or current_page == forum_page %}
            {% assign section_class = section-landing-search %}
            {% if current_page == forum_page %}
              {% assign section_class = section-landing-forums %}
            {% endif %}
           <section class=page_section section-landing-{{ current_page }} {{ section_class | h }} color-inverse>
              <div class=container>
                <div class=row >
                  <div class=col-md-12 text-center>
                    {% if current_page == sr_page %}
                      <h1 class=section-landing-heading>{% editable snippets 'Search/Title' default: resx['Discover_Contoso'] %}</h1>
                      {% include 'Search' %}
                    {% endif %}
                  </div>
                </div>
              </div>
            </section>
          {% endif %}
        {% endsubstitution %}
        ```

5. Guarde la plantilla web.

**Paso 2: Actualizar la plantilla web de pie de página**

1. Abra la aplicación [Administración del portal](configure-portal.md).
2. Vaya a **Portales** > **Plantillas web**.
3. Abra la plantilla web de pie de página.
4. En el campo **Origen** , busque el siguiente código y actualícelo:
    
    **Código existente**
    
    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %} hidden-print>
    ```

    **Código actualizado**

    ```
    <section id=gethelp class=page_section section-diagonal-right color-inverse {% substitution %}{% if page %}{% unless page.parent %}home-section{% endunless %}{% endif %}{% endsubstitution %} hidden-print>
    ```

5. Guarde la plantilla web.

**Paso 3: Actualizar la plantilla web de menú desplegable de idiomas**

1. Abra la aplicación [Administración del portal](configure-portal.md).
2. Vaya a **Portales** > **Plantillas web**.
3. Abra la plantilla web de menú desplegable de idiomas.
4. En el campo **Origen** , busque el siguiente código y actualícelo:
    
    **Código existente**

    ```
    <a href=/{{ language.url }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

    **Código actualizado**

    ```
    <a href=/{{ language.url_substitution }} title={{ language.name }} data-code={{ language.code }}>{{ language.name }}</a>
    ```

5. Guarde la plantilla web.

**Paso 4: Crear configuraciones de sitio**

Cree la siguiente configuración del sitio:

|Nombre|Valor|
|----|-----|
|Header/OutputCache/Enabled|VERDADERO|
|Footer/OutputCache/Enabled|VERDADERO|
|||
