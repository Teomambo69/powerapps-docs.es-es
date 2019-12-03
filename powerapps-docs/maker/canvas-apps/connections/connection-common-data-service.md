---
title: Conectarse a Common Data Service | Microsoft Docs
description: Obtenga información sobre cómo conectarse a Common Data Service y usarlo para compilar aplicaciones en Power apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2473f445839b774ecc28fe007912511095d9316d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723829"
---
# <a name="connect-to-common-data-service"></a>Conectarse a Common Data Service

Puede almacenar de forma segura los datos empresariales en Common Data Service y compilar aplicaciones enriquecidas en Power apps para que los usuarios puedan administrar los datos. También puede integrar los datos en soluciones que incluyen Power Automatic, Power BI y datos de Dynamics 365.

De forma predeterminada, el conector de Common Data Service se conecta a los datos del entorno actual de la aplicación. Si la aplicación se mueve a otro entorno, el conector se conecta a los datos en el nuevo entorno. Este comportamiento funciona bien para una aplicación que usa un solo entorno o una aplicación que sigue un proceso ALM para pasar del desarrollo a la prueba a producción.

Al agregar un origen de datos con el conector de Common Data Service, puede cambiar el entorno y, a continuación, seleccionar una o más entidades. De forma predeterminada, la aplicación se conecta a los datos del entorno actual y la interfaz de usuario muestra **(actual)** en la lista de entidades.

> [!div class="mx-imgBorder"]
> ![entorno predeterminado](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Si selecciona **cambiar**, puede especificar un entorno diferente para extraer datos de él en lugar de o además del entorno actual.

> [!div class="mx-imgBorder"]
> ![otros entornos](media/connection-common-data-service/common-data-service-connection-select-environment.png)

El nombre del entorno seleccionado aparece en el cuadro de búsqueda.

> [!div class="mx-imgBorder"]
> ![nuevos entornos](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

El conector de Common Data Service es más robusto que el conector de Dynamics 365 y el enfoque de la paridad de características.

Más información: [¿Qué es Common Data Service?](../../common-data-service/data-platform-intro.md)
