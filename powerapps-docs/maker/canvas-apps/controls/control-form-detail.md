---
title: 'Controles Formulario de presentación y Formulario de edición: referencia | Microsoft Docs'
description: Información sobre los controles Formulario de presentación y Formulario de edición, con propiedades y ejemplos
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
ms.date: 07/06/2017
ms.author: gregli
ms.openlocfilehash: c238a441c147c148fa619e6068579b75d643339a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="edit-form-and-display-form-controls-in-powerapps"></a>Controles Formulario de presentación y Formulario de edición en PowerApps
Muestra, edición y creación de un registro en un origen de datos.

## <a name="description"></a>Descripción
Si agrega un control **Formulario de presentación** , el usuario puede mostrar todos los campos de un registro o solo los campos que usted especifique. Si agrega un control **Formulario de edición**, el usuario puede editar esos campos, crear un registro y guardar los cambios realizados en un origen de datos.

![Controles de ejemplo y vista de formulario](./media/control-form-detail/form-detail-intro.png)

Si agrega un control **[Galería](control-gallery.md)**, puede configurarlo para mostrar una tabla en un origen de datos y luego configurar un formulario para mostrar cualquier registro que el usuario seleccione en la galería. También puede agregar uno o varios controles **[Botón](control-button.md)** que el usuario puede seleccionar para guardar las modificaciones, cancelar las modificaciones y crear un registro. Al usar varios controles juntos, puede [crear una solución completa](../working-with-forms.md).

### <a name="record-selection"></a>Selección de registros
Para cada tipo de formulario, establezca su propiedad **DataSource** en una tabla de registros y establezca la propiedad **Elemento** para mostrar un registro específico en esa tabla. Por ejemplo, puede establecer la propiedad **Elemento** de un formulario en la propiedad **SelectedItem** de un control **[Galería](control-gallery.md)**. Cuando el usuario selecciona un registro en la galería, aparece el mismo registro en el formulario, excepto que el formulario puede mostrar más campos. Si el usuario vuelve a la galería y selecciona un registro diferente, la propiedad **SelectedItem** de la galería cambia. Este cambio actualiza la propiedad **Elemento** del formulario, que mostrará el registro recién seleccionado.

Cada control de formulario contiene uno o varios controles **[Tarjeta](control-card.md)**. Estableciendo la propiedad **[DataField](control-card.md)** de una tarjeta, se [especifica qué campo muestra esta tarjeta y otros detalles](../add-form.md).

### <a name="create-a-record"></a>Creación de un registro
Cuando un control **Formulario de edición** se encuentra en modo **Edición**, el usuario puede actualizar el registro que se especifica en la propiedad **Elemento** del formulario. Si se inspecciona, la propiedad **Modo** devuelve **Edición**.

Cuando un control **Formulario de edición** se encuentra en modo **Nuevo** pero la propiedad **Elemento** se omite. El formulario no muestra un registro existente; en su lugar, los valores de cada campo coinciden con los valores predeterminados del origen de datos con el que ha configurado el formulario. La función **[NuevoFormulario](../functions/function-form.md)** hace que un formulario cambie a este modo.

Por ejemplo, puede establecer la propiedad **[Texto](properties-core.md)** de un botón para mostrar **Nuevo** y su propiedad **[AlSeleccionar](properties-core.md)** en una fórmula que incluya la función **[NuevoFormulario](../functions/function-form.md)**. Si el usuario selecciona ese botón, el formulario cambia al modo **Nuevo** para que el usuario puede crear un registro a partir de los valores conocidos.

Un formulario vuelve a cambiar a modo **Edición** si es ejecuta la función  **[ResetForm](../functions/function-form.md)** o la función  **[SubmitForm](../functions/function-form.md)**  se ejecuta correctamente.

