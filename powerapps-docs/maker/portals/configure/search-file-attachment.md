---
title: Buscar contenido de archivo adjunto en un portal | MicrosoftDocs
description: Aprenda cómo configurar el portal para buscar contenido de archivo adjunto en un portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 99df8fa13dd066f8e5b2efa134529ac24a8facec
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980105"
---
# <a name="search-within-file-attachment-content"></a>Buscar contenido de archivo adjunto

Puede usar las notas adjuntas para incluir archivos descargables en artículos de Knowledge Base. También puede usar los archivos web para crear una página Preguntas más frecuentes con el contenido descargable.

Puede configurar el portal para permitir que los usuarios del mismo busquen en el contenido de los datos adjuntos de artículos de Knowledge Base. Esto ayuda a los usuarios a encontrar la información que están buscando.

En artículos de Knowledge Base, se indexa cualquier nota adjunta con el prefijo definido. En archivos web, se indexan las últimos notas adjuntas.

Para indexar los datos adjuntos, debe crear las siguientes configuraciones del sitio y establecer su valor en **Verdadero**:

|Configuración del sitio|Descripción|
|------------|-----------|
|Search/IndexNotesAttachments|Indica si se debe indexar el contenido de los datos adjuntos de las notas en artículos de Knowledge Base y archivos web. De forma predeterminada, se establece en **Falso**.|
|KnowledgeManagement/DisplayNotes|Indica si indexar los datos adjuntos de los artículos de Knowledge Base. De forma predeterminada, se establece en **Falso**.|
|||

> [!NOTE]
> Solo los archivos que se adjuntan a los artículos de conocimientos pueden ser buscados. Los archivos que se adjuntan a los archivos web no se pueden buscar.

Cuando busca un período, los resultados de la búsqueda también incluyen los datos adjuntos. Si el término de búsqueda coincide con los datos adjuntos de las notas, también se proporciona el vínculo al artículo correspondiente de Knowledge Base. Para ver los datos adjuntos descargables, seleccione **Descargas** en **Tipo de registro** en el panel izquierdo. Para modificar la etiqueta **Descargas**, edite el fragmento de código de contenido Search/Facet/Downloads. De manera predeterminada, el valor se establece como **Descargas**.

![Descargar datos adjuntos](../media/search-attachment-content.png "Descargar datos adjuntos") 

> [!NOTE]
> - Para usar esta funcionalidad, debe [habilitar la búsqueda por relevancia](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization). Más información: [Búsqueda por relevancia](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>Actualizar configuraciones del portal

Si ya tiene un portal antes de abril de 2018 y ha actualizado el portal a la versión más reciente, debe usar las siguientes configuraciones para que tengan la misma experiencia de usuario que una nueva instalación de portal.

**Fragmentos de contenido**

Para modificar la etiqueta que se muestra en los resultados de la búsqueda para descargas de anotaciones y archivos web, cree un fragmento de código del contenido Search/Facet/Downloads y, a continuación, establezca su valor según corresponda. El valor predeterminado es **Descargas**.

**Archivos web**

Ahora se puede indexar el contenido de los datos adjuntos del archivo asociado a los archivos web. Puede actualizar los archivos web existentes para los archivos CSS y de imagen (por ejemplo, bootstrap.min.css, theme.css y homehero.jpg) que se excluirán de la búsqueda. 

1. Abra la [aplicación Administración del portal](configure-portal.md) y vaya a **Portales** > **Archivos web**.
2. Abra el archivo que se excluirá de la búsqueda.
3. En **Varios**, seleccione **Sí** en el campo **Excluir de la búsqueda**.

**Plantillas web**

La plantilla web Plantilla de búsqueda por facetas - Resultados se revisa para mostrar los archivos asociados a los artículos de Knowledge Base como los elementos principales del resultado de búsqueda con un vínculo de artículo relacionado. Debe actualizar la plantilla web Plantilla de búsqueda por facetas - Resultados para el siguiente origen:

```
{% assign openTag = '{{' %}
{% assign closingTag = '}}' %}
{%raw%}
  <script id=search-view-results type=text/x-handlebars-template>
   {{#if items}}
    <div class=page-header>
     <h3>{%endraw%}{{openTag}} stringFormat {{ resx.Search_Results_Format_String }} firstResultNumber lastResultNumber itemCount {{closingTag}}{%raw%}
      <em class=querytext>{{{query}}}</em>
      {{#if isResetVisible}}
       <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
      {{/if}}
     </h3>
    </div>
   <ul>
    {{#each items}}
     <li>
      <h3><a title={{title}} href={{url}}>{{#if parent}}<span class=glyphicon glyphicon-file pull-left text-muted aria-hidden=true></span>{{/if}}{{title}}</a></h3>
      <p class=fragment>{{{fragment}}}</p>
      {{#if parent}}
       <p class=small related-article>{%endraw%}{{ resx.Related_Article }}{%raw%}: <a title={{parent.title}} href={{parent.absoluteUrl}}>{{parent.title}}</a></p>
      {{/if}}
      <ul class=note-group small list-unstyled>
       {{#if relatedNotes}}
        {{#each relatedNotes}}
         <li class=note-item>
         {{#if isImage}}
          <a target=_blank title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{else}}
          <a title={{title}} href={{absoluteUrl}}><span class=glyphicon glyphicon-file aria-hidden=true></span>&nbsp;{{title}}</a>
         {{/if}}
         <p class=fragment text-muted>{{{fragment}}}</p>
         </li>
        {{/each}}
        {{/if}}
      </ul>
     </li>
    {{/each}}
   </ul>
   {{else}}
    <h2>{%endraw%}{{ resx.Search_No_Results_Found }}{%raw%}<em class=querytext>{{{query}}}</em>
     {{#if isResetVisible}}
      <a class="btn btn-default btn-sm facet-clear-all" role="button" title="{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}" tabIndex="0">{%endraw%}{{ snippets['Search/Facet/ClearConstraints'] | default: res['Search_Filter_Clear_All'] }}{%raw%}</a>
     {{/if}}
    </h2>
   {{/if}}
  </script>
{%endraw%}
```

**Configuraciones de sitios**

Debe agregar el valor `\_logicalname:annotation~0.9^0.25` para la configuración Search/Query. Una vez agregado, el valor debe ser el siguiente:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

Para configurar las facetas para anotaciones de grupo asociadas a los artículos de Knowledge Base y los archivos web en una única faceta, edite el nombre de la configuración del sitio Search/RecordTypeFacetsEntities y anexar `;Downloads:annotation,adx_webfile` a su valor.

Para permitir que los datos adjuntos asociados a los artículos de conocimientos aparezcan en el portal y los resultados de la búsqueda, edite la configuración del sitio **KnowledgeManagement/DisplayNotes** y establezca su valor en **Verdadero**. La configuración del sitio **KnowledgeManagement/NotesFilter** contiene un valor de prefijo que no debe prefijarse al campo de texto de notas en notas; en el portal solo aparecerá las notas con el valor de prefijo especificado. De forma predeterminada, el valor es \*WEB\*, pero puede cambiarlo a través de la configuración del sitio.

Para habilitar la indexación de los datos adjuntos de los archivos asociados a las notas, cree la configuración del sitio **Search/IndexNotesAttachments** y establezca su valor en **Verdadero**.
