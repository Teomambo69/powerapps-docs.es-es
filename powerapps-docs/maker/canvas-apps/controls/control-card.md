---
title: 'Control Tarjeta: referencia | Microsoft Docs'
description: Información sobre el control Card, con propiedades y ejemplos
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: 1874d03f5bf01adca9969bd74e7dbed1007d86e2
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="card-control-in-powerapps"></a>Control Card en PowerApps
Proporciona la experiencia de edición y visualización de un solo campo de un control **[Formulario de presentación](control-form-detail.md)** o **[Formulario de edición](control-form-detail.md)**.

## <a name="description"></a>Descripción
Los controles **[Formulario de presentación](control-form-detail.md)** y **[Formulario de edición](control-form-detail.md)** funcionan como contenedores para mostrar y ver los registros enteros. Cada contenedor puede contener un conjunto de controles **Card** que muestran campos individuales o proporcionan una forma de actualizar esos campos. Cada tarjeta tiene una propiedad **DataField** que especifica el campo del registro en el que se trabaja.  

Hay definidas tarjetas predefinidas para diferentes tipos de datos y experiencias de usuario.  Por ejemplo, puede haber una tarjeta para editar un campo numérico con un control **[Entrada de texto](control-text-input.md)**, que resulta muy adecuado para usar con el teclado. Otra tarjeta podría permitir la edición de un número usando en su lugar un control **[Control deslizante](control-slider.md)**. Con el control de formulario seleccionado, puede seleccionar fácilmente, en el panel derecho, una tarjeta basada en un campo.

Las tarjetas contienen controles. Los controles de una tarjeta constituyen la experiencia para mostrar y editar un único campo. Por ejemplo, una tarjeta de número puede estar formada por un control **[Etiqueta](control-text-box.md)** para proporcionar el nombre para mostrar del campo y un control **[Entrada de texto](control-text-input.md)** para proporcionar un editor para el valor del campo. La tarjeta puede tener también un control **[Etiqueta](control-text-box.md)** que muestra los errores de validación que se producen y un control **[Etiqueta](control-text-box.md)** para el asterisco común que indica que es un campo obligatorio.

Puede personalizar los controles de una tarjeta predefinida: cambiar su tamaño, moverla, ocultarla, agregarle controles y realizar otros cambios. También puede comenzar con una tarjeta completamente en blanco, una "tarjeta personalizada", a la cual agregar controles desde cero.

Las tarjetas predefinidas están *bloqueadas* de forma predeterminada. En una tarjeta bloqueada, solo puede modificar determinadas propiedades de la tarjeta o los controles que contiene. No se puede eliminar una tarjeta bloqueada. Puede mostrar el bloqueo de tarjeta y desbloquearla en la pestaña **Ver** de la vista **Avanzado**. Si una propiedad está bloqueada y no se puede modificar, aparece un icono de candado junto a su nombre. Desbloquear una tarjeta es una actividad avanzada y debe realizarse con cuidado, ya que la generación automática de fórmulas ya no tendrá lugar para la tarjeta, y no se puede volver a bloquear una tarjeta.

Dentro del contenedor del formulario el registro **EsteElemento** está disponible y contiene todos los campos del registro.  Por ejemplo, la propiedad **[Default](properties-core.md)** con frecuencia se establece en **EsteElemento**.*FieldName*.

Puede usar la referencia **Parent** para configurar un control que haga referencia a las propiedades de una tarjeta.  Por ejemplo, un control debe usar **Parent.Default** para leer el estado inicial del campo del origen de datos. Al usar **Parent** en lugar de acceder directamente a la información que desea, la tarjeta está mejor encapsulada y puede cambiarla a un campo diferente sin romper fórmulas internas.

Consulte [Understand data cards](../working-with-cards.md) (Introducción a las tarjetas de datos) para ver ejemplos de cómo personalizar, desbloquear y crear tarjetas.

## <a name="key-properties"></a>Propiedades principales
**DataField**: el nombre del campo dentro de un registro que esta tarjeta muestra y edita.

* Especifique el nombre como una sola cadena estática incluida entre comillas dobles (por ejemplo, **"Nombre"**), no una fórmula.
* Para desenlazar una tarjeta, establezca su propiedad **DataField***en blanco*. Las propiedades **Valid** y **Actualizar** se ignoran en las tarjetas desenlazadas.

**[Predeterminado](properties-core.md)**: el valor inicial de un control antes de que lo cambie el usuario.

