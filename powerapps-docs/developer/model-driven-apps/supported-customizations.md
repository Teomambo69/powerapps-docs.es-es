---
title: Introducción a la personalización de aplicaciones basada en modelos mediante código | Microsoft Docs
description: 'Puede personalizar aplicaciones basadas en modelos mediante las herramientas disponibles en el portal Power Apps o las que aparecen descritas en la documentación. '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Nkrb
ms.author: nabuthuk
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7d6ae1ae1389631987eef030af698d57b2a4235e
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115648"
---
# <a name="get-started-with-model-driven-apps-customization-using-code"></a>Introducción a la personalización de aplicaciones basada en modelos mediante código

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions
Split to just include MDA issues
 -->

Puede personalizar aplicaciones basadas en modelos mediante las herramientas disponibles en el portal Power Apps o las que aparecen descritas en la documentación. Estas personalizaciones están admitidas y se pueden actualizar.

Las personalizaciones realizadas con otros métodos que no sean los que aquí se describen no están admitidas y podrían causar problemas durante la instalación de actualizaciones y mejoras aplicaciones basadas en modelos. Para obtener más información, consulte [Personalizaciones no admitidas](#unsupported-customizations) más adelante en este tema.

Se admiten los temas cubiertos en los artículos técnicos publicados en sitios de Microsoft como este, pero podrían no ser actualizables.


## <a name="customizations-using-power-apps-portal"></a>Personalizaciones utilizando el portal de Power Apps

Hay una variedad de herramientas que se incluyen con aplicaciones basadas en modelos para aplicaciones que puede utilizar para personalizarlas. Las personalizaciones realizadas con las herramientas de aplicaciones basadas en modelos son completamente compatibles y se pueden actualizar por completo.

Se pueden usar los siguientes métodos de personalización para generar personalizaciones completamente compatibles:

- Personalización en el portal de Power Apps o la solución del explorador. Para obtener más información, vea [Información general para generar aplicaciones basadas en modelos](../../maker/model-driven-apps/model-driven-app-overview.md)

- Configuración en la aplicación web. Para obtener más información, vea [Administrar aplicaciones basadas en modelos](/dynamics365/customer-engagement/admin/admin-guide).

- Reporting Services. Para obtener más información, vea [Guía de informes y análisis para aplicaciones basadas en modelos](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)

> [!NOTE]
> El comportamiento de aplicaciones basadas en modelos depende de personalizaciones aplicadas al Common Data Service asociado. Más información: [Personalizaciones compatibles para Common Data Service](../common-data-service/supported-customizations.md)
> *Compatible completamente* significa que la compatibilidad del programador puede proporcionar ayuda para personalizaciones y que la compatibilidad de aplicaciones puede ayudar a los clientes que ejecutan dichas modificaciones.


## <a name="customizations-applied-using-code"></a>Personalizaciones aplicadas con código

La documentación de este sitio para desarrolladores, artículos técnicos, código de ejemplo publicados en este sitio, y la información publicada por el equipo de soporte técnico para programadores de Common Data Service se incluyen en el área de personalización aplicada utilizando código. Las acciones y niveles específicos de compatibilidad y capacidad de actualización se describen más adelante en este tema.

### <a name="client-side-javascript"></a>JavaScript del lado del cliente

Puede usar JavaScript en aplicaciones basadas en modelos en tres áreas:

- **Controladores de eventos para script de formularios**: puede configurar controladores de eventos de formulario para invocar funciones definidas en los recursos web de JavaScript.

- **Comandos de la barra de comandos (cinta de opciones)**: puede usar los elementos de `<CustomRule>` o `<JavaScriptFunction>` para definir acciones que invoquen funciones definidas en los recursos web de JavaScript.

- **Recursos web e IFRAMEs**: puede usar los recursos web de JavaScript dentro de recursos web HTML. Los elementos IFRAMES configurados para permitir scripting entre sitios o los scripts dentro de recursos web HTML incluidos en un formulario pueden interactuar con los métodos documentados `Xrm.Page` o `Xrm.Utility` dentro del formulario mediante la referencia primaria.

Todas las interacciones con las páginas de aplicación solo se deben realizar por medio de los métodos documentados en [Referencia de API de cliente para aplicaciones basadas en modelos](clientapi/reference.md). No se admite el acceso directo al elemento de Document Object Model (DOM) de ninguna de las páginas de aplicaciones basadas en modelos. No se recomienda el uso de jQuery en los scripts y comandos de formularios. Más información: [Ejemplo de scripting del cliente en aplicaciones basadas en modelos mediante JavaScript](client-scripting.md).

Puede abrir formularios, vistas, cuadros de diálogo e informes de aplicaciones basadas en modelos con los métodos que se explican en [Apertura de formularios, vistas, cuadros de diálogo e informes con una dirección URL](open-forms-views-dialogs-reports-url.md).

### <a name="ribbon-customization"></a>Personalización de la cinta de opciones

Se admite el uso de `RibbonDiffXml` para agregar, quitar u ocultar elementos de la cinta de opciones. Se admite la reutilización de los comandos de la cinta de opciones definidos por aplicaciones basadas en modelos; sin embargo, nos reservamos el derecho de cambiar o dejar de usar los comandos disponibles. No se admite la reutilización de las funciones de JavaScript definidas dentro de los comandos de la cinta de opciones.

## <a name="unsupported-customizations"></a>Personalizaciones no admitidas

Las modificaciones en aplicaciones basadas en modelos que se realizan sin usar los métodos descritos en esta documentación o las herramientas del portal Power Apps no se admiten ni se mantienen durante la instalación de actualizaciones o mejoras de aplicaciones basadas en modelos. No se admite nada que no esté reflejado en esta documentación y en los documentos relacionados. Además, las modificaciones no admitidas podrían provocar problemas cuando se actualice a través de la instalación de revisiones, los Service Pack o mejoras de aplicaciones basadas en modelos.

La siguiente es una lista de los tipos de acciones no admitidas por los que recibimos preguntas frecuentes: 

- La reutilización de cualquier código JavaScript de aplicaciones basadas en modelos. Este código puede cambiar o sobrescribirse durante una actualización.
- No se admite la edición de un archivo de solución para editar cualquiera de los componentes de la solución que no sean las cintas de opciones, los formularios, el mapa del sitio o las consultas guardadas. Para obtener más información, consulte [Cuándo editar personalizaciones](when-edit-customization-file.md).
    - No se admite la definición de nuevos componentes de la solución mediante la edición del archivo de solución. 
    - No se admite la edición de los archivos de recursos web exportados con una solución. 
    - Excepto por los pasos que se documentan en [Mantener soluciones administradas](../common-data-service/maintain-managed-solutions.md), no se admite la edición del contenido de una solución administrada.

- No se puede mostrar un formulario de entidad en un iFrame incrustado en otro formulario de entidad.

### <a name="see-also"></a>Vea también

[Personalizaciones compatibles para Common Data Service](../common-data-service/supported-customizations.md)<br/>
[Aplicar la lógica de negocios usando scripting de cliente en aplicaciones basadas en modelos que usan JavaScript](client-scripting.md)<br/>
[Personalización de comandos y la cinta de opciones](customize-commands-ribbon.md)<br/>
[Recursos web en aplicaciones basadas en modelos](web-resources.md)
