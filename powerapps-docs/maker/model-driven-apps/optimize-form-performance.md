---
title: Optimizar el rendimiento de los formularios de aplicaciones controladas por modelos en Power Apps | MicrosoftDocs
description: Aprenda a evitar los diseños de formularios que hacen un formulario se cargue lentamente
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 566a33c267d271618cd31b6225710e2113208350
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285944"
---
# <a name="optimize-model-driven-app-form-performance"></a>Optimizar el rendimiento de los formularios de aplicaciones controladas por modelos

Los formularios que se cargan lentamente pueden reducir la productividad y la adopción por parte del usuario. Siga estas recomendaciones para maximizar la velocidad de carga de los formularios. Muchas de las prácticas recomendadas describen la forma en que un programador puede implementar scripts de formularios para la organización. Asegúrese de discutir estas prácticas recomendadas con los programadores que crean scripts de formularios para los formularios.  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>Diseño de formularios  
 Considere la interacción que el usuario tendrá con el formulario y la cantidad de datos que se deben mostrar en él.  
  
 **Mantenga el número de campos al mínimo**  
 Cuanto más campos tenga en un formulario, más datos deberá transferir a través de Internet o de a una intranet para ver cada registro.
 
 **Diseño para rendimiento**  
 Al diseñar formularios y páginas, coloque lo más importante en la parte superior para que el acceso sea lo más fácil posible para los usuarios. Mueva los componentes utilizados con poca frecuencia a otras pestañas en un formulario, use formularios basados en roles en lugar de mostrar y ocultar componentes, y asegúrese de que los diferentes flujos de trabajo tengan paneles y vistas dedicados. Utilice según desee las secciones para organizar sus controles, esto no hará que sus formularios sean más lentos.
 
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>Scripts de formularios  
 Si tiene personalizaciones que usan scripts de formularios, asegúrese de que el desarrollador comprende estas estrategias para mejorar el rendimiento.  
  
**Evitar el uso de solicitudes sincrónicas**  
Las solicitudes sincrónicas pueden causar lentitud al cargar páginas y hacer que los formularios no respondan. [Utilice solicitudes asincrónicas en su lugar](https://docs.microsoft.com/powerapps/developer/model-driven-apps/best-practices/business-logic/interact-http-https-resources-asynchronously). Consulte esta [entrada de blog](https://powerapps.microsoft.com/en-us/blog/turbocharge-your-model-driven-apps-by-transitioning-away-from-synchronous-requests/) para ver más ejemplos.
  
**Evite incluir bibliotecas de recursos web de JavaScript que no necesite**  
Cuantos más scripts agregue al formulario, más tiempo tardará en descargarlos. Por lo general, los scripts se almacenan en caché en el explorador después de cargarse la primera vez, pero el rendimiento la primera vez que se ve un formulario suele crear una impresión considerable.  
  
**Evite cargar todos los scripts en el evento Onload**  
Si tiene código que únicamente admite los eventos `OnChange` para campos o el evento `OnSave`, asegúrese de definir la biblioteca de scripts con el controlador de eventos para dichos eventos en lugar del evento `OnLoad`. De esta manera, la carga de estas bibliotecas se puede aplazar y aumentar el rendimiento cuando el formulario se carga.  
  
 **Use las fichas contraídas para aplazar la carga de recursos web**  
 Cuando se incluyen recursos web o IFRAMES en secciones en una pestaña contraída, estos no se cargarán si la pestaña está contraída. Se cargarán cuando se expanda la ficha. Cuando el estado de la ficha cambia, se produce el evento `TabStateChange`. Ningún código necesario para admitir recursos web o IFRAMEs en fichas contraídas puede usar controladores de eventos para el evento **TabStateChange** ni reducir código que, de otro modo, debería producirse en el evento `OnLoad`.  
  
**Defina las opciones predeterminadas de visibilidad**  
Evite usar scripts de formularios en el evento `OnLoad` que oculten elementos de formulario. En su lugar, defina las opciones predeterminadas de visibilidad de los elementos de formulario que podrían ocultarse para no ser visibles de forma predeterminada cuando el formulario se carga. A continuación, use los scripts en el evento `OnLoad` para mostrar los elementos de formulario que desee mostrar.  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>Barra de comandos o cinta  
 Tenga en cuenta estas prácticas recomendadas al editar la barra de comandos o la cinta de opciones.  
  
 **Mantenga el número de controles al mínimo**  
 En la barra de comandos o la cinta de opciones del formulario, evalúe qué controles son necesarios y oculte aquellos que no necesite. Cada control que se muestra aumenta los recursos necesarios para descargarse en el explorador.
 
 **Usar solicitudes de red asincrónicas en reglas personalizadas**  
 Al usar reglas personalizadas que realizan solicitudes de red en la Interfaz unificada, [use la evaluación de reglas asincrónicas](https://docs.microsoft.com/powerapps/developer/model-driven-apps/define-ribbon-enable-rules#custom-rule).
  
## <a name="next-steps"></a>Pasos siguientes  
 [Creación y diseño de formularios](create-design-forms.md)    
    
 
