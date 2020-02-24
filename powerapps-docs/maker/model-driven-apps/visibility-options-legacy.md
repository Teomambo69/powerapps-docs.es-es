---
title: Mostrar u ocultar elementos de formularios de aplicaciones controladas por modelos con Power Apps | MicrosoftDocs
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
ms.openlocfilehash: 54a2aeed489cf3e3621bcf21f5f6e0f12b15deff
ms.sourcegitcommit: 2d21c2c65875f97dff6d5843611d4221a4282f22
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2020
ms.locfileid: "3027606"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>Mostrar u ocultar elementos de formularios de aplicaciones controladas por modelos

 Varios tipos de elementos de formulario tienen la opción para mostrarse u ocultarse de forma predeterminada. Todos los recursos web, fichas, secciones, campos e iFrames proporcionan esta opción. Con scripts de formulario o reglas de negocio, la visibilidad de estos elementos se puede controlar para crear un formulario dinámico para proporcionar una interfaz de usuario que se adapte a las condiciones del formulario.  
  
> [!NOTE]
>  Ocultar elementos de formulario no es una forma recomendada para imponer la seguridad. Existen varias formas en que los usuarios pueden ver todos los elementos y datos en el formulario cuando los elementos están ocultos. 
  
 En lugar de diseñar formularios que dependen de scripts para controlar la visibilidad de opciones, piense si flujo de proceso de negocio, un diálogo o el cambio a otro formulario pueden ajustarse mejor a sus requisitos. Si usa scripts, asegúrese de que los elementos que puedan estar ocultos estén ocultos de forma predeterminada. Muéstrelo solo con scripts cuando su lógica lo exija. De esta forma no se mostrará en las presentaciones que no admiten scripts.
 
 > [!NOTE]
> En la Interfaz unificada, para las secciones donde los campos no abarcan más de una columna, al ocultar un campo en la sección se moverá el campo de debajo hacia arriba en el formulario. Si un campo abarca más de dos columnas en una sección, al ocultar un campo en la sección que tiene un control frente a él no se moverá el campo de debajo de él hacia arriba en el formulario. Verá un espacio en blanco adicional donde está el campo oculto en la sección.

## <a name="next-steps"></a>Pasos siguientes

[Información general de la interfaz del editor de formularios](form-editor-user-interface-legacy.md)
