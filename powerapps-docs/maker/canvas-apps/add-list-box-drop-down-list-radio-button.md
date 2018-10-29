---
title: Adición de un cuadro de lista, una lista desplegable o botones de selección a una aplicación de lienzo | Microsoft Docs
description: En PowerApps, cree o configure opciones de selección múltiple en una aplicación de lienzo.
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 293c850c5af980a480a56cb9fb3b8c7866950580
ms.sourcegitcommit: 097ddfb25eb0f09f0229b866668c2b02fa57df55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49991755"
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons-to-a-canvas-app"></a>Adición de un cuadro de lista, una lista desplegable o botones de selección a una aplicación de lienzo

Muestre una sola columna de datos (por ejemplo, de una tabla de varias columnas) en una aplicación de lienzo para que los usuarios puedan seleccionar uno o varios elementos de una lista.

- Agregue un cuadro de lista para permitir a los usuarios seleccionar más de una opción.
- Agregue una lista desplegable para que ocupe menos espacio en una pantalla.
- Agregue un conjunto de botones de selección para obtener un efecto de diseño concreto.

Este tema se centra en los cuadros de listas y botones de selección, pero los mismos principios se aplican a las listas desplegables.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-simple-list"></a>Creación de una lista sencilla

1. Agregue un control **Cuadro de lista**, denomínelo **MyListBox** y establezca su propiedad **Elementos** en esta expresión:

    ```["circle","triangle","rectangle"]```  <br/>

    El diseñador tendrá un aspecto similar al siguiente:

    ![][4]

4. En la pestaña **Insertar**, seleccione **Iconos**, seleccione el círculo y sitúelo bajo **MyListBox**:

    ![][5]  

5. Agregue un triángulo y un rectángulo y, después, disponga las formas en una fila bajo **MyListBox**:

    ![][6]  

6. Defina la propiedad **[Visible](controls/properties-core.md)** de las formas siguientes con las funciones indicadas a continuación:  

   | Forma | Establecer función de Visible en |
   | --- | --- |
   | círculo |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | triángulo |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | rectángulo |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Mientras mantiene presionada la tecla Alt, seleccione una o varias formas en **MyListBox**.

    Solo se mostrarán aquellas formas que seleccione.

En estos pasos, ha utilizado una expresión para crear una lista de elementos. Esto es aplicable a otros elementos de su negocio. Por ejemplo, puede usar un control **desplegable** para mostrar imágenes de productos, descripciones de productos, etc.

## <a name="add-radio-buttons"></a>Adición de botones de selección
1. En la pestaña **Inicio**, seleccione **Nueva pantalla** y luego **En blanco**.

2. En la pestaña **Insertar**, seleccione **Controles** y, a continuación, seleccione **Botón de selección**.

    ![][10]  

3. Cambie el nombre del control **Botón de selección** por **Choices** y establezca la siguiente fórmula para la propiedad **[Elementos](controls/properties-core.md)**:  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    Si es necesario, cambie el tamaño del control para mostrar todas las opciones.

4. En la pestaña **Insertar**, seleccione **Iconos** y, a continuación, seleccione el círculo.

5. Defina la siguiente función para la propiedad **[Fill](controls/properties-color-border.md)** del círculo:  
   ```If(Choices.Selected.Value = "red", Red, Choices.Selected.Value = "green", Green, Choices.Selected.Value = "blue", Blue)```  

    En esta fórmula, el círculo cambia de color dependiendo de qué botón de selección elija.

6. Sitúe el círculo bajo el control **Botón de selección**, como en este ejemplo:

    ![][14]  

7. Mientras mantiene presionada la tecla Alt, seleccione otro botón de selección para cambiar el color del círculo.

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png
