---
title: Usar etiquetas de plantilla para un portal | MicrosoftDocs
description: Obtenga información sobre las etiquetas de plantilla disponibles en el portal.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/24/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a152fc23b71b2e564bad28a9f1717c15acfe9a60
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108825"
---
# <a name="template-tags"></a>Etiquetas de plantilla

Las etiquetas de plantilla controlan el resultado de una plantilla de varias formas, y permiten combinar varias plantillas en una sola.

## <a name="fetchxml"></a>fetchxml

Permite al usuario consultar datos de CDS y representar los resultados en una página.

> [!NOTE]
> Puede obtener más información sobre cómo consultar los datos utilizando fetchxml en [usar FetchXML para consultar datos](https://docs.microsoft.com/powerapps/developer/common-data-service/use-fetchxml-construct-query).

```
{% fetchxml resultVariable %}
<!— Fetchxml query -->
...
{% endfetchxml %}
```

### <a name="results-attribute"></a>Atributo de resultados

El atributo de resultados en la variable proporcionada (como 'resultVariable' en el ejemplo anterior) contiene los resultados de la consulta FetchXML y otros atributos.

- *Entidades*

    Este atributo contiene el resultado de la consulta fetchxml. Puede iterar el resultado y usarlo en su plantilla web.

    ```
    <table> 
    {% for entityVariable in resultVariable.results.entities %} 
    <tr> 
    <td>Attribut-1: {{ entityVariable.attribute1 }}</td> 
    <td>Attribut-2: {{ entityVariable.attribute2 }}</td> 
    </tr> 
    {% endfor %} 
    </table> 
    ```

- *EntityName*

    Obtiene el nombre lógico de la entidad.

- *ExtensionData*

    Obtiene la estructura que contiene datos adicionales.

- *MinActiveRowVersion*

    Obtiene el valor de versión de fila activa más bajo.

- *MoreRecords*

    Obtiene si hay más registros disponibles.

- *PagingCookie*

    Obtiene la información de paginación actual.

- *TotalRecordCount*

    Obtiene el número total de registros de la colección. <br/>
    ReturnTotalRecordCount era verdadero cuando se ejecutó la consulta.

- *TotalRecordCountLimitExceeded*

    Obtiene si los resultados de la consulta exceden el recuento total de registros.

### <a name="xml-attribute"></a>Atributo XML

El atributo XML en la variable proporcionada (como 'resultVariable' en el ejemplo anterior) contiene la consulta resultante que se puede usar para obtener datos de Common Data Service. Este atributo es útil para fines de depuración cuando desea comprender cómo se aplica el permiso de entidad en esta etiqueta *fetchxml*.  

## <a name="include"></a>include

Incluye el contenido de una plantilla en otra, por nombre. En los portales de Power Apps, el origen de esta otra plantilla será normalmente una [plantilla web](store-content-web-templates.md). Esto permite la reutilización de fragmentos comunes de plantilla en varios lugares.  

Cuando una plantilla se incluye en otra, la plantilla incluida tendrá acceso a las variables definidas en la plantilla primaria.

`{% include 'My Template' %}`

También es posible pasar cualquier número de parámetros con nombre a la etiqueta include. Estos a continuación se definirán como variables de la plantilla incluida.

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>block

Usado junto con extends para proporcionar herencia de plantilla. Vea extends para uso.

## <a name="extends"></a>extends

Usado junto con la etiqueta block para proporcionar herencia de plantilla. Esto permite que varias plantillas usen un diseño compartido, al tiempo que reemplazan áreas específicas del diseño primario.

En los portales de Power Apps, el nombre de la plantilla primaria suministrado a la etiqueta normalmente hará referencia al nombre de una [plantilla web](store-content-web-templates.md).  

Cuando se utiliza extends, debe ser el primer contenido de la plantilla, y solo puede ir seguido de una o más etiquetas block.

Si un bloque definido en la plantilla principal no se reemplaza, su contenido en la plantilla primaria (si lo hay) se representarán.

## <a name="comment"></a>comentario

Permite dejar código no representado dentro una plantilla de Liquid. No se representará ningún contenido dentro del bloque y no se ejecutará ningún código de Liquid dentro.

**Código**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**Salida**

`Hello. My name is Charles.`

## <a name="raw"></a>raw

Permite el resultado de código de Liquid en una página sin analizarlo ni ejecutarlo.

**Salida**

`Hello, {{ user.fullname }}. My name is Charles.`

## <a name="substitution"></a>sustitución

Cuando el usuario ha habilitado el almacenamiento en caché del encabezado y pie de página, y desea evitar el almacenamiento en caché de los resultados de cierta sección, puede usar esta etiqueta. Esta etiqueta proporciona el bloque de contenido en el encabezado o pie de página donde el resultado del bloque de contenido envuelto no se almacena en caché. Esto es útil en escenarios en los que el usuario usa un objeto que se puede actualizar con frecuencia, como solicitud, página, idioma y fecha. Por ejemplo, consulte los escenarios de actualización del código fuente de la plantilla web de encabezado y pie de página cuando [el almacenamiento en caché del encabezado y pie de página esté habilitado](../configure/enable-header-footer-output-caching.md).

### <a name="see-also"></a>Vea también

[Etiquetas del flujo de control](control-flow-tags.md)<br>
[Etiquetas de iteración](iteration-tags.md)<br>
[Etiquetas variables](variable-tags.md)<br>
[Etiquetas de entidad de Power Apps common data service](portals-entity-tags.md)