* Puede establecer la propiedad **[Texto](properties-core.md)** de un botón para mostrar **Cancelar** y su propiedad **[AlSeleccionar](properties-core.md)** en una fórmula que incluya la función **[ResetForm](../functions/function-form.md)**. Si el usuario selecciona ese botón, se descartan todos los cambios en curso, y los valores en el formulario, una vez más, coinciden con los valores predeterminados del origen de datos.
* Puede establecer la propiedad **[Texto](properties-core.md)** de un botón para mostrar **Guardar cambios** y su propiedad **[AlSeleccionar](properties-core.md)** en una fórmula que incluya la función **[SubmitForm](../functions/function-form.md)**. Si el usuario selecciona ese botón y se actualiza el origen de datos, los valores en el formulario se restablecen a los valores predeterminados del origen de datos.

### <a name="save-changes"></a>Guardar cambios
Si crea un botón **Guardar cambios** tal y como se describe en la sección anterior, el usuario puede crear o actualizar un registro y luego seleccionar ese botón para guardar esos cambios en el origen de datos. En su lugar, puede configurar un control **[Imagen](control-image.md)** o algún otro control para realizar la misma tarea, siempre y cuando configure ese control con la función **[SubmitForm](../functions/function-form.md)**. En cualquier caso, las propiedades **Error**, **ErrorKind**, **OnSuccess**, y **OnFailure** proporcionan comentarios sobre el resultado.

Cuando la función **[SubmitForm](../functions/function-form.md)** se ejecuta, validará primero los datos que el usuario desea enviar. Si un campo obligatorio no contiene un valor u otro valor no se ajusta a alguna otra restricción, las propiedades **ErrorKind** se establecen y se ejecuta la fórmula **OnFailure**. Puede configurar el botón **Guardar cambios** u otro control de forma que el usuario pueda seleccionarlo solo si los datos son válidos (es decir, si la propiedad **Válido** del formulario es **true**). Tenga en cuenta que el usuario no solo tiene que corregir el problema sino que también tiene que volver a seleccionar el botón **Guardar cambios** (o descartar los cambios seleccionando un botón **Cancelar**, como se describió anteriormente) para restablecer las propiedades **Error** y **ErrorKind**.

Si los datos pasan la validación, **[SubmitForm](../functions/function-form.md)** los envía al origen de datos, lo que puede tardar algún tiempo dependiendo de la latencia de red.

* Si el envío se realiza correctamente, la propiedad **Error** se desactiva, la propiedad **ErrorKind** se establece en **ErrorKind.None**y se ejecuta la fórmula **OnSuccess**. Si el usuario creó un registro (es decir, si el formulario se encontraba anteriormente en modo **Nuevo**), el formulario se cambia a modo **Edición** para que el usuario pueda editar el registro recién creado o uno diferente.
* Si se produce un error en el envío, la propiedad **Error** contiene un mensaje de error descriptivo del origen de datos, en donde se explica el problema. La propiedad **ErrorKind** se establece como corresponda, dependiendo del problema y se ejecuta la fórmula **OnFailure**.

Algunos orígenes de datos pueden detectar cuando hay dos personas tratando de actualizar el mismo registro a la vez. En este caso, **ErrorKind** se establece en **ErrorKind.Conflict**, y la solución es actualizar el origen de datos con los cambios del otro usuario y volver a aplicar los cambios realizados por este usuario.

> [!TIP]
> Si ofrece un botón **Cancelar** en el formulario para que el usuario puede descartar los cambios en curso, agregue la función **[ResetForm](../functions/function-form.md)** a la propiedad **[AlSeleccionar](properties-core.md)** del botón, aunque dicha propiedad contenga también una función **[Navegar](../functions/function-navigate.md)** para cambiar de pantalla. De lo contrario, el formulario conservará los cambios del usuario.

### <a name="layout"></a>Diseño
De forma predeterminada, las tarjetas se colocan en una sola columna para las aplicaciones de teléfono y en tres columnas para las aplicaciones de tableta. Puede especificar cuántas columnas tiene un formulario y si se deben ajustar a ellas las tarjetas al configurar el formulario. Esta configuración no se expone en propiedades, porque se usa únicamente para definir las propiedades **X**, **Y** y **Width** de las tarjetas.

Para más información, consulte [Understand data form layout in Microsoft PowerApps](../working-with-form-layout.md) (Introducción al diseño de formularios de datos en Microsoft PowerApps).

## <a name="key-properties"></a>Propiedades principales
**DataSource**: el origen de datos que contiene el registro que el usuario muestra, edita o crea.

