---
title: Personalización de un formulario de lista de SharePoint | Microsoft Docs
description: Use Power apps para personalizar el formulario con el que los usuarios crean y actualizan las entradas de una lista de SharePoint.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/24/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9e8a7fe44c10d4f189136e05013b68fbd407fe9c
ms.sourcegitcommit: 0e41cc0c944e6b0ee22a7e183e40c52fd553b7be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77563714"
---
# <a name="customize-a-sharepoint-list-or-library-form-by-using-power-apps"></a>Personalización de un formulario de biblioteca o lista de SharePoint con Power apps

Puede personalizar fácilmente el formulario para una lista de SharePoint o una biblioteca de documentos de SharePoint abriendo Power Apps en un explorador. No es necesario escribir código tradicional, como C#, ni descargar otra aplicación, como InfoPath. Al publicar los cambios, el formulario se inserta en la lista de SharePoint para su uso por parte de todos sus usuarios. En Power Apps, también puede revisar los informes de análisis, crear fácilmente formato condicional y conectarse a otros orígenes de datos.

Para seguir los pasos de este tema, tiene que crear una lista simple para que pueda ver cómo funciona la personalización y luego pueda aplicar los mismos conceptos a su propia lista.

> [!NOTE]
> - Si la opción **personalizar formularios** no está disponible o no funciona correctamente para la lista, puede que contenga tipos de datos que las [aplicaciones de Power apps no admitan](connections/connection-sharepoint-online.md#known-issues). Además, no se puede mover el formulario a otra lista o [entorno](working-with-environments.md). 
> - Los formularios personalizados para listas solo se admiten en listas genéricas. Próximamente estará disponible la compatibilidad con las bibliotecas de documentos genéricos. La lista personalizada y las plantillas de biblioteca no se admiten actualmente; incluye, entre otras, listas, como anuncios, contactos y tareas.
> - Los formularios personalizados de las bibliotecas de documentos solo admiten la edición de metadatos personalizados. No se admite la edición o la administración de archivos.

## <a name="create-a-list"></a>Crear una lista

En un sitio de SharePoint, cree una lista y, a continuación, agregue estas columnas a esa lista:

- **Detalles** (sí/no)
- **Precio** (moneda)
- **Disponibilidad** (fecha sin hora)
- **Color** (opción)

> [!div class="mx-imgBorder"]
> ![Seleccione el contenido del sitio > Nueva > lista, escriba el nombre de la lista y seleccione crear. Para cada columna, seleccione Agregar columna, especifique el tipo de lista (sí/no, moneda, fecha, elección), especifique el nombre de la lista (detalles, precio, disponibilidad, color) y seleccione Guardar.](./media/customize-list-form/create-list.gif)

## <a name="open-the-form"></a>Abrir el formulario

1. En la barra de comandos, seleccione **PowerApps**y, a continuación, seleccione **personalizar formulario**.

    Power apps Studio se abre en la misma pestaña del explorador.

1. Si aparece el cuadro de diálogo **Bienvenido a Power apps Studio** , seleccione **omitir**.

> [!div class="mx-imgBorder"]
> ![en la barra de comandos, seleccione Power apps y, a continuación, seleccione Personalizar formulario. Power apps Studio se abre en la misma pestaña del explorador. Si aparece el cuadro de diálogo Bienvenido a Power apps Studio, seleccione Omitir.](./media/customize-list-form/create-form.gif)

## <a name="move-and-remove-a-field"></a>Desplazamiento y eliminación de un campo

1. Arrastre el campo **Availability** hasta la parte inferior de la lista de campos.

    Los campos aparecen en el orden que especifique.

1. Mantenga el mouse sobre el campo **datos adjuntos** , seleccione los puntos suspensivos (...) que aparecen y, a continuación, seleccione **quitar**.

    El campo que especifique desaparece del formulario.

> [!div class="mx-imgBorder"]
> ![arrastre el campo Availability hasta la parte inferior de la lista de campos. Mantenga el mouse sobre el campo datos adjuntos, seleccione los puntos suspensivos (...) que aparecen y, a continuación, seleccione quitar.](./media/customize-list-form/move-remove-fields.gif)

## <a name="set-conditional-formatting"></a>Establecer formato condicional

Puede configurar que los campos **Precio**, **Disponibilidad** y **Color** solo aparezcan si **Detalles** está establecido en Sí.

1. En la barra de navegación izquierda, expanda **Details_DataCard1**y anote el número que aparece al final de **DataCardValue**.

1. Establezca la propiedad **visible** del **color**, la **disponibilidad**y las tarjetas de **precios** en esta fórmula (reemplace, si es necesario, el número por el que anotó en el paso anterior):

    **Si (DataCardValue2. Value = true, true)**

1. Mientras mantiene la tecla Alt presionada, seleccione el botón de alternancia **Detalles** varias veces (al hacer clic o pulsar en él).

    Los tres campos que ha configurado aparecen y desaparecen del formulario.

> [!div class="mx-imgBorder"]
> ![en la barra de navegación izquierda, tenga en cuenta el número que aparece al final de DataCardValue. Establezca la propiedad Visibility del color, la disponibilidad y las tarjetas de precios en esta fórmula. Mantenga presionada la tecla Alt y seleccione varias veces el control detalles.](./media/customize-list-form/conditional-format.gif)

## <a name="save-and-publish-the-form"></a>Guardar y publicar el formulario

1. Abra el menú **Archivo**, seleccione **Guardar** y luego seleccione **Publicar en SharePoint** dos veces.

1. En la esquina superior izquierda, seleccione la flecha Atrás y luego **Volver a SharePoint**.

> [!div class="mx-imgBorder"]
> ![Abra el menú Archivo, seleccione Guardar y, a continuación, seleccione publicar en SharePoint dos veces. En la esquina superior izquierda, seleccione la flecha atrás y, a continuación, seleccione volver a SharePoint.](./media/customize-list-form/save-form.gif)

## <a name="further-customize-your-form"></a>Personalización adicional del formulario

1. Abra la lista, seleccione **nuevo** en la barra de comandos y, a continuación, seleccione **personalizar** cerca de la parte superior del formulario.

1. Personalice el formulario de varias maneras, como las que se describen en estos temas:

    - Cambie su tamaño, orientación o ambos (por ejemplo, para [ensanchar el formulario](set-aspect-ratio-portrait-landscape.md)).
    - [Personalizar una o más tarjetas](working-with-cards.md) (por ejemplo, cambiar el texto para mostrar de una tarjeta o el control de entrada).
    - Cree un [campo de búsqueda](sharepoint-lookup-fields.md).

    Más información: [Descripción](sharepoint-form-integration.md)de la integración de formularios de SharePoint.

## <a name="use-the-default-form"></a>Usar el formulario predeterminado

1. En la lista de SharePoint, abra la página de configuración (al seleccionar el icono de engranaje junto a la esquina superior derecha) y luego seleccione **Configuración de lista**.

2. En **Configuración general**, seleccione **Configuración de formulario**.

3. En la página **Configuración de formulario**, seleccione una de estas opciones y luego **Aceptar**.

    - **Usar el formulario predeterminado de SharePoint**: cuando un usuario abra la lista y seleccione **Nuevo** en la barra de comandos, aparecerá el formulario predeterminado de la lista.

    - **Usar un formulario personalizado creado en Power apps** : cuando un usuario abra la lista y seleccione **nuevo** en la barra de comandos, aparecerá el formulario personalizado. (Como alternativa, puede volver a publicar el formulario en Power apps).

    Puede alternar entre las opciones, según sea necesario.

    ![Opciones de configuración de formulario](./media/customize-list-form/form-settings.png)

## <a name="delete-the-custom-form"></a>Eliminación del formulario personalizado

1. En la lista de SharePoint, abra la página de configuración (al seleccionar el icono de engranaje junto a la esquina superior derecha) y luego seleccione **Configuración de lista**.

1. En **Configuración general**, seleccione **Configuración de formulario**.

1. En la página **Configuración de formulario**, seleccione **Usar el formulario predeterminado de SharePoint** y luego **Eliminar formulario personalizado**.

    ![Eliminación del formulario personalizado](./media/customize-list-form/use-default-sharepoint.png)

## <a name="q--a"></a>Preguntas y respuestas

### <a name="forms-vs-apps"></a>Formularios frente a aplicaciones

**P:** ¿En qué se diferencia un formulario personalizado de una aplicación independiente que se crea desde SharePoint o Power apps?

**R:** Si personaliza el formulario para una lista de SharePoint, el formulario no aparece como una aplicación en Power apps Studio o Power apps Mobile. Solo puede abrir el formulario desde la lista para la que lo ha creado.

**P:** ¿Cuándo se debe personalizar un formulario para administrar datos de una lista de SharePoint y cuándo se debe crear una aplicación independiente?

**R:** Personalice un formulario si quiere que los usuarios administren los datos sin salir de SharePoint (por ejemplo, en un explorador de escritorio). Cree una aplicación si quiere que los usuarios administren los datos fuera de SharePoint (por ejemplo, en un dispositivo móvil).

**P:** ¿Se puede personalizar un formulario y crear una aplicación para la misma lista?

**R:** Sí.

**P:** ¿Se puede personalizar una lista y crear una aplicación con las mismas características?

**R:** Sí.

**P:** ¿Se puede personalizar un formulario en un entorno distinto al predeterminado de la organización?

**A:** No.

### <a name="manage-your-custom-form"></a>Administrar el formulario personalizado

**P:** ¿Cómo se puede compartir fácilmente un formulario con otras personas?

**R:** Abra el formulario, seleccione **Copiar vínculo**y, a continuación, envíe el vínculo a cualquiera que desee usar el formulario.

**P:** ¿Se puede actualizar un formulario sin que los cambios realizados sean visibles para otros usuarios?

**R:** Sí. Puede modificar el formulario y guardarlo tantas veces como quiera, pero los cambios no serán visibles para nadie a menos que seleccione **Publicar en SharePoint** dos veces.

**P:** Si se personaliza un formulario de lista y se comete un error, ¿se puede volver a la versión anterior?

**R:** Sí.

1. Abra la lista, seleccione **PowerApps** en la barra de comandos y luego seleccione **Personalizar formularios**.

1. En Power apps Studio, seleccione **archivo**y, a continuación, seleccione **ver todas las versiones**. Se abre la página **Versiones** en una nueva pestaña de explorador.

    > [!NOTE]
    > Si no ve el botón **Ver todas las versiones**, seleccione **Guardar**. Debería aparecer el botón.

1. Sin cerrar la página **versiones** o la pestaña explorador, vuelva a la página **Guardar** en la otra pestaña del explorador, pulse o haga clic en la flecha situada en la parte superior del panel de navegación izquierdo y, a continuación, haga clic o pulse **en volver a SharePoint** para desbloquear el formulario y cerrar Power apps Studio.

1. Vuelva a la página **Versiones** de la otra pestaña del explorador, busque la versión que quiere restaurar y luego seleccione **Restaurar**.

    > [!NOTE]
    > Si recibe un mensaje de error que indica que se ha producido un error en la restauración porque el formulario está bloqueado por otro usuario, espere a que el usuario desbloquee el formulario e inténtelo de nuevo.

**P:** ¿Se puede mover un formulario de una lista a otra?

**A:** No.

### <a name="administer-your-custom-form"></a>Administrar el formulario personalizado

**P:** ¿Cómo se comparte un formulario?

**R:** No es necesario compartir el formulario; el formulario hereda los permisos de la lista de SharePoint. Cuando haya terminado de personalizarlo, solo tiene que [volver a publicarlo en SharePoint](customize-list-form.md#save-and-publish-the-form) para que otros usuarios puedan usarlo.

**P:** ¿Quién puede personalizar formularios?

**R:** Cualquier persona con permisos de SharePoint para administrar, diseñar o editar la lista asociada.

**P:** ¿Necesito una licencia de Power apps para crear o usar formularios de lista personalizados?

**R:** Necesita un [plan de Office 365 que incluye Power apps](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus#licenses).

**P:** ¿Qué sucede cuando los usuarios invitados acceden a una lista que tiene un formulario personalizado?

**R:** Los usuarios invitados obtienen un mensaje de error si intentan acceder a un formulario de lista personalizado con Power apps.

**P:** ¿Cómo reciben los administradores una lista de todos los formularios personalizados de su organización?

**R:** Si es un administrador de inquilinos de Power Apps o tiene permisos de administrador de entorno en el entorno de Power apps predeterminado de su organización, haga lo siguiente:

1. En el [centro de administración de Power apps](https://admin.powerapps.com), seleccione el entorno predeterminado para su organización en la lista de entornos.

1. En la parte superior de la página del entorno predeterminado, seleccione **Recursos**.

1. En la lista de aplicaciones, busque aplicaciones con un tipo de aplicación de **formulario de SharePoint** : Estos son los formularios personalizados.

    ![Lista de formularios personalizados](./media/customize-list-form/all-customized-forms.png)
