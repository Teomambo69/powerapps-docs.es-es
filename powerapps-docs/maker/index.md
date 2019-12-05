---
title: Información general sobre la creación de aplicaciones | Microsoft Docs
description: Información general sobre la creación de aplicaciones de lienzo o en modo controlado por modelos, y la incorporación de Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 07/18/2018
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d41af83d0a6de68ac94327798e076b19039dadef
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729809"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>Información general sobre la creación de aplicaciones en Power Apps

Power Apps es una plataforma de desarrollo de gran productividad para aplicaciones de negocio y tiene cuatro componentes principales:

- [Las aplicaciones de lienzo](canvas-apps/getting-started.md) comienzan con la experiencia del usuario, diseñando una interfaz muy personalizada con la potencia de un lienzo en blanco y conectándola a uno de los 200 orígenes de datos para elegir. Se pueden compilar aplicaciones de lienzo para aplicaciones web, móviles y de tableta.
- [Las aplicaciones controladas por modelos](model-driven-apps/model-driven-app-overview.md) empiezan con el modelo de datos y se compilan a partir de la forma de los datos y procesos de negocio fundamentales en Common Data Service para crear formularios, vistas y otros componentes. Las aplicaciones controladas por modelos generan automáticamente una interfaz de usuario excelente con capacidad de respuesta en todos los dispositivos.
- [Los portales](portals/overview.md) comienzan a crear sitios web orientados hacia el exterior que permiten a los usuarios ajenos a la organización iniciar sesión con una amplia variedad de identidades, crear y ver datos en Common Data Service, o incluso examinar contenido de forma anónima.
- [Common Data Service](common-data-service/data-platform-intro.md) es la plataforma de datos que viene con Power Apps y que permite almacenar y modelar los datos de negocio. Es la plataforma en la que se compilan las aplicaciones de Dynamics 365; si es un cliente de Dynamics, los datos ya están en Common Data Service.

Intentar la creación de la primera aplicación es fácil. Tenemos un plan de evaluación de 30 días y un plan de la comunidad gratuito; obtenga más información sobre cuál es mejor para usted y empiece a trabajar.

## <a name="canvas-apps"></a>Aplicaciones de lienzo

Las aplicaciones de lienzo proporcionan la flexibilidad de organizar la experiencia del usuario y la interfaz de la forma que se quiera. Permita que el sentido creativo y empresarial le guíe a obtener el aspecto que quiere para las aplicaciones.

Se puede empezar a compilar la aplicación desde las herramientas de Microsoft donde se encuentren los datos, por ejemplo:

- [Desde una lista de SharePoint](canvas-apps/app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online)
- [Desde un panel de Power BI](canvas-apps/embed-powerapps-powerbi.md)

Crear una aplicación de lienzo es fácil; con Power Apps, se puede buscar o crear la aplicación de varias maneras:

- [Desde datos](canvas-apps/app-from-sharepoint.md)
- [Desde un ejemplo](canvas-apps/open-and-run-a-sample-app.md)
- [Desde un origen de Common Data Service](canvas-apps/data-platform-create-app.md)
- [Desde un lienzo en blanco](canvas-apps/data-platform-create-app-scratch.md)
- [A través de AppSource](../user/app-source.md)

## <a name="model-driven-apps"></a>Aplicaciones controladas por modelos

Cuando se crea una aplicación controlada por modelos, se puede usar toda la potencia de Common Data Service para configurar rápidamente los formularios, las reglas de negocio y los flujos de proceso. Una aplicación controlada por modelos se crea desde el sitio de Power Apps.

La introducción a las aplicaciones controladas por modelos es sencilla y se puede empezar con estos temas:

- [Crear una aplicación](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [Crear y diseñar formularios](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Comprender las vistas](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [Crear o editar un gráfico del sistema](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Crear o editar paneles](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [Agregar seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [Agregar lógica de negocio](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service"></a>Common Data Service

Common Data Service permite almacenar y administrar los datos de forma segura en un conjunto de entidades estándar y personalizadas, y agregar datos a esas entidades cuando sea necesario.

Empezar a usar Common Data Service es fácil. Por ejemplo, se puede empezar con estos elementos:

- [Crear una entidad personalizada](common-data-service/data-platform-create-entity.md)
- [Administrar campos](common-data-service/data-platform-manage-fields.md)
- [Crear conjuntos de opciones personalizados](common-data-service/custom-picklists.md)
- [Crear una regla de negocio](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="canvas-and-model-driven-artifacts"></a>Artefactos de lienzo y controlados por modelos

A pesar de la combinación de las experiencias de aplicaciones de lienzo y controladas por modelos, estos artefactos serán importantes tanto para aplicaciones de lienzo como para aquellas controladas por modelos.

| Artefacto            | Tipo de aplicación     |
|---------------------|--------------|
| Entidad > Vistas      | Controlado por modelos |
| Entidad > Formularios      | Controlado por modelos |
| Entidad > Paneles | Controlado por modelos |
| Conexiones         | Lienzo       |
| Puertas de enlace            | Lienzo       |
| Conectores personalizados   | Lienzo       |
| Aplicaciones > Importar       | Lienzo       |

Después de compilar la aplicación, se puede [compartir](canvas-apps/share-app.md) con los miembros del equipo.
