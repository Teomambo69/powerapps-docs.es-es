---
title: Mantener soluciones administradas (Common Data Service) | Microsoft Docs
description: ''
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 48f614c7e938dc243ac0780c7387ea91a1926795
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156148"
---
# <a name="maintain-managed-solutions"></a>Mantener soluciones administradas

Antes de lanzar la solución administrada deberá considerar la forma de mantenerla. Desinstalar y reinstalar una solución administrada prácticamente no es una opción cuando la solución contiene entidades o atributos. Esto se debe a que se pierden datos cuando eliminan entidades. Afortunadamente, las soluciones ofrecen un modo de actualizar la solución administrada mientras se mantienen los datos. Exactamente cómo se actualizan sus soluciones dependerá de las características de la solución y los requisitos del cambio.  

<a name="BKMK_VersionCompatibilty"></a>   

## <a name="version-compatibility"></a>Compatibilidad de versiones  
 Cualquier solución exportada desde una versión más reciente de Common Data Service no se puede importar en una versión anterior de Dynamics 365. Esto incluye versiones principales y secundarias. Las soluciones exportadas desde una versión anterior de Dynamics 365 se pueden importar en versiones posteriores como se muestra en el siguiente gráfico.  
  
![Compatibilidad de la versión de la solución](media/crm_v9.0_solution_compatibility_chart.png)
  
 A medida que se aplican paquetes acumulativos de actualizaciones o actualizaciones de servicio adicionales a Common Data Service, las soluciones exportadas de organizaciones con esas actualizaciones no se pueden importar a las organizaciones que no tienen esas actualizaciones. Más información: [Introducción a soluciones](introduction-solutions.md).  
  
 El elemento raíz de `<ImportExportXml>` usa un atributo de `SolutionPackageVersion` para establecer el valor de la versión con la que la solución es compatible. No debería editar manualmente este valor.  
  
<a name="BKMK_CreateManagedSolutionUpdates"></a>   
## <a name="create-managed-solution-updates"></a>Cree actualizaciones de solución administrada  
 Existen dos métodos básicos para actualizar soluciones:  
  
-   Publicación de una nueva versión de la solución administrada  
  
-   Publicación de una actualización de la solución administrada  
  
<a name="BKMK_ReleaseANewVersion"></a>   
### <a name="release-a-new-version-of-your-managed-solution"></a>Publicación de una nueva versión de la solución administrada  
 El método preferido es publicar una nueva versión de la solución administrada. Utilizando la solución de origen no administrada original, puede realizar cambios necesarios y aumentar el número de versión de la solución antes de empaquetarla como una solución administrada. Cuando las organizaciones que usan la solución instalan la nueva versión, las funciones se actualizarán para incluir los cambios. Si desea volver al comportamiento de una versión anterior, simplemente vuelva a instalar la versión anterior. Esta acción sobrescribe todos los componentes de la solución con las definiciones de la versión anterior pero no quita los componentes de la solución agregados en la versión más reciente. Esos componentes de la solución más reciente permanecen en el sistema pero no tiene efecto porque no se usarán las definiciones de componentes de la antigua solución.  
  
 Durante la instalación de una versión anterior de una solución Common Data Service confirmará que la persona que instala la versión anterior desea continuar.  
<a name="BKMK_ReleaseAnUpdate"></a>   
### <a name="release-an-update-for-your-managed-solution"></a>Publicación de una actualización de la solución administrada  
 Cuando solo un pequeño subconjunto de componentes de la solución requieren urgentemente un cambio, puede publicar una actualización para resolver el problema. Para cancelar una actualización, cree una nueva solución no administrada y agregue todos los componentes de la solución de origen no administrada original que desea actualizar. Debe asociar la nueva solución no administrada con el mismo registro del editor que se usó para la solución original. Cuando finalice con los cambios, empaquete la nueva solución como una solución administrada.  
  
 Cuando la solución de actualización se instale en una organización donde se instaló la solución original, los cambios incluidos en la actualización se aplicarán a la organización. Si una organización necesita "volver" a la versión original, puede simplemente desinstalar la actualización.  
  
 Se reemplazarán las personalizaciones aplicadas a los componentes de la solución en la actualización. Volverán cuando desinstale la actualización.  
  
### <a name="see-also"></a>Vea también  
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Publicar la aplicación en AppSource](publish-app-appsource.md)
