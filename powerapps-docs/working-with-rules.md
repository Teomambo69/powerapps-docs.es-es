---
title: "Creación de una regla | Microsoft Docs"
description: "Instrucciones detalladas para generar una lógica de aplicaciones mediante la creación de reglas"
services: 
suite: PowerApps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/14/2017
ms.author: karthikb
ms.openlocfilehash: c6b7141c20591c1fdbb5278b1fe4d75bfb6a4ebb
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-rule-in-powerapps"></a>Creación de una regla en PowerApps
Las reglas se crean para modificar automáticamente una aplicación en función de los criterios que se especifiquen. Por ejemplo, mostrar los elementos de cada lista en rojo, amarillo o verde según su estado, o bien mostrar un botón de aprobación sólo a determinados usuarios (por ejemplo, los administradores).

Las reglas se pueden agregar a varios controles. En este tema, agregará una regla para cambiar el color del texto de un control **Etiqueta** si el valor de un control **Control deslizante** es mayor que 70.

## <a name="add-a-rule"></a>Adición de una regla
1. Seleccione un control (o agregue un control y déjelo seleccionado).
   
    En este tema, [agregue una etiqueta y un control deslizante](add-configure-controls.md), establezca la propiedad **Texto** de la etiqueta en **Slider1.Value** y, después, seleccione el control deslizante.
2. En el panel derecho, pulse o haga clic en **Reglas**y, después, en **Nueva regla**.
   
    ![Creación de una regla nueva](./media/working-with-rules/new-rule.png)
   
    Si selecciona un control para el que ya se han definido una o varias reglas, puede editar cualquiera de ellas pulsándola o haciendo clic en ella.  

## <a name="add-a-condition"></a>Adición de una condición
Una condición es una expresión que se evalúa como true o false; por ejemplo, si un valor es mayor que 70. La expresión se puede escribir a partir de una plantilla o empezar desde cero, y se puede personalizar en función de la guía de la interfaz de usuario (Intellisense).

1. Pulse o haga clic en **Agregar una condición**y, después, haga clic en una plantilla o en **Condición personalizada**.
   
    En este tema, pulse o haga clic en **Mayor que**.
   
    ![Agregar una condición](./media/working-with-rules/rule-conditions.png)
2. Finalice la expresión para definir cuándo se aplica la regla.
   
    En este tema, use esta expresión:  <br>**Value(Slider1.Value) > 70**
   
    **Tenga en cuenta**: Cuando se redactó este documento, era preciso especificar la propiedad del control que se utiliza en la comparación. En las versiones futuras, PowerApps podrá inferior las propiedades comunes del control (como **Texto** o **Valor**).

## <a name="add-an-action"></a>Agregar una acción
Las acciones definen lo que sucede cuando se aplica la regla. PowerApps puede crear acciones automáticamente en función de los cambios que se realicen en los controles.

1. Pulse o haga clic en **Definir acciones**.
   
    ![Definir acciones](./media/working-with-rules/rule-define-actions.png)
2. En el cuadro de diálogo de confirmación, pulse o haga clic en **Adelante** para que PowerApps capture el siguiente cambio (o los siguientes) como una o varias acciones.
3. Configure uno o varios controles para que cumplan sus expectativas cuando la condición sea true.
   
    En este tema, cambie el color de la etiqueta.
   
    ![Capturar propiedades](./media/working-with-rules/rule-capture-properties.png)
4. (opcional) Revise los cambios, para lo que debe pulsar o hacer clic en **Mostrar acciones**.
   
    ![Revisar acciones](./media/working-with-rules/rule-review-actions.png)
5. Cuando termine de agregar acciones, pulse o haga clic en **Listo**.
6. Revise la condición y las acciones de la regla y haga clic o pulse **Listo** para guardarlo.
   
    ![Revisar regla](./media/working-with-rules/rule-review.png)

## <a name="test-the-rule"></a>Prueba de la regla
1. Para obtener una vista previa de la aplicación, presione F5 (o haga clic o pulse en el botón de reproducción situado cerca de la esquina superior derecha).
   
    ![Abrir vista previa](./media/working-with-rules/open-preview.png)
2. Cree la condición que especificó como true y, después, confirme que las acciones funcionan como se espera de ellas.
   
    En este tema, establezca el control deslizante en un valor que sea mayor que 70 y confirme que el texto de la etiqueta cambia de color.

## <a name="known-limitations"></a>Limitaciones conocidas
En el momento de redactar este documento:

* No se puede cambiar el nombre de las reglas.
* No se puede especificar la propiedad **ThisItem** de un formulario o una galería como parte de una condición.

