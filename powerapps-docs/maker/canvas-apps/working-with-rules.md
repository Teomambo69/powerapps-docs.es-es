---
title: Creación de una regla | Microsoft Docs
description: Instrucciones detalladas para generar una lógica de aplicaciones mediante la creación de reglas
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 52deddf87a1c3ee4604591110cfb08eb2d2680b8
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74672988"
---
# <a name="create-a-rule-in-canvas-apps"></a>Creación de una regla en aplicaciones de lienzo
Las reglas se crean para modificar automáticamente una aplicación en función de los criterios que se especifiquen. Por ejemplo, mostrar los elementos de cada lista en rojo, amarillo o verde según su estado, o bien mostrar un botón de aprobación sólo a determinados usuarios (por ejemplo, los administradores). Las reglas se pueden agregar a varios controles. En este tema, agregará una regla para cambiar el color del texto de un control **Etiqueta** si el valor de un control **Control deslizante** es mayor que 70.

> [!IMPORTANT]
> A partir del 14 de octubre de 2019, la característica reglas de las aplicaciones de canvas está en desuso. Más información: [blog: las reglas de lienzo](https://powerapps.microsoft.com/blog/canvas-rules-feature-deprecation/)están en desuso.

## <a name="add-a-rule"></a>Adición de una regla
1. Seleccione un control (o agregue un control y déjelo seleccionado).

    En este tema, [agregue una etiqueta y un control deslizante](add-configure-controls.md), establezca la propiedad **Texto** de la etiqueta en **Slider1.Value** y, después, seleccione el control deslizante.

1. En el panel derecho, pulse o haga clic en **Reglas**y, después, en **Nueva regla**.

    ![Creación de una regla nueva](./media/working-with-rules/new-rule.png)

    Si selecciona un control para el que ya se han definido una o varias reglas, puede editar cualquiera de ellas pulsándola o haciendo clic en ella.  

## <a name="add-a-condition"></a>Adición de una condición
Una condición es una expresión que se evalúa como true o false; por ejemplo, si un valor es mayor que 70. La expresión se puede escribir a partir de una plantilla o empezar desde cero, y se puede personalizar en función de la guía de la interfaz de usuario (Intellisense).

1. Pulse o haga clic en **Agregar una condición**y, después, haga clic en una plantilla o en **Condición personalizada**.

    En este tema, pulse o haga clic en **Mayor que**.

    ![Agregar una condición](./media/working-with-rules/rule-conditions.png)

1. Actualice la expresión para definir cuándo se aplica la regla.

    Para este tema, cambie 0 por 70 para obtener esta expresión: <br>**Slider1.Value > 70**

## <a name="add-an-action"></a>Agregar una acción
Las acciones definen lo que sucede cuando se aplica la regla. Power apps puede crear acciones automáticamente en función de los cambios que realice en los controles.

1. Pulse o haga clic en **Definir acciones**.

    ![Definir acciones](./media/working-with-rules/rule-define-actions.png)

1. En el cuadro de diálogo de confirmación, pulse o haga clic en **ir** a para que Power apps Capture el siguiente cambio o cambie como una o varias acciones.

1. Configure uno o varios controles para que cumplan sus expectativas cuando la condición sea true.

    En este tema, cambie el color de la etiqueta.

    ![Capturar propiedades](./media/working-with-rules/rule-capture-properties.png)

1. (opcional) Revise los cambios, para lo que debe pulsar o hacer clic en **Mostrar acciones**.

    ![Revisar acciones](./media/working-with-rules/rule-review-actions.png)

1. Cuando termine de agregar acciones, pulse o haga clic en **Listo**.

1. Revise tanto la condición como las acciones de la regla.

    ![Revisar regla](./media/working-with-rules/rule-review.png)

## <a name="rename-the-rule"></a>Cambio de nombre de la regla

1. Mantenga el mouse sobre **Rule1** y haga clic o pulse el botón de edición.

    ![Mantener el mouse sobre el nombre de la regla](./media/working-with-rules/hover-over-rules_name.png)

1. Escriba el nuevo nombre de la regla.

    ![Cambiar nombre de la regla](./media/working-with-rules/rename-rule.png)

1. Haga clic o pulse **Done** (Listo) para descartar el editor.

## <a name="test-the-rule"></a>Prueba de la regla
1. Para obtener una vista previa de la aplicación, presione F5 (o haga clic o pulse en el botón de reproducción situado cerca de la esquina superior derecha).

    ![Abrir vista previa](./media/working-with-rules/open-preview.png)

1. Cree la condición que especificó como true y, después, confirme que las acciones funcionan como se espera de ellas.

    En este tema, establezca el control deslizante en un valor que sea mayor que 70 y confirme que el texto de la etiqueta cambia de color.

## <a name="see-all-rules"></a>Ver todas las reglas
De forma predeterminada, la pestaña **Reglas** muestra solo las reglas del control seleccionado y todos los controles secundarios que se utilizan en una condición o acción de una regla. Para mostrar todas las reglas de la aplicación, desactive la casilla **Mostrar reglas solo para este control**.

![Quitar filtro](./media/working-with-rules/rules-filter.png)

## <a name="known-limitations"></a>Limitaciones conocidas
En el momento de redactar este documento:

* No se puede especificar la propiedad **ThisItem** de un formulario o una galería como parte de una condición.
