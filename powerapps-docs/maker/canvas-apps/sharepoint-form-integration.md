---
title: Comprensión de la integración de formularios de SharePoint | Microsoft Docs
description: Comprensión de cómo funcionan los formularios personalizados con SharePoint
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/11/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 919efacd1a1dc5c931d71e07024aa7c8a30168bf
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61538885"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-sharepoint-forms-integration"></a>Comprensión de la integración de formularios de SharePoint
Ahora puede [personalizar cualquier formulario de lista de SharePoint](customize-list-form.md) de manera fácil en PowerApps. En este artículo, le guiaremos por los detalles de cómo funcionan estos formularios y cómo puede personalizarlos aún más.

Si ha personalizado un formulario de una lista de SharePoint, es probable que haya observado que el formulario generado predeterminado funciona con todas las operaciones, como crear, mostrar o editar un elemento. Esta funcionamiento se logra con la ayuda de las fórmulas generadas y del control **SharePointIntegration**.

## <a name="understand-the-default-generated-form"></a>Descripción del formulario generado predeterminado

El formulario generado predeterminado consta de los siguientes controles y sus valores predeterminados correspondientes:

* **FormScreen1**: esta es la [pantalla](controls/control-screen.md) que contiene el formulario.

* **SharePointForm1**: este es el [formulario](working-with-forms.md) que se usa para crear, mostrar o editar el elemento de lista.

    * **Origen de datos**: la lista para la que se ha personalizado el formulario.

    * **Elemento**: el elemento seleccionado de la lista. Para su comodidad, este se establece en el elemento First() de la lista al trabajar en PowerApps Studio.

        **If(IsBlank(SharePointIntegration.Selected) || IsEmpty(SharePointIntegration.Selected);First('*YourListName*');SharePointIntegration.Selected)**

    * **OnSuccess**: una vez que el elemento se crea o se guarda correctamente, el formulario se restablece y SharePoint oculta el formulario.

        **ResetForm(SharePointForm1);; RequestHide()**

* **SharePointIntegration**: el control responsable de la comunicación de las acciones de los usuarios entre SharePoint y PowerApps.

    * **Origen de datos**: la lista para la que se ha personalizado el formulario.

        **'*YourListName*'**

    * **OnNew**: establece **SharePointForm1** en el modo nuevo.

        **NewForm(SharePointForm1)**

    * **OnNew**: establece **SharePointForm1** en el modo de vista.

        **ViewForm(SharePointForm1)**

    * **OnEdit**: establece **SharePointForm1** en modo de edición.

        **EditForm(SharePointForm1)**

    * **OnSave**: envía los cambios a **SharePointForm1**. Tras el envío correcto del formulario, se ejecuta la fórmula **SharePointForm1.OnSuccess**.

        **SubmitForm(SharePointForm1)**

    * **OnCancel**: restablece los cambios realizados en **SharePointForm1**. SharePoint siempre oculta el formulario cuando un usuario pulsa o hace clic en **Cancelar** en SharePoint.

        **ResetForm(SharePointForm1)**

Estos valores predeterminados garantizan que el formulario funciona cuando se ejecuta en SharePoint (lo que hacen es cambiar el modo del formulario de PowerApps cuando el usuario interactúa con él en SharePoint, y garantizan que los cambios se envían a SharePoint).

## <a name="understand-the-sharepointintegration-control"></a>Descripción del control SharePointIntegration
El control **SharePointIntegration** comunica las acciones de los usuarios entre SharePoint y PowerApps.

![](./media/sharepoint-form-integration/sharepointintegration-object.png)

>[!NOTE]
>Solo puede acceder a las propiedades del control **SharePointIntegration** cuando el formulario se ejecuta en SharePoint, es decir, no al personalizarlo en PowerApps Studio. Es posible que estas propiedades no estén disponibles en **OnStart** u **OnVisible**. 

El control **SharePointIntegration** tiene las siguientes propiedades:

**Selected**: el elemento seleccionado de la lista de SharePoint.

**OnNew**: cómo responde la aplicación cuando un usuario pulsa o hace clic en el botón **Nuevo** o abre el formulario **Crear elemento** en SharePoint.

**OnView**: cómo responde una aplicación cuando un usuario pulsa o hace clic en un **elemento** o abre el formulario **Item detail** (Detalle de elemento) en SharePoint.

**OnEdit**: cómo responde una aplicación cuando un usuario pulsa o hace clic en el botón **Edit all** (Editar todo) o abre el formulario **Editar elemento** de SharePoint.

**OnSave**: cómo responde una aplicación cuando un usuario pulsa o hace clic en el botón **Guardar** en SharePoint.

**OnCancel**: cómo responde una aplicación cuando un usuario pulsa o hace clic en el botón **Cancelar** en SharePoint.

**SelectedListItemID**: identificador del elemento seleccionado en una lista de SharePoint.

**Origen de datos**: la lista que contiene el registro que el formulario mostrará, editará o creará. Tenga en cuenta que si cambia esta propiedad, las propiedades **Selected** y **SelectedItemID** podrían dejar de funcionar.

## <a name="customize-the-default-form"></a>Personalización del formulario predeterminado
Ahora que comprende mejor el formulario generado predeterminado y el control **SharePointIntegration**, puede cambiar las fórmulas para personalizar aún más los formularios. Al personalizar formularios, tenga en cuenta algunas de estas cosas:

* Para crear experiencias personalizadas independientes con el fin de crear, mostrar o editar un elemento, establezca las fórmulas **OnNew**, **OnView** o **OnEdit** del control  **SharePointIntegration** para establecer variables o navegar a distintas pantallas.

* Use la fórmula **OnSave** del control **SharePointIntegration** para personalizar lo que sucede cuando un usuario pulsa o hace clic en **Guardar** en SharePoint. Si tiene varios formularios, asegúrese de enviar los cambios correspondientes solamente al formulario que usa actualmente.

  > [!TIP]
  >    Establezca diferentes valores para una variable en las fórmulas **OnNew**, **OnView** y **OnEdit**. Puede usar esta variable en la fórmula **OnSave** para determinar el formulario que usa.

* No olvide incluir **RequestHide()** en la fórmula **OnSuccess** de todos los formularios. Si lo olvida, SharePoint no sabrá cuándo ocultar el formulario.

* Como no puede controlar que se oculte un formulario cuando un usuario pulsa o hace clic en **Cancelar** en SharePoint, asegúrese de restablecer los formularios de la fórmula **OnCancel** del control **SharePointIntegration**.

* Es posible que las propiedades del control **SharePointIntegration** no estén disponibles en **OnStart** u **OnVisible**. Asimismo, estos eventos solo se ejecutan una vez durante la carga de la lista. Puede usar fórmulas **OnNew**, **OnView** u **OnEdit** para ejecutar lógicas antes de que el formulario se muestre al usuario cada vez. 
