---
title: Personalización de un formulario de lista de SharePoint | Microsoft Docs
description: Use PowerApps para personalizar el formulario con el que los usuarios crean y actualizan las entradas de una lista de SharePoint.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/04/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 66fe60c0d74c86705615522621d8f277fcc343ae
ms.sourcegitcommit: dbd922de8f2e97a478df64e7e9ba33b48574af5c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65088166"
ms.PowerAppsDecimalTransform: true
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>Personalizar un formulario de lista de SharePoint mediante PowerApps

Puede personalizar fácilmente el formulario de una lista de SharePoint si abre PowerApps en un explorador. No es necesario escribir código tradicional, como C#, ni descargar otra aplicación, como InfoPath. Al publicar los cambios, el formulario se inserta en la lista de SharePoint para su uso por parte de todos sus usuarios. En PowerApps también es posible revisar informes de análisis, crear formato condicional con facilidad y conectarse a otros orígenes de datos.

Para seguir los pasos de este tema, tiene que crear una lista simple para que pueda ver cómo funciona la personalización y luego pueda aplicar los mismos conceptos a su propia lista.

> [!NOTE]
> Si la opción **Personalizar formularios** no está disponible o no funciona correctamente, podría contener tipos de datos que [PowerApps no admite](connections/connection-sharepoint-online.md#known-issues). Además, no se puede mover el formulario a otra lista o [entorno](working-with-environments.md).

## <a name="create-a-list"></a>Crear una lista

En un sitio de SharePoint, cree una lista y, a continuación, agregar estas columnas a dicha lista:

- **Detalles** (sí/no)
- **Precio** (moneda)
- **Disponibilidad** (fecha sin hora)
- **Color** (opción)

> [!div class="mx-imgBorder"]
> ![Seleccione el contenido del sitio > Nuevo > lista, escriba el nombre de la lista y seleccione crear. Para cada columna, seleccione Agregar columna, especifique el tipo de lista (Sí/No, moneda, fecha, opción), especifique el nombre de lista (obtener más información, precios, disponibilidad, Color) y seleccione Guardar.](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>Abra el formulario

1. En la barra de comandos, seleccione **PowerApps**y, a continuación, seleccione **personalizar el formulario**.

    PowerApps Studio se abre en la misma pestaña del explorador.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

> [!div class="mx-imgBorder"]
> ![En la barra de comandos, seleccione PowerApps y, a continuación, seleccione la forma de personalizar. PowerApps Studio se abre en la misma pestaña del explorador. Si se abre el cuadro de diálogo de PowerApps Studio Bienvenido, seleccione Omitir.](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>Mover y quitar un campo

1. Arrastre el **disponibilidad** campo a la parte inferior de la lista de campos.

    Los campos aparecen en el orden que especifique.

1. Mantenga el mouse sobre el **datos adjuntos** , seleccione el botón de puntos suspensivos (...) que aparece y, a continuación, seleccione **quitar**.

    El campo que especifique desaparece del formulario.

> [!div class="mx-imgBorder"]
> ![Arrastre el campo de disponibilidad a la parte inferior de la lista de campos. Mantenga el mouse sobre el campo de datos adjuntos, seleccione el botón de puntos suspensivos (...) que aparece y, a continuación, seleccione Quitar.](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>Establecer formato condicional

Puede configurar que los campos **Precio**, **Disponibilidad** y **Color** solo aparezcan si **Detalles** está establecido en Sí.

1. En la barra de navegación izquierdo, expanda **Details_DataCard1**y tenga en cuenta el número que aparece al final de **DataCardValue**.

1. Establecer el **Visible** propiedad de la **Color**, **disponibilidad**, y **precio** tarjetas en esta fórmula (reemplazar, si es necesario, el número con la que anotó en el paso anterior):

    **If(DataCardValue2.Value = true; true)**

1. Mientras mantiene la tecla Alt presionada, seleccione el botón de alternancia **Detalles** varias veces (al hacer clic o pulsar en él).

    Los tres campos que ha configurado aparecen y desaparecen del formulario.

> [!div class="mx-imgBorder"]
> ![En la barra de navegación izquierda, tenga en cuenta el número que aparece al final de DataCardValue. Establezca la propiedad de visibilidad de Color, la disponibilidad y el precio de las tarjetas en esta fórmula. Mantenga presionada la tecla Alt y seleccionar el control de detalles varias veces.](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>Guardar y publicar el formulario

1. Abra el menú **Archivo**, seleccione **Guardar** y luego seleccione **Publicar en SharePoint** dos veces.

1. En la esquina superior izquierda, seleccione la flecha Atrás y luego **Volver a SharePoint**.

> [!div class="mx-imgBorder"]
> ![Abra el menú archivo, seleccione Guardar y, a continuación, seleccione Publicar en SharePoint de dos veces. En la esquina superior izquierda, seleccione la flecha Atrás y, a continuación, seleccione nuevo en SharePoint.](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>Personalizar aún más el formulario

1. Abra la lista, seleccione **New** en el comando de la barra y, a continuación, seleccione **personalizar** cerca de la parte superior del formulario.

1. Personalizar el formulario en una variedad de formas, como las que se describen estos temas:

    - Cambie su tamaño, orientación o ambos (por ejemplo, para [ensanchar el formulario](set-aspect-ratio-portrait-landscape.md)).
    - [Personalizar uno o más tarjetas](working-with-cards.md) (por ejemplo, Cambiar control de texto o una entrada de la pantalla de la tarjeta).
    - Cree un [campo de búsqueda](sharepoint-lookup-fields.md).

    Más información: [Comprensión de la integración de formularios de SharePoint](sharepoint-form-integration.md).

## <a name="use-the-default-form"></a>Usar el formulario predeterminado

1. En la lista de SharePoint, abra la página de configuración (al seleccionar el icono de engranaje junto a la esquina superior derecha) y luego seleccione **Configuración de lista**.

2. En **Configuración general**, seleccione **Configuración de formulario**.

3. En la página **Configuración de formulario**, seleccione una de estas opciones y luego **Aceptar**.

    - **Usar el formulario predeterminado de SharePoint**: cuando un usuario abra la lista y seleccione **Nuevo** en la barra de comandos, aparecerá el formulario predeterminado de la lista.

    - **Usar un formulario personalizado creado en PowerApps**: cuando un usuario abra la lista y seleccione **Nuevo** en la barra de comandos, aparecerá el formulario personalizado. (Como alternativa, puede volver a publicar el formulario en PowerApps).

    Puede alternar entre las opciones, según sea necesario.

    ![Opciones de configuración de formulario](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>Eliminación del formulario personalizado

1. En la lista de SharePoint, abra la página de configuración (al seleccionar el icono de engranaje junto a la esquina superior derecha) y luego seleccione **Configuración de lista**.

1. En **Configuración general**, seleccione **Configuración de formulario**.

1. En la página **Configuración de formulario**, seleccione **Usar el formulario predeterminado de SharePoint** y luego **Eliminar formulario personalizado**.

    ![Eliminación del formulario personalizado](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>PREGUNTAS Y RESPUESTAS

### <a name="forms-vs-apps"></a>Formularios frente a aplicaciones

**P: ¿** ¿Cómo se diferencia un formulario personalizado desde una aplicación independiente que se crea desde SharePoint o PowerApps?

**R:** Si personaliza el formulario para obtener una lista de SharePoint, el formulario no aparece como una aplicación en PowerApps Studio o PowerApps Mobile. Solo puede abrir el formulario desde la lista para la que lo ha creado.

**P: ¿** ¿Cuándo se puede personalizar un formulario para administrar datos en una lista de SharePoint, y cuándo debo crear una aplicación independiente?

**R:** Personalizar un formulario si desea que los usuarios para administrar los datos sin salir de SharePoint (por ejemplo, en un explorador de escritorio). Cree una aplicación si quiere que los usuarios administren los datos fuera de SharePoint (por ejemplo, en un dispositivo móvil).

**P: ¿** ¿Puedo personalizar un formulario y crear una aplicación para la misma lista?

**R:** Sí.

**P: ¿** ¿Puedo personalizar una lista y crear una aplicación con las mismas características?

**R:** Sí.

**P: ¿** ¿Puedo personalizar un formulario en un entorno distinto al predeterminado de mi organización?

**R:** No.

### <a name="manage-your-custom-form"></a>Administrar el formulario personalizado

**P: ¿** ¿Cómo puedo fácilmente compartir mi formulario con otras personas?

**R:** Abra el formulario, seleccione **Copiar vínculo**y, a continuación, envíe el vínculo a nadie que desee utilizar el formulario.

**P: ¿** ¿Puedo actualizar mi formulario sin realizar cambios visibles para otros usuarios?

**R:** Sí. Puede modificar el formulario y guardarlo tantas veces como quiera, pero los cambios no serán visibles para nadie a menos que seleccione **Publicar en SharePoint** dos veces.

**P: ¿** ¿Si comete un error y personalizar un formulario de lista, puedo volver a una versión anterior?

**R:** Sí.

1. Abra la lista, seleccione **PowerApps** en la barra de comandos y luego seleccione **Personalizar formularios**.

1. En PowerApps Studio, seleccione **Archivo** y luego **Ver todas las versiones**. Se abre la página **Versiones** en una nueva pestaña de explorador.

    > [!NOTE]
    > Si no ve el botón **Ver todas las versiones**, seleccione **Guardar**. Debería aparecer el botón.

1. Sin cerrar la página **Versiones** ni la pestaña del explorador, vuelva a la página **Guardar** de la otra pestaña del explorador, pulse o haga clic en la flecha de la parte superior del panel de navegación izquierdo y, después, pulse o haga clic en **Volver a SharePoint** para desbloquear el formulario y cerrar PowerApps Studio.

1. Vuelva a la página **Versiones** de la otra pestaña del explorador, busque la versión que quiere restaurar y luego seleccione **Restaurar**.

    > [!NOTE]
    > Si recibe un mensaje de error que dice que la restauración no se pudo porque el formulario está bloqueado por otro usuario, espere hasta que el usuario desbloquea el formulario y, a continuación, vuelva a intentarlo.

**P: ¿** ¿Puedo mover mi formulario de una lista a otra?

**R:** No.

### <a name="administer-your-custom-form"></a>Administrar el formulario personalizado

**P: ¿** ¿Cómo se puede compartir mi formulario?

**R:** No necesita compartir el formulario, este hereda los permisos de la lista de SharePoint. Cuando haya terminado de personalizarlo, solo tiene que [volver a publicarlo en SharePoint](customize-list-form.md#save-and-publish-the-form) para que otros usuarios puedan usarlo.

**P: ¿** ¿Quién puede personalizar los formularios?

**R:** Cualquier persona con permisos de SharePoint para administrar, diseñar o modificar la lista asociada.

**P: ¿** ¿Necesito una licencia de PowerApps para crear o utilizar formularios de lista personalizados?

**R:** Necesita un [plan de Office 365 que incluye PowerApps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses).

**P: ¿** ¿Qué ocurre cuando los usuarios invitados tienen acceso a una lista que tiene un formulario personalizado?

**R:** Los usuarios invitados recibirán un mensaje de error si intentan tener acceso a un formulario de lista que se ha personalizado mediante PowerApps.

**P: ¿** Como administrador, ¿cómo obtengo una lista de todos los formularios personalizados de mi organización?

**R:** Si un administrador de inquilinos de PowerApps o tener permisos de administrador de entorno en el entorno de PowerApps predeterminado de su organización, realice lo siguiente:

1. En el [centro de administración de PowerApps](https://admin.powerapps.com), seleccione el entorno predeterminado de la organización en la lista de entornos.

1. En la parte superior de la página del entorno predeterminado, seleccione **Recursos**.

1. En la lista de aplicaciones, busque aplicaciones con un **formularios de SharePoint** tipo de aplicación, estos son los formularios personalizados.

    ![Lista de formularios personalizados](./media/customize-list-form/all-customized-forms.png)
