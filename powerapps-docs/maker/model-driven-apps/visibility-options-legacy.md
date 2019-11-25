---
title: Mostrar u ocultar elementos de formularios de aplicaciones controladas por modelos con PowerApps | MicrosoftDocs
description: Aprenda cómo mostrar u ocultar elementos, como pestañas, secciones o campos
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: 7b9e8dc2-229c-455f-ae18-49e8d879ff71
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6004aab267da345dc1681dd920913e7858986d9d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710263"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>Mostrar u ocultar elementos de formularios de aplicaciones controladas por modelos

 Varios tipos de elementos de formulario tienen la opción para mostrarse u ocultarse de forma predeterminada. Todos los recursos web, fichas, secciones, campos e iFrames proporcionan esta opción. Con scripts de formulario o reglas de negocio, la visibilidad de estos elementos se puede controlar para crear un formulario dinámico para proporcionar una interfaz de usuario que se adapte a las condiciones del formulario.  
  
> [!NOTE]
>  Ocultar elementos de formulario no es una forma recomendada para imponer la seguridad. Existen varias formas en que los usuarios pueden ver todos los elementos y datos en el formulario cuando los elementos están ocultos. 
  
 En lugar de diseñar formularios que dependen de scripts para controlar la visibilidad de opciones, piense si flujo de proceso de negocio, un diálogo o el cambio a otro formulario pueden ajustarse mejor a sus requisitos. Si usa scripts, asegúrese de que los elementos que puedan estar ocultos estén ocultos de forma predeterminada. Muéstrelo solo con scripts cuando su lógica lo exija. De esta forma no se mostrará en las presentaciones que no admiten scripts.  

## <a name="next-steps"></a>Pasos siguientes

[Información general de la interfaz del editor de formularios](form-editor-user-interface-legacy.md)
