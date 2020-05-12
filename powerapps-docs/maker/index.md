---
title: Información general de creación de aplicaciones | Microsoft Docs
description: Información general de creación de aplicaciones en el modo de lienzo o el modo basado en modelos e incorporación de Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 12/05/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 79a1a5351bc3fe72a7558697e7cf8e8dfa079ce8
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "3302343"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>Información general de creación de aplicaciones en Power Apps

Power Apps es una plataforma de desarrollo de alta productividad para aplicaciones de negocio y tiene cuatro componentes fundamentales:

- [Aplicaciones de lienzo](canvas-apps/getting-started.md) comience su experiencia de usuario creando una interfaz muy personalizada con el potencial de un lienzo en blanco y conectándola con los 200 orígenes de datos que elija. Puede crear aplicaciones de lienzo para la web, el móvil y la tableta.
- Las [aplicaciones basadas en modelos](model-driven-apps/model-driven-app-overview.md) empiezan con su modelo de datos, y crecen a partir de la forma de los procesos y datos empresariales del núcleo en Common Data Service hasta los formularios, vistas y otros componentes del modelo. Las aplicaciones basadas en modelos generan automáticamente excelentes interfaces de usuario que se pueden emplear en los dispositivos.
- Los [portales](portals/overview.md) comienzan a crear sitios web orientados hacia el exterior que permiten a los usuarios ajenos a la organización iniciar sesión con una amplia variedad de identidades, crear y ver datos en Common Data Service, o incluso examinar contenido de forma anónima.
- [Common Data Service](common-data-service/data-platform-intro.md) es la plataforma de datos que se suministra con Power Apps y que le permite almacenar y modelar los datos profesionales. Es la plataforma en la que se incorporan las aplicaciones de Dynamics 365. Si es cliente de Dynamics, sus datos ya estarán en Common Data Service.

Le resultará fácil y sencillo intentar crear la primera aplicación. Tenemos un plan de prueba gratuita de 30 días y un plan comunitario gratuito. Descubra cuál es el mejor para usted y empiece a usarlo.

## <a name="canvas-apps"></a>Aplicaciones de lienzo

Las aplicaciones de lienzo le ofrecen flexibilidad para organizar la experiencia de usuario y la interfaz del modo en que desea. Deje que su creatividad y olfato empresarial le guíen al determinar el aspecto de sus aplicaciones.

Puede empezar a crear su aplicación desde las herramientas de Microsoft en las que se encuentren sus datos, como:

- [Desde una lista de SharePoint](canvas-apps/app-from-sharepoint.md#create-an-app-from-within-sharepoint-online)
- [Desde un panel de Power BI](canvas-apps/embed-powerapps-powerbi.md)

Crear una aplicación de lienzo es fácil; con Power Apps, puede buscar o crear su aplicación de diversas formas:

- [Desde los datos](canvas-apps/app-from-sharepoint.md)
- [Desde un ejemplo](canvas-apps/open-and-run-a-sample-app.md)
- [Desde un origen de Common Data Service](canvas-apps/data-platform-create-app.md)
- [Desde un lienzo en blanco](canvas-apps/data-platform-create-app-scratch.md)
- [Mediante AppSource](../user/app-source.md)

## <a name="model-driven-apps"></a>Aplicaciones basadas en modelos

Al crear una aplicación basada en modelos, puede usar todo el potencial de Common Data Service para configurar rápidamente los formularios, las reglas de negocio y los flujos de procesos. Puede crear una aplicación basada en modelos a partir del sitio de Power Apps.

Empezar a usar las aplicaciones basadas en modelos es sencillo, y puede empezar con estos temas:

- [Crear una aplicación](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [Creación y diseño de formularios](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Creación o edición de vistas](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [Crear o editar un gráfico del sistema](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Crear o editar paneles](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [Adición de seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [Adición de lógica de negocios](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service"></a>Common Data Service

Common Data Service le permite almacenar y administrar de forma segura datos en un conjunto de entidades estándar y personalizadas, y puede agregar campos a esas entidades cuando lo necesite.

Comenzar a utilizar Common Data Service es fácil. Por ejemplo, puede empezar con estos elementos:

- [Creación de una entidad personalizada](common-data-service/data-platform-create-entity.md)
- [Administración de campos](common-data-service/data-platform-manage-fields.md)
- [Creación de conjuntos de opciones personalizadas](common-data-service/custom-picklists.md)
- [Creación de una regla de negocio](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="canvas-and-model-driven-artifacts"></a>Artefactos de lienzo y controlados por modelos

A pesar de la combinación de las experiencias de aplicaciones de lienzo y controladas por modelos, estos artefactos serán importantes tanto para aplicaciones de lienzo como para aquellas controladas por modelos.

| Artefacto            | Tipo de aplicación     |
|---------------------|--------------|
| Entidad > Vistas      | Basada en modelo |
| Entidad > Formularios      | Basada en modelo |
| Entidad > Paneles | Basada en modelo |
| Conexiones         | Lienzo       |
| Puertas de enlace            | Lienzo       |
| Conectores personalizados   | Lienzo       |
| Aplicaciones > Importar       | Lienzo       |

Después de crear su aplicación, puede [compartirla](canvas-apps/share-app.md) con los integrantes del equipo.
