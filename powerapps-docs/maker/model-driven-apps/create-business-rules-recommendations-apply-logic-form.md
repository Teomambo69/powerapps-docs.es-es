---
title: Creación de recomendaciones y reglas de negocio de aplicaciones basadas en modelos | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
caps.latest.revision: 31
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- PowerApps maker portal impact
ms.openlocfilehash: c1a132648a63845c42cde8a80636d0e87e10a328
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39701414"
---
# <a name="tutorial-create-business-rules-and-recommendations-to-apply-logic-in-a-model-driven-app-form"></a>Tutorial: Creación de recomendaciones y reglas de negocio para aplicar lógica en un formulario de aplicación basado en modelos

En este tutorial se muestra cómo crear recomendaciones y reglas de negocio para aplicar lógica de formulario sin escribir código JavaScript ni crear complementos.  Las reglas de negocio proporcionan una interfaz sencilla para implementar y mantener reglas que cambian con rapidez y son de uso frecuente. Se pueden aplicar a formularios principales y de creación rápida, y funcionan en aplicaciones de PowerApps, aplicaciones web de Dynamics 365 Customer Engagement, Dynamics 365 para tabletas y Dynamics 365 para Outlook (modo en línea y sin conexión).  
  
 Al combinar condiciones y acciones, se pueden realizar cualquiera de las siguientes acciones mediante reglas de negocio:  
  
-   Establecer valores de campo  
  
-   Borrar valores de campo  
  
-   Establecer niveles de requisito de campo  
  
-   Mostrar u ocultar campos  
  
-   Habilitar o deshabilitar campos  
  
-   Validar datos y mostrar mensajes de error  
  
-   Crear recomendaciones de negocio basadas en la inteligencia empresarial  
  
## <a name="create-a-business-rule-or-business-recommendation"></a>Crear una regla de negocio o una recomendación de negocio
  