* Si no establece esta propiedad, el usuario no puede mostrar, editar o crear un registro, y no se proporcionan ni metadatos adicionales ni la validación.

**DefaultMode**: el modo inicial del control de formulario.  Consulte a continuación la descripción de **Modo** para conocer los valores aceptables y sus significados. 

**DisplayMode**: el modo que se utiliza para las tarjetas de datos y los controles del control de formulario.  

Deriva de la propiedad **Modo** en la que se basa y no se puede establecer de forma independiente:

| Modo | DisplayMode | Descripción |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |Las tarjetas de datos y los controles son editables, y están listos para aceptar los cambios de un registro. |
| **FormMode.New** |**DisplayMode.Edit** |Las tarjetas de datos y los controles son editables, y están listos para aceptar un nuevo registro. |
| **FormMode.View** |**DisplayMode.View** |Las tarjetas de datos y los controles no son editables y están optimizados para su visualización. |

**Error**: un mensaje de error descriptivo para mostrar para este formulario cuando se produce un error en la función **[SubmitForm](../functions/function-form.md)**.

* Esta propiedad solo se aplica al control **Formulario de edición**.
* Esta propiedad cambia solo cuando se ejecuta la función **[SubmitForm](../functions/function-form.md)**, **EditForm**, o **[ResetForm](../functions/function-form.md)**.
* Si no se produce ningún error, esta propiedad está *en blanco*, y **ErrorKind** se establece en **ErrorKind.None**.
* Cuando sea posible, el mensaje de error devuelto estará en el idioma del usuario. Algunos mensajes de error proceden directamente del origen de datos y puede que no estén en el idioma del usuario.

**ErrorKind**: si se produce un error cuando se ejecuta **SubmitForm**, el tipo de error que se produjo:

* Solo se aplica a un control **Formulario de edición**.
* Esta propiedad no tiene la misma enumeración que la función **[Errores](../functions/function-errors.md)**. Un control **Formulario de edición** puede devolver estos valores:

| ErrorKind | Descripción |
| --- | --- |
| **ErrorKind.Conflict** |Otro usuario ha cambiado el mismo registro, lo que produce un conflicto de cambios. Ejecute la función **[Actualizar](../functions/function-refresh.md)** para volver a cargar el registro e intente de nuevo el cambio. |
| **ErrorKind.None** |El error es de un tipo desconocido. |
| **ErrorKind.Sync** |El origen de datos informó de un error. Compruebe la propiedad **Error** para obtener más información. |
| **ErrorKind.Validation** |Se detectó un problema de validación general. |

**Elemento**: el registro en el **origen de datos** que el usuario mostrará o editará.

**LastSubmit**: el último registro enviado correctamente, incluidos los campos generada por el servidor.

* Esta propiedad solo se aplica al control **Formulario de edición**.
* Si el origen de datos genera automáticamente o calcula cualquier campo, como un campo de **identificador** con un número único, la propiedad **LastSubmit** tendrá este nuevo valor después de que **SubmitForm** se ejecute correctamente.
* El valor de esta propiedad está disponible en la fórmula **OnSuccess**.

**Modo**: el control se encuentra en modo **Edición** o **Nuevo**.

| Modo | Descripción |
| --- | --- |
| **FormMode.Edit** |El usuario puede editar un registro mediante el formulario. Los valores de las tarjetas del formulario se rellenan con el registro existente, el usuario puede cambiarlos. Si la función **[SubmitForm](../functions/function-form.md)** se ejecuta correctamente, se modifica un registro existente. |
| **FormMode.New** |El usuario puede crear un registro mediante el formulario. Los valores de los controles del formulario se rellenan con los valores predeterminados para un registro del origen de datos. Si la función **[SubmitForm](../functions/function-form.md)** se ejecuta correctamente, se crea un registro. |
| **FormMode.View** |El usuario puede ver un registro mediante el formulario. Los valores de los controles del formulario se rellenan con los valores predeterminados para un registro del origen de datos. |

El formulario cambia de modo **Nuevo** a modo **Edición** cuando se produce cualquiera de estos cambios:

