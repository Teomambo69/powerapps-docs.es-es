---
title: Crear reglas de negocio y recomendaciones de aplicaciones controladas por modelos | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="tutorial-create-business-rules-and-recommendations-to-apply-logic-in-a-model-driven-app-form"></a>Tutorial: Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario de aplicaciones controladas por modelos

En este tutorial se muestra cómo crear reglas de negocio y recomendaciones para aplicar lógica del formulario en una aplicación basada en modelos sin escribir código de JavaScript ni crear complementos. Las reglas de negocio proporcionan una interfaz básica para implementar y mantener reglas de rápida evolución y de uso general. Se pueden aplicar a formularios principales y de creación rápida y funcionan en aplicaciones basadas en modelos, aplicaciones web de Dynamics 365 Customer Engagement, Dynamics 365 for tablets y Dynamics 365 for Outlook (en modo en línea o fuera de línea).

> [!NOTE]
> Para definir una regla de negocio para una entidad para que se aplique a todos los formularios y servidores, consulte [Crear una reglas de negocio para una entidad](/powerapps/maker/common-data-service/data-platform-create-business-rule).
  
 Combinando condiciones y acciones puede realizar cualquiera de las siguientes reglas de negocio:  
  
-   Establecer valores de campo  
  
-   Borrar valores de campos  
  
-   Establecer niveles de requisitos de campo  
  
-   Mostrar u ocultar campos  
  
-   Habilitar o deshabilitar campos  
  
-   Validar datos y mostrar mensajes de error  
  
-   Cree recomendaciones de negocio basadas en inteligencia empresarial.  
  
## <a name="create-a-business-rule-or-business-recommendation"></a>Crear reglas de negocio o recomendaciones de negocio
  
