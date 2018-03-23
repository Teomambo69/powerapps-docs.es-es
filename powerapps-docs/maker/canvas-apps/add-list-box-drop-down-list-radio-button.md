---
title: Adición de un cuadro de lista, una lista desplegable y botones de selección | Microsoft Docs
description: Creación o configuración de opciones de selección múltiple en PowerApps
services: ''
suite: powerapps
documentationcenter: ''
author: lonu
manager: anneta
editor: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/23/2016
ms.author: lonu
ms.openlocfilehash: 8eacac89f7578a83757299b8e627cf757fb1c6d7
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons"></a>Adición de un cuadro de lista, una lista desplegable o botones de selección
PowerApps incluye opciones de selección múltiple y de selección única, como un cuadro de lista, una lista desplegable y botones de selección. En este tema, añadiremos estos controles y usaremos una fórmula de **Tabla** para crear las listas. Cuando se selecciona un elemento de la lista, se actualizan otros controles.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="add-a-list-box"></a>Adición de un cuadro de lista
1. En la pestaña **Insertar**, seleccione **Controles** y, a continuación, seleccione **Cuadro de lista**:  

    ![][2]  

2. Cambie el nombre del control **Cuadro de lista** por **MyListBox**:  

    ![][3]

3. Establezca la propiedad **[Elementos](controls/properties-core.md)** en la siguiente expresión:  
   ```["circle","triangle","rectangle"]```  <br/>

    El diseñador tendrá un aspecto similar al siguiente:

    ![][4]

4. En la pestaña **Insertar**, seleccione **Iconos**, seleccione el círculo y sitúelo bajo el control **Cuadro de lista**:

    ![][5]  

5. Añada un triángulo y un rectángulo y, a continuación, disponga las formas en una fila bajo el control **Cuadro de lista**:

    ![][6]  

6. Defina la propiedad **[Visible](controls/properties-core.md)** de las formas siguientes con las funciones indicadas a continuación:  

   | Forma | Establecer función de Visible en |
   | --- | --- |
   | círculo |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | triángulo |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | rectángulo |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Obtenga una vista previa de lo que ha creado: ![][1]. Seleccione las diferentes formas en el control **Cuadro de lista**. Solo se mostrarán aquellas formas que seleccione. Presione Esc o seleccione **X** para volver a la pantalla.

En estos pasos, ha utilizado una expresión para crear una lista de elementos en un control **Cuadro de lista**. En función de lo que se seleccione en el control **Cuadro de lista**, se muestran distintas formas. Esto es aplicable a otros elementos de su negocio. Por ejemplo, puede usar un control **Cuadro de lista** para mostrar imágenes de productos, descripciones de productos, etc.

## <a name="add-radio-buttons"></a>Adición de botones de selección
1. En la pestaña **Inicio**, seleccione **Nueva pantalla**.

2. En la pestaña **Insertar**, seleccione **Controles** y, a continuación, seleccione **Botón de selección**.

    ![][10]  

3. Cambie el nombre del control **Botón de selección** por **Choices** y establezca la siguiente fórmula para la propiedad **[Elementos](controls/properties-core.md)**:  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    Si es necesario, cambie el tamaño del control para mostrar todas las opciones.

4. En la pestaña **Insertar**, seleccione **Iconos** y, a continuación, seleccione el círculo.

5. Defina la siguiente función para la propiedad **[Fill](controls/properties-color-border.md)** del círculo:  
   ```If(Choices.Selected.Value = "red", RGBA(192, 0, 0, 1), Choices.Selected.Value = "green", RGBA(0, 176, 80, 1), Choices.Selected.Value = "blue", RGBA(0, 32, 96, 1))```  

    En esta fórmula, el círculo cambia de color dependiendo de qué botón de selección elija.

6. Sitúe el círculo bajo el control **Botón de selección**, como en este ejemplo:

    ![][14]  

7. Obtenga una vista previa de lo que ha creado: ![][1]. Elija un botón de selección diferente para cambiar el color del círculo. Presione Esc o seleccione **X** para volver a la pantalla.

## <a name="add-a-drop-down-list"></a>Adición de una lista desplegable
1. Añada una pantalla y, a continuación, un control **Lista desplegable**.

    ![][15]  

2. Cambie el nombre del control a **DDChoices** y establezca la siguiente fórmula para la propiedad **[Elementos](controls/properties-core.md)**:<br>
   **["red","green","blue"]**

3. Añada un círculo, sitúelo debajo del control **Lista desplegable** y defina la siguiente fórmula para la propiedad **[Fill](controls/properties-color-border.md)** del círculo:  
   ```If(DDChoices.Selected.Value = "red", RGBA(192, 0, 0, 1), DDChoices.Selected.Value = "green", RGBA(0, 176, 80, 1), DDChoices.Selected.Value = "blue", RGBA(0, 32, 96, 1))```

4. Obtenga una vista previa de lo que ha creado: ![][1]. Seleccione las diferentes opciones para cambiar el color del círculo.

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
