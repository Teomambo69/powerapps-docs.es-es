---
title: Comprender el diseño de formularios de datos para aplicaciones de lienzo | Microsoft Docs
description: En PowerApps, cree atractivos diseños de formularios en aplicaciones de lienzo mediante filas y columnas.
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/17/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 43d623daecb609fbe3d4e593a7e15f95051871e9
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836427"
---
# <a name="understand-data-form-layout-for-canvas-apps-in-powerapps"></a>Comprender el diseño de formularios de datos para aplicaciones de lienzo en PowerApps

Cree fácilmente un formulario atractivo y eficaz al compilar una aplicación de lienzo en PowerApps. Por ejemplo, considere este formulario básico para grabar pedidos de ventas:

![Pedido de ventas de ejemplo](./media/working-with-form-layout/sales-order.png)

En este tutorial, se le guiará por los pasos necesarios para crear un formulario. También se examinarán algunos temas avanzados como el cambio de tamaño dinámico de campos para llenar el espacio disponible.

## <a name="before-you-start"></a>Antes de comenzar

Si es la primera vez que usa PowerApps (o solo ha generado aplicaciones automáticamente), lo más recomendable es [compilar una aplicación desde cero](get-started-create-from-blank.md) antes de profundizar en este tema. Mediante la compilación de una aplicación desde cero, se familiarizará con los conceptos necesarios, como agregar orígenes de datos y controles, que se mencionan, pero no se explican, en este tema.

## <a name="add-a-gallery"></a>Agregar una galería

1. Cree una aplicación para tableta desde cero.

    Todo lo que se describe en este tema aquí también se aplica a los diseños para teléfono, pero las aplicaciones de teléfono suelen tener solo una columna vertical.
2. Agregue la entidad **Pedido de ventas** en [Common Data Service](../common-data-service/data-platform-intro.md) como origen de datos de la aplicación.

    Fuera de este tutorial, puede utilizar cualquier origen de datos, incluidas las listas de SharePoint y las tablas de Excel.
3. Agregue un control **Galería** vertical y en su propiedad **Elementos**, seleccione **"Sales order"**.
   
    (opcional) Para ajustarse a los ejemplos de este tutorial, cambie el **diseño** de la galería para que muestre solo el **título y subtítulo**.
   
    ![Lista de pedidos de ventas](./media/working-with-form-layout/gallery-layout.png)
4. En la galería, pulse o haga clic en **SO004**.
   
    ![Lista de pedidos de ventas](./media/working-with-form-layout/sales-order-gallery-screen.png)
   
    Este registro aparecerá en el formulario que se crea siguiendo los pasos que encontrará más adelante en este mismo tema.

## <a name="add-a-title-bar"></a>Incorporación de una barra de título
1. Agregue una pantalla en blanco, en la que colocará el formulario.
   
    Fuera de este tutorial, los controles **Galería** y **[Editar formulario](controls/control-form-detail.md)** se pueden colocar en la misma pantalla, pero habrá más espacio para trabajar con si se colocan en pantallas independientes.
2. En la parte superior de la pantalla, agregue un control **[Etiqueta](controls/control-text-box.md)** y en su propiedad **Texto** escriba esta expresión:
   <br>**"Sales Order " & Gallery1.Selected.SalesOrderId**
   
    La etiqueta muestra el número del pedido de ventas del registro que seleccionó en la galería.
3. (opcional) Dé formato a la etiqueta como se indica a continuación:
   
   1. Establezca su propiedad **Align** en **Center**.
   
   2. Establezca su propiedad **Size** en **20**.
   
   3. Establezca su propiedad **Fill** en **Navy**.
   
   4. Establezca su propiedad **Color** en **White**.
   
   5. Establezca su propiedad **Width** en **Parent.Width**.
   
   6. Establecer sus propiedades **X** e **Y** en **0**.
      
      ![Barra de título](./media/working-with-form-layout/title-bar.png)

## <a name="add-a-form"></a>Agregar un formulario
1. Agregue un control **Editar formulario** y muévalo y cámbielo de tamaño para rellenar la pantalla bajo la etiqueta.
   
    En el paso siguiente, conectará el control de formulario al origen de datos **Sales order** mediante el panel derecho, no la barra de fórmulas. Si usa la barra de fórmulas, el formulario no mostrará cambios de manera predeterminada. Siempre puede mostrar todos los campos que desee activando una o varias casillas en el panel derecho.