1. Abra el [explorador de soluciones](advanced-navigation.md#solution-explorer).  
  
2.  Abra la entidad para la que desea crear reglas de negocio (por ejemplo, abra la entidad **Cuenta**), y haga doble clic en **Reglas de negocio**.  
  
 ![Crear reglas de negocio en la solución predeterminada](media/create-business-rule-the-default-solution.png "Crear reglas de negocio en la solución predeterminada")  
  
3.  Seleccione **Nuevo**.  
  
     La ventana del diseñador de reglas de negocio se abre con una sola condición ya creada para usted. Cada regla empieza con una condición. La regla de negocio toma una o varias acciones basadas en esa condición.  
  
 ![Venta del diseñador de reglas de negocio](media/business-rules-design-window.png "Venta del diseñador de reglas de negocio")  
  
   > [!TIP]
> Si desea modificar una regla de negocio existente, debe desactivarla para poder editarla.

4.  Agregue una descripción, si lo desea, en el cuadro de descripción en la esquina superior izquierda de la ventana.  
  
5.  Establezca el ámbito, según lo siguiente:  
  
    |||  
    |-|-|  
    |**Si selecciona este elemento…**|**El ámbito se establece como...**|  
    |**Entidad**|Todos los formularios y el servidor|  
    |**Todos los formularios**|Todos los formularios|  
    |Formulario específico (formulario de **Cuenta**, por ejemplo)|Sólo ese formulario|  
  
6. **Agregar condiciones.** Para agrega más condiciones a su regla de negocio:  
  
    1.  Arrastre el componente **Condición** de la pestaña **Componentes** hasta un signo más en el diseñador.  
  
        ![Agregar una condición a una regla de negocio](media/add-condition-business-rule.png "Agregar una condición a una regla de negocio")  
  
    2.  Para establecer propiedades para la condición, haga clic en el componente **Condición** en la ventana del diseñador y, a continuación establezca las propiedades en la pestaña **Propiedades** a la derecha de la pantalla. A medida establezca propiedades, se crea una expresión en la parte inferior de la pestaña **Propiedades**.  
  
    3.  Para agregar una cláusula adicional (AND u OR) a la condición, haga clic en **Nuevo** en la pestaña **Propiedades** para crear una nueva regla y, a continuación establezca las propiedades para dicha regla. En el campo **Lógica de la regla** puede especificar si agrega la nueva regla como AND u OR.  
  
        ![Agregar una regla nueva a una condición](media/add-new-rule-condition.png "Agregar una regla nueva a una condición")  
  
    4.  Cuando termine de establecer propiedades para la condición, haga clic en **Aplicar**.  
  
7. **Agregar acciones.** Para agregar una acción:  
  
    1.  Arrastre uno de los componentes de acción desde la pestaña **Componentes** hasta un signo más junto al componente **Condición**. Arrastre la acción a un signo más junto a una marca de verificación si desea que la regla de negocio realice esa acción cuando la condición se cumple, o a un signo más junto a una x si desea que la regla de negocio realice esa acción si la condición no se cumple.  
  
        ![Arrastrar una acción a una regla de negocio](media/drag-an-action-business-rule.png "Arrastrar una acción a una regla de negocio")  
  
    2.  Para establecer propiedades para la acción, haga clic en el componente **Acción** en la ventana del diseñador y, a continuación establezca las propiedades en la pestaña **Propiedades**.  
  
    3.  Cuando termine de establecer propiedades, haga clic en **Aplicar**.  
  
8. **Agregar una recomendación de negocio.** Para agregar una recomendación de negocio:  
  
    1.  Arrastre el componente **Recomendación** desde una pestaña **Componentes** hasta un signo más junto a un componente **Condición**. Arrastre el componente **Recomendación** a un signo más junto a una marca de verificación si desea que la regla de negocio realice esa acción cuando la condición se cumple, o a un signo más junto a una x si desea que la regla de negocio realice esa acción si la condición no se cumple.  
  
    2.  Para establecer propiedades para la recomendación, haga clic en el componente **Recomendación** en la ventana del diseñador y, a continuación establezca las propiedades en la pestaña **Propiedades**.  
  
    3.  Para agregar más acciones a la recomendación, arrástrelas desde la pestaña **Componentes** y, a continuación establezca propiedades para cada acción en la pestaña **Propiedades**.  
  
        > [!NOTE]
        >  Al crear una recomendación, se agrega una sola acción de forma predeterminada. Para ver todas las acciones en una recomendación, haga clic en **Detalles** en el componente **Recomendación**.  
  
    4.  Cuando termine de establecer propiedades, haga clic en **Aplicar**.  
  
9. Para validar la regla de negocio, haga clic en **Validar** en la barra de acciones.  
  
10. Para guardar la regla de negocio, haga clic en **Guardar** en la barra de acciones.  
  
11. Para activar la regla de negocio, selecciónela en la ventana Explorador de soluciones y, a continuación haga clic en **Activar**. No puede activar la regla de negocio desde la ventana del diseñador.  
  
> [!TIP]
>  A continuación se proporcionan algunas sugerencias a tener presentes mientras trabaja en reglas de negocio en la ventana del diseñador:  
>   
> - Para realizar una instantánea de todo en la ventana Reglas de negocio, haga clic en **Instantánea** en la barra de acciones. Esto es útil, por ejemplo, si desea compartir y obtener comentarios en la regla de negocio de un miembro del equipo.  
> - Use el minimapa para navegar rápidamente a distintas partes del proceso. Esto es útil cuando tiene un proceso complicado que se desplaza fuera de la pantalla.  
> - A medida que agregue condiciones, acciones, y recomendaciones de negocio a la regla de negocio, se crea el código para la regla de negocio y aparece en la parte inferior de la ventana del diseñador. Este código es de solo lectura.  
  
<a name="BKMK_LocalizingErrorMessages"></a>   
## <a name="localize-error-messages-used-in-business-rules"></a>Buscar los mensajes de error que se usan en reglas de negocio  
 Si tiene más de un idioma aprovisionado para su organización, deseará localizar los mensajes de error que haya configurado. Cada vez que se establece un mensaje, el sistema genera la etiqueta. Si exporta las traducciones de su organización, puede agregar versiones localizadas de sus mensajes y luego importar las etiquetas nuevamente en el sistema, de modo que los usuarios que utilicen otros idiomas distintos del idioma base puedan ver los mensajes traducidos.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Crear una lógica de negocios personalizada con procesos](guide-staff-through-common-tasks-processes.md)   
 [Crear un flujo de proceso de negocio](/flow/create-business-process-flow)   

