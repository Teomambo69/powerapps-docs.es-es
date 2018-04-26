---
title: Presentación de elementos de alturas diferentes en una galería | Microsoft Docs
description: Agregar y configurar una galería de alturas flexibles para que se ajuste automáticamente a la cantidad de contenido de cada elemento de la galería
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 04/01/2017
ms.author: fikaradz
ms.openlocfilehash: 466e0d9cb1acfe4cfeb72256db2deddfd3466e19
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="show-items-of-different-heights-in-a-powerapps-gallery"></a>Mostrar elementos de alturas diferentes en una galería de PowerApps
Si diferentes elementos del conjunto de datos contienen diferentes cantidades de datos en el mismo campo, puede mostrar por completo los elementos que contienen más datos sin tener que agregar espacio vacío después de los elementos que contienen menos datos. Agregue y configure un control de galería **Altura flexible** para que pueda:

* Configure controles **Etiqueta** para que se expandan o se reduzcan según su contenido.
* Coloque cada control para que aparezca automáticamente bajo el control de encima.

En este tutorial, va a mostrar datos sobre productos para el suelo en un control de galería **Altura flexible**. La imagen de cada producto aparece 5 píxeles por debajo de la información general, tanto si esta contiene cinco líneas de texto como solo dos.

![Aplicación final](./media/gallery-dynamic-sizing/dynamic-app.png)

**Lectura recomendada**

Si nunca ha agregado los controles a una galería, siga los pasos descritos en [Mostrar una lista de elementos](add-gallery.md) antes de continuar en este tema.

## <a name="add-data-to-a-blank-app"></a>Agregar datos a una aplicación en blanco
1. Descargue [este archivo de Excel](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx), que contiene nombres, información general y vínculos a imágenes de productos para el suelo.

    ![Productos para el suelo](./media/gallery-dynamic-sizing/flooring-products.png)

2. Cargue el archivo de Excel en una cuenta de almacenamiento en la nube, como OneDrive, Dropbox o Google Drive.

3. En PowerApps Studio, pulse o haga clic en **Nuevo** en el menú **Archivo**.

4. En el icono **Blank app** (Aplicación vacía), pulse o haga clic en **Phone layout** (Diseño de teléfono).

    ![Opción Nuevo en el menú Archivo](./media/gallery-dynamic-sizing/blank-app.png)

5. Agregue una conexión a la tabla **FlooringEstimates** del archivo de Excel.

    Para más información, consulte [Agregar una conexión](add-data-connection.md).

## <a name="add-data-to-a-gallery"></a>Agregar datos a una galería
1. En la pestaña **Insertar**, haga clic o pulse en **Galería** y luego haga clic o pulse en **Altura flexible**.

    ![Agregar galería](./media/gallery-dynamic-sizing/add-flexible.png)
2. Cambie el tamaño de la galería para que ocupe toda la pantalla.

3. Establezca la propiedad **[Elementos](controls/properties-core.md)** de la galería en **FlooringEstimates**.

## <a name="show-the-product-names"></a>Mostrar los nombres de producto
1. En la esquina superior izquierda de la galería, haga clic o pulse en el icono de lápiz para seleccionar la plantilla de la galería.

    ![Icono de lápiz](./media/gallery-dynamic-sizing/edit-template.png)

2. Con la plantilla de la galería seleccionada, agregue un control **[Etiqueta](controls/control-text-box.md)**.

3. Establezca la propiedad **Text** del control **Etiqueta** en esta expresión:<br>
   **ThisItem.Name**

    ![Agregar etiqueta](./media/gallery-dynamic-sizing/add-text-box.png)

## <a name="show-the-product-overviews"></a>Mostrar las informaciones generales de producto
1. Con la plantilla de la galería seleccionada, agregue otro control **Etiqueta** y muévalo debajo del primer control **Etiqueta**.  

2. Establezca la propiedad **Texto** del segundo control **Etiqueta** en esta expresión:<br> **ThisItem.Overview**

3. Con el segundo control **Etiqueta** seleccionado, haga clic o pulse en el icono de etiqueta de nombre en la pestaña **Contenido** y cambie el nombre del control a **OverviewText**.

    ![Cambiar el nombre de etiqueta](./media/gallery-dynamic-sizing/rename-text-box.png)

4. Establezca la propiedad **AutoHeight** del cuadro **OverviewText** en **true**.

    Este paso garantiza que el cuadro aumentará o reducirá su tamaño para ajustarse al contenido.

      ![Altura automática del texto](./media/gallery-dynamic-sizing/autoheight-text.png)

## <a name="show-the-product-images"></a>Mostrar las imágenes de producto
1. Cambie el tamaño de la plantilla para que sea dos veces más alta de lo que era.

    Puede agregar controles a la plantilla más fácilmente cuando compile la aplicación y este cambio no afectará al aspecto de la aplicación cuando esta se ejecute.

2. Con la plantilla de la galería seleccionada, agregue un control **[Imagen](controls/control-image.md)** y muévalo debajo del cuadro **OverviewText**.

3. Asegúrese de que la propiedad **Imagen** del control **Imagen** esté establecida en esta expresión:<br>
    **ThisItem.Image**

4. Establezca la propiedad **[Y](controls/properties-core.md)** del control **Imagen** en función de la posición y el tamaño del cuadro **OverviewText**, como se muestra en esta expresión:
   <br>**OverviewText.Y + OverviewText.Height + 5**

    ![Aplicación final](./media/gallery-dynamic-sizing/final-app.png)

Aplique el mismo concepto se aplica si desea agregar más controles: establezca la propiedad **Y** de cada control en función de las propiedades **Y** y **Altura** del control situado por encima de él.

## <a name="next-steps"></a>Pasos siguientes
Aprenda a trabajar con un control [Galería](working-with-forms.md) y [fórmulas](working-with-formulas.md).
