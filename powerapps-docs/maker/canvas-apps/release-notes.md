---
title: Novedades | Microsoft Docs
description: Actualizaciones de PowerApps, organizadas por fecha de lanzamiento
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/21/2018
ms.author: anneta
ms.openlocfilehash: 55b60abd9dc07d5b6c1979190f20ef893265475f
ms.sourcegitcommit: b9fa569153924af9815db45d52c04e764ddb7fa2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094711"
---
# <a name="whats-new-in-powerapps"></a>Novedades de PowerApps
> [!IMPORTANT]
> **Anuncio de las notas de la versión**<br>
> ¿Tiene preguntas sobre las próximas funciones y las publicadas recientemente en PowerApps?<br>
[Vea las notas de la versión](https://docs.microsoft.com/business-applications-release-notes/april18/powerapps/overview). Se han capturado todos los detalles completos, de arriba abajo, que puede usar para la planificación.

Para más información sobre las limitaciones conocidas, consulte [Problemas y resoluciones habituales](common-issues-and-resolutions.md).

> [!NOTE]
> Las versiones se implementan durante varios días. Es posible que las funcionalidades nuevas o actualizadas no se muestren inmediatamente.

## <a name="may-30"></a>30 de mayo
1. [Control Editor de texto enriquecido](controls/control-richtexteditor.md) (experimental): permite a los usuarios finales dar formato al texto dentro de un área de edición WYSIWYG. 

## <a name="may-21"></a>21 de mayo
1. Se permite a los usuarios de la aplicación importar y exportar datos de archivos de Excel o CSV almacenados localmente usando las características **Obtener datos desde Excel** y **Exportar datos**, ya disponibles para entornos actualizados de Common Data Service (CDS) for Apps. 
1. Se permite a los usuarios de la aplicación [abrir entidades en Excel](../common-data-service/data-platform-excel-addin.md) para crear, actualizar y eliminar datos almacenados en CDS for Apps usando el complemento de Excel para PowerApps. 
1. Se pueden [crear y publicar informes de Power BI](../common-data-service/data-platform-powerbi-connector.md) usando Power BI Desktop conectado a CDS for Apps. 

## <a name="april-23"></a>23 de abril
* Descargue los [datos adjuntos](controls/control-attachments.md) en Internet Explorer dentro de los formularios de lista personalizada de SharePoint.

## <a name="april-9"></a>9 de abril
* Controles para cortar (Ctrl+X), copiar (Ctrl+C), y pegar (Ctrl+V), incluidos los estilos de los controles, fórmulas y propiedades, entre aplicaciones en un explorador web.

## <a name="march-21"></a>21 de marzo
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

## <a name="march-5"></a>5 de marzo
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
