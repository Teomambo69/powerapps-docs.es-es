---
title: Cambio de la navegación dentro de un formulario de aplicación basada en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo cambiar la navegación dentro de un formulario.
ms.custom: ''
ms.date: 06/06/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 4c379202-9f0e-4003-a49c-efff53e7f79f
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 5a8156875f669854a4ba4649e50a23e340f3ceff
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698149"
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>Cambio de la navegación dentro de un formulario de aplicación basada en modelos

 La navegación dentro de un formulario permite a los usuarios de aplicaciones ver listas de registros relacionados. Cada relación de entidad tiene propiedades para controlar si debe mostrarse. Más información: [Elemento del panel de navegación para la entidad principal](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)  
  
 En el editor de formularios, se pueden invalidar las relaciones de entidad que están configuradas para mostrarse. También puede incluir vínculos de navegación para mostrar recursos de web u otros sitios web mediante la navegación del formulario.  
  
 Para obtener instrucciones detalladas, vea [Creación y edición de relaciones de entidad de Common Data Service para aplicaciones](../common-data-service/create-edit-entity-relationships.md).  
  
 Para habilitar la edición de la navegación, primero debe seleccionar **Navegación** en el grupo **Seleccionar** de la pestaña **Inicio** del diseñador de formularios.  
 
 ![Comando de navegación](media/navigation-command.png)
 
 En el panel derecho del **Explorador de soluciones**, puede filtrar por relaciones 1: n (uno a varios) o N:N (varios a varios) o ver todas las relaciones disponibles. La casilla **Mostrar solo las relaciones no utilizadas** está deshabilitada y seleccionada. Por tanto, solo puede agregar cada relación una sola vez.  
  
 ![Explorador de relaciones](media/relationship-explorer.png)

 Para agregar una relación desde el **Explorador de relaciones**, simplemente haga doble clic en la relación y se agregará a continuación de la relación seleccionada actualmente en el área de navegación. Haga doble clic en una relación en el área de navegación y puede cambiar la etiqueta en la pestaña **Mostrar**. En la pestaña **Nombre**, puede ver información sobre la relación. Use el botón **Editar** para abrir la definición de la entidad.  
  
 Hay cinco grupos en el área de navegación. Puede arrastrarlos para cambiar la posición y hacer doble clic en ellos para cambiar la etiqueta, pero no podrá eliminarlos. Estos grupos solo se mostrarán cuando hay algo en ellos. Por tanto, si no desea que un grupo aparezca, no agregue nada a él.  
  
 Use el botón **Vínculo de navegación** situado en el grupo **Control** de la pestaña **Insertar** para agregar un vínculo a un recurso web o a una dirección URL externa.  
 
 ![Vínculo de navegación](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>Propiedades del vínculo de navegación  
 Los vínculos de navegación tienen las siguientes propiedades:  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Nombre|**Requerido**: texto para mostrar como una etiqueta.|  
|Icono|Use un recurso web de 32 x 32 píxeles. Se recomienda usar una imagen PNG con un fondo transparente.|  
|Recurso web|Especifique un recurso web para mostrar en el panel principal del formulario.|  
|Dirección URL externa|Especifique una dirección URL de una página para mostrar en el panel principal del formulario.|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>Avisos de privacidad  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>Pasos siguientes

[Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md)