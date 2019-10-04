---
title: Opciones de buscar y Find en Common Data Service | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/02/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c7192b98d3f97a4aba57f58c52b02245cb71b155
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950896"
---
# <a name="compare-search-and-find-options-in-common-data-service"></a>Comparar las opciones de búsqueda y búsqueda en Common Data Service

Hay cuatro maneras de buscar datos en Common Data Service:

-   Búsqueda por relevancia  
  
-   Búsqueda rápida de texto completo (de una o varias entidades)  
  
-   Búsqueda rápida (de una o varias entidades)  

-   Búsqueda avanzada

> [!NOTE]
> La búsqueda rápida en varias entidades también se denomina búsqueda por categorías. 
  
En la tabla siguiente se proporciona una breve comparación de las cuatro opciones disponibles.

|Functional|[Búsqueda de relevancia](search-records.md#relevance-search)|[Búsqueda rápida de texto completo](search-records.md#start-a-search)|[Búsqueda rápida](search-records.md#start-a-search)|[Búsqueda avanzada](create-edit-or-save-advanced-find-search.md)|  
|-------------------|----------------------|---------------------------|----------------|-------------------|  
|¿Habilitado de forma predeterminada?|No. Un administrador debe habilitarlo manualmente.|No. Un administrador debe habilitarlo manualmente.|Sí|Sí|  
|Ámbito de búsqueda de una sola entidad|No está disponible en una cuadrícula de entidades. Puede filtrar los resultados de la búsqueda por una entidad en la página de resultados.|Disponible en una cuadrícula de entidades.|Disponible en una cuadrícula de entidades.|Disponible en una cuadrícula de entidades.|  
|Ámbito de búsqueda de varias entidades|No hay ningún límite máximo en el número de entidades que se pueden buscar. **Nota**:  Aunque no hay ningún límite máximo en el número de entidades que se pueden buscar, el filtro de tipo de registro solo muestra datos de 10 entidades.|Busca hasta 10 entidades, agrupadas por una entidad.|Busca hasta 10 entidades, agrupadas por una entidad.|Búsqueda de varias entidades no disponible.|  
|Comportamiento de búsqueda|Busca coincidencias con cualquier palabra del término de búsqueda en cualquier campo de la entidad.|Busca coincidencias en todas las palabras del término de búsqueda en un campo de una entidad. sin embargo, las palabras se pueden comparar en cualquier orden del campo.|Busca coincidencias como en una consulta SQL con cláusulas "like". Tiene que usar los caracteres comodín en el término de búsqueda para buscar dentro de una cadena. Todas las coincidencias deben coincidir exactamente con el término de búsqueda.|Generador de consultas en el que puede definir criterios de búsqueda para el tipo de registro seleccionado. También se puede usar para preparar los datos para la exportación a Office Excel, de modo que pueda analizar, resumir o agregar datos, o crear tablas dinámicas para ver los datos desde distintas perspectivas.|  
|Campos de búsqueda|Campos de texto como una sola línea de texto, varias líneas de texto, búsquedas y conjuntos de opciones. No admite la búsqueda en campos de tipos de datos numéricos o de fecha.|Todos los campos de búsqueda.|Todos los campos de búsqueda.|Todos los campos de búsqueda.|  
|Resultados de la búsqueda|Devuelve los resultados de la búsqueda en orden de relevancia, en una sola lista.|En el caso de una sola entidad, devuelve los resultados de la búsqueda en una cuadrícula de entidades. En el caso de varias entidades, devuelve los resultados de la búsqueda agrupados por categorías, como cuentas, contactos o clientes potenciales.|En el caso de una sola entidad, devuelve los resultados de la búsqueda en una cuadrícula de entidades. En el caso de varias entidades, devuelve los resultados de la búsqueda agrupados por categorías, como cuentas, contactos o clientes potenciales.|Devuelve los resultados de la búsqueda del tipo de registro seleccionado con las columnas especificadas, en el criterio de ordenación que ha configurado.|
|Caracteres comodín (*)|Carácter comodín final admitido para la finalización de palabras.|Se admite el carácter comodín inicial. Carácter comodín final agregado de forma predeterminada.|Se admite el carácter comodín inicial. Carácter comodín final agregado de forma predeterminada.|No compatible.|  
