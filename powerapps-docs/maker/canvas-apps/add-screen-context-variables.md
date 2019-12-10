---
title: Agregar una pantalla a una aplicación de lienzo y navegar por diferentes pantallas | Microsoft Docs
description: Agregar una pantalla a una aplicación de lienzo y usar las flechas siguiente y atrás para ir entre pantallas en Power apps
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
ms.openlocfilehash: cbe6173c94f001874b126a5b8ecb1bdf9ad21b70
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724448"
ms.PowerAppsDecimalTransform: true
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Agregar una pantalla a una aplicación de lienzo y navegar por diferentes pantallas

Cree una aplicación con varias pantallas e incorpore mecanismos que permitan a los usuarios desplazarse por ellas.

## <a name="add-and-rename-a-screen"></a>Agregar una pantalla y cambiarle el nombre

1. En la pestaña **Inicio** , seleccione **nueva pantalla**y, a continuación, seleccione el tipo de pantalla que desea agregar.

    ![Opción Agregar pantalla de la pestaña Inicio](./media/add-screen-context-variables/add-screen.png)

2. En el panel derecho, seleccione el nombre de la pantalla (justo encima de la pestaña **propiedades** ) y, a continuación, escriba **source**.

    ![Cambie el nombre de la pantalla predeterminada](./media/add-screen-context-variables/name-source-screen.png)

3. Agregue otra pantalla y asígnele el nombre **Target**.

    ![Dos pantallas en la barra de navegación izquierda](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>Cambiar el orden de las pantallas

En la barra de navegación izquierda, mantenga el mouse sobre una pantalla que desea mover hacia arriba o hacia abajo, seleccione el botón de puntos suspensivos que aparece y, a continuación, seleccione **subir** o **bajar**.

![Volver a ordenar pantalla](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> Cuando se abre la aplicación, la pantalla situada en la parte superior de la lista jerárquica de controles suele aparecer en primer lugar. Pero puede especificar una pantalla diferente si establece la propiedad **[OnStart](controls/control-screen.md)** en una fórmula que incluya la función **[Navigate](functions/function-navigate.md)** .

## <a name="add-navigation"></a>Agregar la funcionalidad de navegación

1. Con la pantalla **origen** seleccionada, abra la pestaña **Insertar** , seleccione **iconos**y, a continuación, seleccione **flecha siguiente**.  

    ![Opción Formas de la pestaña Insertar](./media/add-screen-context-variables/add-next-arrow.png)

2. (Opcional) Mueva la flecha hasta que aparezca en la esquina inferior derecha de la pantalla.

3. Con la flecha aún seleccionada, seleccione la pestaña **acción** y, a continuación, seleccione **navegar**.

    La propiedad **[AlSeleccionar](controls/properties-core.md)** de la flecha se establece automáticamente en la función **Navegar**.

    ![Propiedad AlSeleccionar establecida en la función Navegar](./media/add-screen-context-variables/onselect-default.png)

    Cuando un usuario selecciona la flecha, la pantalla de **destino** se atenúa.

4. En la pantalla **Target**, agregue el icono **Flecha atrás** y establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** en esta fórmula:

    `Navigate(Source; ScreenTransition.Fade)`

5. Mientras mantiene presionada la tecla Alt, alterne entre las pantallas seleccionando la flecha en cada pantalla.

## <a name="more-information"></a>Más información

[Referencia de control de pantalla](controls/control-screen.md)