---
title: Novedades de PowerApps | Microsoft Docs
description: Actualizaciones de PowerApps, organizadas por fecha de lanzamiento
services: powerapps
suite: powerapps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/09/2018
ms.author: sharik
ms.openlocfilehash: 92438c37b870ace2ed5b2ec086cf6c5fb1548fdc
ms.sourcegitcommit: d7ed5144f96d1ecc17084c30ed0e2ba3c6b03c26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="whats-new-in-powerapps"></a>Novedades de PowerApps
Para más información sobre las limitaciones conocidas, consulte [Problemas y resoluciones habituales](common-issues-and-resolutions.md).


> [!NOTE]
> Las versiones se implementan durante varios días. Es posible que las funcionalidades nuevas o actualizadas no se muestren inmediatamente.

## <a name="announcing-the-business-applications-spring-18-release-notes"></a>Anuncio de la notas de la versión de aplicaciones empresariales de la primavera de 2018

Detecte las actualizaciones más recientes para nuestras aplicaciones empresariales, así como infinidad de nuevas funcionalidades para que compile sus propias aplicaciones y extensiones sobre nuestra plataforma. [Descargue el PDF de las notas de la versión de la primavera de 2018](https://aka.ms/businessappsreleasenotes), que cubre Dynamics 365, PowerApps, Microsoft Flow y Power BI.

**Próximamente:** el PDF de las notas de la versión se seguirá actualizando como características de envío y también se pondrá a disposición de los usuarios en una página web.

## <a name="apr-9"></a>9 de abril
* Controles para cortar (Ctrl+X), copiar (Ctrl+C), y pegar (Ctrl+V), incluidos los estilos de los controles, fórmulas y propiedades, entre aplicaciones en un explorador web.

## <a name="mar-21"></a>21 de marzo
1. Cree [aplicaciones controladas por modelos](../model-driven-apps/model-driven-app-overview.md), que empiezan con el modelo de datos y se compilan a partir de la forma de los datos y procesos de negocio fundamentales en Common Data Service for Apps para crear formularios, vistas y otros componentes. Las aplicaciones controladas por modelos generan automáticamente una interfaz de usuario excelente con capacidad de respuesta en todos los dispositivos.
2. [Cree una base de datos](../../administrator/create-database.md) en la versión más reciente de CDS for Apps en un entorno.
3. CDS for Apps ahora incluye lo siguiente:
    - **Tipos de datos adicionales** que admiten definiciones de entidades más complejas y proporcionan experiencias más enriquecidas. (Se aplica a las aplicaciones de lienzo y controladas por modelos).
    - [Cree y personalice entidades](../common-data-service/data-platform-create-entity.md) en CDS for Apps directamente desde el sitio de PowerApps. La **experiencia actualizada** incluye rendimiento mejorado, una interfaz de usuario más fácil de usar y funciones útiles como la creación en línea de conjuntos de opciones. (Se aplica a las aplicaciones de lienzo y controladas por modelos).
    - Cree **reglas de negocio del lado servidor** para validar los datos introducidos en CDS for Apps. (Se aplica a las aplicaciones de lienzo y controladas por modelos).
    - Cree **campos calculados y consolidados** en entidades de CDS for Apps directamente desde el sitio de PowerApps. (Se aplica a las aplicaciones de lienzo y controladas por modelos).  
    - Los desarrolladores pueden usar el **Kit de desarrollo de software** (SDK) de CDS for Apps para crear personalizaciones basadas en código para CDS for Apps.
    - Los usuarios avanzados pueden tener acceso a los datos almacenados en CDS for Apps a través de una nueva **API web de OData**.
    - [Importe datos](../common-data-service/data-platform-cds-newentity-pq.md) a CDS for Apps con **Power Query**. Use Power Query en la Web para importar datos directamente a CDS for Apps desde varios orígenes.

## <a name="mar-5"></a>5 de marzo
1. Se han agregado (y eliminado) [datos adjuntos](controls/control-attachments.md) a listas de SharePoint.
2. Se abren archivos [PDF](controls/control-pdf-viewer.md) externos en un explorador web. (característica experimental)

## <a name="feb-12"></a>12 de febrero
* El control de volumen para la reproducción de [vídeo](controls/control-audio-video.md) y [audio](controls/control-audio-video.md) incrustados ahora está en línea. Para silenciar la reproducción, en lugar de hacer clic o pulsar en un botón, los usuarios ahora deben usar el control de volumen para reducir el volumen.

## <a name="feb-7"></a>7 de febrero
1. Se han eliminado las propiedades Zoom, Brillo y Contraste de los controles de [Cámara](controls/control-camera.md) y [Escáner de código de barras](controls/control-barcodescanner.md).
2. Se ha corregido el problema en el que los botones Borrar de los controles de [Entrada de texto](controls/control-text-input.md) limitaban el espacio asignado para que el usuario escriba texto. Como resultado de esta corrección, la propiedad [Borrar](controls/control-text-input.md#additional-properties) de un control de Entrada de texto solo se admite en los exploradores web Microsoft Edge (última versión) e Internet Explorer 11.
3. Se han agregado mejoras de accesibilidad en los controles [multimedia](add-images-pictures-audio-video.md).

## <a name="jan-31"></a>31 de enero
1. Se han agregado subtítulos a los controles de [Vídeo](controls/control-audio-video.md).
2. Se ha mejorado el control de los errores en los controles del [Visor de PDF](controls/control-pdf-viewer.md).

## <a name="jan-18"></a>18 de enero
1. PowerApps para iOS y Android ahora admiten la integración con Microsoft Authenticator.
2. A [cuadro combinado](controls/control-combo-box.md) reemplaza el [control de búsqueda de SharePoint](sharepoint-lookup-fields.md) en los formularios y se selecciona una nueva plantilla de [tarjeta de datos](working-with-cards.md) para los campos de búsqueda de selección única de manera predeterminada en PowerApps Studio.
3. En los [cuadros combinados](controls/control-combo-box.md), todos los elementos se ven en lista larga con modo de lectura mejorado.
4. Control del tamaño del límite de registros locales que se almacenan, hasta un máximo de 2000 registros en las [consultas no delegables](delegation-overview.md#non-delegable-limits). (característica experimental)

## <a name="jan-5"></a>5 de enero
* Actúe en los datos directamente desde un informe o panel de Power BI mediante la integración de un [objeto visual personalizado de PowerApps (versión preliminar)](https://powerapps.microsoft.com/blog/powerbi-powerapps-visual/), que extrae los datos contextuales del informe de Power BI.

## <a name="dec-8"></a>8 de diciembre
1. [Plantillas de condición](working-with-rules.md) para que las reglas deduzcan las propiedades comunes de un control (como **Texto** o **Valor**).
2. Deja de mostrarse el cuadro de dialogo de confirmación [**Definición de acciones**](working-with-rules.md) al definir acciones de regla.

## <a name="nov-13"></a>13 de noviembre
1. Selección de varios valores para el mismo campo en las listas de SharePoint.
2. [Visualización y descarga de datos adjuntos ](controls/control-attachments.md) en listas de SharePoint.
3. [Personalización de los formularios de las listas de SharePoint](customize-list-form.md) mediante PowerApps.

## <a name="nov-10"></a>10 de noviembre
* [Cambiar el nombre de las reglas](working-with-rules.md) en una aplicación y mostrar las reglas cuando el control seleccionado está en la condición de la regla.
