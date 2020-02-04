---
title: Función SetProperty | Microsoft Docs
description: Información de referencia sobre la función SetProperty en Power Apps Test Studio, incluida la sintaxis
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dac65ed25a9e286b056cf3c1408554ca79ea3e11
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541161"
ms.PowerAppsDecimalTransform: true
---
# <a name="setproperty-function-in-power-apps-test-studio"></a>Función SetProperty en Power Apps Test Studio

La función SetProperty simula interacciones con controles de entrada como si el usuario hubiera especificado o establecido un valor en el control. Esta función solo está disponible si está escribiendo pruebas en Power Apps Test Studio. Las siguientes propiedades se pueden establecer mediante la función SetProperty.

## <a name="syntax"></a>Sintaxis

*SetProperty(propiedad de control, valor)*

- *Propiedad de control*: obligatoria. La propiedad de control que se establece en nombre del usuario.
- *Value*: requerido. El valor de la propiedad que se establece en nombre del usuario. 

## <a name="examples"></a>Ejemplos

| Controlar   | Propiedad  | Expresión de ejemplo
| :- | :- | :-
| TextInput | Texto  | ```SetProperty(TextInput1.Text; "Sample text")```
| RichTextEditor    | HtmlText  | ```SetProperty(RichTextEditor1.HtmlText; "<p>Sample text</p>")```
| Alternancia    | Valor | ```SetProperty(Toggle1.Value; false)```
| Casilla de verificación  | Valor | ```SetProperty(Checkbox1.Value; false)```
| Control deslizante    | Valor | ```SetProperty(Slider1.Value; 10)```
| Clasificación    | Valor | ```SetProperty(Rating1.Value; 5)```
| DatePicker    | SelectedDate  | ```SetProperty(DatePicker1.SelectedDate; Date(2020;3;10))```
| Radio | Seleccionado  | ```SetProperty(Radio1.Selected; "Yes")```
| Radio | SelectedText | ```SetProperty(Radio1.SelectedText; "Yes")```
| Desplegable | Seleccionado | ```SetProperty(Dropdown1.Selected; {Value:"Sample value"})```
| Desplegable | SelectedText | ```SetProperty(Dropdown1.SelectedText; {Value:"Sample value"})```
| ComboBox | Seleccionado | ```SetProperty(Dropdown1.Selected; {Value:"Sample value"})```
| ComboBox | SelectedItems | ```SetProperty(ComboBox1.SelectedItems; Table({Value:"Sample value"};({Value:"Sample value"}))```
| ListBox | Seleccionado | ```SetProperty(Listbox1.Selected; {'Value':"Sample value"})```
| ListBox | SelectedItems | ```SetProperty(Listbox1.SelectedItems; Table({Value:"Sample value"};({Value:"Sample value"}))```

### <a name="see-also"></a>Vea también

[Información general de Test Studio](../test-studio.md) <br>
[Trabajo con Test Studio](../working-with-test-studio.md)