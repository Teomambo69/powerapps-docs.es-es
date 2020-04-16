---
title: Usar una solución para personalizar Power Apps | MicrosoftDocs
description: Aprenda cómo personalizar Power Apps
ms.custom: ''
ms.date: 02/20/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: f993c4ed-1fc3-4e47-bef1-d38695ddb11a
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e32920e3a3ae2bd3c65bfaae6da4b875d4dff645
ms.sourcegitcommit: 3e6c499a65ada8a9f28022a02f64030b0c069a17
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2020
ms.locfileid: "3226445"
---
# <a name="use-a-solution-to-customize"></a>Use una solución para personalizar
Se recomienda crear una solución para administrar sus personalizaciones. Con una solución personalizada, puede encontrar fácilmente los componentes de la solución que ha personalizado, aplicar consistentemente su prefijo editor de soluciones y exportar su solución para distribuirla a otros entornos.  

Si no utiliza una solución personalizada, estará trabajando en una solución predeterminada en la capa no administrada. Hay dos soluciones predeterminadas en cada entorno de Common Data Service:  
- Solución predeterminada de Common Data Service. Se trata de una solución base que está disponible para los creadores para que la usen como solución predeterminada para sus personalizaciones en un entorno. La solución predeterminada de Common Data Service es útil cuando desea evaluar o aprender Power Apps.  
- Solución predeterminada. Es un solución especial que contiene todos los componentes en el sistema. La solución predeterminada es útil para descubrir todos los componentes y configuraciones en su sistema.  

## <a name="why-you-shouldnt-use-the-default-solutions-to-manage-customizations"></a>¿Por qué no debería usar la solución predeterminada para administrar las personalizaciones?
Hay algunas razones por las que no debe crear aplicaciones y realizar personalizaciones en cualquiera de las soluciones predeterminadas:  
- La solución predeterminada contiene todos los componentes y personalizaciones de todas las soluciones en el entorno. 
- De forma predeterminada, todos los usuarios habilitados en un entorno pueden crear aplicaciones y personalizar componentes en la solución predeterminada de Common Data Services. 
- Es difícil localizar o identificar las personalizaciones que ha realizado en el entorno utilizando cualquier solución predeterminada. 
- Al usar cualquier solución predeterminada, al crear componentes también se usará el editor predeterminado asignado. Esto puede provocar que se aplique el prefijo de editor incorrecto a algunos componentes. 
- La solución predeterminada no se puede exportar. Por lo tanto, no puede distribuir la solución predeterminada a otro entorno. 

<!-- Notice that if you have installed or imported other applications or solutions, additional solutions may be available in the solutions list. 

By default,  when you build or customize a model-driven app, you work with the solution called Common Data Services Default Solution. You can open the Common Data Services Default Solution to view and edit the components that are contained in it. To do this, follow these steps.
 
1.  On the left navigation pane select **Solutions**.

2.  In the list of solutions, select **Common Data Services Default Solution**.
  
> [!TIP]
>  If you plan to distribute the applications your make, consider changing the publisher customization prefix. More information: [Solution publisher prefix](change-solution-publisher-prefix.md).  -->
  
<a name="BKMK_PrivacyNotice"></a>   

## <a name="privacy-notices"></a>Avisos de privacidad  
 [!INCLUDE[cc_privacy_crm_gcc_solution_import](../../includes/cc-privacy-crm-gcc-solution-import.md)]  
  
 [!INCLUDE[cc_privacy_crm_customizations](../../includes/cc-privacy-crm-customizations.md)]  
  
### <a name="see-also"></a>Vea también  
[Crear una solución](create-solution.md) <br />
[Conocer los componentes de las aplicaciones basadas en modelos](../model-driven-apps/model-driven-app-components.md)