2. En el panel derecho, pulse o haga clic en la flecha abajo junto a **No se ha seleccionado un origen de datos** y después en **Sales order**.
   
    Un conjunto de campos predeterminado del origen de datos **Sales order** aparecerá en un diseño sencillo de tres columnas. Sin embargo, muchos están en blanco y es posible que tarden un tiempo en quedarse en sus posiciones finales.  
3. En la propiedad **Item** del formulario, seleccione **Gallery1.Selected**.
   
    El formulario muestra el registro que seleccionó en la galería, pero es posible que el conjunto de campos predeterminado no coincida con el que desea en el producto final.
4. En el panel derecho, oculte todos estos campos, para lo que debe desactivando su casilla:
   
   * **Sales order ID**
   * **Account**
   * **Sales person**
   * **Account contact**
5. Mueva el campo **Order status**, para lo que debe arrastrarlo a la izquierda y soltarlo en el otro lado del campo **Customer purchase order reference**.
   
    La pantalla debe ser similar al ejemplo:
   
    ![Pedido de ventas en un diseño básico de tres columnas](./media/working-with-form-layout/sales-order-form-screen-3.png)

## <a name="select-a-data-card"></a>Seleccione una tarjeta de datos
Cada campo mostrado cuenta con una tarjeta de datos correspondiente en el formulario. Esta tarjeta consta de un conjunto de controles para el título de campo, un cuadro de entrada, una estrella (que aparece si el campo es obligatorio) y un mensaje de error de validación.

También puede seleccionar tarjetas directamente en el formulario. Cuando se selecciona una tarjeta, aparece un subtítulo negro sobre ella.

![Selección de tarjetas de datos](./media/working-with-form-layout/sales-order-data-card-selection.png)

> [!NOTE]
> Para eliminar una tarjeta (no solo ocultarla), selecciónela y presione Supr.

## <a name="arrange-cards-in-columns"></a>Organización de tarjetas en columnas
De forma predeterminada, los formularios de las aplicaciones para tableta tienen tres columnas, mientras que las aplicaciones para teléfono tienen una. Puede especificar no solo el número de columnas un formulario, sino también si todas las tarjetas deben ajustarse a los bordes de la columna.

En este gráfico, se ha cambiado el número de columnas del formulario de tres a cuatro con la casilla **Ajustar en columnas** activada. Las tarjetas del formulario se han organizado automáticamente para ajustarse al nuevo diseño.

![Pedido de ventas en un diseño básico de cuatro columnas](./media/working-with-form-layout/sales-order-form-screen-4.png)

## <a name="resize-cards-across-multiple-columns"></a>Cambio del tamaño de las tarjetas en varias columnas
En función de los datos que haya en cada tarjeta, es posible que desee que algunas tarjetas quepan en una sola columna, mientras que otras que abarcan varias columnas. Si una tarjeta contiene más datos de los que desea mostrar en una sola columna, puede ensancharla, para lo que debe seleccionarla y, después, arrastrar el controlador de agarre de los bordes izquierdo o derecho de su cuadro de selección. Al arrastrar el controlador, la tarjeta se "ajustará" a los límites de la columna.

Para aumentar la flexibilidad del diseño, pero conservar cierta estructura, puede aumentar el número de columnas a 12. Con ese cambio, puede configurar fácilmente cada tarjeta para que abarque todo el formulario, la mitad del formulario, un tercio, un cuarto, un sexto, etc. Vamos a ver esto en acción.

1. En el panel derecho, defina el número de columnas del formulario, **12**.
   
    ![Especificar número de columnas](./media/working-with-form-layout/12-columns.png)
   
    El formulario no cambia visiblemente, pero tendrá más puntos de acoplamiento al arrastrar el controlador de agarre derecho o izquierdo.
2. Para aumentar el ancho de la tarjeta **Order date**, arrastre hacia la derecha el controlador de agarre del punto de acoplamiento derecho.
   
    La tarjeta abarca cuatro de 12 columnas del formulario (o 1/3 del formulario), en lugar de solo tres de las 12 columnas del formulario (o 1/4 del formulario). Cada vez que aumenta el ancho de la tarjeta en un punto de acoplamiento, la tarjeta abarca un 1/12 adicional del formulario.
   
    ![Cambiar el tamaño de una tarjeta con arrastrar y colocar](./media/working-with-form-layout/card-resize-1.png)
