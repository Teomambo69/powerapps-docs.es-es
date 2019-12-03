---
title: Agregar una pantalla de desplazamiento a una aplicación de lienzo | Microsoft Docs
description: En Power Apps, cree una pantalla en la que los usuarios puedan desplazarse para mostrar más tipos de contenido de los que la pantalla puede mostrar a la vez en una aplicación de lienzo.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: de0aba95b4bb5c3a308b0b86b739302dc0dc70e3
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724657"
---
# <a name="add-a-scrolling-screen-to-a-canvas-app-in-power-apps"></a>Agregar una pantalla de desplazamiento a una aplicación de lienzo en Power apps

En una aplicación de lienzo, cree una pantalla por la que puedan desplazarse los usuarios para ver diferentes elementos. Por ejemplo, cree una aplicación de teléfono que muestre datos en varios gráficos, que los usuarios podrán ver al desplazarse.

Cuando se agregan varios controles en una sección, estos mantienen su posición relativa en dicha sección tanto si se trata de una aplicación para el teléfono como de una aplicación para la tableta. Tenga en cuenta que el tamaño y la orientación de la pantalla pueden determinar la organización de las secciones.  

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-scrolling-screen"></a>Crear una pantalla de desplazamiento

1. En la pestaña **Inicio**, pulse o haga clic en **Nueva pantalla**:

    ![Opción para agregar una pantalla a la aplicación][1]

2. En la pestaña **Inicio**, pulse o haga clic en **Diseños** y en la opción que permite agregar un lienzo de desplazamiento infinito:  
   
    ![Opción para agregar un lienzo de desplazamiento infinito][2]
   
    Se agrega el lienzo:  
   
    ![Pantalla con un lienzo de desplazamiento infinito que aparece de forma predeterminada][3]

## <a name="add-elements"></a>Agregar elementos
Ahora, vamos a agregar algunos controles al lienzo para ver cómo funciona la pantalla de desplazamiento.

1. En el lienzo que acaba de agregar, pulse o haga clic en **Agregar un elemento desde la pestaña Insertar**.
   
    ![][4]
2. En la pestaña **Insertar**, pulse o haga clic en **Gráficos** y, a continuación, en **Gráfico de columnas**.
   
    ![Opción para agregar un gráfico de columnas][5]
   
    El gráfico de columnas aparece en la primera tarjeta de la pantalla:  
   
    ![Gráfico de columnas predeterminado][7]
3. En la pestaña **Insertar**, pulse o haga clic en **Texto** y en **Entrada manuscrita**:  
   
    ![Opción para agregar un control de entrada manuscrita][8]
4. Mueva el control de entrada manuscrita hasta situarlo bajo el gráfico y cambie su tamaño para que ocupe la parte inferior de la tarjeta:  
   
    ![Mueva el control de entrada manuscrita y cambie su tamaño][9]

## <a name="add-a-section"></a>Agregar una sección
Ahora, vamos a agregar una nueva tarjeta con otro control.

1. En la parte inferior de la pantalla, pulse o haga clic en **Agregar sección**:  
   
    ![Opción para agregar una sección][10]
   
    Se agrega una nueva tarjeta a la pantalla:  
   
    ![Nueva tarjeta situada bajo la sección predeterminada][11]
2. Con la tarjeta seleccionada, vaya a la pestaña **Insertar** y pulse o haga clic en **Gráficos** y en **Gráfico de líneas**.
   
    El nuevo gráfico es demasiado grande y no puede aparecer en la pantalla con los demás controles:  
   
    ![Gráfico de líneas agregado en la parte inferior de una nueva tarjeta][12]
3. Para abrir el modo de vista previa, presione F5 (o haga clic o pulse en el icono de reproducción situado cerca de la esquina superior derecha).
   
    ![Abrir el modo de vista previa](./media/add-scrolling-screen/open-preview.png)
4. Desplácese hacia abajo para ver el nuevo gráfico de líneas.  
   
    ![Vista previa con el gráfico de líneas][13]

[1]: ./media/add-scrolling-screen/add-screen.png
[2]: ./media/add-scrolling-screen/add-canvas.png
[3]: ./media/add-scrolling-screen/default-canvas.png
[4]: ./media/add-scrolling-screen/insert-visual.png
[5]: ./media/add-scrolling-screen/add-chart.png
[7]: ./media/add-scrolling-screen/default-chart.png
[8]: ./media/add-scrolling-screen/add-pen.png
[9]: ./media/add-scrolling-screen/move-resize-pen.png
[10]: ./media/add-scrolling-screen/add-section.png
[11]: ./media/add-scrolling-screen/new-card.png
[12]: ./media/add-scrolling-screen/add-line-chart.png
[13]: ./media/add-scrolling-screen/line-chart-preview.png
