---
ms.openlocfilehash: 41ec7aed42a950e5adf0b87783fc568dbe9d02af
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61588440"
---
Al habilitar la inserción de iconos y paneles de Power BI, cuando un usuario inserta un icono o un panel de Power BI, el token de autorización de [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] de ese usuario para [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] se usa para autenticarse con el servicio Power BI con una concesión implícita, lo que proporciona una experiencia de "inicio de sesión único" integral para el usuario final.  
  
 Un administrador puede deshabilitar la inserción de iconos y paneles de Power BI en cualquier momento para detener el uso del token de autorización de [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] para la autenticación con el servicio Power BI. Los iconos o paneles existentes dejarán de representarse para el usuario final.  
  
 En la siguiente sección se detalla el componente o servicio de [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] que interviene en la inserción de iconos de Power BI.  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 Este servicio proporciona el token de autenticación intercambiado con el servicio Power BI para la autenticación de la API y la interfaz de usuario.