* Para cada control de una tarjeta, establezca esta propiedad en **Parent.Default** para hacer referencia al valor predeterminado del campo según el origen de datos. Por ejemplo, establezca la propiedad **[Default](properties-core.md)** de un control deslizante en **Parent.Default** para garantizar que el usuario comienza con un valor genérico para ese control deslizante.

**DisplayMode**: los valores pueden ser **Edit, View** o **Disabled**. Permite configurar si el control de la tarjeta permite entradas de usuario (**Edit**), solo muestra datos (**View**) o si está deshabilitado (**Disabled**).  

* Mediante la configuración de esta propiedad, que está vinculada al comportamiento predeterminado del formulario, se permite que se pueda usar una sola tarjeta en los formularios Edit y View.
* En el modo **View**, los controles secundarios como **[Entrada de texto](control-text-input.md)**, **[Lista desplegable](control-drop-down.md)** y **[Selector de fecha](control-date-picker.md)** solo mostrarán el valor del texto y no representarán ninguna otra decoración ni elemento interactivo.

**DisplayName**: el nombre descriptivo de un campo en un origen de datos.

* La función **[DataSourceInfo](../functions/function-datasourceinfo.md)** proporciona estos metadatos desde el origen de datos.
* Los controles de la tarjeta deben usar **Parent.DisplayName** para hacer referencia al nombre del campo.

**Error**: el mensaje de error descriptivo para mostrar de este campo cuando se produce un error de validación.

* Esta propiedad se establece cuando se llama a **SubmitForm**.  
* El mensaje describe los problemas de validación basándose en los metadatos del origen de datos y la comprobación de la propiedad **Required** de la tarjeta.

**Required**: indica si una tarjeta, al editar el campo de un origen de datos, debe contener un valor.

* La función  **[DataSourceInfo](../functions/function-datasourceinfo.md)** proporciona los metadatos necesarios desde el origen de datos.
* Los controles dentro de la tarjeta deben usar **Parent.Required** para determinar si el campo de la tarjeta es obligatorio.

**Actualizar**: el valor para escribir en el origen de datos de un campo.

* Use la fórmula de esta propiedad para extraer los valores de los controles de edición de la tarjeta con el fin de escribir en el origen de datos. Por ejemplo, establezca la propiedad **Actualizar** en **Slider.Value** para actualizar el origen de datos con un valor del control deslizante de esa tarjeta.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[WidthFit](properties-size-location.md)**: indica si un control crece automáticamente en la horizontal para rellenar el espacio vacío de un control de contenedor como el control **[Formulario de edición](control-form-detail.md)**. Si varias tarjetas tienen esta propiedad establecida en **true**, el espacio se divide entre ellas. Para más información, consulte [Understand data form layout in Microsoft PowerApps](../working-with-form-layout.md) (Introducción al diseño de formularios de datos en Microsoft PowerApps).

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**Valid**: indica si un control **Card** o **[Edit form](control-form-detail.md)** contiene entradas válidas listas para enviarse al origen de datos.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario). Para un control **[Tarjeta](control-card.md)** en un contenedor con varias columnas, esta propiedad determina la columna en la que aparece la tarjeta.

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario). Para un control **[Tarjeta](control-card.md)** en un contenedor con varias filas, esta propiedad determina la fila en la que aparece la tarjeta.

## <a name="examples"></a>Ejemplos
Encontrará ejemplos en [Tarjetas de datos](../working-with-cards.md) y la [introducción al diseño de los formularios de datos](../working-with-form-layout.md).


## <a name="accessibility-guidelines"></a>Directrices de accesibilidad
### <a name="color-contrast"></a>Contraste de color
Debe haber un contraste de color adecuado entre:
* **[Fill](properties-color-border.md)** y cualquier control secundario. Por ejemplo, si una tarjeta contiene una **[etiqueta](control-text-box.md)** y esta tiene relleno transparente, la propiedad **[Fill](properties-color-border.md)** de la tarjeta se convierte de hecho en el color de fondo de la etiqueta. Por tanto, debe haber un contraste adecuado entre la propiedad **[Fill](properties-color-border.md)** de la tarjeta y la propiedad **[Color](properties-color-border.md)** de la etiqueta.

### <a name="screen-reader-support"></a>Soporte técnico para el lector de pantalla
* La propiedad **DisplayName** debe existir.