3. Repita el paso anterior con las tarjetas **Order status** y **Customer purchase order reference**.
   
    ![Las tres tarjetas de la primera fila](./media/working-with-form-layout/card-resize-2.png)

4. Cambie el tamaño de las tarjetas **Name** y **Description** para que ocupen seis columnas (o 1/2) del formulario.

5. Estire las dos primeras líneas de la dirección de envío para que ocupen todo el formulario:

¡Listo! El formulario deseado, en el que se mezclan filas con distintos números de columnas, está listo:

![Pedido de ventas en diseño de 12 columnas con cambio de tamaño](./media/working-with-form-layout/card-resize-done.png)

## <a name="manipulate-controls-in-a-card"></a>Manipulación de los controles de una tarjeta
La dirección de entrega consta de varios datos que se desean mostrar de forma visualmente agrupada al usuario. Cada campo permanecerá en su propia tarjeta de datos, pero se pueden manipular los controles de la tarjeta para que se ajusten mejor juntos.

1. Seleccione la tarjeta **First line of Delivery address**, seleccione la etiqueta de dicha tarjeta y elimine las tres primeras palabras del texto.
   
    ![Dirección de entrega de pedido de venta: cambio de nombre de la etiqueta de la primera línea](./media/working-with-form-layout/delivery-address-rename.png)
2. Seleccione la tarjeta **Second line of Delivery address**, seleccione la etiqueta de dicha tarjeta y elimine todo el texto.
   
    Puede ser tentador quitar simplemente el control de etiqueta, y en muchos casos será suficiente. Sin puede que haya fórmulas que dependan de que dicho control esté presente. El enfoque más seguro es quitar el texto o establecer la propiedad **Visible** del control en **false**.
   
    ![Dirección de entrega de pedido de venta: cambio de nombre de la etiqueta de la segunda línea](./media/working-with-form-layout/delivery-address-rename-2.png)
3. En la misma tarjeta, mueva el cuadro de entrada de texto sobre la etiqueta para reducir el espacio entre la primera y la segunda línea de la dirección.
   
    El alto de la tarjeta se reduce cuando su contenido ocupa menos espacio.
   
    ![Dirección de entrega de pedido de venta: cambio de nombre de la etiqueta de la segunda línea](./media/working-with-form-layout/delivery-address-move-input.png)

Ahora se va a prestar atención a la tercera línea de dirección. De forma similar al paso anterior, se va a reducir el texto de cada etiqueta para estas tarjetas y a mover el cuadro de entrada de texto a la derecha de cada etiqueta. Estos son los pasos para la tarjeta **State**:

| Paso | Descripción | Resultado |
| --- | --- | --- |
| 1 |Seleccione la tarjeta **State** para que aparezcan controladores de agarre alrededor. |![Seleccionar una tarjeta](./media/working-with-form-layout/state-morph-2.png) |
| 2 |Seleccione la etiqueta de la tarjeta para que aparezcan controladores de agarre alrededor. |![Seleccionar un control dentro de una tarjeta](./media/working-with-form-layout/state-morph-3.png) |
| 3 |Coloque el cursor a la derecha del texto y elimine la parte que no sea necesaria. |![Cambiar el texto de un control dentro de una tarjeta](./media/working-with-form-layout/state-morph-3b.png) |
| 4 |Use los controladores de agarre de los lados y cambie el tamaño del control de etiqueta para ajustarlo al nuevo tamaño del texto. |![Cambiar el tamaño de un control dentro de una tarjeta](./media/working-with-form-layout/state-morph-4b.png) |
| 5 |Seleccione el control de entrada de texto dentro de esta tarjeta. |![Seleccionar un control diferente dentro de la tarjeta](./media/working-with-form-layout/state-morph-6.png) |
| 6 |Con los controladores de agarre de los lados, cambie el tamaño del control de entrada de texto al que desee. |![Cambiar el tamaño de un control dentro de una tarjeta](./media/working-with-form-layout/state-morph-6b.png) |
| 7 |Arrastre el cuadro de entrada de texto hacia arriba y a la derecha del control de etiqueta y suelte el cuadro de entrada de texto. |![Mover un control dentro de una tarjeta](./media/working-with-form-layout/state-morph-7b.png) |
| Las modificaciones en la tarjeta **State** están completadas. |![Modificaciones en la tarjeta completadas](./media/working-with-form-layout/state-morph-8.png) | |