* El formulario se envía correctamente y se crea un registro. Si se establece la galería para mover automáticamente la selección a este nuevo registro, el formulario estará en modo **Edición** para el registro creado para que el usuario puede realizar cambios adicionales.
* Se ejecuta la función **[EditForm](../functions/function-form.md)**.
* Se ejecuta la función **[ResetForm](../functions/function-form.md)**. Por ejemplo, el usuario puede seleccionar un botón **Cancelar** que se haya configurado con esta función.

**OnFailure**: la forma en la que responde una aplicación cuando una operación de datos ha sido incorrecta.

* Esta propiedad solo se aplica al control **Formulario de edición**.

**OnReset**: la forma en la que responde una aplicación cuando se restablece un control **Formulario de edición**.

* Esta propiedad solo se aplica al control **Formulario de edición**.

**OnSuccess**: la forma en la que responde una aplicación cuando una operación de datos se ha realizado correctamente.

* Esta propiedad solo se aplica al control **Formulario de edición**.

**Sin guardar**: True si el control **Formulario de edición** contiene cambios de usuario que no se guardaron.

* Esta propiedad solo se aplica al control **Formulario de edición**.
* Utilice esta propiedad para advertir al usuario antes de que pierda los cambios no guardados.  Para impedir que el usuario seleccione un registro diferente en un control **[Galería](control-gallery.md)** antes de guardar los cambios en el registro actual, establezca la propiedad **[Deshabilitado](properties-core.md)** en **Form.Unsaved** y, asimismo, deshabilite las operaciones de actualización.

**Actualizaciones**: los valores que se van a escribir en el origen de datos para un registro cargado en un control de formulario.  

* Esta propiedad solo se aplica al control **Formulario de edición**.
* Utilice esta propiedad para extraer los valores de campo de las tarjetas en el control.  A continuación, puede utilizar estos valores para actualizar manualmente el origen de datos con una llamada de función **[Revisión](../functions/function-patch.md)** u otro método expuesto por una conexión.  No es necesario utilizar esta propiedad si usa la función **[SubmitForm](../functions/function-form.md)**.
* Esta propiedad devuelve un registro de valores.  Por ejemplo, si el control de formulario contiene controles de tarjeta para los campos **Nombre** y **Cantidad** y los valores de la propiedad **[Actualizaciones](control-card.md)** para dichas tarjetas devuelven "Widget" y 10, respectivamente, la propiedad **Actualizaciones** para el control de formulario devolvería **{Nombre: "Widget", Cantidad: 10}**.

**Válido**: indica si un control **[Tarjeta](control-card.md)** o **Formulario de edición** contiene entradas válidas listas para enviarse al origen de datos.

* Esta propiedad solo se aplica al control **Formulario de edición**.
* La propiedad **Válido** de un control de **formulario** agrega las propiedades **Válido** de todos los controles **[Tarjeta del formulario](control-card.md)**. La propiedad **Válido** de un formulario es **true** solamente si los datos en todas las tarjetas de ese formulario son válidos, de lo contrario, la propiedad **Válido** del formulario es **false**.
* Para habilitar un botón para guardar los cambios solo cuando los datos en un formulario son válidos pero aún no se han enviado, establezca el botón **Habilitado** con esta fórmula:
  
    **SubmitButton.Enabled = IsBlank( Form.Error ) || Form.Valid**

## <a name="additional-properties"></a>Propiedades adicionales
**[BorderColor](properties-color-border.md)**: el color de un borde del control.

**[BorderStyle](properties-color-border.md)**: si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)**: el grosor de un borde del control.

**[Fill](properties-color-border.md)**: el color de fondo de un control.

**[Height](properties-size-location.md)**: la distancia entre los bordes superior e inferior de un control.

**[Visible](properties-core.md)**: indica si un control aparece o está oculto.

**[Width](properties-size-location.md)**: la distancia entre los bordes derecho e izquierdo de un control.

**[X](properties-size-location.md)**: la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario).

**[Y](properties-size-location.md)**: la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario).

## <a name="more-information"></a>Más información
Para información general integral sobre cómo funcionan los formularios, consulte la [introducción a los formularios de datos](../working-with-forms.md).

