---
title: Incorporación de una pantalla y desplazamiento por diferentes pantallas | Microsoft Docs
description: Agregue una pantalla a una aplicación y utilice las flechas Siguiente y Atrás para desplazarse por diferentes pantallas en PowerApps.
documentationcenter: na
author: aftowen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 07/10/2017
ms.author: anneta
ms.openlocfilehash: 19c06fa9bfc7098227e5f30a1c913522d9e6e7a3
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "31825266"
---
# <a name="add-a-screen-and-navigate-between-screens"></a>Agregar una pantalla y desplazarse por diferentes pantallas
Cree una aplicación con varias pantallas e incorpore mecanismos que permitan a los usuarios desplazarse por ellas.

## <a name="prerequisites"></a>Requisitos previos
* Tiene que saber [configurar un control](add-configure-controls.md).
* Tiene que crear o abrir una aplicación.

## <a name="add-and-rename-a-screen"></a>Agregar una pantalla y cambiarle el nombre
1. En la pestaña **Inicio**, pulse o haga clic en **Nueva pantalla**.

    ![Opción Agregar pantalla de la pestaña Inicio](./media/add-screen-context-variables/add-screen.png)

2. En el panel derecho, haga clic o pulse en el nombre de la pantalla (justo encima de la pestaña **Propiedades**) y, a continuación, escriba el nuevo nombre **Source**.

    ![Cambie el nombre de la pantalla predeterminada](./media/add-screen-context-variables/name-source-screen.png)

3. Agregue otra pantalla y asígnele el nombre **Target**.

    ![Dos pantallas en la barra de navegación izquierda](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="add-navigation"></a>Agregar la funcionalidad de navegación
1. Con la pantalla **Source** seleccionada, abra la pestaña **Insertar** y pulse o haga clic en **Iconos** y en **Flecha siguiente**.  

    ![Opción Formas de la pestaña Insertar](./media/add-screen-context-variables/add-next-arrow.png)

2. (Opcional) Mueva la flecha hasta que aparezca en la esquina inferior derecha de la pantalla.

3. Sin dejar de seleccionar la flecha, pulse o haga clic en la pestaña **Acción** y en **Navegar**.

    La propiedad **[AlSeleccionar](controls/properties-core.md)** de la flecha se establece automáticamente en la función **Navegar**.  

    ![Propiedad AlSeleccionar establecida en la función Navegar](./media/add-screen-context-variables/onselect-default.png)

    Cuando un usuario pulsa o hace clic en la flecha, comienza a aparecer la pantalla **Target**.

4. En la pantalla **Target**, agregue el icono **Flecha atrás** y establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** en esta fórmula:
   <br>**Navigate(Origen, ScreenTransition.Fade)**

5. Abra el modo de vista previa (![](./media/add-screen-context-variables/preview.png) o presione F5) y pase de una pantalla a otra pulsando o haciendo clic en las flechas que agregó.

6. Presione **Esc** para volver al área de trabajo predeterminada.
