---
title: 'Control Tabla de datos: referencia | Microsoft Docs'
description: Información sobre el control Tabla de datos, con propiedades y ejemplos
author: jasongre
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/05/2017
ms.author: jasongre
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fb7c2ac88c24197d014ebdc1b2b6a50e4802e0bf
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63319375"
---
# <a name="data-table-control-in-powerapps"></a>Control Tabla de datos en PowerApps
Muestra un conjunto de datos en formato tabular.

## <a name="description"></a>Descripción
El control **Tabla de datos** muestra un conjunto de datos en un formato que incluye encabezados de columna para cada campo que el control muestra. Como responsable de una aplicación, tiene control total sobre los campos que aparecen y en qué orden. Al igual que en el control **Galería**, el control **Tabla de datos** mantiene una propiedad **Seleccionado** que apunta a la única fila seleccionada. Por lo tanto, puede vincular el control **Tabla de datos** a otros controles.

## <a name="capabilities"></a>Funcionalidades
PowerApps implementó el control **Tabla de datos** el 5 de mayo de 2017. En esta sección se proporciona información sobre las funcionalidades compatibles e incompatibles.

### <a name="now-available"></a>Ahora disponible
* Los datos de un control **Tabla de datos** es de solo lectura.
* En los controles **Tabla de datos** siempre se selecciona una única fila.
* Vincule un control **Tabla de datos** a un origen de datos local o conectado.
* Ajuste el ancho de las columnas del control **Tabla de datos** mientras se ejecuta la aplicación, aunque los cambios no se guardan.
* En el control **Tabla de datos** aparece un conjunto de campos predeterminados cuando se vincula a un conector con esta funcionalidad implementada, como Common Data Service. A continuación, puede mostrar u ocultar estos y otros campos según sea necesario.
* Personalice el ancho de la columna y el texto de encabezado.
* Muestre los hipervínculos en un control **Tabla de datos**.
* Copie y pegue un control **Tabla de datos**.

### <a name="not-yet-available"></a>Aún no está disponible
* Personalice el estilo de las columnas individuales.
* Agregue un control **Tabla de datos** a un control de formulario.
* Cambie el alto de todas las filas.
* Muestre imágenes en un control **Tabla de datos**.
* Muestre campos de entidades relacionadas.
* Utilice la funcionalidad integrada para filtrar y ordenar los datos por encabezado de columna.
* Agregue un control **Tabla de datos** a un control de formulario**Galería**.
* Edite datos en el control **Tabla de datos**.
* Seleccione varias filas.

### <a name="known-issues"></a>Problemas conocidos
* No aparecen datos al usar la función **FirstN** en la propiedad **Elementos**.

## <a name="key-properties"></a>Propiedades principales
* [**Elementos**](properties-core.md): el origen de datos que aparece en el control **Tabla de datos**.
* **Seleccionado**: la fila seleccionada en el control **Tabla de datos**.

## <a name="other-properties"></a>Otras propiedades
* [**ColorDeLosBordes**](properties-color-border.md): el color del borde del control **Tabla de datos**.
* [**EstiloDelBorde**](properties-color-border.md): el estilo del borde del control **Tabla de datos**. Las opciones son **Sólido**, **Rayado**, **Punteado** y **Ninguno**.
* [**GrosorDelBorde**](properties-color-border.md): el grosor del borde del control **Tabla de datos**.
* [**Color**](properties-color-border.md): el color de texto predeterminado para todas las filas de datos.
* [**Relleno**](properties-color-border.md): el color de fondo predeterminado para todas las filas de datos.
* [**Fuente**](properties-text.md): la fuente predeterminada para todas las filas de datos.
* [**EspesorDeFuente**](properties-text.md): el espesor de fuente predeterminado para todas las filas de datos.
* **HeadingColor** (ColorDeEncabezado): el color del texto de los encabezados de columna.
* **HeadingFill** (RellenoDeEncabezado): el color de fondo de los encabezados de columna.
* **HeadingFont** (FuenteDeEncabezado): la fuente de los encabezados de columna.
* **HeadingFontWeight** (EspesorDeFuenteDeEncabezado): el espesor de fuente de los encabezados de columna.
* **HeadingSize** (TamañoDeEncabezado): el tamaño de fuente de los encabezados de columna.
* [**Altura**](properties-size-location.md): la distancia entre los bordes superior e inferior del control **Tabla de datos**.
* [**ColorAlMantener**](properties-color-border.md): el color del texto de la fila a la cual apunta el puntero del mouse.
* [**RellenoAlMantener**](properties-color-border.md): el color del fondo de la fila a la cual apunta el puntero del mouse.
* **NoDataText** (SinTextoEnLosDatos): el mensaje que el usuario recibe cuando no hay registros para mostrar en el control **Tabla de datos**.
* **SelectedColor** (ColorSeleccionado): el color del texto de la fila seleccionada.
* **SelectedFill** (RellenoSeleccionado): el color de fondo de la fila seleccionada.
* [**Tamaño**](properties-text.md): el tamaño de fuente predeterminado para todas las filas de datos.
* [**Visible**](properties-core.md): un valor que determina si el control **Tabla de datos** aparece o está oculto.
* [**Ancho**](properties-size-location.md): la distancia entre los bordes derecho e izquierdo del control **Tabla de datos**.
* [**X**](properties-size-location.md): la distancia entre el borde izquierdo del control **Tabla de datos** y el borde izquierdo de su contenedor principal (o el borde izquierdo de la pantalla si no hay contenedor principal).
* [**Y**](properties-size-location.md): la distancia entre el borde superior del control **Tabla de datos** y el borde superior de su contenedor principal (o el borde superior de la pantalla si no hay contenedor principal).

