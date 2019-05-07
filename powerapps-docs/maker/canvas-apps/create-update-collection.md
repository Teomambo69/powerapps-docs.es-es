---
title: Crear y actualizar una colección en una aplicación de lienzo | Microsoft Docs
description: Crear una colección en una aplicación de lienzo, agregar elementos a la colección y quitar uno o todos los elementos
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/28/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6089063e2478c95bb5bfbc5926608d85552cea40
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61561735"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Crear y actualizar una colección en una aplicación de lienzo

Usar una colección para almacenar los datos que los usuarios pueden administrar en la aplicación. Una colección es un grupo de elementos que son similares, como los productos en una lista de productos. Para obtener más información acerca de diferentes tipos de variables como colecciones: [Descripción de las variables de aplicación de lienzo](working-with-variables.md).

## <a name="prerequisites"></a>Requisitos previos

- [Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.
- Cree una aplicación o abra una existente en PowerApps.
- Aprenda a [configurar un control](add-configure-controls.md) en PowerApps.

## <a name="create-a-multicolumn-collection"></a>Crear una colección de varias columnas

1. En PowerApps Studio, agregue un **entrada de texto** control.

    ![Insertar un control de entrada de texto](./media/create-update-collection/add-textbox.png)

1. Cambie el nombre del control seleccionando los puntos suspensivos en el panel de navegación izquierdo, seleccione **cambiar el nombre de**y, a continuación, escriba **ProductName**.

    ![Cambiar el nombre de un control](./media/create-update-collection/rename-textbox.png)

1. Agregar un **desplegable** control.

    ![Agregar lista desplegable](./media/create-update-collection/add-dropdown.png)

1. Cambiar el nombre de la **desplegable** control **colores**y asegúrese de que el **elementos** propiedad está seleccionada en la lista de propiedades.

    ![Propiedad Items](./media/create-update-collection/items-property.png)

1. En la barra de fórmulas, reemplace **DropDownSample** con esta expresión:

    `["Red";"Green";"Blue"]`

1. Agregar un **botón** , establezca su **texto** propiedad **"Agregar"** y establezca su **OnSelect** propiedad en esta fórmula:

    ```powerapps-comma
    Collect(
        ProductList;
        {
            Product: ProductName.Text;
            Color: Colors.Selected.Value
        }
    )
    ```

1. Presione F5, escriba algún texto en **ProductName**, seleccione una opción en **colores**y, a continuación, seleccione **agregar**.

    ![Vista previa de la aplicación](./media/create-update-collection/preview-add.png)

1. Repita el paso anterior al menos dos veces y, a continuación, presione Esc.

1. En el **archivo** menú, seleccione **colecciones** para mostrar la colección que ha creado.

    ![Mostrar la colección](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>Mostrar una colección

1. Agregar una vertical **galería** control.

    ![Agregar una galería vertical](./media/create-update-collection/add-gallery.png)

1. La galería **elementos** propiedad **Listadeproductos**.

1. En el **datos** panel, establezca el campo de subtítulo en **Color**y establezca el campo de título en **producto**.

    ![Establezca la propiedad Items de la galería y cambie los campos que muestra](./media/create-update-collection/configure-gallery.png)

1. Cerrar la **datos** panel, seleccione la galería y, a continuación, establezca el **diseño** campo **título y subtítulo**.

    ![Establezca la propiedad Items de la galería y cambie los campos que muestra](./media/create-update-collection/change-layout.png)

    La pantalla es similar a este ejemplo:

    ![Primer ejemplo de la pantalla](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>Quitar uno o todos los elementos

1. Seleccione la plantilla de la galería haciendo clic en o pulsar cerca de la parte inferior de la galería y, a continuación, haciendo clic o pulsando el icono de lápiz junto a la esquina superior izquierda.

    ![Seleccione la plantilla de la Galería](./media/create-update-collection/select-template.png)

1. Agregar un **Papelera** icono para la plantilla de la galería.

    ![Agregar icono de Papelera](./media/create-update-collection/trash-icon.png)

1. Establecer el icono **OnSelect** propiedad en esta fórmula:

    `Remove(ProductList; ThisItem)`

1. Fuera de la galería, agregue un botón, establezca su **texto** propiedad **"Borrar"** y establezca su **OnSelect** propiedad en esta fórmula:

    `Clear(ProductList)`

1. Mientras mantiene presionada la tecla Alt, seleccione el **Papelera** icono de un elemento para quitar ese elemento de la colección, o seleccione el **clara** botón Quitar todos los elementos de la colección.

## <a name="put-a-sharepoint-list-into-a-collection"></a>Colocar una lista de SharePoint en una colección

1. [Cree una conexión a una lista de SharePoint](connections/connection-sharepoint-online.md#create-a-connection).

1. Agregue un botón y establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta función, sustituyendo *ListName* por el nombre de la lista de SharePoint:<br>

    `Collect(MySPCollection; ListName)`

    Esta función crea una colección que se denomina **MySPCollection** y que contiene los mismos datos que la lista de SharePoint.

1. Mientras mantiene presionada la tecla Alt, seleccione el botón.

1. (opcional) Para obtener una vista previa de la colección que ha creado, seleccione **colecciones** en el **archivo** menú.

Para obtener información acerca de cómo mostrar datos de una lista de SharePoint (por ejemplo, fechas, las opciones y las personas) en una galería: [Mostrar columnas de la lista en una galería](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery). Para obtener información acerca de cómo mostrar datos en un formulario (con las listas desplegables, los selectores de fecha y selectores de personas): [Controles de formulario de presentación y formulario de edición](controls/control-form-detail.md).

## <a name="next-steps"></a>Pasos siguientes

- Revise el [tema de referencia](functions/function-clear-collect-clearcollect.md) para el **recopilar** función.
- Obtenga información sobre cómo dar forma a datos en una colección mediante el uso de la [AddColumns, DropColumns, Cambiarnombrecolumnas y Mostrarcolumnas](functions/function-table-shaping.md) funciones.
