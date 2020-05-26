---
title: Página de inquilino de ISV Studio | Microsoft Docs
description: Conozca las capacidades de la página de inquilino proporcionada por el portal ISV Studio.
services: ''
suite: powerapps
documentationcenter: na
author: phecke
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 07/11/2019
ms.author: prkoduku
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e94e5a0058d6f892a06e982fba454551b15f5374
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "3261791"
---
# <a name="the-tenant-page"></a>La página de inquilino

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Para ver el historial de instalación de un inquilino, ISV puede cambiar a la vista **Inquilinos principales** en la página principal y seleccionar un inquilino.

![Historial de instalación de un inquilino](media/isv-portal-homepage-tenantpivot.png)

La página de inquilino contiene los gráficos y las métricas siguientes:

![Página de inquilino](media/isv-portal-tenantpage.png)

## <a name="successfully-installed-apps"></a>Aplicaciones instaladas correctamente

El gráfico circular mostrado a continuación visualiza la distribución de la aplicación de ISV en todos los entornos del inquilino seleccionado.

Al mantener el puntero sobre los elementos del gráfico, se muestra la siguiente información:

1. Nombre de aplicación
2. Recuento de instalación de la aplicación en el inquilino seleccionado

![Aplicaciones instaladas correctamente](media/isv-portal-tenantpage-graph1.png)

## <a name="successful-production-vs-sandbox-package-installs-by-environment"></a>Instalaciones correctas de producción frente a de espacio aislado por entorno

El gráfico de barras mostrado a continuación visualiza las instalaciones de producción frente a las de espacio aislado de aplicaciones ISV en el inquilino seleccionado. Por razones de privacidad, el nombre del entorno no se puede mostrar en este momento.

Al mantener el puntero sobre cualquier elemento el gráfico, se muestra la siguiente información:

1. Id. de entorno
2. Tipo de entorno (producción o espacio aislado)
3. Recuento de instalaciones del paquete en el entorno

![Instalaciones de paquetes por tipo de entorno](media/isv-portal-tenantpage-graph2.png)

## <a name="successful-package-installs-by-environment-location"></a>Instalaciones correctas del paquete por ubicación de entorno

El mapa mostrado a continuación ilustra la distribución geográfica de las instalaciones de paquete ISV por ubicación de entorno.

Al mantener el puntero sobre cualquier ubicación del gráfico, se muestra la siguiente información:

1. Ubicación
2. Recuento de instalaciones del paquete en la ubicación seleccionada

![Instalaciones del paquete por ubicación de entorno](media/isv-portal-tenantpage-graph3.png)

## <a name="successful-app-package-and-version-installs-by-environment"></a>Instalaciones correctas del paquete de la aplicación y versión por entorno

El gráfico de columnas que se muestra a continuación visualiza los nombres de la aplicación, los nombres únicos del paquete y las versiones del inquilino seleccionado en menús desplegables. Todas las aplicaciones están seleccionadas de forma predeterminada y ISV puede explorar en profundidad seleccionando una o varias aplicaciones, paquetes y versiones. Cuando el usuario selecciona una aplicación, el desplegable **Paquete** se actualiza para mostrar los paquetes correspondientes de la aplicación seleccionada. Cuando el usuario selecciona un paquete, el desplegable **Versiones** se actualiza para mostrar las versiones correspondientes del paquete seleccionado.

Al mantener el puntero sobre cualquier elemento el gráfico, se muestra la siguiente información:

1. Id. de entorno
2. Versión del paquete
3. Recuento de instalación del paquete en el entorno

![Instalaciones del paquete y versión por entorno](media/isv-portal-tenantpage-graph4.png)

### <a name="see-also"></a>Vea también

[Introducción a ISV Studio para Power Platform](isv-app-management.md)  
[Página principal](isv-app-management-homepage.md)<br/> 
[Página de aplicación](isv-app-management-apppage.md)<br/> 
[Comprobador de AppSource](isv-app-management-appsource-checker.md)<br/> 
[Certificación de conector](isv-app-management-certification.md)
