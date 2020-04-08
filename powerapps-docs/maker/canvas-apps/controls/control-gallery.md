---
title: 'Control Galería: referencia | Microsoft Docs'
description: Información sobre el control Galería, con propiedades y ejemplos
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ca48ccaf4aca72301d3a8b7f2eb79885d7c7cdf5
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871336"
---
# <a name="gallery-control-in-canvas-apps"></a>Control Galería en aplicaciones de lienzo

Un control que contiene otros controles y muestra un conjunto de datos.

## <a name="description"></a>Descripción

Un control **Galería** puede mostrar varios registros de un origen de datos, y cada registro puede contener varios tipos de datos. Por ejemplo, use un control **Galería** para mostrar varios contactos con cada elemento que muestre información de contacto que incluye un nombre, una dirección y un número de teléfono para cada contacto.

Cada campo de datos aparece en un control independiente dentro del control **Galería** . Además, puede configurar esos controles en su plantilla. La plantilla aparece como el primer elemento dentro de la Galería:

- En el borde izquierdo de un control de **Galería** en orientación horizontal u horizontal.
- Y en la parte superior de un control de **Galería** en orientación vertical u horizontal. 

Los cambios realizados en la plantilla se reflejarán en todo el control **Galería**.

Están disponibles las plantillas predefinidas para mostrar imágenes y texto en una galería, y una galería para elementos de alto variable.

## <a name="limitations"></a>Limitaciones

Si un usuario desplaza el control de la galería de **alto flexible** antes de que se carguen todos los elementos, el elemento que está actualmente en la vista se puede desplazar hacia abajo y fuera de la vista cuando finaliza la carga de datos. Para evitar este problema, use un control de **Galería** estándar en lugar de la variante de **alto flexible** .

## <a name="key-properties"></a>Propiedades principales

[Predeterminado](properties-core.md) : el elemento o registro del origen de datos que se va a seleccionar en la Galería cuando se inicia la aplicación.

[Items](properties-core.md): origen de datos que aparece en un control como una galería, una lista o un gráfico.

**Seleccionados**: el elemento seleccionado.

## <a name="additional-properties"></a>Propiedades adicionales

[Propiedad accessiblelabel](properties-accessibility.md) : etiqueta de la galería (no los elementos que contiene) para los lectores de pantalla. Debe describir cuáles es la lista de elementos.

**TodosLosElementos**: todos los elementos de una galería, como valores de control adicionales que sean parte de la plantilla de la galería.

[BorderColor](properties-color-border.md): el color de un borde del control.

[BorderStyle](properties-color-border.md) : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

[BorderThickness](properties-color-border.md): el grosor de un borde del control.

**DelayItemLoading** : retrasar la carga de elementos (filas) hasta que la pantalla se carga por primera vez.

[DisplayMode](properties-core.md) : indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**deshabilitado**).

[Fill](properties-color-border.md): el color de fondo de un control.

[Height](properties-size-location.md): la distancia entre los bordes superior e inferior de un control.

**ItemAccessibleLabel** : etiqueta de cada elemento de la galería para lectores de pantalla. Debe describir qué es cada elemento.

**LoadingSpinner** (**ninguno**, **controles** o **datos**): Si no hay ninguno, no se mostrará el control de número. Cuando controla | Datos, el control de número se mostrará cuando se produzca una fase de representación que tenga como resultado filas vacías visibles.

**LoadingSpinnerColor** : el color de relleno del control de carga.  El valor predeterminado se establece en BorderColor.

**PasoDeNavegación**: indica lo lejos que se desplaza una galería si su propiedad **Mostrar Navegación** está establecida en **true** y el usuario selecciona una flecha de navegación de cualquier extremo de esa galería.

**Seleccionable** : indica si se pueden seleccionar elementos de la galería. Cuando se establece en **true**, los lectores de pantalla identifican la Galería como una lista seleccionable. Y selecciona un elemento seleccionándolo. Cuando se establece en **false**, los lectores de pantalla identifican la Galería como una lista normal y la selección de un elemento no la selecciona.

**Mostrarnavegación** : indica si aparece una flecha en cada extremo de una galería para que un usuario pueda desplazarse por los elementos de la Galería seleccionando una flecha.

**MostrarBarraDesplazamiento**: indica si aparecerá una barra de desplazamiento cuando el usuario mantenga el cursor sobre una galería.

**Snap**: indica si, cuando un usuario se desplaza por una galería, esta se ajusta automáticamente para que aparezca el siguiente elemento en su totalidad.

