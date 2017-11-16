---
title: Funciones EditarFormulario, NewForm, SubmitForm, ResetForm y ViewForm | Microsoft Docs
description: "Información de referencia sobre las funciones EditarFormulario, NewForm, SubmitForm, ResetForm y ViewForm de PowerApps, incluidos ejemplos y sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/06/2017
ms.author: gregli
ms.openlocfilehash: 7e64426cfee2b72cd8fda51b889b99b285147fcc
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="editform-newform-submitform-resetform-and-viewform-functions-in-powerapps"></a>Funciones EditarFormulario, NewForm, SubmitForm, ResetForm y ViewForm de PowerApps
Vea, edite o cree un elemento, guarde el contenido y restablezca los controles de un control **[Editar formulario](../controls/control-form-detail.md)**.

## <a name="overview"></a>Información general
Estas funciones cambian el estado del control **Editar formulario**.  El control de formulario puede estar en uno de estos modos:

| Modo | Descripción |
| --- | --- |
| **FormMode.Edit** |El formulario se rellena con un registro existente y el usuario puede modificar los valores de los campos.  Una vez que haya finalizado, el usuario puede guardar los cambios en el registro. |
| **FormMode.New** |El formulario se rellena con los valores predeterminados y el usuario puede modificar los valores de los campos.  Una vez que haya finalizado, el usuario puede agregar el registro al origen de datos. |
| **FormMode.View** |El formulario se rellena con un registro existente pero el usuario no puede modificar los valores de los campos. |

## <a name="description"></a>Descripción
Estas funciones a menudo se invocan desde la fórmula **[AlSeleccionar](../controls/properties-core.md)** de un control **[Botón](../controls/control-button.md)** o **[Imagen](../controls/control-image.md)** para que el usuario pueda guardar las modificaciones, abandonarlas o crear un registro. También puede [usar conjuntamente controles y estas funciones](../working-with-forms.md) para crear una solución completa.

Estas funciones no devuelven ningún valor.

### <a name="submitform"></a>SubmitForm
Use la función **SubmitForm** de la propiedad **[AlSeleccionar](../controls/properties-core.md)** de un control Botón para guardar los cambios de un control Formulario en el origen de datos.

Antes de enviar cualquier cambio, esta función comprueba problemas de validación con cualquier campo que se haya marcado como requerido o que tenga una o más restricciones en su valor. Este comportamiento es idéntico al de la función **[Validar](function-validate.md)**.

**SubmitForm** también comprueba la propiedad **[Valid](../controls/control-form-detail.md)** del control Formulario, que es una agregación de todas las propiedades **[Valid](../controls/control-card.md)** de los controles **[Card](../controls/control-card.md)** que contiene el control Formulario. Si se produce un problema, no se envían los datos y las propiedades **[Error](../controls/control-form-detail.md)** y **[ErrorKind](../controls/control-form-detail.md)** del control Formulario se establecen en consecuencia.

Si se supera la validación, **SubmitForm** envía el cambio al origen de datos.

* Si se realiza correctamente, se ejecutará el comportamiento **[OnSuccess](../controls/control-form-detail.md)** del formulario y se borrarán las propiedades **[Error](../controls/control-form-detail.md)** y **[ErrorKind](../controls/control-form-detail.md)**.  Si el formulario se encontraba en modo **FormMode.New**, se devolverá al modo **FormMode.Edit**.
* Si no se realiza correctamente, se ejecutará el comportamiento **[OnFailure](../controls/control-form-detail.md)** del formulario y se establecerán las propiedades **[Error](../controls/control-form-detail.md)** y **[ErrorKind](../controls/control-form-detail.md)** en consecuencia.  El modo del formulario no se modifica.  

### <a name="editform"></a>EditarFormulario
La función **EditarFormulario** cambia el modo del control Formulario a **FormMode.Edit**. En este modo, el contenido de la propiedad **[Elemento](../controls/control-form-detail.md)** del control Formulario se utiliza para rellenar el formulario.  Si la función **SubmitForm** se ejecuta cuando el formulario está en este modo, se cambiará un registro, no se creará.  **FormMode.Edit** es el valor predeterminado del control Formulario.

### <a name="newform"></a>NewForm
La función **NewForm** cambia el modo del control Formulario a **FormMode.New**. En este modo, el contenido de la propiedad **[Elemento](../controls/control-form-detail.md)** del control Formulario se omite y los valores predeterminados de la propiedad **[DataSource](../controls/control-form-detail.md)** rellenan el formulario. Si la función **SubmitForm** se ejecuta cuando el formulario está en este modo, se creará un registro, no se cambiará.

### <a name="resetform"></a>ResetForm
La función **ResetForm** restablece el contenido de un formulario a sus valores iniciales, el contenido que había antes de que el usuario realizara cambios. Si el formulario está en modo **FormMode.New**, se restablecerá al modo **FormMode.Edit**. El comportamiento **[OnReset](../controls/control-form-detail.md)** del control Formulario también se ejecutará.  También puede restablecer controles individuales con la función **[Reset](function-reset.md)** pero únicamente desde dentro del formulario.

