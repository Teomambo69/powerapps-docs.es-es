---
title: Cambiar la navegación en un formulario de aplicación controlada por modelos en PowerApps | MicrosoftDocs
description: Aprenda cómo cambiar la navegación en un formulario
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>Cambiar la navegación en un formulario de aplicación controlada por modelos

 La navegación en un formulario permite que los usuarios de la aplicación vean listas de registros relacionados. Cada relación de entidad tiene propiedades para controlar si se debe mostrar. Más información: [Elemento del panel de navegación para una entidad principal](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)  
  
 Las relaciones de entidad configuradas para mostrarse se pueden reemplazar en el editor de formularios. También puede incluir vínculos de navegación para mostrar recursos web u otros sitios web mediante la navegación del formulario.  
  
 Para obtener instrucciones paso a paso, consulte [Crear y editar relaciones de entidad para Common Data Service for Apps](../common-data-service/create-edit-entity-relationships.md)  
  
 Para habilitar la edición de la navegación debe seleccionar primero **Navegación** en el grupo **Seleccionar** de la pestaña **Inicio** del diseñador de formularios.  
 
> [!div class="mx-imgBorder"] 
> ![Comando de navegación](media/navigation-command.png)
 
 En el panel derecho, en **Explorador de relaciones** puede filtrar por las relaciones 1:N (uno a varios) o N:N (varios a varios), o ver todas las relaciones disponibles. La opción **Mostrar únicamente la casilla de verificación sin usar de relaciones** está deshabilitada y seleccionada. Cada una de las relaciones se puede agregar una vez.  
 
 > [!div class="mx-imgBorder"] 
 > ![Explorador de relaciones](media/relationship-explorer.png)

 Para agregar una relación desde el **Explorador de relaciones** haga doble clic en la relación y se agregará debajo de la relación actualmente seleccionada en el área de navegación. Haga doble clic en una relación en el área de navegación y podrá cambiar la etiqueta en la pestaña **Visualización**. Asimismo, en la pestaña **Nombre**, puede obtener información sobre la relación. Use el botón **Editar** para abrir la definición de la entidad.  
  
 Hay cinco grupos en el área de navegación. Puede arrastrarlos para cambiar su ubicación y hacer doble clic encima para cambiar la etiqueta, pero no puede quitarlos. Estos grupos solo se mostrarán cuando contengan algo. Si no desea que un grupo aparezca, no le agregue ningún elemento.  
  
 Use el botón **Vínculo de navegación** en el grupo **Control** de la ficha **Insertar** para agregar un vínculo a un recurso web o una dirección URL externa.  
 
 ![Vínculo de navegación](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>Propiedades de los vínculos de navegación  
 Los vínculos de navegación tienen las siguientes propiedades:  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Nombre|**Requerido**: texto que se muestra como una etiqueta.|  
|Icono|Use un recurso web de 32 x 32 píxeles. Se recomienda usar una imagen PNG con un fondo transparente.|  
|Recurso web|Especifique un recurso web para mostrar en el panel principal del formulario.|  
|Dirección URL externa|Especifique la dirección URL de una página para mostrar en el panel principal del formulario.|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>Avisos de privacidad  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>Pasos siguientes

[Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md)