**RellenoDePlantilla**: el color de fondo de una galería.

**EspaciadoInternoDePlantilla**: la distancia entre los elementos de una galería.

**Template** : el alto de la plantilla de una galería en orientación vertical u horizontal. O el ancho de la plantilla de una galería en orientación horizontal u horizontal.

**Transition**: el efecto visual (**Pop**, **Push** o **None**) cuando el usuario mantiene el puntero sobre un elemento de la galería.

[Visible](properties-core.md): indica si un control aparece o está oculto.

[Width](properties-size-location.md): la distancia entre los bordes derecho e izquierdo de un control.

**WrapCount**: número de elementos que se muestran por fila o columna en función del diseño horizontal o vertical.

[X](properties-size-location.md) : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor o pantalla primaria.

[Y](properties-size-location.md) : la distancia entre el borde superior de un control y el borde superior del contenedor o la pantalla primarios.

## <a name="related-functions"></a>Funciones relacionadas

[Filter ( *DataSource*, *fórmula* )](../functions/function-filter-lookup.md)

[Restablecer ( *control* )](../functions/function-reset.md) : restablece la galería de nuevo a su estado inicial. El estado inicial incluye desplazarse hasta el primer elemento y seleccionar el primer elemento o el valor predeterminado, si está presente. 

  > [!NOTE]
  > El control de **restablecimiento** no restablece de forma recursiva todos los elementos secundarios de la galería.

## <a name="examples"></a>Ejemplos

### <a name="show-and-filter-data"></a>Mostrar y filtrar los datos

- [Mostrar texto](control-text-box.md#show-data-in-a-gallery)
- [Mostrar imágenes](control-image.md#show-a-set-of-images-from-a-data-source)
- [Filtrar datos mediante la selección de una opción de la lista](control-drop-down.md#example)
- [Filtrar datos mediante el ajuste de un control deslizante](control-slider.md#example)

### <a name="get-data-from-the-user"></a>Obtener datos del usuario

- [Obtener texto](control-text-input.md#collect-data)
- [Obtener imágenes](control-add-picture.md#add-images-to-an-image-gallery-control)
- [Obtener fotografías](control-camera.md#examples)
- [Obtener sonidos](control-microphone.md#examples)
- [Obtener dibujos](control-pen-input.md#create-a-set-of-images)

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="color-contrast"></a>Contraste de color

Si la finalidad de hacer clic en cualquier parte en un elemento de la galería es seleccionarlo, debe haber un contraste de color adecuado entre:

- [BorderColor](properties-color-border.md) y el color fuera de la galería (si hay un borde).
- [Relleno](properties-color-border.md) y el color fuera de la galería (si no hay borde).

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

- [Propiedad accessiblelabel](properties-accessibility.md) debe estar presente.

    > [!NOTE]
    > Los lectores de pantalla anunciarán cuando cambien los elementos de la galería. La propiedad **AccessibleLabel** también se menciona. De esta forma, se proporciona contexto al anuncio y es incluso más importante cuando hay varias galerías en la misma pantalla.

- Cuando un elemento de la galería contiene varios controles, use **ItemAccessibleLabel** para mostrar el contenido de los elementos de la galería.

- Establezca el valor de **Selectable** en **true** si desea que los usuarios seleccionen un elemento de la galería. De lo contrario, establezca el valor en **false**.

- Cuando un elemento de la galería contiene varios controles, use **ItemAccessibleLabel** para proporcionar un resumen del contenido del elemento de la galería.

- **Selectable** debe establecerse correctamente, en función de si los usuarios están diseñados para seleccionar un elemento de la galería.

### <a name="keyboard-support"></a>Compatibilidad con el teclado

- Considere la posibilidad de establecer **ShowScrollbar** en **true**. En la mayoría de los dispositivos de pantalla táctil, la barra de desplazamiento no se mostrará hasta que comience el desplazamiento.
- Si la finalidad de hacer clic en cualquier parte en un elemento de la galería es seleccionarlo, debe haber también una forma de que los usuarios de teclado seleccionen el elemento de la galería. Por ejemplo, al agregar un [botón](control-button.md) que tiene su propiedad **alseleccionar** establecida en **Select (Parent)** .

    > [!NOTE]
  > Los controles situados fuera de la galería no se tienen en cuenta en el orden de desplazamiento por el teclado dentro de la galería. El ámbito de los controles [TabIndex](properties-accessibility.md) dentro de una galería es. Consulte las [propiedades de accesibilidad](properties-accessibility.md) para obtener más información.
