---
title: Buscar en el contenido de los archivos adjuntos en un portal | MicrosoftDocs
description: Aprenda a configurar el portal para buscar en el contenido de los archivos adjuntos en un portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 52d7701ac84072c84886ea86969f28809d0e7960
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551655"
---
# <a name="search-within-file-attachment-content"></a>Buscar en el contenido de los archivos adjuntos

Puede usar los datos adjuntos de notas para incluir archivos descargables en los artículos de Knowledge base. También puede usar archivos Web para crear una página de preguntas más frecuentes con contenido descargable.

Puede configurar el portal para permitir que los usuarios del portal busquen en el contenido de los datos adjuntos de los artículos de Knowledge base. Esto ayuda a los usuarios a encontrar la información que están buscando.

En los artículos de Knowledge base, se indexan todos los datos adjuntos de notas con el prefijo definido. En archivos Web, se indizan los datos adjuntos más recientes de notas.

Para indizar los datos adjuntos, debe crear la siguiente configuración del sitio y establecer su valor en **true**:

|Configuración del sitio|Descripción|
|------------|-----------|
|Buscar/IndexNotesAttachments|Indica si se debe indizar el contenido de los datos adjuntos de las notas de los artículos de Knowledge base y los archivos Web. De forma predeterminada, se establece en **false**.|
|KnowledgeManagement/DisplayNotes|Indica si se van a indizar los datos adjuntos de los artículos de Knowledge base. De forma predeterminada, se establece en **false**.|
|||

> [!NOTE]
> Solo se pueden buscar en los archivos adjuntos a artículos de conocimientos. No se pueden realizar búsquedas en los archivos adjuntos a archivos Web.

Al buscar un término, los resultados de la búsqueda también incluyen datos adjuntos. Si el término de búsqueda coincide con los datos adjuntos de notas, también se proporciona el vínculo al artículo de Knowledge base correspondiente. Para ver los datos adjuntos descargables, seleccione **descargas** en **tipo de registro** en el panel izquierdo. Para modificar la etiqueta **downloads** , edite el fragmento de contenido Search/Face/downloads. De forma predeterminada, el valor se establece en **downloads**.

![Descargar datos adjuntos](../media/search-attachment-content.png "Descargar datos adjuntos") 

> [!NOTE]
> - Para usar esta funcionalidad, debe [Habilitar la búsqueda de relevancia](https://docs.microsoft.com/dynamics365/customer-engagement/admin/configure-relevance-search-organization). Más información: [búsqueda de relevancia](https://docs.microsoft.com/dynamics365/customer-engagement/basics/relevance-search-results)
 
## <a name="update-portal-configurations"></a>Actualizar configuraciones del portal

Si ya tiene un portal antes del 2018 de abril y ha actualizado el portal a la versión más reciente, debe usar las siguientes configuraciones para tener la misma experiencia de usuario que una nueva instalación del portal.

**Fragmentos de código de contenido**

Para modificar la etiqueta que se muestra en los resultados de la búsqueda para las descargas de archivos Web y de anotaciones, cree una búsqueda, faceta y descargas de fragmentos de contenido y, a continuación, establezca su valor en requerido. El valor predeterminado es **downloads**.

**Archivos Web**

Ahora se puede indizar el contenido de los datos adjuntos de archivos asociados con archivos Web. Puede actualizar los archivos Web existentes para los archivos CSS y los archivos de imagen (por ejemplo, bootstrap. min. CSS, Theme. CSS y homehero. jpg) que se van a excluir de la búsqueda. 

1. Abra la [aplicación de administración del portal](configure-portal.md) y vaya a **Portals** > **archivos Web**.
2. Abra el archivo que se va a excluir de la búsqueda.
3. En **varios**, seleccione **sí** en el campo **excluir de la búsqueda** .

**Plantillas web**

La plantilla Web de plantilla de búsqueda por facetas se revisa para mostrar los archivos asociados a los artículos de Knowledge base como elementos de resultados de búsqueda principales con un vínculo de artículo relacionado. Debe actualizar la plantilla Web de la plantilla búsqueda por facetas-resultados al siguiente origen:

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

**Configuración del sitio**

Debe agregar `\_logicalname:annotation~0.9^0.25` valor a la configuración del sitio de búsqueda/consulta. Una vez agregado, el valor debe ser el siguiente:
```
+(@Query) \_title:(@Query) \_logicalname:knowledgearticle~0.9^0.3 \_logicalname:annotation~0.9^0.25 \_logicalname:adx_webpage~0.9^0.2 -\_logicalname:adx_webfile~0.9 adx_partialurl:(@Query) \_logicalname:adx_blogpost~0.9^0.1 -\_logicalname:adx_communityforumthread~0.9
```

Para configurar las facetas para agrupar anotaciones asociadas a los artículos de Knowledge base y archivos Web en una sola faceta, edite el nombre de la configuración del sitio de Search/RecordTypeFacetsEntities y anexe `;Downloads:annotation,adx_webfile` a su valor.

Para permitir que los datos adjuntos asociados con los artículos de conocimientos aparezcan en el portal y en los resultados de la búsqueda, edite la configuración del sitio **KnowledgeManagement/DisplayNotes** y establezca su valor en **true**. La configuración del sitio **KnowledgeManagement/NotesFilter** contiene un valor de prefijo que se debe anteponer al campo de texto de nota en las notas; en el portal solo aparecerán las notas con el valor de prefijo especificado. De forma predeterminada, el valor es \*\*WEB, pero puede cambiarlo a través de la configuración del sitio.

Para habilitar la indización de archivos adjuntos asociados a notas, cree la configuración del sitio de **Search/IndexNotesAttachments** y establezca su valor en **true**.