1. Abra el [Explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  Abra la entidad para la que quiera crear la regla de negocio (por ejemplo, abra la entidad **Account**) y, después, haga doble clic en la pestaña **Reglas de negocio**.  
  
 ![Creación de una regla de negocio en la solución predeterminada](media/create-business-rule-the-default-solution.png "Create a business rule in the default solution")  
  
3.  Seleccione **Nueva**.  
  
     Se abre la ventana del Diseñador de reglas de negocio con una única condición ya creada de forma automática. Cada regla se inicia con una condición. La regla de negocio toma una o varias acciones en función de esa condición.  
  
 ![Ventana de diseño de reglas de negocio](media/business-rules-design-window.png "Business Rules design window")  
  
   > [!TIP]
> Si quiere modificar una regla de negocio existente, primero debe desactivarla antes de poder modificarla.

4.  Si quiere, agregue una descripción en el cuadro de descripción en la esquina superior izquierda de la ventana.  
  
5.  Establezca el ámbito, según lo siguiente:  
  
    |||  
    |-|-|  
    |**Si selecciona este elemento...**|**El ámbito se establece en...**|  
    |**Entidad**|Todos los formularios y el servidor|  
    |**Todos los formularios**|Todos los formularios|  
    |Formulario específico (por ejemplo, el formulario **Account**)|Solo ese formulario|  
  
6. **Agregar condiciones.** Para agregar más condiciones a la regla de negocio:  
  
    1.  Arrastre el componente **Condición** desde la pestaña **Componentes** a un signo más en el diseñador.  
  
        ![Agregar una condición en una regla de negocio](media/add-condition-business-rule.png "Add a condition in a business rule")  
  
    2.  Para establecer las propiedades de la condición, haga clic en el componente **Condición** en la ventana del diseñador y, después, establezca las propiedades en la pestaña **Propiedades** en el lado derecho de la pantalla. Al establecer las propiedades, se crea una expresión en la parte inferior de la pestaña **Propiedades**.  
  
    3.  Para agregar una cláusula adicional (OR o AND) a la condición, haga clic en **Nueva** en la pestaña **Propiedades** para crear una regla y, después, establezca las propiedades para esa regla. En el campo **Lógica de la regla**, puede especificar si quiere agregar la regla nueva como condición AND u OR.  
  
        ![Agregar una regla nueva a una condición](media/add-new-rule-condition.png "Add a new rule to a condition")  
  
    4.  Cuando haya terminado de establecer las propiedades de la condición, haga clic en **Aplicar**.  
  
7. **Agregar acciones.** Para agregar una acción:  
  
    1.  Arrastre uno de los componentes de acción desde la pestaña **Componentes** a un signo más junto al componente **Condición**. Arrastre la acción a un signo más junto a una marca de verificación si quiere que la regla de negocio realice esa acción cuando se cumpla la condición, o bien a un signo más junto a una x si quiere que la regla de negocio realice esa acción si no se cumple la condición.  
  
        ![Arrastrar una acción a una regla de negocio](media/drag-an-action-business-rule.png "Drag an action to a business rule")  
  
    2.  Para establecer las propiedades de la acción, haga clic en el componente **Acción** en la ventana del diseñador de componentes y, después, establezca las propiedades en la pestaña **Propiedades**.  
  
    3.  Cuando haya terminado de establecer las propiedades, haga clic en **Aplicar**.  
  
8. **Agregar una recomendación de negocio.** Para agregar una recomendación de negocio:  
  
    1.  Arrastre el componente **Recomendación** desde la pestaña **Componentes** a un signo más junto al componente **Condición**. Arrastre el componente **Recomendación** a un signo más junto a una marca de verificación si quiere que la regla de negocio realice esa acción cuando se cumpla la condición, o bien a un signo más junto a una x si quiere que la regla de negocio realice esa acción si no se cumple la condición.  
  
    2.  Para establecer las propiedades de la recomendación, haga clic en el componente **Recomendación** en la ventana del diseñador y, después, establezca las propiedades en la pestaña **Propiedades**.  
  
    3.  Para agregar más acciones a la recomendación, arrástrelas desde la pestaña **Componentes** y, después, establezca las propiedades de cada acción en la pestaña **Propiedades**.  
  
        > [!NOTE]
        >  Cuando se crea una recomendación, se agrega de forma predeterminada una única acción. Para ver todas las acciones de una recomendación, haga clic en **Detalles** en el componente **Recomendación**.  
  
    4.  Cuando haya terminado de establecer las propiedades, haga clic en **Aplicar**.  
  
9. Para validar la regla de negocio, haga clic en **Validar** en la barra de acciones.  
  
10. Para guardar la regla de negocio, haga clic en **Guardar** en la barra de acciones.  
  
11. Para activar la regla de negocio, selecciónela en la ventana del Explorador de soluciones y, después, haga clic en **Activar**. No se puede activar la regla de negocio desde la ventana del diseñador.  
  
> [!TIP]
>  Estas son algunas sugerencias que hay que tener en cuenta cuando se trabaja con reglas de negocio en la ventana del diseñador:  
>   
> - Para tomar una instantánea de todos los elementos en la ventana Regla de negocio, haga clic en **Instantánea** en la barra de acciones. Esto es útil, por ejemplo, si se quiere compartir la regla de negocio y obtener comentarios sobre ella de un miembro del equipo.  
> - Use el minimapa para desplazarse rápidamente a otras partes del proceso. Esto es útil cuando se tiene un proceso complicado que se desplaza fuera de la pantalla.  
> - Al agregar condiciones, acciones y recomendaciones de negocio a la regla de negocio, el código de la regla de negocio se compila y aparece en la parte inferior de la ventana del diseñador. Este código es de solo lectura.  
  
<a name="BKMK_LocalizingErrorMessages"></a>   
## <a name="localize-error-messages-used-in-business-rules"></a>Localizar los mensajes de error usados en las reglas de negocio  
 Si tiene más de un idioma aprovisionado para la organización, le interesará localizar los mensajes de error que haya configurado. Cada vez que se establece un mensaje, el sistema genera una etiqueta. Si exporta las traducciones de la organización, puede agregar versiones localizadas de los mensajes y después importar esas etiquetas de vuelta al sistema, así los usuarios que usen otros idiomas que no sean el idioma base podrán ver los mensajes traducidos.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear una lógica de negocios personalizada con procesos](guide-staff-through-common-tasks-processes.md)   
 [Crear un flujo de proceso de negocio](/flow/create-business-process-flow)   

