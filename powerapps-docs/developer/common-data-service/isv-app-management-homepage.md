---
title: La página principal de ISV Studio | Microsoft Docs
description: Conozca las capacidades de la página principal proporcionada por el portal ISV Studio.
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
---

# <a name="the-home-page"></a>La página principal

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Cuando usuario inicia sesión en ISV Studio, se le muestra la página de aterrizaje conocida como página *principal*. Se muestra un mensaje de bienvenida que define el objetivo de esta página.

Si un usuario está asociado con varios editores, muestran todos los editores y el primer editor está seleccionado de forma predeterminada. Todas las métricas de esta página son específicas del editor seleccionado. El usuario puede cambiar a otro nombre de editor para ver las métricas correspondiente para ese editor.

![Página principal](media/isv-portal-homepage.png)

La sección de resumen de la página principal contiene los gráficos y las métricas siguientes.

## <a name="successful-app-package-installs-by-tenant"></a>Instalaciones correctas del paquete de la aplicación y versión por inquilino

El primer gráfico visualiza las aplicaciones publicadas y los inquilinos en los que están instalados los paquetes de la aplicación, y se muestran en orden descendente en función del número de instalaciones del paquete.

Al mantener el puntero sobre una ventana del inquilino del gráfico, se muestra la siguiente información:

1. Nombre de aplicación
2. Nombre del inquilino e identificador de inquilino
3. Número de instalaciones del paquete de la aplicación en el inquilino

![Instalaciones del paquete por inquilino](media/isv-portal-homepage-graph1.png)

## <a name="package-install-attempts-by-app-last-28-days"></a>Intentos de instalación del paquete por aplicación (los últimos 28 días)

Este gráfico de barras visualiza las aplicaciones publicadas y el número de instalaciones correctas frente a erróneas en todos los entornos de producción durante los últimos 28 días.

Al mantener el puntero sobre una aplicación del gráfico, se muestra la siguiente información:

1. Nombre de aplicación
2. Estado de instalación del paquete (correcta frente a errónea)
3. Recuento de los intentos de instalación del paquete

![Intentos de instalación del paquete por aplicación (los últimos 28 días)](media/isv-portal-homepage-graph2.png)

## <a name="additional-insights"></a>Información adicional

Debajo de la sección de resumen el usuario puede tener acceso a ideas adicionales y puede explorar en profundidad el historial de instalación a través de la lente de aplicaciones o usuarios certificados.

**Aplicaciones certificadas principales** e **Inquilinos principales** están visibles en la página de forma predeterminada. El usuario también puede seleccionar **Ver todos** para mostrar todas las aplicaciones.

Los nombres y los iconos de la aplicación proceden de AppSource.

![Todas las aplicaciones](media/isv-portal-homepage-seeall.png)

### <a name="see-also"></a>Vea también

[Introducción a ISV Studio para Power Platform](isv-app-management.md)  
[Página de aplicación](isv-app-management-apppage.md)  
[Página de inquilino](isv-app-management-tenantpage.md)
