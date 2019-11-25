---
title: Privilegios necesarios para personalizar aplicaciones controladas por modelos | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 43cf7f3a-7e26-4990-8b5a-c817ac6d51bb
caps.latest.revision: 13
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2dd56a541ab765bc990bba8fe7911d193b3eacc7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711539"
---
# <a name="privileges-required-for-model-driven-app-customization"></a>Privilegios necesarios para la personalización de aplicaciones controladas por modelos

Los usuarios de la aplicación pueden personalizar el sistema e incluso compartir algunas de las personalizaciones con otros usuarios, pero solo los usuarios con los privilegios adecuados pueden aplicar los cambios para todos.  
  
> [!NOTE]
>  En esta sección se supone que sabe cómo trabajar con roles de seguridad. Para obtener más información acerca de cómo trabajar con roles de seguridad, consulte [Crear usuarios y asignar roles de seguridad](https://docs.microsoft.com/dynamics365/customer-engagement/admin/create-users-assign-online-security-roles).  
  
<a name="BKMK_SysAdminAndSysCustomizer"></a>   
## <a name="system-administrator-and-system-customizer-security-roles"></a>Roles de seguridad Administrador del sistema y Personalizador del sistema  
 Cualquiera que personalice tendrá el rol de seguridad de administrador o personalizador del sistema asociados a su cuenta. Estos roles de seguridad proporcionan los permisos que necesita personalizar la implementación de la aplicación.  
  
|Administrador del sistema|Personalizador del sistema|  
|--------------------------|-----------------------|  
|Tiene privilegios completos para personalizar el sistema|Tiene privilegios completos para personalizar el sistema|  
|Puede ver todos los datos del sistema|Solo puede ver los registros de las entidades del sistema que cree|  
  
 La diferencia entre los roles de seguridad de administrador del sistema y de personalizador del sistema es que un administrador del sistema tiene privilegios de lectura para la mayoría de los registros del sistema y puede verlo todo. Asigne el rol de personalizador del sistema a alguien que necesite realizar tareas de personalización, pero que no debería ver ningún dato de las entidades del sistema. Sin embargo, las pruebas son una parte importante de la personalización del sistema. Si los personalizadores del sistema no pueden ver datos, deberán crear registros para probar sus personalizaciones. De forma predeterminada, los personalizadores del sistema tienen acceso completo a entidades personalizadas. Si desea tener las mismas limitaciones que existen para entidades del sistema, necesitará ajustar el rol de seguridad de personalizador del sistema para que el nivel de acceso sea **Usuario** en lugar de **Organización** para entidades personalizadas.  
  
<a name="BKMK_DelegatingCustomizationTasks"></a>   
## <a name="delegate-customization-tasks"></a>Delegar tareas de personalización  
 Es posible que desee delegar algunas tareas a usuarios de confianza para que puedan aplicar los cambios que necesitan. Tenga en cuenta que cualquier persona puede tener varios roles de seguridad asociados a su cuenta de usuario, y que los privilegios y derechos de acceso concedidos por los roles de seguridad se basan en el nivel de permisos *menos restrictivo*.  
  
 Esto significa que puede conceder el rol de seguridad Personalizador del sistema a alguien que ya tenga otro rol de seguridad; por ejemplo, un jefe de ventas. Esto le permite personalizar el sistema además de otros privilegios que ya tenga. No necesita modificar el rol de seguridad que ya tiene y puede quitar el rol de seguridad de personalizador del sistema de la cuenta de usuario de la persona cuando desee.  
  
<a name="BKMK_UsingTwoUserAccounts"></a>   
## <a name="test-customizations-without-customization-privileges"></a>Probar personalizaciones sin privilegios de personalización  
 Siempre debe probar las personalizaciones que haya creado con una cuenta de usuario que no tenga privilegios de personalización. De esta manera puede asegurarse de que las personas sin los roles de seguridad de administrador o personalizador del sistema podrán usar las personalizaciones. Para hacerlo de manera efectiva necesita acceso a dos cuentas de usuario: una cuenta con el rol de seguridad de administrador del sistema y otra con roles de seguridad que representen a los usuarios que utilizarán las personalizaciones.  
  
> [!IMPORTANT]
>  No intente eliminar su rol de seguridad de administrador del sistema si solo tiene una cuenta de usuario. El sistema le advertirá si lo intenta, pero si continúa, es posible que no pueda recuperarlo. La mayoría de los roles de seguridad no permiten modificar los roles de seguridad de un usuario.  
  
## <a name="next-steps"></a>Pasos siguientes  
[Conocer los componentes de las aplicaciones basadas en modelos](model-driven-app-components.md)

