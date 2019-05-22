---
title: Conectarse a Common Data Service | Microsoft Docs
description: Obtenga información sobre cómo conectarse a Common Data Service y usarlo para compilar aplicaciones en PowerApps.
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c521fd5961bc9b8d940a374383baca1aeef0cbe4
ms.sourcegitcommit: 93096dfa1aadba77159db1e5922f3d5528eecb7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986365"
---
# <a name="connect-to-common-data-service"></a>Conectarse a Common Data Service

Puede almacenar sus datos empresariales en Common Data Service y crear aplicaciones enriquecidas en PowerApps para que los usuarios puedan administrar esos datos de forma segura. También puede integrar esos datos en soluciones que incluyen datos de Dynamics 365, Power BI y Microsoft Flow.

De forma predeterminada, el conector de Common Data Service se conecta a los datos en el entorno actual de la aplicación. Si la aplicación se mueve a otro entorno, el conector se conecta a los datos en el nuevo entorno. Este comportamiento funciona bien para una aplicación con un único entorno o una aplicación que sigue un proceso ALM para mover desde el desarrollo a prueba a producción.

Cuando se agrega un origen de datos con el conector de Common Data Service, puede cambiar el entorno y, a continuación, seleccione una o más entidades. De forma predeterminada, la aplicación se conecta a los datos en el entorno actual y se muestra la interfaz de usuario **(actual)** a través de la lista de entidades.

> [!div class="mx-imgBorder"]
> ![Entorno predeterminado](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Si selecciona **cambio**, puede especificar un entorno diferente para extraer datos de ella en lugar o además del entorno actual.

> [!div class="mx-imgBorder"]
> ![Otros entornos](media/connection-common-data-service/common-data-service-connection-select-environment.png)

El nombre del entorno seleccionado aparece en el cuadro de búsqueda.

> [!div class="mx-imgBorder"]
> ![Nuevos entornos](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

El conector de Common Data Service es más sólido que el conector de Dynamics 365 y proximidad paridad de características.

Más información: [¿Qué es Common Data Service?](../../common-data-service/data-platform-intro.md)
