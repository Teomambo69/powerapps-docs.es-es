---
title: 'Control de cuadro combinado: referencia | Microsoft Docs'
description: Información acerca del control de cuadro combinado, incluyendo sus propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/13/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ad3b8efc2306540862d0470223cee4f46fb5703c
ms.sourcegitcommit: 50404720bed371bbc93feb08d296c954ef8038e1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031363"
---
# <a name="combo-box-control-in-powerapps"></a>Control de cuadro combinado en PowerApps
Un control que permite a los usuarios seleccionar entre las opciones proporcionadas.  Admite tanto la búsqueda como la selección múltiple.

## <a name="description"></a>Descripción
Con un control de **cuadro combinado** puede buscar los elementos que va a seleccionar.  La búsqueda se realiza en el lado del servidor de la propiedad SearchField, por lo que el rendimiento no se ve afectado por orígenes de datos muy grandes.  

El modo de selección individual o múltiple se configura mediante la propiedad SelectMultiple.

Cuando se buscan elementos que se van a seleccionar, en todos los elementos puede elegir mostrar un valor de datos único, dos valores o una imagen y dos valores (Persona) mediante la modificación de la configuración de diseño en el panel Data (Datos).

## <a name="people-picker"></a>Selector de personas
Para usar **cuadro combinado** como selector de personas, elija la plantilla **Persona** desde la configuración de diseño del panel Data (Datos) y configure las propiedades de datos relacionadas que se mostrará para la persona que aparece a continuación.

## <a name="key-properties"></a>Propiedades principales
**[Items](properties-core.md)**: el origen de datos del que se puede elegir.

**DefaultSelectedItems** : los elementos seleccionados inicialmente antes de que el usuario interactúa con el control.

**SelectedItems**: lista de los elementos seleccionados resultante de la interacción con el usuario.

**SelectMultiple**: si el usuario puede seleccionar un solo elemento o varios.

**IsSearchable**: indica si el usuario puede buscar elementos antes de realizar la selección.

**SearchFields**: campos de datos del origen de datos en los que se busca cuando el usuario escribe texto.  Para buscar en varios campos, establezca ComboBox1.SearchFields = ["MyFirstColumn", "MySecondColumn"]

## <a name="additional-properties"></a>Propiedades adicionales
**[AccessibleLabel](properties-accessibility.md)**: etiqueta para lectores de pantalla.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**DisplayFields**: lista de campos que se muestran en cada elemento que devuelve la búsqueda.  Lo más fácil es configurarlo mediante el panel Datos de la pestaña de la opción Propiedades.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[FocusedBorderColor](properties-color-border.md)**: el color del borde de un control cuando el control recibe el foco.

**[FocusedBorderThickness](properties-color-border.md)**: el grosor del borde de un control cuando el control recibe el foco.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**InputTextPlaceholder**: texto informativo que se muestra a los usuarios finales cuando no hay elementos seleccionados.

**OnChange**: cómo responde la aplicación cuando el usuario cambia una selección.

**OnNavigate**: cómo responde la aplicación cuando el usuario hace clic en un elemento.

**[OnSelect](properties-core.md)**: indica cómo responde la aplicación cuando el usuario toca o hace clic en un control.

**[TabIndex](properties-accessibility.md)**: orden de navegación del teclado en relación con otros controles.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="example"></a>Ejemplo
1. Agregue un control de **cuadro combinado** desde la pestaña Insertar, menú Controles.  
2. En la pestaña de opciones Propiedades, haga clic en Datos.  
3. Seleccione el origen de datos, el diseño y las propiedades relacionadas a continuación.
4. Establezca la propiedad **SelectMultiple** en la ficha Opciones avanzadas.

    Aparecerá un **cuadro combinado** funcional en la aplicación.

    ¿No sabe cómo [agregar y configurar un control](../add-configure-controls.md)?


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **ChevronFill** y **ChevronBackground**
* **ChevronHoverFill** y **ChevronHoverBackground**
* **SelectionColor** y **SelectionFill**
* **SelectionFill** y **[Fill](properties-color-border.md)**
* **SelectionTagColor** y **SelectionTagFill**

Y esto, además de los [requisitos estándar de contraste de color](../accessible-apps-color.md).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

    > [!NOTE]
  > En pantallas táctiles, los usuarios de lector de pantalla pueden desplazarse por el contenido del cuadro combinado secuencialmente. El cuadro combinado actúa como botón que muestra u oculta su contenido cuando se selecciona.

### <a name="keyboard-support"></a>Compatibilidad con el teclado
* La propiedad **[TabIndex](properties-accessibility.md)** debe ser cero o superior para que los usuarios del teclado puedan desplazarse hasta él.
* Los indicadores de foco deben ser claramente visibles. Use **[FocusedBorderColor](properties-color-border.md)** y **[FocusedBorderThickness](properties-color-border.md)** para conseguirlo.

    > [!NOTE]
  > La tecla de tabulación permite desplazarse hasta el cuadro combinado o fuera de él. Las teclas de dirección permiten desplazarse por el contenido del cuadro combinado. La tecla escape cierra la lista desplegable cuando está abierta.
