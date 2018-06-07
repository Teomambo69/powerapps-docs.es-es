---
title: Introducción a las regiones | Microsoft Docs
description: Información sobre las regiones en PowerApps
author: manasmams
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
ms.openlocfilehash: 818d751a45eee6d746d4f318a98169a771787d92
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445784"
---
# <a name="regions-overview-in-powerapps"></a>Introducción a las regiones en PowerApps
## <a name="how-do-i-find-out-where-my-app-is-deployed"></a>¿Cómo averiguar dónde se implementa la aplicación?
La aplicación se implementa en la región que hospeda el entorno. Por ejemplo, si su entorno se crea en la región Europa, la aplicación se implementa en centros de datos de Europa.

Los administradores pueden determinar la región de cada entorno en el centro de administración de PowerApps.

* Vaya al [centro de administración](https://admin.powerapps.com) e inicie sesión con su cuenta profesional.
  
    En el centro de administración, todos los entornos existentes aparecen en la pestaña **Entornos**. En esta lista se muestra la **región** donde se implementa la aplicación:
  
   ![Pestaña Entornos](./media/regions-overview/environment-list.png)

## <a name="what-regions-are-available"></a>¿Qué regiones hay disponibles?
* Estados Unidos
* Canadá
* Europa
* Asia
* Australia
* India
* Japón
* Reino Unido

## <a name="what-features-are-specific-to-a-given-region"></a>¿Qué características son específicas de una región determinada?
Los entornos se pueden crear en regiones diferentes y se enlazan a esa ubicación geográfica. Cuando crea una aplicación en un entorno, esa aplicación se implementa en centros de datos de esa ubicación geográfica. Esto se aplica a cualquier elemento que cree en ese entorno, incluidas las bases de datos en Common Data Service, las aplicaciones, las conexiones, las puertas de enlace y los conectores personalizados.

Para obtener un rendimiento óptimo, si los usuarios están en Europa, cree y use el entorno en la región Europa. Si los usuarios se encuentran en los Estados Unidos, cree y use el entorno de Estados Unidos.

> [!NOTE]
> Actualmente, solo se puede crear una base de datos en un entorno de producción o evaluación, que se encuentre en la misma región que la región principal de Azure AD o el espacio empresarial de Office 365. Estamos trabajando en permitir la creación de bases de datos en entornos creados en una región distinta a la principal del inquilino. Además, actualmente no se puede crear una base de datos en el entorno predeterminado y un entorno individual (creado con el Plan de la comunidad de PowerApps).

> [!NOTE]
> Las puertas de enlace de datos locales no están disponibles en la región de India ni en los entornos personalizados. Debe crear las puertas de enlace en el entorno predeterminado.

