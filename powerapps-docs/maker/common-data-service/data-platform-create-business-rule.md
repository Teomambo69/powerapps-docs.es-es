---
title: Creación de una regla de negocio en Common Data Service for Apps | Microsoft Docs
description: Instrucciones paso a paso sobre cómo crear una regla de negocio en Common Data Service (CDS) for Apps.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
ms.openlocfilehash: 5cf2a312ddba83312805f6b3b517738f1bc1da78
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218036"
---
# <a name="create-a-business-rule"></a>Crear una regla de negocio

Puede crear reglas de negocio y recomendaciones para aplicar lógica y validaciones sin escribir código o crear complementos.  Las reglas de negocio proporcionan una interfaz sencilla para implementar y mantener reglas que cambian con rapidez y son de uso frecuente. 
  
Al combinar condiciones y acciones, se pueden realizar cualquiera de las siguientes acciones mediante reglas de negocio:  
  
* Establecer valores de campo  
* Borrar valores de campo  
* Establecer niveles de requisito de campo  
* Mostrar u ocultar campos  
* Habilitar o deshabilitar campos  
* Validar datos y mostrar mensajes de error  
* Crear recomendaciones de negocio basadas en la inteligencia empresarial  
  
## <a name="differences-between-canvas-and-model-driven-apps"></a>Diferencias entre las aplicaciones de lienzo y las controladas por modelos

Las aplicaciones controladas por modelos pueden usar todas las acciones disponibles en las reglas de negocio, pero en este momento no todas las acciones de regla de negocio están disponibles en las aplicaciones de lienzo. Las acciones siguientes **no** están disponibles en las aplicaciones de lienzo:

* Mostrar u ocultar campos  
* Habilitar o deshabilitar campos  
* Crear recomendaciones de negocio basadas en la inteligencia empresarial  

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tema, debe cambiar a un [entorno](../canvas-apps/working-with-environments.md) en el que se puedan crear y modificar entidades.

## <a name="create-a-business-rule"></a>Crear una regla de negocio
  
1. Inicie sesión en [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) y pulse o haga clic en la flecha hacia abajo para **Datos** cerca del borde izquierdo.

2. En la lista que aparece, pulse o haga clic en **Entidades**.
  
3. Abra la entidad para la que quiera crear la regla de negocio (por ejemplo, abra la entidad **Cuenta**) y, después, haga clic en la pestaña **Reglas de negocio**.  

4. Haga clic en **Nuevo**.  
  
    Se abre la ventana del Diseñador de reglas de negocio con una única condición ya creada de forma automática. Cada regla se inicia con una condición. La regla de negocio toma una o varias acciones en función de esa condición.  

    > [!TIP]
    > Si quiere modificar una regla de negocio existente, primero debe desactivarla antes de poder modificarla.  
  
5. Si quiere, agregue una descripción en el cuadro de descripción en la esquina superior izquierda de la ventana.
  
6. Establezca el ámbito, según lo siguiente:  
  
    |||  
    |-|-|  
    |**Si selecciona este elemento...**|**El ámbito se establece en...**|  
    |**Entidad**|Formularios y servidor controlados por modelos|  
    |**Todos los formularios**|Formularios controlados por modelos|  
    |Formulario específico (por ejemplo, el formulario **Account**)|Solo ese formulario controlado por modelos|  

    > [!TIP]
    > Si va a compilar una aplicación de lienzo, debe usar la entidad como el ámbito.
  
7. **Agregar condiciones.** Para agregar más condiciones a la regla de negocio:  
  
    1. Arrastre el componente **Condición** desde la pestaña **Componentes** a un signo más en el diseñador.  
  
        ![Agregar una condición en una regla de negocio](./media/data-platform-cds-create-business-rule/add-condition-business-rule.png "Add a condition in a business rule")  
  
    2. Para establecer las propiedades de la condición, haga clic en el componente **Condición** en la ventana del diseñador y, después, establezca las propiedades en la pestaña **Propiedades** en el lado derecho de la pantalla. Al establecer las propiedades, Common Data Service crea una expresión en la parte inferior de la pestaña **Propiedades**.  
  
    3. Para agregar una cláusula adicional (OR o AND) a la condición, haga clic en **Nueva** en la pestaña **Propiedades** para crear una regla y, después, establezca las propiedades para esa regla. En el campo **Lógica de la regla**, puede especificar si quiere agregar la regla nueva como condición AND u OR.  
  
        ![Agregar una regla nueva a una condición](./media/data-platform-cds-create-business-rule/add-new-rule-condition.png "Add a new rule to a condition")  
  
    4. Cuando haya terminado de establecer las propiedades de la condición, haga clic en **Aplicar**.  
  
