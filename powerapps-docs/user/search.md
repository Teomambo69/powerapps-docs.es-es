---
title: Opciones de búsqueda en Common Data Service | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/27/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 440241571f716fa1931b5c11935c70de5c85e7ee
ms.sourcegitcommit: 5bfd0448f1d5ca3d938e3bd928d1dd3d4042afff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2020
ms.locfileid: "3303033"
---
# <a name="compare-search-options-in-common-data-service"></a>Comparar opciones de búsqueda en Common Data Service

Hay tres formas para buscar registros en Common Data Service:

-   Búsqueda por relevancia   
  
-   Búsqueda rápida (una sola o varias entidades)  

-   Búsqueda avanzada

> [!NOTE]
> La búsqueda rápida de varias entidades también se denomina búsqueda categorizada. 
  
En la tabla siguiente se ofrece una breve comparación de las tres opciones.

|Funcionalidad|[Búsqueda por relevancia](relevance-search.md)|[Búsqueda rápida](quick-find.md)|[Búsqueda avanzada](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|¿Habilitada de forma predeterminada?|Núm. Un administrador debe habilitarla manualmente.|Sí|Sí|  
|Ámbito de búsqueda de una sola entidad|No disponible en una cuadrícula de entidades. Puede filtrar los resultados de la búsqueda por entidad en la página de resultados.|Disponible en una cuadrícula de entidades.|Disponible en una cuadrícula de entidades.|  
|Ámbito de búsqueda en varias entidades|No hay límite máximo en el número de entidades que puede buscar. **Nota:** Aunque no hay ningún límite máximo en el número de entidades que puede buscar, el filtro de tipo de registro muestra datos solo para 10 entidades.|Busca hasta en diez entidades, agrupadas por una entidad.|Búsqueda de varias entidades no disponible.|  
|Comportamiento de búsqueda|Busca coincidencias con cualquier palabra en el término de búsqueda en cualquier campo de la entidad.|Busca coincidencias con todas las palabras del término de búsqueda en un campo de una entidad, aunque las palabras se pueden comparar en cualquier orden en el campo.|Generador de consultas en el que se pueden definir criterios de búsqueda para el tipo de registro seleccionado. Se puede usar para preparar los datos para la exportación a Office Excel, por lo que puede analizar, resumir o agregar datos, o crear PivotTables para ver sus datos desde diferentes perspectivas.|  
|Campos de búsqueda|Campos de texto como Línea de texto única, Varias líneas de texto, Consultas y Conjuntos de opciones. No admite la búsqueda en campos con tipos de datos numéricos o de fecha.|Todos los campos que permiten búsquedas.|Todos los campos que permiten búsquedas.|  
|Resultado de la búsqueda|Devuelve los resultados de búsqueda en orden de relevancia, en una lista única.|Para una sola entidad, devuelve los resultados de la búsqueda en una cuadrícula de entidades. Para varias entidades, devuelve resultados de la búsqueda agrupados por categorías, tales como cuentas, contactos o clientes potenciales.|Devuelve resultados de búsqueda del tipo de registro seleccionado con las columnas que ha especificado con el criterio de ordenación configurado.|
|Comodines (*)|Comodín final admitido para finalización de la palabra.|Carácter comodín inicial admitido. Carácter comodín final agregado de forma predeterminada.|No compatible.|  
