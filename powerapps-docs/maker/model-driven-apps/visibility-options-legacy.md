---
title: Mostrar u ocultar elementos de los formularios de una aplicación controlada por modelos con PowerApps | Microsoft docs
description: Obtenga información sobre cómo mostrar u ocultar elementos de formularios, como pestañas, secciones o campos
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: 7b9e8dc2-229c-455f-ae18-49e8d879ff71
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 86fafe70ae3bc04eff5e85a4baf3682c32427149
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712343"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>Mostrar u ocultar elementos de los formularios de una aplicación controlada por modelos

 Varios tipos de elementos de formularios tienen la opción de mostrarse u ocultarse de manera predeterminada. Tanto pestañas como secciones, campos, iFrames y recursos web proporcionan esta opción. Mediante scripts de formularios o reglas de negocio, es posible controlar la visibilidad de estos elementos para crear un formulario dinámico y proporcionar una interfaz de usuario que se adapta a las condiciones del formulario.  
  
> [!NOTE]
>  Ocultar los elementos de los formularios no es un método recomendado para aplicar la seguridad. Hay varias formas en que los usuarios pueden ver todos los elementos y datos en el formulario cuando los elementos están ocultos. 
  
 En lugar de diseñar formularios que dependen de los scripts para controlar la visibilidad de las opciones, considere si un flujo de proceso de negocio, un cuadro de diálogo o cambiar a otro formulario podría ser más adecuado para satisfacer sus requisitos. Si finalmente usa los scripts, asegúrese de que cualquier elemento que pueda estar oculto lo estará de manera predeterminada. Solo use scripts para mostrarlo cuando la lógica así lo indique. De este modo, no se mostrará en presentaciones que no admitan scripts.  

## <a name="next-steps"></a>Pasos siguientes

[Información general de la interfaz de usuario del editor de formularios](form-editor-user-interface-legacy.md)