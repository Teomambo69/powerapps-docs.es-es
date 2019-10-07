---
title: Personalización de un formulario de lista de SharePoint | Microsoft Docs
description: Use PowerApps para personalizar el formulario con el que los usuarios crean y actualizan las entradas de una lista de SharePoint.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/04/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 60d4fb21bc2f298b1dd2ce37c3e25f5355e881cb
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993137"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>Personalizar un formulario de lista de SharePoint mediante PowerApps

Puede personalizar fácilmente el formulario de una lista de SharePoint si abre PowerApps en un explorador. No es necesario escribir código tradicional, como C#, ni descargar otra aplicación, como InfoPath. Al publicar los cambios, el formulario se inserta en la lista de SharePoint para su uso por parte de todos sus usuarios. En PowerApps también es posible revisar informes de análisis, crear formato condicional con facilidad y conectarse a otros orígenes de datos.

Para seguir los pasos de este tema, tiene que crear una lista simple para que pueda ver cómo funciona la personalización y luego pueda aplicar los mismos conceptos a su propia lista.

> [!NOTE]
> Si la opción **Personalizar formularios** no está disponible o no funciona correctamente, podría contener tipos de datos que [PowerApps no admite](connections/connection-sharepoint-online.md#known-issues). Además, no se puede mover el formulario a otra lista o [entorno](working-with-environments.md).

## <a name="create-a-list"></a>Crear una lista

En un sitio de SharePoint, cree una lista y, a continuación, agregue estas columnas a esa lista:

- **Detalles** (sí/no)
- **Precio** (moneda)
- **Disponibilidad** (fecha sin hora)
- **Color** (opción)

> [!div class="mx-imgBorder"]
> @no__t: contenido del sitio de 0Select > nueva lista de >, escriba el nombre de la lista y seleccione crear. Para cada columna, seleccione Agregar columna, especifique el tipo de lista (sí/no, moneda, fecha, elección), especifique el nombre de la lista (detalles, precio, disponibilidad, color) y seleccione Guardar. ](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>Abrir el formulario

1. En la barra de comandos, seleccione **PowerApps**y, a continuación, seleccione **personalizar formulario**.

    PowerApps Studio se abre en la misma pestaña del explorador.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

> [!div class="mx-imgBorder"]
> @no__t 0In la barra de comandos, seleccione PowerApps y, luego, seleccione Personalizar formulario. PowerApps Studio se abre en la misma pestaña del explorador. Si aparece el cuadro de diálogo Asistente para PowerApps Studio, seleccione Omitir. ](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>Desplazamiento y eliminación de un campo

1. Arrastre el campo **Availability** hasta la parte inferior de la lista de campos.

    Los campos aparecen en el orden que especifique.

1. Mantenga el mouse sobre el campo **datos adjuntos** , seleccione los puntos suspensivos (...) que aparecen y, a continuación, seleccione **quitar**.

    El campo que especifique desaparece del formulario.

> [!div class="mx-imgBorder"]
> @no__t: 0Drag el campo disponibilidad en la parte inferior de la lista de campos. Mantenga el mouse sobre el campo datos adjuntos, seleccione los puntos suspensivos (...) que aparecen y, a continuación, seleccione quitar. ](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>Establecer formato condicional

Puede configurar que los campos **Precio**, **Disponibilidad** y **Color** solo aparezcan si **Detalles** está establecido en Sí.

1. En la barra de navegación de la izquierda, expanda **Details_DataCard1**y anote el número que aparece al final de **DataCardValue**.

1. Establezca la propiedad **visible** del **color**, la **disponibilidad**y las tarjetas de **precios** en esta fórmula (reemplace, si es necesario, el número por el que anotó en el paso anterior):

    **Si (DataCardValue2. Value = true, true)**

1. Mientras mantiene la tecla Alt presionada, seleccione el botón de alternancia **Detalles** varias veces (al hacer clic o pulsar en él).

    Los tres campos que ha configurado aparecen y desaparecen del formulario.

> [!div class="mx-imgBorder"]
> ![In la barra de navegación izquierda, tenga en cuenta el número que aparece al final de DataCardValue. Establezca la propiedad Visibility del color, la disponibilidad y las tarjetas de precios en esta fórmula. Mantenga presionada la tecla Alt y seleccione el control de detalles varias veces. ](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>Guardar y publicar el formulario

1. Abra el menú **Archivo**, seleccione **Guardar** y luego seleccione **Publicar en SharePoint** dos veces.

1. En la esquina superior izquierda, seleccione la flecha Atrás y luego **Volver a SharePoint**.

> [!div class="mx-imgBorder"]
> ![Open en el menú Archivo, seleccione Guardar y, a continuación, seleccione publicar en SharePoint dos veces. En la esquina superior izquierda, seleccione la flecha atrás y, a continuación, seleccione volver a SharePoint. ](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>Personalización adicional del formulario

1. Abra la lista, seleccione **nuevo** en la barra de comandos y, a continuación, seleccione **personalizar** cerca de la parte superior del formulario.

1. Personalice el formulario de varias maneras, como las que se describen en estos temas:

    - Cambie su tamaño, orientación o ambos (por ejemplo, para [ensanchar el formulario](set-aspect-ratio-portrait-landscape.md)).
    - [Personalizar una o más tarjetas](working-with-cards.md) (por ejemplo, cambiar el texto para mostrar de una tarjeta o el control de entrada).
    - Cree un [campo de búsqueda](sharepoint-lookup-fields.md).

    Más información: [Comprender la integración de formularios de SharePoint](sharepoint-form-integration.md).

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

## <a name="q--a"></a>Q & A

### <a name="forms-vs-apps"></a>Formularios frente a aplicaciones

**RESPUESTAS** ¿En qué se diferencia un formulario personalizado de una aplicación independiente que se crea desde SharePoint o PowerApps?

**UN** Si personaliza el formulario para una lista de SharePoint, el formulario no aparece como una aplicación en PowerApps Studio o en PowerApps Mobile. Solo puede abrir el formulario desde la lista para la que lo ha creado.

**RESPUESTAS** ¿Cuándo debo personalizar un formulario para administrar datos en una lista de SharePoint y Cuándo debo crear una aplicación independiente?

**UN** Personalizar un formulario si desea que los usuarios administren los datos sin tener SharePoint (por ejemplo, en un explorador de escritorio). Cree una aplicación si quiere que los usuarios administren los datos fuera de SharePoint (por ejemplo, en un dispositivo móvil).

**RESPUESTAS** ¿Puedo personalizar un formulario y crear una aplicación para la misma lista?

**UN** Sí.

**RESPUESTAS** ¿Puedo personalizar una lista y crear una aplicación con las mismas características?

**UN** Sí.

**RESPUESTAS** ¿Puedo personalizar un formulario en un entorno que no sea el predeterminado de mi organización?

**UN** No.

### <a name="manage-your-custom-form"></a>Administrar el formulario personalizado

**RESPUESTAS** ¿Cómo puedo compartir fácilmente mi formulario con otros usuarios?

**UN** Abra el formulario, seleccione **Copiar vínculo**y, a continuación, envíe el vínculo a cualquiera que desee usar el formulario.

**RESPUESTAS** ¿Puedo actualizar mi formulario sin hacer que mis cambios sean visibles para otras personas?

**UN** Sí. Puede modificar el formulario y guardarlo tantas veces como quiera, pero los cambios no serán visibles para nadie a menos que seleccione **Publicar en SharePoint** dos veces.

**RESPUESTAS** Si puedo personalizar un formulario de lista y cometer un error, ¿puedo revertir a una versión anterior?

**UN** Sí.

1. Abra la lista, seleccione **PowerApps** en la barra de comandos y luego seleccione **Personalizar formularios**.

1. En PowerApps Studio, seleccione **Archivo** y luego **Ver todas las versiones**. Se abre la página **Versiones** en una nueva pestaña de explorador.

    > [!NOTE]
    > Si no ve el botón **Ver todas las versiones**, seleccione **Guardar**. Debería aparecer el botón.

1. Sin cerrar la página **Versiones** ni la pestaña del explorador, vuelva a la página **Guardar** de la otra pestaña del explorador, pulse o haga clic en la flecha de la parte superior del panel de navegación izquierdo y, después, pulse o haga clic en **Volver a SharePoint** para desbloquear el formulario y cerrar PowerApps Studio.

1. Vuelva a la página **Versiones** de la otra pestaña del explorador, busque la versión que quiere restaurar y luego seleccione **Restaurar**.

    > [!NOTE]
    > Si recibe un mensaje de error que indica que se ha producido un error en la restauración porque el formulario está bloqueado por otro usuario, espere a que el usuario desbloquee el formulario e inténtelo de nuevo.

**RESPUESTAS** ¿Puedo transferir mi formulario de una lista a otra?

**UN** No.

### <a name="administer-your-custom-form"></a>Administrar el formulario personalizado

**RESPUESTAS** ¿Cómo compartir mi formulario?

**UN** No es necesario compartir el formulario; el formulario hereda los permisos de la lista de SharePoint. Cuando haya terminado de personalizarlo, solo tiene que [volver a publicarlo en SharePoint](customize-list-form.md#save-and-publish-the-form) para que otros usuarios puedan usarlo.

**RESPUESTAS** ¿Quién puede personalizar los formularios?

**UN** Cualquier persona con permisos de SharePoint para administrar, diseñar o editar la lista asociada.

**RESPUESTAS** ¿Necesito una licencia de PowerApps para crear o usar formularios de lista personalizados?

**UN** Necesita un [plan de Office 365 que incluya PowerApps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses).

**RESPUESTAS** ¿Qué ocurre cuando los usuarios invitados acceden a una lista que tiene un formulario personalizado?

**UN** Los usuarios invitados obtienen un mensaje de error si intentan acceder a un formulario de lista que se ha personalizado mediante PowerApps.

**RESPUESTAS** Como administrador, ¿Cómo obtengo una lista de todos los formularios personalizados en mi organización?

**UN** Si es un administrador de inquilinos de PowerApps o tiene permisos de administrador de entorno en el entorno predeterminado de PowerApps de la organización, haga lo siguiente:

1. En el [centro de administración de PowerApps](https://admin.powerapps.com), seleccione el entorno predeterminado de la organización en la lista de entornos.

1. En la parte superior de la página del entorno predeterminado, seleccione **Recursos**.

1. En la lista de aplicaciones, busque aplicaciones con un tipo de aplicación de **formulario de SharePoint** : Estos son los formularios personalizados.

    ![Lista de formularios personalizados](./media/customize-list-form/all-customized-forms.png)
