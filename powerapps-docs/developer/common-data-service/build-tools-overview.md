---
title: Información general sobre herramientas de compilación para Azure DevOps| Microsoft Docs
description: Power Apps build tools son una colección de tareas de compilación de Azure DevOps específicas de Power Apps que eliminan la necesidad de descargar manualmente los scripts para administrar el desarrollo de Power Apps
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mikkelsen2000
ms.author: pemikkel
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8909a11491a068dd623cc911887418ff49f37151
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341227"
---
# <a name="power-apps-build-tools-for-azure-devops-overview"></a>Información general sobre Power Apps build tools para Azure DevOps


[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Utilice Power Apps build tools para automatizar tareas comunes de compilación y de implementación relacionadas con Power Apps. Esto incluye la sincronización de los metadatos de la solución (es decir, las soluciones) entre entornos de desarrollo y control de origen, generar artefactos de compilación, implementar en entornos descendentes, aprovisionamiento o desaprovisionamiento de entornos, y la capacidad de realizar comprobaciones de análisis estático con la solución utilizando el servicio del comprobador de Power Apps.

> [!IMPORTANT]
>
> - Power Apps build tools son una característica de vista previa.
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

Para obtener más información sobre el uso de las herramientas de compilación con la administración del ciclo de vida de las aplicaciones, vea [Power Apps build tools para Azure DevOps](/power-platform/alm/devops-build-tools).
  
## <a name="what-are-power-apps-build-tools"></a>¿Qué son Power Apps build tools?

Power Apps build tools son una colección de tareas de compilación de Azure DevOps específicas de Power Apps que eliminan la necesidad de descargar manualmente las herramientas y los scripts personalizados para administrar el ciclo de vida de la aplicación de Power Apps. Las tareas pueden usarse individualmente para realizar una tarea simple, como importar una solución en un entorno descendente, o usarse juntas en una canalización para coordinar un escenario, como “Genera artefacto de compilación”, “Implementa para probar“ o “Recoger cambios del creador”. Las tareas de compilación se pueden clasificar en general en cuatro tipos:

- Ayuda 
- Comprobación de calidad 
- Solución 
- Administración de entornos 

## <a name="get-the-power-apps-build-tools"></a>Obtener Power Apps build tools 
Power Apps build tools se pueden instalar en la organización de Azure DevOps desde el [Azure Marketplace](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerApps-BuildTools). Una vez instaladas, todas las taras incluidas en Power Apps build tools estarán disponibles para agregar en cualquier canalización nueva o existente y son fáciles de encontrar buscando **PowerApps**.

![Obtener herramientas de compilación](media/build-tools-download.png)
 
## <a name="next-step"></a>Paso siguiente

[Tareas de herramientas de compilación](build-tools-tasks.md)
