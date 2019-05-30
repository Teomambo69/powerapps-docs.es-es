---
title: 'Control Galería: referencia | Microsoft Docs'
description: Información sobre el control Galería, con propiedades y ejemplos
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/25/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba5df28f03ec5e7c9a3d8146aecb0427d8145b13
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61544255"
---
# <a name="gallery-control-in-canvas-apps"></a>Control de galería de aplicaciones de lienzo

Un control que contiene otros controles y muestra un conjunto de datos.

## <a name="description"></a>Descripción

Un control **Galería** puede mostrar varios registros de un origen de datos, y cada registro puede contener varios tipos de datos. Por ejemplo, un control **Galería** puede mostrar varios contactos y cada elemento mostrar a su vez información de contacto que incluye un nombre, una dirección y un número de teléfono para cada contacto. Cada campo de datos aparece en un control independiente dentro del control **Galería** y esos controles se pueden configurar en su plantilla. La plantilla aparece como primer elemento dentro de la galería, en el borde izquierdo de un control **Galería** en orientación horizontal o vertical y en la parte superior de un control **Galería** en orientación vertical. Los cambios realizados en la plantilla se reflejarán en todo el control **Galería**.

Plantillas predefinidas para que muestre imágenes y texto en una galería están disponibles, así como una galería de elementos de alto variable.

## <a name="limitations"></a>Limitaciones

Si un usuario se desplaza el **altura Flexible** control de galería antes de que se cargan todos los elementos, el elemento de vista actualmente en que puede insertarse hacia abajo y hacia afuera de la vista cuando finaliza la carga de datos. Para evitar este problema, use un estándar **galería** control en lugar de la **altura Flexible** variant.

## <a name="key-properties"></a>Propiedades principales

**[Predeterminado](properties-core.md)**: el elemento o registro del origen de datos que se va a seleccionar en la galería al iniciarse la aplicación.

**[Elementos](properties-core.md)**: origen de datos que aparece en un control, como una galería, una lista o un gráfico.

**Seleccionados**: el elemento seleccionado.

## <a name="additional-properties"></a>Propiedades adicionales

**[AccessibleLabel](properties-accessibility.md) ** : etiqueta de la Galería (no los elementos que contiene) para los lectores de pantalla. Debe describir cuáles es la lista de elementos.

**TodosLosElementos**: todos los elementos de una galería, como valores de control adicionales que sean parte de la plantilla de la galería.

**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[DisplayMode](properties-core.md)**: indica si el control permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**ItemAccessibleLabel** : etiqueta de cada elemento de la Galería para los lectores de pantalla. Debe describir cada elemento es.

**PasoDeNavegación**: indica lo lejos que se desplaza una galería si su propiedad **Mostrar Navegación** está establecida en **true** y el usuario selecciona una flecha de navegación de cualquier extremo de esa galería.

**Puede seleccionar** : indica si se pueden seleccionar elementos de la galería. Cuando se establece en **true**, la Galería como una lista seleccionable por identifican los lectores de pantalla y seleccione un elemento haciendo clic o pulsando en él. Cuando se establece en **false**, los lectores de pantalla identifican la Galería como una lista normal y haciendo clic o pulsando en un elemento no se selecciona.

**MostrarNavegación**: indica si aparece una flecha en cada extremo de una galería para que un usuario puede desplazarse por los elementos de la galería haciendo clic en una flecha o pulsando en ella.

**MostrarBarraDesplazamiento**: indica si aparecerá una barra de desplazamiento cuando el usuario mantenga el cursor sobre una galería.

**Snap**: indica si, cuando un usuario se desplaza por una galería, esta se ajusta automáticamente para que aparezca el siguiente elemento en su totalidad.

**RellenoDePlantilla**: el color de fondo de una galería.

**EspaciadoInternoDePlantilla**: la distancia entre los elementos de una galería.

**TamañoDePlantilla**: el alto de la plantilla en una galería en orientación vertical o el ancho de la plantilla en una galería en orientación horizontal o vertical.

**Transition**: el efecto visual (**Pop**, **Push** o **None**) cuando el usuario mantiene el puntero sobre un elemento de la galería.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**WrapCount**: número de elementos que se muestran por fila o columna en función del diseño horizontal o vertical.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="related-functions"></a>Funciones relacionadas

[**Filter**( *DataSource*, *Formula* )](../functions/function-filter-lookup.md)

## <a name="examples"></a>Ejemplos

### <a name="show-and-filter-data"></a>Mostrar y filtrar los datos

* [Mostrar texto](control-text-box.md#show-data-in-a-gallery)
* [Mostrar imágenes](control-image.md#show-a-set-of-images-from-a-data-source)
* [Filtrar datos mediante la selección de una opción de la lista](control-drop-down.md#example)
* [Filtrar datos mediante el ajuste de un control deslizante](control-slider.md#example)

### <a name="get-data-from-the-user"></a>Obtener datos del usuario

* [Obtener texto](control-text-input.md#collect-data)
* [Obtener imágenes](control-add-picture.md#add-images-to-an-image-gallery-control)
* [Obtener fotografías](control-camera.md#example)
* [Obtener sonidos](control-microphone.md#example)
* [Obtener dibujos](control-pen-input.md#create-a-set-of-images)

## <a name="accessibility-guidelines"></a>Directrices de accesibilidad

### <a name="color-contrast"></a>Contraste de color

Si la finalidad de hacer clic en cualquier parte en un elemento de la galería es seleccionarlo, debe haber un contraste de color adecuado entre:

* **[BorderColor](properties-color-border.md) ** y el color de fuera de la galería (si hay un borde)
* **[Fill](properties-color-border.md)** y el color situado fuera de la galería (si hay un borde)

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla

* La propiedad **[AccessibleLabel](properties-accessibility.md)** debe estar presente.

    > [!NOTE]
    > Los lectores de pantalla le avisará cuando cambian los elementos en la galería. La propiedad **AccessibleLabel** también se menciona. De esta forma, se proporciona contexto al anuncio y es incluso más importante cuando hay varias galerías en la misma pantalla.

* Cuando un elemento de la galería contiene varios controles, utilizar **ItemAccessibleLabel** para resumir el contenido del elemento de galería.

* Establezca el valor de **Selectable** a **true** si desea que los usuarios seleccionar un elemento de la galería. De lo contrario, se establece ese valor en **false**.

* Cuando un elemento de la galería contiene varios controles, utilizar **ItemAccessibleLabel** para proporcionar un resumen de la Galería de contenido del elemento.

* **Puede seleccionar** debe establecerse como corresponda, dependiendo de si los usuarios están diseñados para seleccionar un elemento de la galería.

### <a name="keyboard-support"></a>Compatibilidad con el teclado

* Considere la posibilidad de establecer **ShowScrollbar** en **true**. En la mayoría de los dispositivos de pantalla táctil, la barra de desplazamiento no se muestra hasta que comienza el desplazamiento.
* Si la finalidad de hacer clic en cualquier parte en un elemento de la galería es seleccionarlo, debe haber también una forma de que los usuarios de teclado seleccionen el elemento de la galería. Por ejemplo, agregar un control **[Botón](control-button.md)** cuya propiedad **OnSelect** esté establecida en **Select(Parent)**.

    > [!NOTE]
  > Los controles situados fuera de la galería no se tienen en cuenta en el orden de desplazamiento por el teclado dentro de la galería. Se tiene en cuenta la propiedad **[TabIndex](properties-accessibility.md)** de los controles dentro de una galería. Consulte las [propiedades de accesibilidad](properties-accessibility.md) para obtener más información.
