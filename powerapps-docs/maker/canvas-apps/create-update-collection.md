---
title: Crear y actualizar una colección en una aplicación de lienzo | Microsoft Docs
description: Crear una colección en una aplicación de lienzo, agregar elementos a la colección y quitar uno o todos los elementos de él
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/28/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 375c4f19ed7715eed662c8456c539d5590c9f1ec
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993212"
ms.PowerAppsDecimalTransform: true
---
# <a name="create-and-update-a-collection-in-a-canvas-app"></a>Crear y actualizar una colección en una aplicación de lienzo

Use una colección para almacenar los datos que los usuarios pueden administrar en la aplicación. Una colección es un grupo de elementos que son similares, como los productos de una lista de productos. Para obtener más información sobre los distintos tipos de variables, como las colecciones: [Descripción de las variables de la aplicación Canvas](working-with-variables.md).

## <a name="prerequisites"></a>Requisitos previos

- [Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.
- Cree una aplicación o abra una existente en PowerApps.
- Aprenda a [configurar un control](add-configure-controls.md) en PowerApps.

## <a name="create-a-multicolumn-collection"></a>Crear una colección de varias columnas

1. En PowerApps Studio, agregue un control **entrada de texto** .

    ![Insertar un control de entrada de texto](./media/create-update-collection/add-textbox.png)

1. Cambie el nombre del control; para ello, seleccione sus puntos suspensivos en el panel de navegación izquierdo, seleccione **cambiar nombre**y, a continuación, escriba **ProductName**.

    ![Cambiar el nombre de un control](./media/create-update-collection/rename-textbox.png)

1. Agregue un control **lista** desplegable.

    ![Agregar lista desplegable](./media/create-update-collection/add-dropdown.png)

1. Cambie el nombre **de los** **colores**del control desplegable y asegúrese de que la propiedad **elementos** está seleccionada en la lista de propiedades.

    ![Propiedad Items](./media/create-update-collection/items-property.png)

1. En la barra de fórmulas, reemplace **DropDownSample** por esta expresión:

    `["Red";"Green";"Blue"]`

1. Agregue un control **botón** , establezca su propiedad **texto** en **"agregar"** y establezca su propiedad **alseleccionar** en esta fórmula:

    ```powerapps-comma
    Collect(
        ProductList;
        {
            Product: ProductName.Text;
            Color: Colors.Selected.Value
        }
    )
    ```

1. Presione F5, escriba el texto en **NombreProducto**, seleccione una opción en **colores**y, a continuación, seleccione **Agregar**.

    ![Vista previa de la aplicación](./media/create-update-collection/preview-add.png)

1. Repita el paso anterior al menos dos veces más y, a continuación, presione ESC.

1. En el menú **archivo** , seleccione **colecciones** para mostrar la colección que ha creado.

    ![Mostrar colección](./media/create-update-collection/show-collection.png)

## <a name="show-a-collection"></a>Mostrar una colección

1. Agregue un control **Galería** vertical.

    ![Agregar una galería vertical](./media/create-update-collection/add-gallery.png)

1. Establezca la propiedad **elementos** de la galería en **productlist**.

1. En el panel **datos** , establezca el campo subtítulo en **color**y establezca el campo título en **producto**.

    ![Establecer la propiedad elementos de la galería y cambiar los campos que se muestran](./media/create-update-collection/configure-gallery.png)

1. Cierre el panel **datos** , seleccione la galería y, a continuación, establezca el campo **diseño** en **título y subtítulo**.

    ![Establecer la propiedad elementos de la galería y cambiar los campos que se muestran](./media/create-update-collection/change-layout.png)

    La pantalla es similar a la de este ejemplo:

    ![Ejemplo de primera pantalla](./media/create-update-collection/screen-example1.png)

## <a name="remove-one-or-all-items"></a>Quitar uno o todos los elementos

1. Seleccione la plantilla de la Galería haciendo clic o pulsando cerca de la parte inferior de la galería y haciendo clic o pulsando en el icono de lápiz situado cerca de la esquina superior izquierda.

    ![Seleccionar plantilla de la galería](./media/create-update-collection/select-template.png)

1. Agregue un icono de **papelera** a la plantilla de la galería.

    ![Icono Agregar papelera](./media/create-update-collection/trash-icon.png)

1. Establezca la propiedad **alseleccionar** del icono en esta fórmula:

    `Remove(ProductList; ThisItem)`

1. Fuera de la galería, agregue un botón, establezca su propiedad **Text** en **"Clear"** y establezca su propiedad **alseleccionar** en esta fórmula:

    `Clear(ProductList)`

1. Mientras mantiene presionada la tecla Alt, seleccione el icono de la **papelera** de un elemento para quitar ese elemento de la colección o seleccione el botón **Borrar** para quitar todos los elementos de la colección.

## <a name="put-a-sharepoint-list-into-a-collection"></a>Colocar una lista de SharePoint en una colección

1. [Cree una conexión a una lista de SharePoint](connections/connection-sharepoint-online.md#create-a-connection).

1. Agregue un botón y establezca su propiedad **[OnSelect](controls/properties-core.md)** en esta función, sustituyendo *ListName* por el nombre de la lista de SharePoint:<br>

    `Collect(MySPCollection; ListName)`

    Esta función crea una colección que se denomina **MySPCollection** y que contiene los mismos datos que la lista de SharePoint.

1. Mientras mantiene presionada la tecla Alt, seleccione el botón.

1. opta Para obtener una vista previa de la colección que ha creado, seleccione **colecciones** en el menú **archivo** .

Para obtener información sobre cómo mostrar los datos de una lista de SharePoint (como fechas, elecciones y personas) en una galería: [Mostrar las columnas de la lista en una galería](connections/connection-sharepoint-online.md#show-list-columns-in-a-gallery). Para obtener información sobre cómo mostrar los datos en un formulario (con listas desplegables, selectores de fechas y selectores de personas): [Editar formulario y mostrar controles de formulario](controls/control-form-detail.md).

## <a name="next-steps"></a>Pasos siguientes

- Revise el [tema de referencia](functions/function-clear-collect-clearcollect.md) de la función **Collect** .
- Obtenga información sobre cómo dar forma a los datos de una colección mediante las funciones [AddColumns, DropColumns, cambiarnombrecolumnas y mostrarcolumnas](functions/function-table-shaping.md) .
