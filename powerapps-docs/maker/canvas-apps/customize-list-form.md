---
title: Personalización de un formulario de lista de SharePoint mediante PowerApps | Microsoft Docs
description: Use PowerApps para personalizar un formulario de lista de SharePoint.
documentationcenter: na
author: aftowen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 02/05/2018
ms.author: anneta
ms.openlocfilehash: c5dafffba91f4e4ce8e4e27d4780e91bf5ddc415
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="customize-a-sharepoint-list-form-using-powerapps"></a>Personalización de un formulario de lista de SharePoint mediante PowerApps

Ahora puede personalizar fácilmente cualquier formulario de lista de SharePoint en PowerApps. Gran parte de lo que hacía con InfoPath para personalizar formularios de lista de SharePoint puede hacerlo ahora en línea en un explorador con PowerApps. Pero, PowerApps ofrece además muchas otras posibilidades.

PowerApps está directamente integrado en SharePoint: no es necesario descargar otra aplicación en el equipo. Y con PowerApps, puede crear formularios enormemente personalizados sin necesidad de escribir código. Una vez publicados, los formularios se insertan en la lista de SharePoint y están disponibles para todos los usuarios de la lista.

Y como PowerApps se integra perfectamente en SharePoint, no es necesario administrar los formularios desde dos lugares: los permisos se heredan y se administran en SharePoint. Lo mejor de todo es que al tener PowerApps integrado con SharePoint, dispone de acceso a muchas características eficaces, como informes de análisis, reglas sencillas de apuntar y hacer clic para el formato condicional y conexiones a otros orígenes de datos.

¿Está preparado para empezar a personalizar? ¡Pues vamos a ello!

## <a name="create-a-custom-list-form-app-in-powerapps"></a>Creación de una aplicación de formulario de lista personalizado en PowerApps

> [!NOTE]
> La opción **Customize forms** (Personalizar formularios) dejará de estar disponible, o puede que no funcione correctamente, si la lista de SharePoint contiene tipos de datos que no admiten PowerApps.

En la lista de SharePoint, pulse o haga clic en **PowerApps** en la barra de comandos y, a continuación, pulse o haga clic en **Customize forms** (Personalizar formularios). Esta acción le lleva a PowerApps Studio para web en un explorador, donde PowerApps genera una aplicación de formulario de una única pantalla, como se muestra en el ejemplo siguiente.

![Aplicación de formulario de una única pantalla](./media/customize-list-form/list-form-app.png)

Para volver a la lista de SharePoint en cualquier momento, pulse o haga clic en **Volver a SharePoint** en la esquina superior izquierda de PowerApps Studio para web.

## <a name="customize-the-list-form"></a>Personalización del formulario de lista

PowerApps ofrece muchas maneras de personalizar el formulario. Estos son algunos ejemplos:

