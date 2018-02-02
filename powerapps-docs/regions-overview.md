---
title: "Información general de las regiones | Microsoft Docs"
description: "Regiones en PowerApps: dónde se implementan las aplicaciones, regiones disponibles, características específicas de una región"
services: 
suite: powerapps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/04/2017
ms.author: sharik
ms.openlocfilehash: 114aa01bd745ed501e209e314e75904751aad3f5
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
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

## <a name="what-features-are-specific-to-a-given-region"></a>¿Qué características son específicas de una región determinada?
Los entornos se pueden crear en regiones diferentes y se enlazan a esa ubicación geográfica. Cuando crea una aplicación en un entorno, esa aplicación se implementa en centros de datos de esa ubicación geográfica. Esto se aplica a cualquier elemento que cree en ese entorno, incluidas las bases de datos en Common Data Service, las aplicaciones, las conexiones, las puertas de enlace y los conectores personalizados.

Para obtener un rendimiento óptimo, si los usuarios están en Europa, cree y use el entorno en la región Europa. Si los usuarios se encuentran en los Estados Unidos, cree y use el entorno de Estados Unidos.

> [!NOTE]
> Las puertas de enlace de datos locales no están disponibles en la región de India ni en los entornos personalizados. Debe crear las puertas de enlace en el entorno predeterminado.