## <a name="related-functions"></a>Funciones relacionadas
* [**Filtro (Origen de datos, Fórmula)**](../functions/function-filter-lookup.md)(*Origen de datos*, *Fórmula*)
* [**Búsqueda (Origen de datos, SearchString [BuscarCadena], Columna)**](../functions/function-filter-lookup.md)(*Origen de datos*, *SearchString* [BuscarCadena], *Columna*)

## <a name="examples"></a>Ejemplos
### <a name="basic-usage"></a>Uso básico
1. Cree una aplicación de tableta vacía.
2. En la pestaña **Insertar**, pulse o haga clic en **Tabla de datos**.
   
    ![Agregar un control Tabla de datos a una pantalla](./media/control-data-table/insert-data-table.png)
   
    Se agrega un control **Tabla de datos** a la pantalla.
3. Cambie el nombre de **SalesOrderTable** (TablaDePedidosDeVentas) del control **Tabla de datos** y auméntele el tamaño de modo que cubra toda la pantalla.
4. En el panel derecho, haga clic o pulse en la flecha abajo a la derecha del texto **No se ha seleccionado un origen de datos** y en **Agregar un origen de datos**.
   
    ![Agregar un origen de datos](./media/control-data-table/add-data-to-data-table.png)
5. En la lista de conexiones, pulse o haga clic en la conexión para la base de datos de Common Data Service.
   
    ![Seleccionar la conexión para el origen de datos](./media/control-data-table/choose-cds-data-table.png)
6. En la lista de entidades, haga clic o pulse en **Pedido de ventas** y en **Conectar**.
   
    ![Selección de la entidad Pedido de ventas](./media/control-data-table/choose-so-data-table.png)
   
    El control **Tabla de datos** está ahora conectado al origen de datos **Pedido de ventas**. En el control **Tabla de datos** aparecen varios campos iniciales, ya que se usa un conector que admite esa funcionalidad.
   
    ![Tabla de datos](./media/control-data-table/pre-order-data-table.png)
7. En el panel derecho, seleccione una o más casillas para mostrar u ocultar campos.
   
    Por ejemplo, seleccione la casilla junto al campo **CustomerPurchaseOrderReference** (ReferenciaDelPedidoDeCompraDelCliente) para ocultarlo.
8. Para volver a ordenar los campos, arrástrelos hacia arriba o hacia abajo en el panel derecho.
   
    ![Cambiar el orden de los campos según sea necesario](./media/control-data-table/field-re-order-data-table.png)
   
    El control **SalesOrderTable** (TablaDePedidosDeVentas) muestra los campos en el orden especificado.
   
    ![Tabla de datos actualizada](./media/control-data-table/post-order-data-table.png)

### <a name="restyle-the-header-for-the-data-table-control"></a>Cambio de estilo del encabezado para el control Tabla de datos
1. Con el control **Tabla de datos** seleccionado, pulse o haga clic en la pestaña **Avanzado** en el panel derecho.
2. Pulse o haga clic en el campo para la propiedad **HeadingFill** (RellenoDeEncabezado) y cambie el valor a **RGBA(62,96,170,1)**.
3. Pulse o haga clic en el campo para la propiedad **HeadingColor** (ColorDeEncabezado) y cambie el valor a **White** (Blanco).
4. Pulse o haga clic en el campo para la propiedad **HeadingSize** (TamañoDeEncabezado) y cambie el valor a **14**.
   
    ![Tabla de datos](./media/control-data-table/restyled-data-table.png)

### <a name="connect-a-data-table-control-to-another-control"></a>Conexión de un control Tabla de datos a otro control
1. Agregue un control **Formulario de edición** a la pantalla.
2. Cambie el tamaño de los controles **Tabla de datos** y **Editar formulario** de forma que el control **Tabla de datos** aparezca en la parte izquierda de la pantalla y el control **Editar formulario**, en la parte derecha.
   
    ![Tabla de datos y Editar formulario en la misma pantalla](./media/control-data-table/data-table-empty-form.png)
3. Con **Form1** seleccionado, en el panel derecho, cambie el número de columnas a **1**.
4. Conecte **Form1** al origen de datos **Pedido de ventas**.
   
    En **Form1** aparecen varios campos iniciales.
   
    ![Form1 con campos iniciales](./media/control-data-table/data-table-disconnected-form.png)
5. En el panel derecho, pulse o haga clic en la pestaña **Avanzado**.
6. Establezca la propiedad **Elementos** De **Form1** en **SalesOrderTable.Selected** (TablaDePedidosDeVentas.Seleccionado).
   
    **Form1** muestra información de la fila que está seleccionada en el control **Tabla de datos**.
   
    ![Editar formulario conectado a Tabla de datos](./media/control-data-table/connected-form-data-table.png)


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* [**Color**](properties-color-border.md) y [**Fill**](properties-color-border.md)
* **HeadingColor** y **HeadingFill**
* **SelectedColor** y **SelectedFill**
* [**HoverColor**](properties-color-border.md) y [**HoverFill**](properties-color-border.md)

Y esto, además de los [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **NoDataText** debe existir.