8. **Agregar acciones.** Para agregar una acción:  
  
    1. Arrastre uno de los componentes de acción desde la pestaña **Componentes** a un signo más junto al componente **Condición**. Arrastre la acción a un signo más junto a una marca de verificación si quiere que la regla de negocio realice esa acción cuando se cumpla la condición, o bien a un signo más junto a una x si quiere que la regla de negocio realice esa acción si no se cumple la condición.
  
        ![Arrastrar una acción a una regla de negocio](./media/data-platform-cds-create-business-rule/drag-an-action-business-rule.png "Drag an action to a business rule")  
  
    2. Para establecer las propiedades de la acción, haga clic en el componente **Acción** en la ventana del diseñador de componentes y, después, establezca las propiedades en la pestaña **Propiedades**.  
  
    3. Cuando haya terminado de establecer las propiedades, haga clic en **Aplicar**.  
  
9. **Agregar una recomendación de negocio. (Solo para aplicaciones controladas por modelos)** Para agregar una recomendación de negocio:  
  
    1. Arrastre el componente **Recomendación** desde la pestaña **Componentes** a un signo más junto al componente **Condición**. Arrastre el componente **Recomendación** a un signo más junto a una marca de verificación si quiere que la regla de negocio realice esa acción cuando se cumpla la condición, o bien a un signo más junto a una x si quiere que la regla de negocio realice esa acción si no se cumple la condición.  
  
    2. Para establecer las propiedades de la recomendación, haga clic en el componente **Recomendación** en la ventana del diseñador y, después, establezca las propiedades en la pestaña **Propiedades**.  
  
    3. Para agregar más acciones a la recomendación, arrástrelas desde la pestaña **Componentes** y, después, establezca las propiedades de cada acción en la pestaña **Propiedades**.  
  
        > [!NOTE]
        >  Cuando se crea una recomendación, Common Data Service agrega una única acción de forma predeterminada. Para ver todas las acciones de una recomendación, haga clic en **Detalles** en el componente **Recomendación**.  
  
    4. Cuando haya terminado de establecer las propiedades, haga clic en **Aplicar**.  
  
10. Para validar la regla de negocio, haga clic en **Validar** en la barra de acciones.  
  
11. Para guardar la regla de negocio, haga clic en **Guardar** en la barra de acciones.  
12. Para activar la regla de negocio, selecciónela en la ventana del Explorador de soluciones y, después, haga clic en **Activar**. No se puede activar la regla de negocio desde la ventana del diseñador.  
  
    > [!TIP]
    >  Estas son algunas sugerencias que hay que tener en cuenta cuando se trabaja con reglas de negocio en la ventana del diseñador:  
    >   
    > - Para tomar una instantánea de todos los elementos en la ventana Regla de negocio, haga clic en **Instantánea** en la barra de acciones. Esto es útil, por ejemplo, si se quiere compartir la regla de negocio y obtener comentarios sobre ella de un miembro del equipo.  
    > - Use el minimapa para desplazarse rápidamente a otras partes del proceso. Esto es útil cuando se tiene un proceso complicado que se desplaza fuera de la pantalla.  
    > - Al agregar condiciones, acciones y recomendaciones de negocio a la regla de negocio, Common Data Service genera el código para la regla de negocio en la parte inferior de la ventana del diseñador. Este código es de solo lectura.  
  
## <a name="localize-error-messages-used-in-business-rules"></a>Localizar los mensajes de error usados en las reglas de negocio  
 Si tiene más de un idioma aprovisionado para la organización, le interesará localizar los mensajes de error que haya configurado. Cada vez que se establece un mensaje, el sistema genera una etiqueta. Si exporta las traducciones de la organización, puede agregar versiones localizadas de los mensajes y después importar esas etiquetas a Common Data Service, para que los usuarios que utilicen otros idiomas que no sean el idioma base puedan ver los mensajes traducidos.  
  