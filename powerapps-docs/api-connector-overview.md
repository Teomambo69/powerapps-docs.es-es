---
title: "Introducción a los conectores de API | Microsoft Docs"
description: Los fabricantes de software independiente y propietarios de servicios SaaS pueden crear conectores que certifique Microsoft.
services: 
suite: powerapps
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 74bac3b0f5bad2b95ab9b6b312fc5209bf5da3a2
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2018
---
# <a name="api-connector-overview-powerapps"></a>Introducción a los conectores de API (PowerApps)
Un **conector de API** es un contenedor de OpenAPI (Swagger) para una API de REST que permite al servicio subyacente comunicarse con [Microsoft Flow](https://flow.microsoft.com), [PowerApps](https://powerapps.microsoft.com) y [Logic Apps](https://docs.microsoft.com/azure/logic-apps/). Es una manera para que los usuarios conecten sus cuentas y aprovechen un conjunto de **desencadenadores** y **acciones** creados previamente al crear aplicaciones y flujos de trabajo.

Como **fabricante de software independiente (ISV)** o **propietario de servicios SaaS**, puede crear conectores para habilitar una amplia gama de escenarios empresariales y de productividad para los usuarios. Un conector le ayudará a ir más allá de un conjunto definido de integraciones y a aumentar la cobertura, la detectabilidad y el uso del servicio.

## <a name="requirements"></a>Requisitos
Para crear y enviar un conector, el servicio debe cumplir los siguientes requisitos:

* Escenario de usuario de empresa que se adapta bien a Microsoft Flow, PowerApps y Logic Apps
* Servicio disponible públicamente con API de REST estables

## <a name="build-your-connector"></a>Creación del conector
Es el primer paso para crear un conector de API crear un conector personalizado completamente funcional. Un conector personalizado funciona exactamente igual que un conector de API, pero su disponibilidad se limita al autor y a usuarios específicos del inquilino del autor.

El proceso de creación de un conector consta de varios pasos:

![Pasos para crear un conector de API](./media/api-connectors-overview/authoring-steps.png)

[Más información](api-connector-dev.md) sobre cómo desarrollar un conector de API.

## <a name="submit-for-certification"></a>Envío para la certificación
Cuando haya creado un conector, debe enviarlo para su certificación. Como parte de nuestro proceso de certificación de terceros, Microsoft revisa el conector antes de la publicación.

En este proceso se valida la funcionalidad del conector en Microsoft Flow y PowerApps, y se comprueban los requisitos técnicos y de contenido.

[Más información](api-connector-submission.md) sobre el proceso de envío del conector para la certificación y la publicación.

## <a name="get-support"></a>Obtener soporte
Para soporte técnico de incorporación y desarrollo, envíe un correo electrónico a [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com). Esta cuenta está sometida a supervisión y administración. Los incidentes y las consultas de los desarrolladores llegarán rápidamente al equipo correspondiente.

