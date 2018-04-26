---
title: Inserción de una aplicación nueva en un informe de Power BI | Microsoft Docs
description: Inserte una aplicación que use el mismo origen de datos y se pueda filtrar como otros elementos de informe.
documentationcenter: na
author: mgblythe
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/15/2018
ms.author: mblythe
ms.openlocfilehash: 33656e44f782a626eecc28787af984ace7339cd6
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="tutorial-embed-a-new-app-in-a-power-bi-report"></a>Tutorial: Inserción de una aplicación nueva en un informe de Power BI

Power BI permite ampliar sus características mediante la adición de *objetos visuales personalizados* a un informe. En este tutorial, se usa el objeto visual personalizado de PowerApps para crear una aplicación que se inserta en un informe de ejemplo. Esta aplicación interactúa con otros elementos de ese informe.

Si no tiene una suscripción a PowerApps, [cree una cuenta gratuita](../signup-for-powerapps.md) antes de comenzar.

En este tutorial, obtendrá información sobre cómo:
> [!div class="checklist"]
> * Importar el objeto visual personalizado de PowerApps en un informe de Power BI
> * Crear una aplicación que usa los datos del informe
> * Ver la aplicación en el informe

## <a name="prerequisites"></a>Requisitos previos

* El explorador [Google Chrome](https://www.google.com/chrome/browser/) o [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* Una [suscripción a Power BI](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi), con el [Ejemplo de análisis de oportunidades](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample) instalado
* Conocimientos sobre cómo [crear aplicaciones en PowerApps](data-platform-create-app-scratch.md) y cómo [editar informes de Power BI](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)

## <a name="import-the-powerapps-custom-visual"></a>Importar el objeto visual personalizado de PowerApps

El primer paso consiste en importar el objeto visual personalizado de PowerApps para se que pueda usar en el informe de ejemplo.

1. En el informe Ejemplo de análisis de oportunidades, pulse o haga clic en la pestaña **Próximas oportunidades**.

2. En la parte superior del informe, pulse o haga clic en **Editar informe**.

3. En el panel **Visualizaciones**, pulse o haga clic en el botón de puntos suspensivos (**. . .**) > **Importar de Marketplace**. 

    ![Importar de Marketplace](media/embed-powerapps-powerbi/import-visual.png)

4. En la pantalla **Objetos visuales de Power BI**, busque "PowerApps" y, después, pulse o haga clic en **Agregar**. Power BI agrega el icono de objeto visual personalizado a la parte inferior del panel **Visualizaciones**.

    ![Icono del objeto visual de PowerApps](media/embed-powerapps-powerbi/powerapps-icon.png)

5. Guarde el informe.

## <a name="create-a-new-app"></a>Crear una aplicación
Ahora agregue el objeto visual personalizado al informe y cree una aplicación en función de los datos del informe. Al crear la aplicación, se inicia PowerApps Studio con una conexión de datos dinámica entre PowerApps y Power BI.

1. Mueva y cambie el tamaño de algunos de los iconos de informe para dejar espacio para una aplicación.

    ![Mover y cambiar el tamaño de los iconos de informe](media/embed-powerapps-powerbi/move-resize.png)

2. Pulse o haga clic en el icono del objeto visual personalizado de PowerApps y, después, cambie el tamaño del icono para ajustarlo al espacio creado.

3. En el panel **Campos**, seleccione **Nombre**, **Código de producto** y **Fase de ventas**. 

    ![Seleccionar los campos](media/embed-powerapps-powerbi/select-fields.png)

4. En el icono de objeto visual personalizado, seleccione el entorno de PowerApps donde quiera crear la aplicación y, después, pulse o haga clic en **Crear nuevo**.

    ![Crear la aplicación](media/embed-powerapps-powerbi/create-new-app.png)

    En PowerApps Studio, verá que se ha creado una aplicación básica, con una *galería* en la que se muestra uno de los campos seleccionados en Power BI.

5.  Cambie el tamaño de la galería para que solo ocupe la mitad de la pantalla. 

6. En el panel de la izquierda, pulse o haga clic en **Screen1** y, después, establezca la propiedad **Fill** (Relleno) de la pantalla en "LightBlue" (para que se presente mejor en el informe).

    ![Aplicación con la galería cambiada de tamaño](media/embed-powerapps-powerbi/app-gallery.png)

6. Agregue un control de etiqueta debajo de la galería, con la propiedad **Text** establecida en `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Ahora se muestra el número total de oportunidades en el conjunto de datos.

    ![Recuento de oportunidades](media/embed-powerapps-powerbi/opportunity-count.png)

7. Guarde la aplicación con el nombre "Oportunidades". 


## <a name="view-the-app-in-the-report"></a>Ver la aplicación en el informe
Ahora la aplicación está disponible en el informe e interactúa con otros objetos visuales porque comparte el mismo origen de datos.

En el informe de Power BI, haga clic en **Jan** (enero) en la segmentación de datos, para que se filtre todo el informe, incluidos los datos de la aplicación.

![Informe filtrado](media/embed-powerapps-powerbi/filtered-report.png)

Tenga en cuenta que el recuento de oportunidades en la aplicación coincide con el número de la parte superior izquierda del informe. Puede seleccionar otros elementos en el informe y los datos de la aplicación se actualizarán.


## <a name="clean-up-resources"></a>Limpiar los recursos
Si ya no quiere usar el Ejemplo de análisis de oportunidades, puede eliminar el panel, el informe y el conjunto de datos.


## <a name="next-steps"></a>Pasos siguientes
En este tutorial, ha obtenido información sobre cómo:
> [!div class="checklist"]
> * Importar el objeto visual personalizado de PowerApps en un informe de Power BI
> * Crear una aplicación que usa los datos del informe
> * Ver la aplicación en el informe

Avance hasta el artículo siguiente para obtener más información.
> [!div class="nextstepaction"]
> [Objeto visual personalizado de PowerApps para Power BI](powerapps-custom-visual.md)

