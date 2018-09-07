---
title: Crear un gráfico en una aplicación de lienzo | Microsoft Docs
description: En PowerApps, muestre categorías de datos como gráficos de líneas, gráficos circulares o gráficos de barras en una aplicación de lienzo.
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/23/2016
ms.author: lonu
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 142bb0e19fb8b9647c1808dcca10e781c4f69d4a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42862044"
---
# <a name="show-data-in-a-line-pie-or-bar-chart-in-powerapps"></a>Visualización de datos en un gráfico de líneas, circular o de barras en PowerApps

Utilice gráficos de líneas, gráficos circulares y gráficos de barras para mostrar los datos en una aplicación de lienzo. Cuando trabaje con gráficos, los datos que importe deben estar estructurados en función de los criterios siguientes:

* Todas las series deben estar en la primera fila.
* Las etiquetas deben estar en la columna izquierda.

Por ejemplo, los datos deben tener un aspecto similar al siguiente:

![][9]

Puede crear y usar estos gráficos en PowerApps. Empecemos.

## <a name="prerequisites"></a>Requisitos previos

* [Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.
* Cree una aplicación a partir de una [plantilla](get-started-test-drive.md), de [datos](get-started-create-from-data.md) o desde [cero](get-started-create-from-blank.md).
* Aprenda a [configurar un control](add-configure-controls.md) en PowerApps.
* Descargue [ChartData.zip](http://pwrappssamples.blob.core.windows.net/samples/ChartData.zip), que contiene datos de ejemplo como un archivo XML. Siga los pasos descritos en este tema para importarlo directamente desde su aplicación. Como alternativa, descomprima el archivo .zip, abra el archivo XML en Excel y guárdelo en una [cuenta de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).

## <a name="import-the-sample-data"></a>Importar los datos de ejemplo
En estos pasos importaremos los datos de ejemplo en una colección, denominada **ProductRevenue**.

1. En la pestaña **Insertar**, seleccione **Controles** e **Importar**:  

    ![][11]  

2. Establezca la propiedad **[OnSelect](controls/properties-core.md)** del control en la función siguiente:  

   ```Collect(ProductRevenue, Import1.Data)```

3. Presione F5 para abrir el modo de vista previa y seleccione el botón **Importar datos**.

4. En el cuadro de diálogo **Abrir**, elija ChartData.zip, seleccione **Abrir** y, después, presione Esc.

5. En el menú **Archivo**, seleccione **Colecciones**.

    Aparece la colección ProductRevenue con los datos de gráfico que ha importado:

    ![][1]  

   > [!NOTE]
   > El control de importación se usa para importar datos en forma de Excel y crear la colección. El control de importación importa los datos cuando se crea la aplicación y se obtiene una vista previa de esta. Actualmente, el control de importación no importa datos cuando se publica la aplicación.
   >

6. Presione Esc para volver al área de trabajo predeterminada.

## <a name="add-a-pie-chart"></a>Agregar un gráfico circular
1. En la pestaña **Insertar**, seleccione **Gráficos** y **Gráfico circular**.

2. Mueva el gráfico circular bajo el botón**Importar datos**.

3. En el control de gráfico circular, seleccione el centro del gráfico circular:   

    ![][10]

4. Establezca la propiedad **[Elementos](controls/properties-core.md)** del gráfico circular en esta expresión: `ProductRevenue.Revenue2014`

    ![][2]  

    El gráfico circular muestra los datos de los ingresos de 2014.

    ![][3]  

## <a name="add-a-bar-chart-to-display-your-data"></a>Agregar un gráfico de barras para mostrar los datos
Ahora vamos a usar esta colección ProductRevenue en un gráfico de barras:

1. En la pestaña **Inicio**, agregue una pantalla.]

2. En la pestaña **Insertar**, seleccione **Gráficos** y **Gráfico de columnas**.

3. Seleccione el centro del gráfico de columnas. Establezca la propiedad **[Items](controls/properties-core.md)** del gráfico de columnas en ```ProductRevenue```:

    ![][12]  

    El gráfico de columnas muestra los datos de los ingresos de 2012:

    ![][4]  

4. En el gráfico de columnas, seleccione el cuadrado central:

    ![][5]

5. En la pestaña **Gráfico**, seleccione **Número de series** y escriba **3** en la barra de fórmulas:

    ![][6]  

    El gráfico de columnas muestra los datos de los ingresos de cada producto durante tres años:

    ![][7]  

[1]: ./media/use-line-pie-bar-chart/productrevenuecollection.png
[2]: ./media/use-line-pie-bar-chart/itemsexpression.png
[3]: ./media/use-line-pie-bar-chart/piechart.png
[4]: ./media/use-line-pie-bar-chart/columnchart.png
[5]: ./media/use-line-pie-bar-chart/columnchartseries.png
[6]: ./media/use-line-pie-bar-chart/columnchartseriesfunction.png
[7]: ./media/use-line-pie-bar-chart/columnchartthreeyears.png
[8]: ./media/use-line-pie-bar-chart/preview.png
[9]: ./media/use-line-pie-bar-chart/tableformat.png
[10]: ./media/use-line-pie-bar-chart/middlepiechart.png
[11]: ./media/use-line-pie-bar-chart/import.png
[12]: ./media/use-line-pie-bar-chart/itemscolumnchart.png