* [Cambiar el tamaño y la orientación](set-aspect-ratio-portrait-landscape.md)
* [Dar formato al texto](controls/properties-text.md)
* [Agregar imágenes](add-images-pictures-audio-video.md) o [gráficos](use-line-pie-bar-chart.md)
* [Agregar validación de datos personalizados](functions/function-validate.md)
* [Agregar reglas](working-with-rules.md)
* [Crear vistas adicionales](https://powerapps.microsoft.com/blog/separate-custom-forms/)

A modo de ejemplo, supongamos que el formulario tiene un campo **AccountID** que no desea que se vea.

![Selección del campo AccountID](./media/customize-list-form/select-card.png)

Ocultar el campo es muy sencillo en PowerApps en las opciones de personalización del formulario, solo tiene que desactivar la casilla **AccountID**.

![Desactivación de la casilla AccountID](./media/customize-list-form/checkbox.png)

Para obtener instrucciones paso a paso sobre cómo ocultar campos y realizar otros cambios en el formulario, consulte [Customize forms in PowerApps](customize-forms-sharepoint.md) (Personalización de los formularios en PowerApps). Para ver una lista completa de los recursos, consulte [Microsoft PowerApps docs](https://docs.microsoft.com/powerapps/) (Documentos de Microsoft PowerApps).

## <a name="save-and-publish-the-list-form-back-to-sharepoint"></a>Almacenamiento y publicación del formulario de lista de nuevo en SharePoint

1. Cuando haya terminado, pulse o haga clic en **Archivo** y, a continuación, pulse o haga clic en **Guardar**. Los cambios se guardan en la aplicación de formulario de PowerApps.

1. Para volver a publicar el formulario en SharePoint para que otros usuarios puedan usarlo, pulse o haga clic en **Publicar en SharePoint**. No es necesario preocuparse de compartir el formulario, ya que este hereda los permisos de la lista de SharePoint.

    ![Publicar en SharePoint](./media/customize-list-form/publish-to-sharepoint.png)  

## <a name="view-your-list-form-in-sharepoint"></a>Visualización del formulario de lista en SharePoint

1. Para ver el formulario personalizado, pulse o haga clic en **Volver a SharePoint** y, a continuación, pulse o haga clic en cualquier elemento de la lista de SharePoint. El formulario se abre alineado en el lado derecho de la ventana del explorador.

    ![Apertura del formulario alineado en SharePoint](./media/customize-list-form/list-form-open.png)

1. Si desea [personalizar aún más el formulario](sharepoint-form-integration.md), pulse o haga clic en **Personalizar** y, a continuación, realice los cambios. Cuando haya terminado, asegúrese de guardar los cambios.

    ![Botón Personalizar](./media/customize-list-form/customize-button.png)

    Puede personalizar el formulario y guardar los cambios tantas veces como desee, pero dichos cambios no serán visibles en SharePoint hasta que pulse o haga clic en **Publicar en SharePoint**.

## <a name="toggle-between-using-the-default-sharepoint-form-and-the-custom-form"></a>Alternancia entre el uso del formulario de SharePoint predeterminado y el formulario personalizado

1. En la lista de SharePoint, pulse o haga clic en **Configuración**, pulse o haga clic en **Configuración de lista** y, luego, pulse o haga clic en **Form settings** (Configuración de formulario).

1. En la página **Form Settings** (Configuración de formulario), pulse o haga clic en una de las siguientes opciones y, luego, pulse o haga clic en **Aceptar**.

    * **Use the default SharePoint form** (Usar el formulario de SharePoint predeterminado): SharePoint usará el formulario de SharePoint predeterminado para su lista.

    * **Use a custom form created in PowerApps** (Usar un formulario personalizado creado en PowerApps): SharePoint usará el formulario que personalizó en PowerApps (también puede volver a publicar el formulario desde la página **Guardar** de PowerApps Studio para web).

    Puede alternar entre las opciones, según sea necesario.

    ![Opciones de configuración de formulario](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-list-form"></a>Eliminación del formulario de lista personalizado

1. En la lista de SharePoint, pulse o haga clic en **Configuración**, pulse o haga clic en **Configuración de lista** y, luego, pulse o haga clic en **Form settings** (Configuración de formulario).

1. En la página **Form Settings** (Configuración de formulario), pulse o haga clic en **Use the default SharePoint form** (Usar el formulario de SharePoint personalizado) y, en la opción **Use a custom form created in PowerApps** (Usar un formulario personalizado creado en PowerApps), pulse o haga clic en **Delete custom form** (Eliminar formulario personalizado). Esta acción elimina el formulario personalizado que ha creado en PowerApps y el formulario vuelve al predeterminado de SharePoint.

    ![Eliminación del formulario personalizado](./media/customize-list-form/use-default-sharepoint.png)

## <a name="top-questions-about-list-form-customization"></a>Preguntas principales sobre la personalización de formularios de lista

### <a name="customizing-forms-versus-creating-apps"></a>Personalización de formularios frente a creación de aplicaciones

**P:** ¿En qué se diferencia un formulario de lista personalizado de una aplicación independiente que se crea desde SharePoint o PowerApps?

**R:** La aplicación de formulario de lista que se crea desde SharePoint es un tipo especial de aplicación de PowerApps que solo se puede usar en una lista de SharePoint. Estas aplicaciones de formulario de lista no aparecen en la lista de aplicaciones de PowerApps Studio para web o PowerApps Mobile y no se pueden ejecutar fuera de la lista de SharePoint.

**P:** ¿Cuándo se debe crear un formulario de lista personalizado y cuándo una aplicación independiente?

**R:** Si quiere que los usuarios accedan al formulario mediante SharePoint, y quiere personalizar cómo crean, ven o editan elementos de lista, se recomienda crear un formulario de lista personalizado dentro de SharePoint. Si quiere crear una experiencia totalmente personalizada para los usuarios que puedan usar con independencia del sitio de SharePoint, se recomienda crear una aplicación independiente.

**P:** ¿Se puede personalizar un formulario de lista y crear una aplicación independiente para la misma lista?

**R:** Sí. Las aplicaciones independientes y los formularios de lista personalizados son independientes entre sí; puede personalizarlos y administrarlos de manera individual.

**P:** ¿Las características de personalización para personalizar un formulario de lista son las mismas que las que se usan para personalizar una aplicación independiente?

**R:** Sí. También puede [agregar y configurar controles](add-configure-controls.md), [conectarse a orígenes de datos disponibles](add-data-connection.md) o [agregar sus propios orígenes de datos](../canvas-apps/register-custom-api.md), exactamente igual que con las aplicaciones independientes.

**P:** ¿Se pueden crear formularios de lista personalizados en un entorno distinto al predeterminado de la organización?

**A:** No. Actualmente solo puede crear formularios de lista personalizados en el entorno de PowerApps predeterminado de su organización; no puede crear formularios de lista personalizados en otro entorno ni migrarlos a otro entorno.

### <a name="managing-your-custom-list-form"></a>Administración del formulario de lista personalizado

**P:** ¿Cómo se obtiene un vínculo directo a un formulario de lista que se puede compartir con otros?

**R:** Abra el formulario en la lista de SharePoint y luego pulse o haga clic en **Copiar vínculo**.

**P:** ¿Se puede actualizar un formulario de lista sin realizar cambios visibles en otros?

**R:** Sí. Puede realizar cambios en el formulario y guardarlos tantas veces como desee, pero los cambios no serán visibles para otros usuarios hasta que pulse o haga clic en **[Publicar en SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint)**.

**P:** Si se personaliza un formulario de lista y se comete un error, ¿se puede volver a la versión anterior?

**R:** Sí. Si realiza cambios en el formulario y guarda esos cambios y luego se da cuenta de que ha cometido algún error, puede volver a una versión anterior del formulario mediante PowerApps:

1. En la lista de SharePoint, pulse o haga clic en **PowerApps** en la barra de comandos y, a continuación, pulse o haga clic en **Customize forms** (Personalizar formularios).

1. En PowerApps Studio para web, pulse o haga clic en **Archivo** y, a continuación, en la página **Guardar**, pulse o haga clic en **Ver todas las versiones**. Se abre la página **Versiones** en una nueva pestaña de explorador.

    > [!NOTE]
    > Si no ve el botón **Ver todas las versiones**, pulse o haga clic en **Guardar**. Debería aparecer el botón.

1. Sin cerrar la página **Versiones** o la pestaña del explorador, vuelva a la página **Guardar** en la otra pestaña del explorador, pulse o haga clic en la flecha en la parte superior del panel de navegación izquierdo y, a continuación, pulse o haga clic en **Volver a SharePoint** para desbloquear el formulario y salir de PowerApps Studio para web.

1. Vuelva a la página **Versiones** de la otra pestaña del explorador, busque la versión que quiere restaurar y, luego, haga clic en **Restaurar**.

    > [!NOTE]
    > Si recibe un mensaje de error que indica que la restauración no se pudo realizar porque otro usuario ha bloqueado el formulario, espere a que el usuario lo desbloquee y, a continuación, vuelva a intentarlo.

**P:** ¿Se puede mover un formulario de lista personalizado de una lista a otra?

**A:** No. Esta funcionalidad no se admite actualmente.

### <a name="administering-custom-list-forms"></a>Administración de formularios de lista personalizados

**P:** ¿Cómo se comparte un formulario de lista personalizado con otros usuarios?

**R:** No es necesario compartir el formulario, ya que este hereda los permisos de la lista de SharePoint. Cuando haya terminado de personalizarlo, solo tiene que [volver a publicarlo en SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint) para que otros usuarios puedan usarlo.

**P:** ¿Quién puede personalizar los formularios de lista?

**R:** Cualquier persona con permisos de SharePoint para administrar, diseñar o editar la lista asociada.

**P: ¿** ¿Se necesita una licencia de PowerApps para crear o utilizar formularios de lista personalizados?

**R:** Si tiene algún [plan de Office 365 que incluya PowerApps](../../administrator/pricing-billing-skus.md#licenses), puede crear o utilizar formularios de lista personalizados.

**P:** ¿Qué sucede cuando los usuarios invitados acceden a una lista que tiene un formulario personalizado?

**R:** Los usuarios invitados reciben un mensaje de error si intentan acceder a un formulario de lista que se ha personalizado mediante PowerApps.

**P:** ¿Cómo reciben los administradores una lista de todos los formularios personalizados de su organización?

**A:** Si es un administrador de inquilinos de PowerApps o tiene permisos de administrador en el entorno predeterminado de PowerApps de la organización, haga lo siguiente:

1. Vaya al [centro de administración de PowerApps](https://admin.powerapps.com) y seleccione el entorno predeterminado de su organización en la lista de entornos.

1. En la parte superior de la página del entorno predeterminado, pulse o haga clic en **Recursos**.

1. En la lista de aplicaciones, busque aplicaciones con un tipo de aplicación de **formulario de SharePoint**, que son los formularios personalizados.

    ![Lista de formularios personalizados](./media/customize-list-form/all-customized-forms.png)
