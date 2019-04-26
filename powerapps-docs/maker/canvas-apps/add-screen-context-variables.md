---
title: Agregar una pantalla a una aplicación de lienzo y navegar por diferentes pantallas | Microsoft Docs
description: Agregue una pantalla a una aplicación de lienzo y utilice las flechas Siguiente y Atrás para navegar por diferentes pantallas en PowerApps.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6f83d21b2964dac7c4925d45efdf11a3a1e6b02
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63321378"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Agregar una pantalla a una aplicación de lienzo y navegar por diferentes pantallas

Cree una aplicación con varias pantallas e incorpore mecanismos que permitan a los usuarios desplazarse por ellas.

## <a name="add-and-rename-a-screen"></a>Agregar una pantalla y cambiarle el nombre

1. En el **inicio** ficha, seleccione **nueva pantalla**y, a continuación, seleccione el tipo de pantalla que desea agregar.

    ![Opción Agregar pantalla de la pestaña Inicio](./media/add-screen-context-variables/add-screen.png)

2. En el panel derecho, seleccione el nombre de la pantalla (justo encima el **propiedades** pestaña) y, a continuación, escriba **origen**.

    ![Cambie el nombre de la pantalla predeterminada](./media/add-screen-context-variables/name-source-screen.png)

3. Agregue otra pantalla y asígnele el nombre **Target**.

    ![Dos pantallas en la barra de navegación izquierda](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>Cambiar el orden de las pantallas

En la barra de navegación izquierda, mantenga el mouse sobre una pantalla que desea mover hacia arriba o hacia abajo, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **Subir** o **Bajar**.

![Cambiar el orden de pantalla](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> Cuando se abre la aplicación, la pantalla en la parte superior de la lista jerárquica de los controles normalmente aparece en primer lugar. Pero puede especificar una pantalla diferente estableciendo el **[OnStart](controls/control-screen.md)** propiedad en una fórmula que incluya el **[Navigate](functions/function-navigate.md)** función.

## <a name="add-navigation"></a>Agregar la funcionalidad de navegación

1. Con el **origen** pantalla seleccionado, abra el **insertar** ficha, seleccione **iconos**y, a continuación, seleccione **flecha siguiente**.  

    ![Opción Formas de la pestaña Insertar](./media/add-screen-context-variables/add-next-arrow.png)

2. (Opcional) Mueva la flecha hasta que aparezca en la esquina inferior derecha de la pantalla.

3. Con la flecha aún seleccionada, seleccione el **acción** pestaña y, a continuación, seleccione **Navigate**.

    La propiedad **[AlSeleccionar](controls/properties-core.md)** de la flecha se establece automáticamente en la función **Navegar**.

    ![Propiedad AlSeleccionar establecida en la función Navegar](./media/add-screen-context-variables/onselect-default.png)

    Cuando un usuario selecciona la flecha, la **destino** pantalla desaparece.

4. En la pantalla **Target**, agregue el icono **Flecha atrás** y establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** en esta fórmula:

    `Navigate(Source, ScreenTransition.Fade)`

5. Mientras mantiene presionada la tecla Alt, alternar entre pantallas seleccionando la flecha en cada pantalla.

## <a name="more-information"></a>Más información

[Referencia de control de pantalla](controls/control-screen.md)