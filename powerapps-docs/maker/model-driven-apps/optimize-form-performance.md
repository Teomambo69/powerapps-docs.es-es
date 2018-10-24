---
title: Optimizar el rendimiento de los formularios de aplicaciones basadas en modelos en PowerApps | Microsoft Docs
description: Obtenga información sobre cómo evitar los diseños de formulario que provocan que un formulario se cargue lentamente.
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
ms.openlocfilehash: c9dd764fe565b59e68411dabf453207c4e01a320
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39698766"
---
# <a name="optimize-model-driven-app-form-performance"></a>Optimizar el rendimiento de los formularios de aplicaciones basadas en modelos

Los formularios que se cargan lentamente pueden reducir la productividad y la adopción por parte del usuario. Siga estas recomendaciones para maximizar la velocidad de carga de los formularios. Muchas de estas recomendaciones describen la forma en que un desarrollador puede implementar scripts de formularios para la organización. Asegúrese de tratar estas recomendaciones con los desarrolladores que crean scripts de formularios para los formularios.  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>Diseño de formularios  
 Considere la interacción que el usuario tendrá con el formulario y la cantidad de datos que se deben mostrar en él.  
  
 **Mantener el número de campos al mínimo**  
 Cuanto más campos tenga en un formulario, más datos deberá transferir a través de Internet o de a una intranet para ver cada registro.  
  
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>Scripts de formularios  
 Si tiene personalizaciones que usan scripts de formularios, asegúrese de que el desarrollador comprende estas estrategias para mejorar el rendimiento.  
  
 **Evite incluir bibliotecas de recursos web de JavaScript que no necesite**  
 Cuantos más scripts agregue al formulario, más tiempo tardará en descargarlos. Por lo general, los scripts se almacenan en caché en el explorador después de cargarse la primera vez, pero el rendimiento la primera vez que se ve un formulario suele crear una impresión considerable.  
  
 **Evite cargar todos los scripts en el evento Onload**  
 Si tiene código que únicamente admite los eventos `OnChange` para campos o el evento `OnSave`, asegúrese de definir la biblioteca de scripts con el controlador de eventos para dichos eventos en lugar del evento `OnLoad`. De esta manera, la carga de estas bibliotecas se puede aplazar y aumentar el rendimiento cuando el formulario se carga.  
  
 **Utilice pestañas contraídas para aplazar la carga de recursos web**  
 Cuando se incluyen recursos web o IFRAMES en secciones en una pestaña contraída, estos no se cargarán si la pestaña está contraída. Se cargarán cuando la pestaña está expandida. Cuando el estado de la pestaña cambia, se produce el evento `TabStateChange`. Ningún código necesario para admitir recursos web o IFRAMEs en pestañas contraídas puede usar controladores de eventos para el evento **TabStateChange** ni reducir código que, de otro modo, debería producirse en el evento `OnLoad`.  
  
 **Defina las opciones predeterminadas de visibilidad**  
 Evite usar scripts de formularios en el evento `OnLoad` que oculten elementos de formulario. En su lugar, defina las opciones predeterminadas de visibilidad de los elementos de formulario que podrían ocultarse para no ser visibles de forma predeterminada cuando el formulario se carga. A continuación, utilice los scripts en el evento `OnLoad` para mostrar los elementos de formulario que desee mostrar.  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>Barra de comandos o cinta de opciones  
 Tenga en cuenta estas recomendaciones al editar la barra de comandos o la cinta de opciones.  
  
 **Mantener el número de controles al mínimo**  
 En la barra de comandos o la cinta de opciones del formulario, evalúe qué controles son necesarios y oculte aquellos que no necesite. Cada control que se muestra aumenta los recursos necesarios para descargarse en el explorador.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear y diseñar formularios](create-design-forms.md)    
    
 
