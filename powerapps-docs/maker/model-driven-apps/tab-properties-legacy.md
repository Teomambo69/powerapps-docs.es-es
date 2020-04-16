---
title: Propiedades de pestaña para formularios de aplicaciones controladas por modelos en Power Apps | MicrosoftDocs
description: Comprender las propiedades de pestañas para formularios principales
Keywords: Propiedades de pestaña; Dynamics 365; formularios principales
author: matp
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: Mattp123
manager: kvivek
ms.date: 03/17/2020
ms.service: powerapps
ms.topic: article
ms.assetid: e0790865-c5a4-4e86-bce2-584af2b8ed93
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 613352e9ec86101b776fce5b0bf18d64b175f363
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166550"
---
# <a name="tab-properties-for-model-driven-app-forms-overview"></a>Información general de propiedades de pestaña para formularios de aplicaciones controladas por modelos

 En el cuerpo de un formulario, las pestañas proporcionan separación horizontal. Las pestañas tienen una etiqueta que puede mostrarse. Si se muestra la etiqueta, las pestañas se pueden expandir o contraer para mostrar u ocultar su contenido eligiendo la etiqueta.  
  
 Las pestañas contienen hasta tres columnas y el ancho de cada columna se puede establecer en un porcentaje del ancho total. Al crear una nueva pestaña, cada columna se rellena previamente con una sección.  

Puede acceder a las **Propiedades de pestaña** desde el sitio de Power Apps. 
1.  Inicie sesión en [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).

2.  Expanda **Datos**, seleccione **Entidades**, seleccione la entidad que desee y, a continuación, seleccione la pestaña **Formularios**.  

3.  En la lista de formularios, abra el formulario de tipo **Principal**. A continuación, seleccione una de las pestañas para ver las propiedades de la pestaña.

|Propiedad|Descripción|  
|--------------|-----------------|  
|**Etiqueta de pestaña**|**Requerido**: etiqueta localizable de la pestaña visible para los usuarios.|  
|**Nombre**|**Requerido**: el nombre único de la pestaña que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado.|  
|**Expandir esta ficha de forma predeterminada**|El estado de la ficha puede alternar entre expandida o contraída usando scripts de formulario o cuando los usuarios seleccionan la etiqueta. Elija el estado predeterminado para la pestaña.|  
|**Ocultar pestaña**|Mostrar la pestaña es opcional y se puede controlar mediante scripts. Elija si desea que la pestaña sea visible. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|  
|**Ocultar en teléfono**|Elija si desea que la pestaña esté disponible en el teléfono. Para una versión condensada de este formulario en pantallas de teléfono, puede ocultar la pestaña.|  
|**Formato**|Las pestañas pueden tener hasta tres columnas. Use las opciones para establecer el número de pestañas y qué porcentaje del ancho total deben ocupar.|  

  > [!div class="mx-imgBorder"] 
  > ![pestaña-propiedades](media/newform-tab-properties.png "Propiedades de las pestañas")

## <a name="tab-properties-for-model-driven-app-main-forms-classic"></a>Propiedades de pestaña para formularios principales de aplicaciones controladas por modelos: Clásico

Éstas son las propiedades disponibles para configurar cuando utiliza una pestaña en un formulario usando el diseñador de formularios clásico. La siguiente tabla muestra las propiedades que se pueden definir para las pestañas en el formulario:
  
|Pestaña|Propiedad|Descripción|  
|---------|--------------|-----------------|  
|**Mostrar**|**Nombre**|**Requerido**: el nombre único de la pestaña que se usa al hacerle referencia en los scripts. El nombre solo puede contener caracteres alfanuméricos y de subrayado.|  
||**Etiqueta**|**Requerido**: etiqueta localizable de la pestaña visible para los usuarios.|  
||**Muestra la etiqueta de esta ficha en el formulario**|Cuando se muestra la etiqueta, los usuarios pueden seleccionar en esta para alternar entre expandir o contraer la pestaña. Elija si desea mostrar la etiqueta.|  
||**Expandir esta ficha de forma predeterminada**|El estado de la ficha puede alternar entre expandida o contraída usando scripts de formulario o cuando los usuarios seleccionan la etiqueta. Elija el estado predeterminado para la pestaña.|  
||**Visible de forma predeterminada**|Mostrar la pestaña es opcional y se puede controlar mediante scripts. Elija si desea que la pestaña sea visible. Más información: [Opciones de visibilidad](visibility-options-legacy.md)|  
||**Disponibilidad**|Elija si desea que la pestaña esté disponible en el teléfono.|  
|**Formato**|**Diseño**|Las pestañas pueden tener hasta tres columnas. Use las opciones para establecer el número de pestañas y qué porcentaje del ancho total deben ocupar.|  
|**Eventos**|**Bibliotecas de formularios**|Especifique cualquier recurso web de JavaScript que se usará en el controlador de eventos `TabStateChange` de la pestaña.<br /><br />|  
||**Controladores de eventos**|Configure las funciones de las bibliotecas que deben llamarse para el evento `TabStateChange` de la pestaña. Más información: [Configurar controladores de eventos](configure-event-handlers-legacy.md)|  

  > [!div class="mx-imgBorder"] 
  > ![pestaña-propiedades clásica](media/tab-properties.png "Pestaña propiedades en Clásico")

## <a name="next-steps"></a>Pasos siguientes

[Utilizar el formulario Principal y sus componentes](use-main-form-and-components.md)