El resultado de la tercera línea de dirección:

![Dirección de entrega de pedido de ventas: tercera línea más concisa](./media/working-with-form-layout/delivery-address-resize-city-1.png)

Tenga en cuenta que muchas de las tarjetas empiezan con fórmulas dinámicas para las propiedades. Por ejemplo, el control Entrada de texto cuyo tamaño hemos cambiado y encima del que nos hemos movido tenía una propiedad **Ancho** basada en el ancho de su control principal. Cuando se mueve o se cambia el tamaño de un control, estas fórmulas dinámicas se reemplazan por valores estáticos. Si lo desea, puede restaurar las fórmulas dinámicas mediante la barra de fórmulas.

## <a name="turning-off-snap-to-columns"></a>Desactivar Ajustar en columnas
A veces es conveniente proporcionar un control más preciso que el pueden hacerlo las 12 columnas estándar. Para estos casos, puede desactivar **Ajustar en columnas** y colocar las tarjetas manualmente. El formulario seguirá ajustándose a 12 columnas, pero también es posible mantener presionada la tecla Alt para colocar una tarjeta y cambiarla de tamaño manualmente como desee.

En este ejemplo, los cuatro componentes que constituyen la tercera línea de la dirección tienen exactamente la misma anchura. Pero es posible que éste no sea el diseño óptimo, ya que los nombres de ciudad son más largos que los nombres de estado y el cuadro de entrada de texto para países o regiones es corto debido a la longitud de la etiqueta.

Para optimizar este espacio, desactive **Ajustar en columnas** en el panel derecho y, después, mantenga presionada la tecla Alt mientras ajusta el tamaño y coloca estas tarjetas. Cada vez que mantenga presionada la tecla Alt, todos los controles mostrarán subtítulos negros. Este comportamiento es por diseño para mostrar los nombres de los controles.

![Posición y cambio de tamaño con la tecla ALT presionada](./media/working-with-form-layout/delivery-address-alt-resize.png)

Después de colocarlas con cuidado, se logran tamaños adecuados para cada campo y un espaciado horizontal uniforme entre los campos:

![Dirección de entrega de pedido de venta: tercera línea en la posición correcta](./media/working-with-form-layout/delivery-address-resize-city-2.png)

En resumen, ¿cuáles son las diferencias cuando la opción **Ajustar en columnas** está activada y desactivada?

| Comportamiento | Ajustar en columnas activada | Ajustar en columnas desactivada |
| --- | --- | --- |
| El cambio de tamaño se ajusta a |Número de columnas que selecciona:<br>1, 2, 3, 4, 6 o 12 |12 columnas |
| Se puede invalidar el ajuste de cambio de tamaño |No |Sí, con la tecla Alt |
| Se cambia el diseño de las tarjetas automáticamente entre filas (se explica más adelante) |Sí |No |

## <a name="set-width-and-height"></a>Establecer ancho y alto
Como con todo en PowerApps, el diseño del formulario se rige por las propiedades de los controles de tarjeta. Como ya se ha descrito, para cambiar los valores de estas propiedades tiene que arrastrar controles a ubicaciones diferentes o arrastrar los controladores de agarre para cambiar el tamaño de los controles. Pero encontrará situaciones en las que deseará conocer y manipular estas propiedades con mayor precisión, especialmente al usar fórmulas para que los formularios sean dinámicos.

### <a name="basic-layout-x-y-and-width"></a>Diseño básico: X, Y y Ancho
Las propiedades **X** e **Y** controlan la posición de las tarjetas. Cuando se trabaja con controles en el lienzo en blanco, estas propiedades proporcionan una posición absoluta. En un formulario, estas propiedades tienen un significado diferente:

* **X**: orden dentro de una fila.
* **Y**: número de fila.

De forma similar a los controles en el lienzo, la propiedad **Ancho** especifica la anchura mínima de la tarjeta (más información sobre el aspecto mínimo en un momento).