### <a name="viewform"></a>ViewForm
La función **ViewForm** cambia el modo del control Formulario a **FormMode.View**. En este modo, el contenido de la propiedad **[Elemento](../controls/control-form-detail.md)** del control Formulario se utiliza para rellenar el formulario.  Las funciones **SubmitForm** y **RestForm** no tienen ningún efecto en este modo.

### <a name="displaymode-poperty"></a>Propiedad DisplayMode
El modo actual se puede leer mediante la propiedad **Modo**.  El modo determina también el valor de la propiedad **DisplayMode** que pueden usar las tarjetas de datos y controles del control de formulario.  Normalmente, la propiedad **DisplayMode** de la tarjeta de datos se establecerá en **Parent.DisplayMode** (que hace referencia al formulario) al igual que lo hará la propiedad **DisplayMode** del control (que hace referencia a la tarjeta de datos): 

| Modo | DisplayMode | Descripción |
| --- | --- | --- |
| **FormMode.Edit** |**DisplayMode.Edit** |Las tarjetas de datos y los controles son editables, y están listos para aceptar los cambios de un registro. |
| **FormMode.New** |**DisplayMode.Edit** |Las tarjetas de datos y los controles son editables, y están listos para aceptar un nuevo registro. |
| **FormMode.View** |**DisplayMode.View** |Las tarjetas de datos y los controles no son editables y están optimizados para su visualización. |

## <a name="syntax"></a>Sintaxis
**SubmitForm**( *FormName* )

* *FormName*: requerido. Control Formulario para enviar al origen de datos.

**EditarFormulario**( *FormName* )

* *FormName*: requerido.  Control Formulario para cambiar al modo **FormMode.Edit**.

**NewForm**( *FormName* )

* *FormName*: requerido. Control Formulario para cambiar al modo **FormMode.New**.

**ResetForm**( *FormName* )

* *FormName*: requerido. Control Formulario para restablecer los valores iniciales. También cambia el formulario del modo **FormMode.New** al modo **FormMode.Edit**.

**ViewForm**( *FormName* )

* *FormName*: requerido.  Control Formulario para cambiar al modo **FormMode.View**.

## <a name="examples"></a>Ejemplos
Consulte [Formularios de datos](../working-with-forms.md) para obtener ejemplos completos.

1. Agregue un control Botón, establezca la propiedad **[Texto](../controls/properties-core.md)** para mostrar **Guardar** y establezca la propiedad **[AlSeleccionar](../controls/properties-core.md)** en esta fórmula:
   
    **SubmitForm( EditarFormulario )**
2. Establezca la propiedad **[OnFailure](../controls/control-form-detail.md)** de un control Formulario en blanco y la propiedad **[OnSuccess](../controls/control-form-detail.md)** en esta fórmula:
   
    **Atrás()**
3. Asigne el nombre **ErrorText** a un control **[Etiqueta](../controls/control-text-box.md)** y establezca su propiedad **[Texto](../controls/properties-core.md)** en esta fórmula:
   
    **EditForm.Error**
   
    Cuando el usuario selecciona el botón **Guardar**, los cambios del control Formulario se envían al origen de datos subyacente.
   
   * Si el envío se realiza correctamente, los cambios se guardan o, si el control Formulario está en modo **New**, se creará un registro. **ErrorText** está *en blanco* y vuelve a aparecer la pantalla anterior.
   * Si se produce un error en el envío, **ErrorText** mostrará un mensaje de error descriptivo y la pantalla actual permanecerá visible para que el usuario pueda corregir el problema e intentarlo de nuevo.
4. Agregue un control Botón, establezca su propiedad **[Texto](../controls/properties-core.md)** para que muestre **Cancelar** y establezca su propiedad **[AlSeleccionar](../controls/properties-core.md)** en esta fórmula:
   
    **ResetForm( EditarFormulario ); Atrás()**
   
    Si el usuario selecciona el botón **Cancelar**, los valores del control Formulario se restablecen a su estado original, el estado que tenían antes de que el usuario empezara a editarlo, vuelve a aparecer la pantalla anterior y se devuelve el control Formulario al modo **Edit** si estaba en modo **New**.
5. Agregue un control Botón, establezca su propiedad **[Texto](../controls/properties-core.md)** para mostrar **Nuevo** y establezca su propiedad **[AlSeleccionar](../controls/properties-core.md)** en esta fórmula:
   
    **NewForm( EditarFormulario ); Navigate( EditarPantalla, None )**
   
    Cuando el usuario selecciona el botón **New**, se activa el control Formulario en modo **New**, los valores predeterminados del origen de datos del control Formulario rellenan el control y aparece la pantalla que contiene el control Formulario. Cuando se ejecuta la función **SubmitForm**, se crea un registro en lugar de actualizarlo.

