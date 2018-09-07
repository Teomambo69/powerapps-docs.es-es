---
title: Visualización, ordenación y filtrado de los datos de una galería | Microsoft Docs
description: Use una galería para mostrar imágenes y texto. Ordene y filtre las imágenes en PowerApps.
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/02/2015
ms.author: lonu
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e782b7082e8dbf0d4efee2060131aa620e7a4af1
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42844467"
---
# <a name="show-sort-and-filter-data-in-a-powerapps-gallery"></a>Mostrar, ordenar y filtrar los datos en una galería de PowerApps
Cree una galería para mostrar imágenes y texto sobre diversos productos, y ordene y filtre esa información.

En PowerApps, puede usar una galería para mostrar varios elementos relacionados, como si se tratara de un catálogo. Las galerías son ideales para mostrar información sobre productos, como nombres y precios. En este tema, crearemos una galería y ordenaremos y filtraremos la información mediante el uso de funciones similares a las de Excel. Además, cuando se seleccione un elemento, se colocará un borde a su alrededor.

> [!NOTE]
> En este tema se usa una aplicación de tableta. Puede usar una aplicación de teléfono, pero deberá cambiar el tamaño de algunos de los controles.
> 
> 

### <a name="prerequisites"></a>Requisitos previos
* [Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.
* Cree una aplicación de tableta a partir de una [plantilla](get-started-test-drive.md), de [datos](get-started-create-from-data.md) o desde [cero](get-started-create-from-blank.md).
* Tiene que saber [configurar un control](add-configure-controls.md).
* En estos pasos se usa [CreateFirstApp](http://pwrappssamples.blob.core.windows.net/samples/CreateFirstApp.zip) como datos de entrada de ejemplo, que incluye imágenes .jpg. El archivo zip incluye un archivo XML que se puede convertir a Excel. De lo contrario, PowerApps lee automáticamente los archivos dentro los archivos .zip y lo importa correctamente. Puede descargar y usar estos datos de ejemplo o importar los suyos propios.

## <a name="show-data-in-a-gallery"></a>Mostrar datos en una galería
1. Cree una colección denominada **Inventory** con los datos de ejemplo. Siga estos pasos:  
   
   1. En la pestaña **Insertar**, seleccione **Controles** e **Importar**:
      
      ![][1]  
   2. Establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** del control de importación en la siguiente fórmula:  
      **Collect(Inventory, Import1!Data)**
      
      ![][12]  
   3. Seleccione el botón **Importar datos** para abrir el Explorador de Windows. Seleccione *CreateFirstApp.zip* y **Abrir**.
   4. En el menú **Archivo**, seleccione **Colecciones**. La colección Inventory se muestra con los datos que ha importado:
      
      ![][3]  
      
      Acaba de crear la colección Inventory, que contiene información sobre cinco productos, incluida una imagen del diseño, el nombre del producto y el número de unidades disponibles.
      
      > [!NOTE]
      > El control de importación se usa para importar datos en forma de Excel y crear la colección. El control de importación importa los datos cuando se crea la aplicación y se obtiene una vista previa de esta. Actualmente, el control de importación no importa datos cuando se publica la aplicación.
      > 
      > 
2. Seleccione la flecha Atrás para volver al diseñador.
3. En la pestaña **Insertar**, haga clic o pulse en **Galería** y luego haga clic o pulse en la galería **Horizontal**.
   
    ![][4]
4. En el panel derecho, haga clic o pulse en la opción en la que el título y el subtítulo se superponen en superposición en el gráfico:
   
    ![][15]
5. Establezca la propiedad **[Items](controls/properties-core.md)** de la galería en **Inventory**:
   
    ![][5]
6. Cambie el nombre de la galería a **ProductGallery** y muévala de modo que no bloquee los demás controles. Cambie el tamaño de la galería para que muestre tres productos:
   
    ![][6]
7. En el primer elemento de la galería, seleccione la etiqueta inferior:  
   
    ![][7]  
   
   > [!NOTE]
   > Cuando se cambia el primer elemento de una galería, se cambian automáticamente los demás elementos de la galería.  
   > 
   > 
8. Establezca la propiedad **[Text](controls/properties-core.md)** de la etiqueta en la expresión siguiente:  
    **ThisItem!UnitsInStock** <br/>
   
    Al hacerlo, en la etiqueta se muestran las unidades disponibles de cada producto:

![][8]  

> [!NOTE]
> De forma predeterminada, la propiedad **[Text](controls/properties-core.md)** de la etiqueta superior está establecida en ```ThisItem!ProductName```. Puede cambiarla a cualquier otro elemento de la colección. Por ejemplo, si la colección tiene los campos *ProductDescription* o *Price*, puede establecer la etiqueta en ```ThisItem!ProductDescription``` o ```ThisItem!Price```.
> 
> 

Mediante estos pasos, ha importado datos que incluyen imágenes .jpg en una colección. Después, ha agregado una galería en la que se muestran los datos y ha configurado una etiqueta para mostrar las unidades disponibles de cada producto.

## <a name="highlight-the-gallery-item-you-select"></a>Resaltar el elemento seleccionado de la galería
1. Seleccione un elemento cualquiera de la galería *excepto* el primero. Aparece el icono de edición en la esquina superior izquierda. Seleccione el icono de edición:  
   ![][9]  
2. En la pestaña **Insertar**, seleccione **Formas** y, luego, el rectángulo. Aparece un rectángulo sólido azul en cada elemento de la galería.
3. En la pestaña **Inicio**, seleccione **Relleno** y, después, **Sin relleno**.
4. Seleccione **Borde**, **Estilo de borde** y la línea sólida.
5. Seleccione **Borde** de nuevo y establezca el grosor en 3. Cambie el tamaño del rectángulo de modo que rodee el elemento de la galería. Ahora los elementos de la galería tienen un borde azul y deberían tener un aspecto similar al siguiente:  
   ![][10]  
6. En la pestaña **Forma**, seleccione **Visible** y escriba la siguiente fórmula en la barra de fórmulas:  
   
    **If(ThisItem!IsSelected, true)**
   
    Un rectángulo azul rodea la selección actual en la galería. Seleccione algunos elementos de la galería para confirmar que el rectángulo aparece alrededor de cada elemento seleccionado. Recuerde que también puede abrir **Vista previa** ![][2] para ver y probar lo que está creando.

> [!TIP]
> Seleccione el rectángulo, **Reordenar** en la pestaña **Inicio** y **Enviar al fondo**. Con esta característica, puede seleccionar un elemento de galería sin que el borde bloquee nada.
> 
> 

Mediante estos pasos, ha agregado un borde alrededor de la selección actual en la galería.

## <a name="sort-and-filter-items-in-the-gallery"></a>Ordenar y filtrar elementos en la galería
Mediante estos pasos, vamos a ordenar los elementos de la galería en orden ascendente y descendente. Además, vamos a agregar un control deslizante para "filtrar" los elementos de la galería por las unidades disponibles que elija.

#### <a name="sort-in-ascending-or-descending-order"></a>Ordenar en orden ascendente o descendente
1. Seleccione un elemento cualquiera de la galería *excepto* el primero.
2. La propiedad **[Items](controls/properties-core.md)** está establecida actualmente en Inventory (el nombre de la colección). Cámbiela a lo siguiente:  
   
    **Sort(Inventory, ProductName)**
   
    Cuando lo haga, los elementos de la galería se ordenarán por nombre de producto en orden ascendente: ![][11]  
   
    Pruebe un orden descendente. Establezca la propiedad **[Elementos](controls/properties-core.md)** de la galería en la siguiente fórmula:  
   
    Sort(Inventory, ProductName, Descending)  

#### <a name="add-a-slider-control-and-filter-items-in-the-gallery"></a>Agregar un control deslizante y filtrar los elementos de la galería
1. Agregue un control deslizante (pestaña **Insertar** > **Controles**), cambie su nombre a **StockFilter** y muévalo debajo de la galería.
2. Configure el control deslizante de modo que los usuarios no puedan establecerlo en un valor fuera del intervalo de unidades disponibles:  
   
   1. En la pestaña **Contenido**, seleccione **Mín.** y escriba la expresión siguiente:  
      ```Min(Inventory, UnitsInStock)```  
   2. En la pestaña **Contenido**, seleccione **Máx.** y escriba la expresión siguiente:  
      ```Max(Inventory, UnitsInStock)```
3. Seleccione un elemento cualquiera de la galería *excepto* el primero. Establezca la propiedad **[Items](controls/properties-core.md)** de la galería en la expresión siguiente:  
   ```Filter(Inventory, UnitsInStock<=StockFilter!Value)```
4. En **Vista previa**, ajuste el control deslizante en un valor comprendido entre la cantidad mínima y máxima en la galería. A medida que ajuste el control deslizante, la galería mostrará solo los productos con una cantidad inferior al valor que elija:  
   ![][13]  

Ahora vamos a agregar un filtro:

1. Vuelva al diseñador.
2. En la pestaña **Insertar**, seleccione **Texto**, elija **Texto de entrada** y cambie el nombre del control nuevo a **NameFilter**. Mueva el control de texto debajo del control deslizante.
3. Establezca la propiedad **[Items](controls/properties-core.md)** de la galería en la expresión siguiente:  
   ```Filter(Inventory, UnitsInStock<=StockFilter!Value && NameFilter!Text in ProductName)```
4. En **Vista previa**, establezca el control deslizante en *30* y escriba la letra *g* en el control de entrada de texto. En la galería se muestra el único producto con menos de 30 unidades disponibles *y* con un nombre que empieza por la letra "g":  
   ![][14]  

## <a name="tips-and-tricks"></a>consejos y trucos
* En cualquier momento, puede seleccionar el botón de vista previa (![][2]) para ver lo que ha creado y probarlo.
* Al diseñar la aplicación, puede volver a cambiar el tamaño de los controles y moverlos haciendo clic en ellos y arrastrándolos.
* Presione **ESC** o seleccione la **X** para cerrar la ventana de vista previa.
* Cuando use una galería, seleccione el primer elemento para cambiar todos los elementos de la galería. Por ejemplo, seleccione el primer elemento para agregar un borde a todos los elementos de la galería.
* Para actualizar las propiedades de la galería, seleccione un elemento cualquiera de la galería *excepto* el primero. Por ejemplo, seleccione el segundo elemento para actualizar la propiedad *Items*, *ShowScrollbar* u otra propiedad que se aplique a la galería (no a los elementos de la galería).  

## <a name="what-you-learned"></a>Qué ha aprendido
En este tema:

* Ha creado una colección, ha importado datos que incluían imágenes .jpg en esta colección y ha hecho que los datos aparecieran en una galería.
* Debajo de cada imagen de la galería, ha configurado una etiqueta que indica las unidades disponibles de ese elemento.
* Ha agregado un borde alrededor del elemento que se seleccione.
* Ha ordenado los elementos por nombre de producto de manera ascendente y descendente.
* Ha agregado un control deslizante y un control de texto de entrada para filtrar los productos por unidades disponibles y nombre de producto.

[1]: ./media/show-images-text-gallery-sort-filter/import.png
[2]: ./media/show-images-text-gallery-sort-filter/preview.png
[3]: ./media/show-images-text-gallery-sort-filter/inventorycollection.png
[4]: ./media/show-images-text-gallery-sort-filter/insert-vertical.png
[5]: ./media/show-images-text-gallery-sort-filter/itemsinventory.png
[6]: ./media/show-images-text-gallery-sort-filter/threeimages.png
[7]: ./media/show-images-text-gallery-sort-filter/firstitem.png
[8]: ./media/show-images-text-gallery-sort-filter/bottomlabel.png
[9]: ./media/show-images-text-gallery-sort-filter/editgallery.png
[10]: ./media/show-images-text-gallery-sort-filter/border.png
[11]: ./media/show-images-text-gallery-sort-filter/sort.png
[12]: ./media/show-images-text-gallery-sort-filter/onselect.png
[13]: ./media/show-images-text-gallery-sort-filter/slider.png
[14]: ./media/show-images-text-gallery-sort-filter/inputandslider.png
[15]: ./media/show-images-text-gallery-sort-filter/select-overlay.png
