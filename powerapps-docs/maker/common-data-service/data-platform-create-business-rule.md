---
title: Crear una regla de negocio en Common Data Service | Microsoft Docs
description: Instrucciones paso a paso para ver cómo crear una regla de negocio en Common Data Service.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-business-rule-for-an-entity"></a>Crear una regla de negocio para una entidad

Puede crear reglas de negocio y recomendaciones para aplicar lógica y validaciones sin escribir código ni crear complementos. Las reglas de negocio proporcionan una interfaz básica para implementar y mantener reglas de rápida evolución y de uso general.

> [!IMPORTANT]
> Las reglas de negocio definidas para una entidad se aplican a las *aplicaciones de lienzo* y las *aplicaciones basadas en modelos* si la entidad se usa en la aplicación. No todas las acciones de reglas de negocio están disponibles en aplicaciones de lienzo en este momento. Más información: [Diferencias entre aplicaciones de lienzo y aplicaciones basadas en modelos](#differences-between-canvas-and-model-driven-apps)<br/><br/>
> Para definir una regla de negocio que se aplique a un formulario en una aplicación basada en modelos, consulte [Crear reglas de negocio para aplicar lógica en un formulario de aplicaciones controladas por modelos](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).

Combinando condiciones y acciones puede realizar cualquiera de las siguientes reglas de negocio:  
  
* Establecer valores de campo  
* Borrar valores de campos  
* Establecer niveles de requisitos de campo  
* Mostrar u ocultar campos  
* Habilitar o deshabilitar campos  
* Validar datos y mostrar mensajes de error  
* Cree recomendaciones de negocio basadas en inteligencia empresarial.  
  
## <a name="differences-between-canvas-and-model-driven-apps"></a>Diferencias entre aplicaciones de lienzo y controladas por modelos

Las aplicaciones controladas por modelos pueden usar todas las acciones disponibles en las reglas de negocio, aunque no todas las acciones de reglas de negocio están disponibles en aplicaciones de lienzo en este momento. Las siguientes acciones **no** están disponible en aplicaciones de lienzo:

* Mostrar u ocultar campos  
* Habilitar o deshabilitar campos  
* Cree recomendaciones de negocio basadas en inteligencia empresarial.  

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tema, debe cambiar a un [entorno](../canvas-apps/working-with-environments.md) en el que pueda crear y editar entidades.

## <a name="create-a-business-rule"></a>Crear una regla de negocio
  
1. Inicie sesión en [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y haga clic o pulse en la flecha hacia abajo para **Datos** cerca del borde izquierdo.

2. En la lista que aparece, haga clic o pulse en **Entidades**.
  
3. Abra la entidad para la que desea crear la regla de negocio (por ejemplo, abra la entidad **Cuenta**) y haga clic en la pestaña **Reglas de negocio**.  

4. Haga clic en **Nuevo**.  
  
    La ventana del diseñador de reglas de negocio se abre con una sola condición ya creada para usted. Cada regla empieza con una condición. La regla de negocio toma una o varias acciones basadas en esa condición.  

    > [!TIP]
    > Si desea modificar una regla de negocio existente, debe desactivarla para poder editarla.  
  
5. Agregue una descripción, si lo desea, en el cuadro de descripción en la esquina superior izquierda de la ventana.
  
6. Establezca el ámbito, según lo siguiente:  
  
    |||  
    |-|-|  
    |**Si selecciona este elemento…**|**El ámbito se establece como...**|  
    |**Entidad**|Formularios controlador por modelos y servidor|  
    |**Todos los formularios**|Formularios controlados por modelos|  
    |Formulario específico (formulario de **Cuenta**, por ejemplo)|Simplemente ese formulario controlado por modelos|  

    > [!TIP]
    > Si está creando una aplicación de lienzo, debe usar la entidad como ámbito.
  
7. **Agregar condiciones.** Para agrega más condiciones a su regla de negocio:  
  
    1. Arrastre el componente **Condición** de la pestaña **Componentes** hasta un signo más en el diseñador.  
  
        ![Agregar una condición a una regla de negocio](./media/data-platform-cds-create-business-rule/add-condition-business-rule.png "Agregar una condición a una regla de negocio")  
  
    2. Para establecer propiedades para la condición, haga clic en el componente **Condición** en la ventana del diseñador y, a continuación establezca las propiedades en la pestaña **Propiedades** a la derecha de la pantalla. A medida establezca propiedades, Common Data Service crea una expresión en la parte inferior de la pestaña **Propiedades**.  
  
    3. Para agregar una cláusula adicional (AND u OR) a la condición, haga clic en **Nuevo** en la pestaña **Propiedades** para crear una nueva regla y, a continuación establezca las propiedades para dicha regla. En el campo **Lógica de la regla** puede especificar si agrega la nueva regla como AND u OR.  
  
        ![Agregar una regla nueva a una condición](./media/data-platform-cds-create-business-rule/add-new-rule-condition.png "Agregar una regla nueva a una condición")  
  
    4. Cuando termine de establecer propiedades para la condición, haga clic en **Aplicar**.  
  
8. **Agregar acciones.** Para agregar una acción:  
  
    1. Arrastre uno de los componentes de acción desde la pestaña **Componentes** hasta un signo más junto al componente **Condición**. Arrastre la acción a un signo más junto a una marca de verificación si desea que la regla de negocio realice esa acción cuando la condición se cumple, o a un signo más junto a una x si desea que la regla de negocio realice esa acción si la condición no se cumple.
  
        ![Arrastrar una acción a una regla de negocio](./media/data-platform-cds-create-business-rule/drag-an-action-business-rule.png "Arrastrar una acción a una regla de negocio")  
  
    2. Para establecer propiedades para la acción, haga clic en el componente **Acción** en la ventana del diseñador y, a continuación establezca las propiedades en la pestaña **Propiedades**.  
  
    3. Cuando termine de establecer propiedades, haga clic en **Aplicar**.  
  
9. **Agregue una recomendación de negocio. (Solo para controlado por modelos)** Para agregar una recomendación de negocio:  
  
    1. Arrastre el componente **Recomendación** desde una pestaña **Componentes** hasta un signo más junto a un componente **Condición**. Arrastre el componente **Recomendación** a un signo más junto a una marca de verificación si desea que la regla de negocio realice esa acción cuando la condición se cumple, o a un signo más junto a una x si desea que la regla de negocio realice esa acción si la condición no se cumple.  
  
    2. Para establecer propiedades para la recomendación, haga clic en el componente **Recomendación** en la ventana del diseñador y, a continuación establezca las propiedades en la pestaña **Propiedades**.  
  
    3. Para agregar más acciones a la recomendación, arrástrelas desde la pestaña **Componentes** y, a continuación establezca propiedades para cada acción en la pestaña **Propiedades**.  
  
        > [!NOTE]
        >  Al crear una recomendación, Common Data Service agrega una sola acción de forma predeterminada. Para ver todas las acciones en una recomendación, haga clic en **Detalles** en el componente **Recomendación**.  
  
    4. Cuando termine de establecer propiedades, haga clic en **Aplicar**.  
  
10. Para validar la regla de negocio, haga clic en **Validar** en la barra de acciones.  
  
11. Para guardar la regla de negocio, haga clic en **Guardar** en la barra de acciones.  
12. Para activar la regla de negocio, selecciónela en la ventana Explorador de soluciones y, a continuación haga clic en **Activar**. No puede activar la regla de negocio desde la ventana del diseñador.  
  
    > [!TIP]
    >  A continuación se proporcionan algunas sugerencias a tener presentes mientras trabaja en reglas de negocio en la ventana del diseñador:  
    >   
    > - Para realizar una instantánea de todo en la ventana Reglas de negocio, haga clic en **Instantánea** en la barra de acciones. Esto es útil, por ejemplo, si desea compartir y obtener comentarios en la regla de negocio de un miembro del equipo.  
    > - Use el minimapa para navegar rápidamente a distintas partes del proceso. Esto es útil cuando tiene un proceso complicado que se desplaza fuera de la pantalla.  
    > - A medida que agregue condiciones, acciones y recomendaciones de negocio a la regla de negocio, Common Data Service crea el código para la regla de negocio en la parte inferior de la ventana del diseñador. Este código es de solo lectura.  
  
## <a name="localize-error-messages-used-in-business-rules"></a>Buscar los mensajes de error que se usan en reglas de negocio  
 Si tiene más de un idioma aprovisionado para su organización, deseará localizar los mensajes de error que haya configurado. Cada vez que se establece un mensaje, el sistema genera la etiqueta. Si exporta las traducciones de su organización, puede agregar versiones localizadas de sus mensajes y luego importar las etiquetas nuevamente en Common Data Service, de modo que los usuarios que utilicen otros idiomas distintos del idioma base puedan ver los mensajes traducidos.  
  