Aquí se ven las propiedades **X**, **Y** y **Ancho** de las tarjetas en el formulario:

![Formulario de pedido de ventas: coordenadas X e Y](./media/working-with-form-layout/sales-order-xy.png)

### <a name="overflowing-rows"></a>Filas desbordantes
¿Qué ocurre si las tarjetas de una fila son demasiado anchas para caber en ella? Por lo general, no es necesario que se preocupe por esta posibilidad. Con la opción **Ajustar en columnas** activada, estas tres propiedades se ajustarán automáticamente para que todo quepa en las filas sin desbordarse.

Sin embargo, con la opción **Ajustar en columnas** desactivada o con una propiedad**Ancho** basada en fórmula en una o varias de las tarjetas, puede que se desborde una fila. En este caso, las tarjetas se ajustarán automáticamente para que se cree otra fila. Por ejemplo, se cambia manualmente la propiedad **Ancho** de la tarjeta **Referencia de pedido de compra de cliente** (primera fila, tercer elemento) a **500**:

![Cambio de tamaño manual de la tarjeta, redistribución a una nueva fila](./media/working-with-form-layout/manual-size-500.png)

Las tres tarjetas de la fila superior ya no caben horizontalmente y que se ha creado una fila para ajustar lo que desborda. La coordenada **Y** de todas estas tarjetas sigue siendo la misma, 0, mientras que las tarjetas **Nombre** y **Descripción** siguen teniendo 1 como valor de **Y**. Las tarjetas que tienen diferentes valores de **Y** no se combinan en filas.

Este comportamiento se puede usar para crear un diseño totalmente dinámico en el que las tarjetas se colocan en función de un orden Z, rellenando el mayor espacio posible antes de pasar a la siguiente fila. Para lograr este efecto, asigne a todas las tarjetas el mismo valor de **Y** y use **X** para el orden de las tarjetas.

### <a name="filling-spaces-widthfit"></a>Rellenar espacios: WidthFit (AjusteDeAncho)
El desbordamiento del último ejemplo creaba un espacio después de **Estado de pedido**, que era la segunda tarjeta de la primera fila. Se podrían ajustar manualmente los valores de la propiedad **Ancho** de las dos tarjetas restantes para llenar este espacio, pero este método es tedioso.

Como alternativa, use la propiedad **WidthFit** (AjusteDeAncho). Si esta propiedad establecida en **True** en una o varias tarjetas de una fila, el espacio restante de la fila se dividirá uniformemente entre ellas. A este comportamiento es a lo que se debe que antes se indicara que la propiedad **Ancho** de una tarjeta es un *mínimo* y que lo que se ve en realidad puede ser más ancho. Esta propiedad nunca hará que una tarjeta encoja, solo que se expanda.

Si en **WidthFit** (AjusteDeAncho) se selecciona **true** en la tarjeta **Order status**, rellena el espacio disponible, mientras que la primera tarjeta permanece sin cambios:

![WidthFit (AjusteDeAncho) establecida en True en la segunda tarjeta](./media/working-with-form-layout/manual-widthfit-1.png)

Si **WidthFit** (AjusteDeAncho) también se establece en **true** en la tarjeta **Fecha de pedido**, ambas tarjetas se dividirán uniformemente el espacio disponible:

![WidthFit (AjusteDeAncho) establecida en True en la primera y segunda tarjeta](./media/working-with-form-layout/manual-widthfit-2.png)

Observe que los controles de agarre en estas tarjetas tienen en cuenta el ancho adicional proporcionado por **WidthFit** (AjusteDeAncho), no el ancho mínimo proporcionado por la propiedad **Ancho**. Puede resultar confuso manipular la propiedad **Ancho** con la propiedad **WidthFit** (AjusteDeAncho) activada; puede desactivarla, realizar cambios en **Ancho** y volver a activarla.

¿Cuando podría ser útil **WidthFit** (AjusteDeAncho)? Si tiene un campo que se usa solo en determinadas situaciones, puede establecer su propiedad **Visible** en **false** y las restantes tarjetas de la fila rellenarán automáticamente el espacio alrededor de ella. Puede usar una fórmula que muestre un campo solo cuando otro campo tenga un valor determinado.

