---
title: Uso de la búsqueda por facetas para mejorar la búsqueda en el portal | MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552345"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>Uso de la búsqueda por facetas para mejorar la búsqueda en el portal

Se puede buscar en el contenido del portal mediante el uso de filtros basados en las características del contenido. Los filtros implementados por la búsqueda de portal faceteados permiten a los clientes encontrar el contenido que desean más rápidamente que una búsqueda tradicional.

## <a name="enable-or-disable-faceted-search"></a>Habilitar o deshabilitar la búsqueda por facetas

La búsqueda de facetas no actualizada está habilitada en los portales. Para controlarlo o habilitarlo, siga estos pasos:

1. Abra la [aplicación de administración del portal](configure-portal.md) y vaya a **portales** &gt; **sitio web** &gt; **configuración del sitio**.
2. Seleccione la configuración del sitio de **Search/FacetedView** . 
3. Cambie el **valor** a **true** para habilitar o **false** para deshabilitar la búsqueda por facetas.

Para deshabilitar una sola parte de la vista faceteada:

1. Abra la [aplicación de administración del portal](configure-portal.md) y vaya a **portales** &gt; **plantillas web**.
2. Seleccione la vista que desea deshabilitar (es decir, administración del conocimiento – artículos destacados)
3. Seleccione **desactivar** en la parte superior de la página.

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>Agrupar entidades como parte de un tipo de registro para la vista faceteada

La configuración del sitio **Search/RecordTypeFacetsEntities** permite agrupar entidades similares para que los usuarios tengan formas lógicas de filtrar los resultados de la búsqueda. Por ejemplo, en lugar de tener opciones independientes para foros, publicaciones de foros y subprocesos de foros, estas entidades se agrupan en el tipo de registro de foros.

Vaya a **portales** &gt; **sitios web** &gt; **configuración del sitio** y abra la configuración del sitio de **Search/RecordTypeFacetsEntities** . 

Tenga en cuenta que las diferentes entidades van precedidas de la palabra **forums:** . Esto se debe a que el primer valor es el nombre con el que se agrupan como. Esta palabra se traducirá en función del idioma que se usa en el portal.

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>Uso de la búsqueda por facetas para mejorar los resultados de la búsqueda de conocimiento

La búsqueda por facetas permite que los portales tengan filtros de búsqueda en el lado izquierdo, lo que le permite elegir entre elementos como foros, blogs y artículos de conocimientos. Se agregan más filtros para tipos de búsqueda específicos. Por ejemplo, los artículos de conocimientos se pueden filtrar por tipo de registro, fecha de modificación, clasificación y productos para ayudar a los clientes a encontrar el contenido que necesitan. El lado derecho también tiene un cuadro desplegable que ordena los resultados en función de la elección de la relevancia o el recuento de vistas (específico de los artículos de conocimientos). A continuación se muestra una captura de pantalla con un ejemplo de algunos de los filtros disponibles.

![Usar filtros para mejorar los resultados de la búsqueda](../media/faceted-search-filter.png "Usar filtros para mejorar los resultados de la búsqueda")
