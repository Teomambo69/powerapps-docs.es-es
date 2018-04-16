---
title: 'Aplicaciones controladas por modelos: introducción para desarrolladores | Microsoft Docs'
description: Obtenga información sobre cómo los desarrolladores pueden agregar valor a las aplicaciones controladas por modelos.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
ms.openlocfilehash: 4e8a935dbef2c46478f99ecbf82a7fc837feb284
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="model-driven-apps-developer-overview"></a>Aplicaciones controladas por modelos: introducción para desarrolladores

PowerApps ofrece a usuarios, empresas, socios, proveedores de software independientes (ISV) e integradores de sistemas (SI) una plataforma eficaz para la creación de aplicaciones de línea de negocio. La novedad incorporada en PowerApps en esta versión son las aplicaciones controladas por modelos que se compilan con el nuevo Common Data Service for Apps. Common Data Service for Apps ahora contiene la funcionalidad básica de las aplicaciones de Dynamics 365 Customer Engagement. Con las aplicaciones controladas por modelos, se pueden compilar aplicaciones que usen las mismas características de extensibilidad que esas aplicaciones.

Las aplicaciones controladas por modelos son principalmente un enfoque de componentes sin código o con poca cantidad de código enfocado al desarrollo de aplicaciones. El valor que los desarrolladores pueden proporcionar es mediante la extensión de la aplicación. Antes de empezar a escribir código, comience por aprender a compilar una aplicación controlada por modelos y las opciones que se pueden aplicar sin necesidad de código. 

## <a name="get-started"></a>Introducción
Si ya tiene experiencia con las aplicaciones de Dynamics 365 Customer Engagement, encontrará que podrá aplicarla para compilar aplicaciones controladas por modelos. Hay algunos diseñadores nuevos disponibles pero, por lo general, los conceptos son los mismos.

> [!NOTE]
> Las aplicaciones controladas por modelos se conectan a Common Data Service for Apps. Para obtener información sobre cómo los desarrolladores pueden agregar valor en el nivel de servicio, vea [Common Data Service for Apps Developer Overview](../common-data-service/overview.md) (Introducción para desarrolladores de Common Data Service for Apps).
> El contenido de esta sección hará referencia únicamente a lo que los desarrolladores de extensiones pueden hacer que se aplica a la experiencia para los usuarios de aplicaciones controladas por modelos. 

Si no está familiarizado con las aplicaciones de Dynamics 365 Customer Engagement, en los temas de esta sección se proporciona información general de los conceptos importantes para ayudar a los desarrolladores a empezar a trabajar con aplicaciones controladas por modelos. 

> [!NOTE]
> Dado que Common Data Service for Apps y Dynamics 365 Customer Engagement aprovechan la misma plataforma, encontrará información más completa para desarrolladores en la [Guía para desarrolladores de Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/developer-guide). En estos temas se proporciona una introducción con vínculos a la guía para desarrolladores y otras guías para obtener más información.


## <a name="community-tools-for-model-driven-apps"></a>Herramientas de la comunidad para aplicaciones controladas por modelos

La comunidad de Dynamics 365 crea herramientas. Muchas de las más populares se distribuyen a través de [XrmToolBox](https://www.xrmtoolbox.com/). XrmToolBox es una aplicación Windows que se conecta a Common Data Service for Apps, y proporciona herramientas para facilitar las tareas de personalización, configuración y funcionamiento. Incluye más de 30 complementos para realizar tareas de administración, personalización o configuración con más facilidad y en mucho menos tiempo.

La siguiente es una lista seleccionada de herramientas de la comunidad distribuidas a través de XrmToolBox que se pueden usar cuando se trabaja con aplicaciones controladas por modelos.

|Herramienta  |Descripción  |
|---------|---------|
|[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/)|Importa y exporta traducciones con información contextual|
|[Export to Excel](https://www.xrmtoolbox.com/plugins/Ryr.XrmToolBox.ExportToExcel/)|Exportar fácilmente los registros desde la vista o fetchxml seleccionado a Excel.|
|[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)|Administrar iconos de entidades personalizadas en una única pantalla|
|[Ribbon Workbench 2016](https://www.xrmtoolbox.com/plugins/RibbonWorkbench2016/)|Modificar la cinta de opciones de Dynamics CRM o la barra de comandos desde dentro de XrmToolbox|
|[Diseñador de vistas](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.ViewDesigner/)|Interfaz de usuario sencilla para crear diseños de vista y modificar consultas mediante FetchXML Builder|
|[View Layout Replicator](https://www.xrmtoolbox.com/plugins/MsCrmTools.ViewLayoutReplicator/)|Aplicar el mismo diseño a varias vistas de la misma entidad en una sola operación|
|[WebResources Manager](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/)|Administrar fácilmente los recursos web|

Otra herramienta que no se distribuye a través de XrmToolBox es [CRM REST Builder](https://github.com/jlattimer/CRMRESTBuilder) de Jason Lattimer. Esta herramienta genera código de JavaScript para su uso con la API web.

> [!NOTE]
> Microsoft no admite las herramientas creadas por la comunidad. Si tiene preguntas o problemas con las herramientas de la comunidad, póngase en contacto con el publicador de la herramienta.




