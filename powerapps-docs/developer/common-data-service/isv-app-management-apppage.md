---
title: Página de la aplicación de ISV Studio | Microsoft Docs
description: Conozca las capacidades de la página de la aplicación proporcionadas por el portal ISV Studio.
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
ms.openlocfilehash: 9624293706f8b1307f19fc168f37c6464c724c65
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749428"
---
# <a name="the-app-page"></a>La página de la aplicación

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Cuando el usuario selecciona una aplicación, pasa a la página de detalles de la aplicación, que proporciona una vista para analizar el historial de instalación de los usuarios para esa aplicación específica. La descripción de la aplicación procede de [AppSource](https://appsource.microsoft.com/).

![Página de detalles de la aplicación](media/isv-portal-apppage-appname.png)

La página de detalles de la aplicación contiene los gráficos y las métricas siguientes.

## <a name="successful-package-installs-by-environment-type"></a>Instalaciones correctas de paquetes por tipo de entorno

El gráfico circular que se muestra a continuación ilustra la relación de instalaciones de paquetes de producción en comparación con espacio aislado de la aplicación seleccionada en la base de instalación.

Al mantener el puntero sobre el gráfico, se muestra la siguiente información:

1. Tipo de organización – producción o espacio aislado
2. Número de instalaciones de paquetes para el tipo de la organización

![Instalaciones de paquetes por tipo de entorno](media/isv-portal-apppage-graph1.png)

## <a name="package-install-attempts-by-tenant-last-28-days"></a>Intentos de instalación de paquetes por inquilino (los últimos 28 días)

El gráfico de barras siguiente muestra el número de instalaciones de paquetes correctas frente a erróneas de la aplicación seleccionada por inquilino durante los últimos 28 días.

Al mantener el puntero sobre cualquier elemento el gráfico, se muestra la siguiente información:

1. Nombre del inquilino e identificador de inquilino
2. Estado de instalación del paquete (correcta frente a errónea) en el inquilino
3. Recuento de los intentos de instalación del paquete en el inquilino

![Intentos de instalación de paquetes por inquilino (los últimos 28 días)](media/isv-portal-apppage-graph2.png)

## <a name="successful-package-installs-by-location-of-tenants"></a>Instalaciones correctas del paquete por ubicación de inquilinos

El mapa mostrado a continuación ilustra la distribución geográfica de la aplicación por ubicación de inquilino.

Al mantener el puntero sobre cualquier región el gráfico, se muestra la siguiente información:

1. Ubicación
2. Recuento de instalaciones del paquete en la ubicación seleccionada

![Instalaciones del paquete por ubicación de inquilinos](media/isv-portal-apppage-graph3.png)

## <a name="successful-package-and-version-installs-by-tenant"></a>Instalaciones correctas del paquete y versión por inquilino

El gráfico de columnas que se muestra a continuación ilustra los nombres únicos del paquete cuyas versiones de la aplicación seleccionada aparecen en un menú desplegable. Todos los paquetes están seleccionados de forma predeterminada, y todas las versiones instaladas de todos los paquetes (por inquilino) se muestran en el gráfico. El usuario puede seleccionar uno o varios paquetes y versiones para segmentar y analizar más en profundidad. Cuando el usuario selecciona un paquete, el desplegable de versiones se actualizan para mostrar las versiones correspondientes del paquete seleccionado.

Al mantener el puntero sobre cualquier elemento el gráfico, se muestra la siguiente información:

1. Nombre del inquilino e identificador de inquilino
2. Versión del paquete
3. Recuento de instalación del paquete en el inquilino seleccionado


![Instalaciones del paquete y versión por inquilino](media/isv-portal-apppage-graph4.png)

### <a name="see-also"></a>Vea también

[Introducción a ISV Studio para Power Platform](isv-app-management.md)  
[Página principal](isv-app-management-homepage.md)  
[Página de inquilino](isv-app-management-tenantpage.md)