En este caso, se establecerá la propiedad **Visible** del campo **Estado de pedido** en un valor **false** estático:

![WidthFit (AjusteDeAncho) establecida en True en la primera tarjeta con Estado de pedido invisible](./media/working-with-form-layout/manual-widthfit-3.png)

Con la segunda tarjeta eliminada en la práctica, la tercera tarjeta ahora puede volver a la misma fila que la primera. La primera tarjeta aún tiene la propiedad **WidthFit** (AjusteDeAncho) establecida en **true**, por lo que es la única que se expande para rellenar el espacio disponible.

Dado que **Order status** no se ve, no se puede seleccionar fácilmente en el lienzo. Sin embargo, puede seleccionar cualquier control, visible o no, de la lista jerárquica de controles en el lado izquierdo de la pantalla.

### <a name="height"></a>Alto
La propiedad **Alto** rige la altura de cada tarjeta. Las tarjetas tienen el equivalente de **WidthFit** (AjusteDeAncho) para **Alto**, y siempre se establece en **true**. Imagine que un existe una propiedad **HeightFit** (AjusteDeAlto), pero no lo busca en el producto porque dicha propiedad aún no está expuesta.

No se puede desactivar este comportamiento, por lo que cambiar la altura de las tarjetas puede ser complicado. Todas las tarjetas de una fila parecen tener la misma altura que la tarjeta más alta. La fila podría ser similar a la siguiente:

![WidthFit (AjusteDeAncho) establecida en true en la primera tarjeta con estado de pedido invisible](./media/working-with-form-layout/height-3.png)

¿Qué tarjeta determina la altura de la fila? En el gráfico anterior, la tarjeta **Importe total** está seleccionada y parece alta, pero su propiedad **Alto** está establecida en **80** (la misma altura que la primera fila). Para reducir el alto de una fila, debe reducir la propiedad **Alto** de la tarjeta más alta de dicha fila, pero dicha tarjeta no se puede identificar sin examinar la propiedad **Alto** de cada tarjeta.

### <a name="autoheight"></a>AutoHeight (AlturaAutomática)
U na tarjeta también puede ser más alta de lo esperable si contiene un control cuya propiedad **AutoHeight** (AlturaAutomática) está establecida en **true**. Por ejemplo, muchas tarjetas contienen una etiqueta que muestra un mensaje de error si el valor del campo provoca un problema de validación.

Si no hay texto para mostrar (no hay error), la etiqueta se contrae a una altura de valor cero. Si no lo supiera, no se daría cuenta de que está ahí, que es como debería ser:

![Las tarjetas que contienen controles con AutoHeight (AlturaAutomática) establecida en True se muestran sin altura](./media/working-with-form-layout/autoheight-0.png)

A la izquierda de la pantalla, la lista de controles muestra **ErrorMessage1** (MensajeDeError1), que es el control de etiqueta. Al actualizar una aplicación, puede seleccionar este control para darle cierta altura y mostrar controladores de agarre con los que se puede colocar y ajustar su tamaño. Una "A" en un cuadro azul indica que el control tiene la propiedad **AutoHeight** (AlturaAutomática) establecido en **true**:

![Durante la creación, los controles de AutoHeight (AlturaAutomática) muestran cierta altura, lo que hace que arrastrarlos y colocarlos sea más fácil.](./media/working-with-form-layout/autoheight-1.png)

La propiedad **Texto** de este control está establecida en **Parent.Error**, que se usa para obtener información de error dinámica basada en reglas de validación. Con fines meramente ilustrativos, vamos a establecer de manera estática la propiedad **Texto** de este control, lo que aumentará su altura (y, por extensión, la de la tarjeta) para acomodarse a la longitud del texto:

![Con un mensaje de error, el control y la tarjeta crecen de forma automática](./media/working-with-form-layout/autoheight-2.png)

Si el mensaje de error es un poco más largo, de nuevo el control y la tarjeta crecen para darle cabida. Tenga en cuenta que la fila en general crece a lo alto, conservando la alineación vertical entre las tarjetas:

![Con un mensaje de error más largo, el control y la tarjeta crecen aún más; observe que las tarjetas en la misma fila crecen todas juntas](./media/working-with-form-layout/autoheight-3.png)

