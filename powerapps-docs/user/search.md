---
title: Opciones de búsqueda de Common Data Service | Microsoft Docs
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
ms.locfileid: "76828601"
---
# <a name="compare-search-options-in-common-data-service"></a>Comparación de las opciones de búsqueda de Common Data Service

Hay tres formas de buscar registros en Common Data Service:

-   Búsqueda por relevancia   
  
-   Búsqueda rápida (una sola o varias entidades)  

-   Búsqueda avanzada

> [!NOTE]
> La búsqueda rápida de varias entidades también se denomina búsqueda categorizada. 
  
En la tabla siguiente se ofrece una breve comparación de las tres opciones.

|Funcionalidad|[Búsqueda por relevancia](relevance-search.md)|[Búsqueda rápida](quick-find.md)|[Búsqueda avanzada](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|¿Habilitada de forma predeterminada?|No. Un administrador debe habilitarla manualmente.|Sí|Sí|  
|Ámbito de búsqueda de una sola entidad|No disponible en una cuadrícula de entidad. Puede filtrar los resultados de búsqueda por una entidad en la página de resultados.|Disponible en una cuadrícula de entidad.|Disponible en una cuadrícula de entidad.|  
|Ámbito de búsqueda de varias entidades|No hay ningún límite máximo en cuanto al número de entidades en que se puede buscar. **Nota**:  Aunque no hay límite máximo en cuanto al número de entidades en que se puede buscar, el filtro Tipo de registro solo muestra datos de diez entidades.|Busca hasta en diez entidades, agrupadas por una entidad.|Búsqueda de varias entidades no disponible.|  
|Comportamiento de búsqueda|Busca coincidencias con cualquier palabra del término de búsqueda en cualquier campo de la entidad.|Busca coincidencias con todas las palabras del término de búsqueda en un campo de una entidad, aunque las palabras se pueden comparar en cualquier orden en el campo.|Generador de consultas en el que se pueden definir criterios de búsqueda para el tipo de registro seleccionado. También se puede usar para preparar datos para exportar a Office Excel, de modo que se puedan analizar, resumir o agregar, o para crear tablas dinámicas para ver los datos desde distintas perspectivas.|  
|Campos que permiten búsquedas|Campos de texto como Una línea de texto, Varias líneas de texto, Búsquedas y Conjuntos de opciones. No admite la búsqueda en campos con tipos de datos numéricos o de fecha.|Todos los campos que permiten búsquedas.|Todos los campos que permiten búsquedas.|  
|Resultados de la búsqueda|Devuelve los resultados de búsqueda en orden de relevancia, en una sola lista.|En el caso de una sola entidad, devuelve los resultados de búsqueda en una cuadrícula de entidad. En el caso de varias entidades, devuelve los resultados de búsqueda agrupados por categorías, como cuentas, contactos o clientes potenciales.|Devuelve los resultados de búsqueda del tipo de registro seleccionado con las columnas especificadas, por el criterio de ordenación configurado.|
|Caracteres comodín (*)|Carácter comodín final admitido para la finalización de palabras.|Carácter comodín inicial admitido. Carácter comodín final agregado de forma predeterminada.|No compatible.|  
