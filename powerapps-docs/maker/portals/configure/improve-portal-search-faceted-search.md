---
title: Usar búsqueda por facetas para mejorar la búsqueda del portal | MicrosoftDocs
description: Instrucciones para habilitar o deshabilitar la búsqueda por facetas.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6b605acf1d11ecbc98760810f390f63c9a27a0a6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761108"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>Usar búsqueda por facetas para mejorar la búsqueda del portal

Puede realizar búsquedas en el contenido del portal mediante los filtros basados en características del contenido. Los filtros implementados por la búsqueda del portal por facetas permiten a los clientes buscar el contenido deseado más rápidamente que una búsqueda tradicional.

## <a name="enable-or-disable-faceted-search"></a>Habilitación o deshabilitación de la búsqueda por facetas

La búsqueda por facetas predefinida está habilitada en los portales. Para controlarla o habilitarla, siga estos pasos:

1. Abra la [aplicación Administración del portal](configure-portal.md) y vaya a **Portales** &gt; **Sitio web** &gt; **Configuración del sitio**.
2. Seleccione el valor de sitio **Search/FacetedView**. 
3. Cambie el **Valor** a **True** para habilitar o **False** para deshabilitar la búsqueda por faceta.

Para deshabilitar un solo elemento de la vista por faceta:

1. Abra la aplicación [Administración del portal](configure-portal.md) y vaya a **Portales** &gt; **Plantillas web**.
2. Seleccione la vista que desea deshabilitar (es decir, Administración del conocimiento – Artículos con la clasificación más alta)
3. Seleccione **Desactivar** en la parte superior de la página.

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>Agrupe las entidades como parte de un tipo de registro para la vista por faceta

La configuración del sitio **Buscar/RecordTypeFacetsEntities** le permite agrupar entidades similares para que los usuarios tengan formas lógicas de filtrar los resultados de la búsqueda. Por ejemplo, en lugar de tener opciones independientes para foros, mensajes de foro e hilos del foro, estas entidades se agrupan con el tipo de registro Foros.

Vaya a **Portales** &gt; **Páginas web** &gt; **Configuración del sitio** y abra la configuración del sitio **Search/RecordTypeFacetsEntities**. 

Tenga en cuenta que las distintas entidades van precedidas de la palabra **Foros:**. Esto es porque el primer valor es el nombre con el que se agrupan. Esta palabra se traducirá en función del idioma que se use en el portal.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>Usar búsqueda por facetas para mejorar los resultados de búsqueda de conocimientos.

La búsqueda por facetas permite a los portales tener filtros de búsqueda en el lateral izquierdo permitiéndole elegir entre elementos como foros, blogs y artículos de conocimientos. Se agregan más filtros para tipos de búsqueda específicos. Por ejemplo, los artículos de conocimientos se pueden filtrar por Tipo de registro, Fecha de modificación, Valoración y Productos para ayudar a los clientes a encontrar el contenido que necesitan. El lado derecho también tiene un cuadro desplegable que ordena los resultados en función de la opción del cliente de Relevancia o Número de visualizaciones (algo específico de los artículos de conocimientos). A continuación se proporciona una captura de pantalla con un ejemplo de algunos de los filtros disponibles.

![Usar filtros para mejorar resultados de la búsqueda](../media/faceted-search-filter.png "Usar filtros para mejorar resultados de la búsqueda")
