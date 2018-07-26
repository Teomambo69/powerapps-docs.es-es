---
title: Creación y actualización de una colección | Microsoft Docs
description: Cree colecciones y agregue columnas a colecciones existentes en PowerApps
author: lonu
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/30/2015
ms.author: lonu
ms.openlocfilehash: 98407181bc654874d749bb57da22c9fde1259fb6
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2018
ms.locfileid: "39195505"
---
# <a name="create-and-update-a-collection-in-your-app"></a>Crear y actualizar una colección en su aplicación
Use una colección para almacenar datos que se pueden usar en la aplicación. Una colección es un grupo de elementos que son similares. Por ejemplo, cree una colección MisImágenes que almacene todas las imágenes de los productos que vende su compañía. En PowerApps, puede agregar la colección MisImágenes y crear una aplicación que muestre todas las imágenes de estos productos. En otro ejemplo, puede crear una colección PriceList que incluya los productos y el precio de cada uno de ellos.

Puede crear y usar colecciones en PowerApps. Empecemos.

### <a name="prerequisites"></a>Requisitos previos
* [Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.
* Cree una aplicación o abra una existente en PowerApps.
* Aprenda a [configurar un control](add-configure-controls.md) en PowerApps.
* En estos pasos se utiliza el archivo [PriceList.zip](http://pwrappssamples.blob.core.windows.net/samples/PriceList.zip) como datos de entrada de ejemplo. El archivo zip incluye un archivo XML que se puede convertir a Excel. De lo contrario, PowerApps lee automáticamente los archivos dentro los archivos .zip y lo importa correctamente. Puede descargar y usar estos datos de ejemplo o importar los suyos propios.

## <a name="create-a-single-column-collection"></a>Crear una colección de una sola columna
En los pasos siguientes se muestra cómo crear una colección dentro de la aplicación mediante la función Recopilar y cómo agregar elementos a la colección.

1. Abra la aplicación.
2. En la pestaña **Insertar**, seleccione **Texto** y **Entrada de texto**:  
   ![][1]  
3. En la esquina superior izquierda, seleccione **Text1** y cambie el nombre del control a **Destino**:  
   ![][2]  
4. En la pestaña **Insertar**, seleccione **Botón** para agregar un control de botón al diseñador. En la lista desplegable, aparece la propiedad **[AlSeleccionar](controls/properties-core.md)**. Establézcala en la siguiente función:  
   
    ```Collect(Destinations, Destination!Text)```
   
    Debería parecerse a lo siguiente:  
    ![][3]  
5. Seleccione el texto del botón y escriba **Agregar**:  
   ![][5]  
6. Seleccione el botón **Agregar** y muévalo bajo el control de texto. Puede moverlo a cualquier lugar:  
   ![][6]  

En estos pasos, ha usado la función Recopilar para crear una colección denominada **Destinos**. También ha agregado un control de botón que, cuando se selecciona, agrega nuevos elementos a la colección. Ahora, vea lo que ha creado:

1. Seleccione Vista previa:  
   ![][7]  
2. Escriba un nombre de ciudad en el cuadro y seleccione el botón **Agregar**.
3. Escriba más nombres de ciudades y seleccione el botón **Agregar** con cada una.
4. Presione la tecla **Esc** para cerrar la ventana de vista previa.
5. Vea la colección Destinos y los valores de texto que ha especificado. En la pestaña **Archivo**, seleccione **Colecciones**. Aparece el texto que escribió:  
   ![][8]

#### <a name="extra-credit"></a>Crédito extra
Ahora, va a enlazar la colección Destinos a un cuadro de lista:

1. Vuelva al diseñador.
2. En la pestaña **Insertar**, seleccione **Controles** y **Cuadro de lista**:  
   ![][22]  
3. Mueva el cuadro de lista para que se vea fácilmente. Establezca la propiedad **[Elementos](controls/properties-core.md)** en la siguiente expresión:  
   ```Destinations!Value```  <br/>
   
    Cuando lo haga, el cuadro de lista se rellena automáticamente con los elementos que especificó antes en la colección Destinos:  
   ![][4]  

Obtenga una vista previa de los cambios: ![][7]. En el cuadro de lista, puede ver las distintas ciudades que especificó. En el control de entrada de texto, escriba una nueva ciudad y seleccione el botón **Agregar**. El cuadro de lista se actualiza automáticamente para incluir la nueva ciudad que escribió.

## <a name="create-a-multi-column-collection"></a>Crear una colección de varias columnas
En los pasos siguientes se muestra cómo crear una colección dentro de la aplicación mediante la función Recopilar y cómo agregar varias filas a la colección.

1. En la pestaña **Inicio**, abra una nueva pantalla.
2. En la pestaña **Insertar**, seleccione **Texto** y **Entrada de texto**.
3. Cambie el nombre del control de texto a **Ciudad**:  
   ![][9]  
4. Inserte otro control de entrada de texto y cambie su nombre a **Estados**.
5. Mueva los controles de texto Ciudad y Provincias de forma que se vean ambos:  
   ![][10]  
   
    > [!NOTE]
   > Puede reemplazar "Entrada de texto" por algo como "Ciudad" o "Provincia", como en la imagen.  
6. En la pestaña **Insertar**, seleccione **Botón**. Establezca su propiedad **[AlSeleccionar](controls/properties-core.md)** en la función siguiente:  
   ```Collect(Destinations, {Cities:City!Text, States:States!Text})```  
   
    Debería parecerse a lo siguiente:  
    ![][11]  
   
    > [!NOTE]
   > Puede usar esta misma función para agregar más columnas a esta colección. Por ejemplo, puede agregar otro control de entrada de texto para País para agregar una columna Países:
   
    `Collect(Destinations, {Cities:City!Text, States:States!Text}, {Countries:Country!Text})`
7. Cambie el nombre del control de botón **AddCityStateButton** y establezca su propiedad **[Texto](controls/properties-core.md)** en **Agregar ciudad y provincia**:  
   ![][12]  

En estos pasos, ha agregado una columna **Ciudades** y una columna **Provincias** a la colección **Destinos**. El control de botón agrega estos nuevos elementos de texto a la colección. Ahora, vea lo que ha creado:

1. Seleccione Vista previa:  
   ![][7]  
2. Escriba texto en los cuadros Ciudad y Provincia, y seleccione el botón **Agregar ciudad y provincia**.
3. Agregue más ciudades y provincias.
4. Presione la tecla **Esc** para cerrar la ventana de vista previa.
5. Para ver los elementos que agregó a la colección Destinos, seleccione la pestaña **Archivo** y seleccione **Colecciones**:  
   ![][13]

## <a name="add-columns-to-a-collection"></a>Agregar columnas a una colección
Hay algunas secciones en este tutorial. Cuando haya finalizado, sabrá importar datos a la colección, crear una galería que muestre datos en una lista de precios y usar un control deslizante que determina la cantidad de un producto.

### <a name="import-the-price-list-and-create-the-collection"></a>Importar la lista de precios y crear la colección
1. Descargue el archivo [PriceList](http://pwrappssamples.blob.core.windows.net/samples/PriceList.zip).zip.
2. En la pestaña **Inicio**, agregue una nueva pantalla.
3. En la pestaña **Insertar**, seleccione **Controles** e **Importar**:  
   ![][14]  
4. En la pestaña **Acción**, seleccione **Cuando se selecciona**. Escriba la siguiente función:  
   
    ```Collect(PriceList, Import1!Data)```  
5. Obtenga una vista previa de la aplicación. Seleccione el botón **Importar datos**, el archivo PriceList.zip y **Abrir**.
6. Cierre la ventana de vista previa.
7. Seleccione la pestaña **Archivo** y **Colecciones**. Aparecen en la lista los elementos de PriceList que se han importado:  
   ![][15]

### <a name="add-the-gallery-to-show-the-collection-items"></a>Agregar la galería para mostrar los elementos de la colección
1. Vuelva al diseñador.
2. En la pestaña **Insertar**, seleccione **Galería**, baje hasta **Galería personalizada** y seleccione **Vertical**:    
   ![][16]  
3. Cambie el nombre de la galería a **GaleríaDePrecios** y establezca la propiedad **[Elementos](controls/properties-core.md)** en **PriceList**:  
   ![][18]  
4. Mueva la galería de PriceList bajo el control **Importar datos**. Seleccione los bordes de la galería y haga clic y arrastre para cambiar su tamaño de forma que se muestren tres recuadros.
5. En la galería, seleccione el primer recuadro y agregue tres etiquetas (pestaña **Insertar** > **Etiqueta**).
6. Cambie el tamaño de las etiquetas y organícelas en una fila cerca de la parte superior del primer recuadro. La galería tendrá un aspecto similar al siguiente:  
   ![][19]
7. Establezca la propiedad **[Texto](controls/properties-core.md)** de cada etiqueta en la siguiente expresión:  
   
   | Etiquetas | Establezca la propiedad Texto en |
   | --- | --- |
   | Etiqueta1 |``ThisItem!Name`` |
   | Etiqueta2 |``Text(ThisItem!Price, "$#")`` |
   | Etiqueta3 |``ThisItem!Maker`` |
   
    Cuando hace esto, las etiquetas se actualizan automáticamente con los valores de nombre, precio y fabricante dentro de la colección PriceList.
8. Cambie el tamaño de las etiquetas y la galería para quitar el espacio extra. El pantalla tiene un aspecto similar al siguiente:  
   ![][17]

### <a name="add-the-quantity-slider-and-update-the-collection"></a>Agregar el control deslizante de cantidad y actualizar la colección
1. En el menú **Insertar**, seleccione **Controles** y **Control deslizante**. Cambie el nombre del control deslizante a **CantPedido** y muévalo bajo la galería.
2. Agregue un botón, establezca la propiedad **[Texto](controls/properties-core.md)** en **Agregar** y muévalo bajo el control deslizante **CantPedido**. La aplicación tendrá un aspecto similar al siguiente:  
   ![][20]
3. Establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** del botón **Agregar** en la siguiente expresión:  
   
    ```Collect(OrderList, {Name:PriceGallery!Selected!Name, Qty:OrderQty!Value, Cost:OrderQty!Value*LookUp(PriceList, PriceGallery!Selected!Name in Name, Price)});SaveData(OrderList, "orderfile")```  
   
    > [!NOTE]
   > Cuando seleccione este botón más adelante en este procedimiento, creará y guardará una colección llamada **ListaDePedidos**. La colección contendrá el nombre de un producto que especifique en la galería, una cantidad que elija con el control deslizante y el costo total calculado al multiplicar la cantidad por el precio del producto.
4. Seleccione la pestaña **Pantalla** y establezca la propiedad **[AlEstarVisible](controls/control-screen.md)** en la siguiente expresión:  
   
    ```If(IsEmpty(PriceList), LoadData(PriceList, "pricefile"));If(IsEmpty(OrderList), LoadData(OrderList, "orderfile"))```

Ahora, vea lo que ha creado:

1. Abra **Vista previa**.
2. Seleccione un producto en la galería, mueva el control deslizante a la cantidad deseada y seleccione el botón **Agregar**.  
   
   > [!IMPORTANT]
   > Cuando selecciona un producto, este no se resalta para indicar que se ha seleccionado. Cuando se creó la galería, no se agregó esta funcionalidad. Tenga en cuenta que, si hace clic en el producto, se selecciona.  
   > 
   > 
3. Repita estos pasos para agregar algunos productos más. Presione **ESC** para cerrar la ventana de vista previa.
4. En la pestaña **Archivo**, seleccione **Colecciones** para mostrar una vista previa de la colección **ListaDePedidos** creada:  
   ![][21]

> [!TIP]
> Para quitar todos los elementos de la lista de pedidos, agregue un botón, establezca su propiedad **[Texto](controls/properties-core.md)** en **Borrar** y establezca su propiedad **[OnSelect](controls/properties-core.md)** en la siguiente expresión:  
> ```Clear(OrderList);SaveData(OrderList, "orderfile")```  
> Para quitar un elemento cada vez, muestre la colección **ListaDePedidos** en una galería y establezca la propiedad **[AlSeleccionar](controls/properties-core.md)** de una etiqueta de dicha galería en la siguiente expresión:  
> ```Remove(OrderList, ThisItem);SaveData(OrderList, "orderfile")```
> 
> 

## <a name="tips-and-tricks"></a>consejos y trucos
* En cualquier momento, puede seleccionar el botón Vista previa (![][7]) para ver los gráficos y cómo se muestran con los datos.
* Al diseñar la aplicación, puede volver a cambiar el tamaño de los controles y moverlos haciendo clic en ellos y arrastrándolos.

## <a name="what-you-learned"></a>Qué ha aprendido
En este tema:

* Ha usado la función Collect() para crear una colección dentro de la aplicación.
* Ha agregado un control de botón que, cuando se selecciona, agrega nuevos elementos a la colección.
* Ha usado un cuadro de lista para agregar elementos a la colección.
* Ha agregado un control deslizante para actualizar elementos dentro de la colección.

[1]: ./media/create-update-collection/insertmenu-inputtext.png
[2]: ./media/create-update-collection/renametext.png
[3]: ./media/create-update-collection/buttononselect.png
[4]: ./media/create-update-collection/listboxpreview.png
[5]: ./media/create-update-collection/buttontext.png
[6]: ./media/create-update-collection/buttonundertext.png
[7]: ./media/create-update-collection/preview.png
[8]: ./media/create-update-collection/existingcollections.png
[9]: ./media/create-update-collection/renametext-city.png
[10]: ./media/create-update-collection/citystate.png
[11]: ./media/create-update-collection/buttononselectcitystate.png
[12]: ./media/create-update-collection/buttononcitystate.png
[13]: ./media/create-update-collection/existingcollectionscitystate.png
[14]: ./media/create-update-collection/import.png
[15]: ./media/create-update-collection/pricelistcollection.png
[16]: ./media/create-update-collection/portrait.png
[17]: ./media/create-update-collection/resizedgallery.png
[18]: ./media/create-update-collection/galleryitems.png
[19]: ./media/create-update-collection/gallerylabels.png
[20]: ./media/create-update-collection/slider.png
[21]: ./media/create-update-collection/existingcollectionsorderlist.png
[22]: ./media/create-update-collection/listbox.png
