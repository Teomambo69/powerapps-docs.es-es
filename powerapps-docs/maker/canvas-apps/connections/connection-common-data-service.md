---
title: Conectarse a Common Data Service | Microsoft Docs
description: Obtenga información sobre cómo conectarse a Common Data Service y usarlo para compilar aplicaciones en PowerApps.
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
ms.openlocfilehash: fcadc4d214494380f50f712e453554d41d08eabe
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994004"
---
# <a name="connect-to-common-data-service"></a>Conectarse a Common Data Service

Puede almacenar de forma segura los datos empresariales en Common Data Service y compilar aplicaciones enriquecidas en PowerApps para que los usuarios puedan administrar los datos. También puede integrar los datos en soluciones que incluyen Microsoft Flow, Power BI y datos de Dynamics 365.

De forma predeterminada, el conector de Common Data Service se conecta a los datos del entorno actual de la aplicación. Si la aplicación se mueve a otro entorno, el conector se conecta a los datos en el nuevo entorno. Este comportamiento funciona bien para una aplicación que usa un solo entorno o una aplicación que sigue un proceso ALM para pasar del desarrollo a la prueba a producción.

Al agregar un origen de datos con el conector de Common Data Service, puede cambiar el entorno y, a continuación, seleccionar una o más entidades. De forma predeterminada, la aplicación se conecta a los datos del entorno actual y la interfaz de usuario muestra **(actual)** en la lista de entidades.

> [!div class="mx-imgBorder"]
> ![Default entorno @ no__t-1

Si selecciona **cambiar**, puede especificar un entorno diferente para extraer datos de él en lugar de o además del entorno actual.

> [!div class="mx-imgBorder"]
> entornos de @no__t 0Other a no__t-1

El nombre del entorno seleccionado aparece en el cuadro de búsqueda.

> [!div class="mx-imgBorder"]
> entornos de @no__t 0New a no__t-1

El conector de Common Data Service es más robusto que el conector de Dynamics 365 y el enfoque de la paridad de características.

Más información: [¿Qué es Common Data Service?](../../common-data-service/data-platform-intro.md)
