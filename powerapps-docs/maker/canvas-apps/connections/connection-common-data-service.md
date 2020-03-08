---
title: Conectarse a Common Data Service | Microsoft Docs
description: Obtenga información sobre cómo conectarse a Common Data Service y usarlo para compilar aplicaciones en Power apps.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/04/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 227482b383acd3117cc78eddf97698ffa9146698
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845201"
---
# <a name="connect-to-common-data-service"></a>Conectarse a Common Data Service

## <a name="overview"></a>Información general

Puede almacenar de forma segura los datos empresariales en Common Data Service y compilar aplicaciones enriquecidas en Power apps para que los usuarios puedan administrar los datos. También puede integrar los datos en soluciones que incluyen Power Automatic, Power BI y datos de Dynamics 365.

De forma predeterminada, el conector de Common Data Service se conecta a los datos del entorno actual de la aplicación. Si la aplicación se mueve a otro entorno, el conector se conecta a los datos en el nuevo entorno. Este comportamiento funciona bien para una aplicación que usa un solo entorno o una aplicación que sigue un proceso ALM para pasar del desarrollo a la prueba a producción.

Al agregar un origen de datos con el conector de Common Data Service, puede cambiar el entorno y, a continuación, seleccionar una o más entidades. De forma predeterminada, la aplicación se conecta a los datos del entorno actual.

![Entorno predeterminado](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Si selecciona **cambiar**, puede especificar un entorno diferente para extraer datos de él en lugar de o además del entorno actual.

![Otros entornos](media/connection-common-data-service/common-data-service-connection-select-environment.png)

El nombre del entorno seleccionado aparece bajo la lista entidades.

![Nuevos entornos](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

El conector de Common Data Service es más robusto que el conector de Dynamics 365 y el enfoque de la paridad de características.

### <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service y la mejor experiencia de origen de datos

Si ha creado una aplicación de lienzo con un conector de Common Data Service antes del 2019 de noviembre, es posible que no tenga la ventaja de la versión más reciente del Common Data Service. Lea [Common Data Service mejoras de conexión](../use-native-cds-connector.md) para obtener más detalles y para actualizar la conexión.