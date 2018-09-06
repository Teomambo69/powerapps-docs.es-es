---
title: Personalización de un formulario de lista de SharePoint | Microsoft Docs
description: Use PowerApps para personalizar el formulario con el que los usuarios crean y actualizan las entradas de una lista de SharePoint.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/11/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc2940f726c23c79bcf894bb61c3e6b884ca7112
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42865786"
---
# <a name="customize-a-sharepoint-list-form-by-using-powerapps"></a>Personalizar un formulario de lista de SharePoint mediante PowerApps

Puede personalizar fácilmente el formulario de una lista de SharePoint si abre PowerApps en un explorador. No es necesario escribir código tradicional, como C#, ni descargar otra aplicación, como InfoPath. Al publicar los cambios, el formulario se inserta en la lista de SharePoint para su uso por parte de todos sus usuarios. En PowerApps también es posible revisar informes de análisis, crear formato condicional con facilidad y conectarse a otros orígenes de datos.

Para seguir los pasos de este tema, tiene que crear una lista simple para que pueda ver cómo funciona la personalización y luego pueda aplicar los mismos conceptos a su propia lista.

> [!NOTE]
> Si la opción **Personalizar formularios** no está disponible o no funciona correctamente, podría contener tipos de datos que [PowerApps no admite](connections/connection-sharepoint-online.md#known-issues). Además, no se puede mover el formulario a otra lista o [entorno](working-with-environments.md).

## <a name="prerequisites"></a>Requisitos previos

En un sitio de SharePoint, cree una lista que contenga estas columnas:

- **NombreProducto** (única línea de texto)
- **Detalles** (sí/no)
- **Precio** (moneda)
- **Disponibilidad** (fecha sin hora)
- **Color** (opción)

## <a name="open-the-form-in-powerapps"></a>Abrir el formulario en PowerApps

1. Abra la lista que ha creado y luego seleccione **Nuevo** en la barra de comandos.

    El formulario se abre y muestra los campos que ha agregado, además de **Título** y **Datos adjuntos**.

1. Junto a la parte superior del formulario, seleccione **Personalizar**.

    PowerApps Studio se abre en la misma pestaña del explorador.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

## <a name="hide-extra-fields"></a>Ocultar campos adicionales

En el centro de la pantalla, PowerApps muestra el formulario, que contiene algunos campos que quizás no quiera mostrar.

- En el panel **Datos**, desactive las casillas de esos campos.

  - **Title**
  - **Modificado**
  - **Creado**
  - **Creado por**
  - **Modificado por**
  - **Id.**

    Esos campos desaparecen del formulario y quedan solo los que ha creado.

    ![Lista de campos](./media/customize-list-form/field-list.png)

## <a name="set-conditional-formatting"></a>Establecer formato condicional

Puede configurar que los campos **Precio**, **Disponibilidad** y **Color** solo aparezcan si **Detalles** está establecido en Sí.

1. Seleccione la tarjeta **Precio** al hacer clic o pulsar en ella.

    ![Selección de la tarjeta Disponibilidad](./media/customize-list-form/select-card.png)

1. En la lista de propiedades, seleccione **Visible**.

    ![Selección de la propiedad Visible](./media/customize-list-form/select-property.png)

1. En la barra de fórmulas, escriba o pegue esta fórmula:

    **If(DataCardValue3.Value = true, true)**

    ![Establecimiento del valor de la propiedad Visible](./media/customize-list-form/build-formula.png)

1. Repita los tres últimos pasos con las tarjetas **Disponibilidad** y **Color**.

1. Mientras mantiene la tecla Alt presionada, seleccione el botón de alternancia **Detalles** varias veces (al hacer clic o pulsar en él).

    Los tres campos que ha configurado aparecen y desaparecen del formulario.

1. (Opcional) Personalice el formulario de varias formas distintas, incluidas estas:

    - Cambie su tamaño, orientación o ambos (por ejemplo, para [ensanchar el formulario](set-aspect-ratio-portrait-landscape.md)).
    - Agregue un control para que los usuarios puedan [cargar datos adjuntos](controls/properties-text.md).
    - Cree un [campo de búsqueda](sharepoint-lookup-fields.md).

## <a name="save-publish-and-show-the-form"></a>Guardar, publicar y mostrar el formulario

1. Abra el menú **Archivo**, seleccione **Guardar** y luego seleccione **Publicar en SharePoint** dos veces.

1. En la esquina superior izquierda, seleccione la flecha Atrás y luego **Volver a SharePoint**.

1. En la barra de comandos, seleccione **Nuevo** para abrir el formulario personalizado.

1. Seleccione el botón de alternancia **Detalles** varias veces para ocultar y mostrar los últimos tres campos.

Para [personalizar aún más el formulario](sharepoint-form-integration.md), ábralo, seleccione **Personalizar** junto a la parte superior de este y luego realice, guarde y publique los cambios.

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

## <a name="q--a"></a>Preguntas y respuestas

### <a name="forms-vs-apps"></a>Formularios frente a aplicaciones

**P:** ¿En qué se diferencia un formulario personalizado de una aplicación independiente que se crea desde SharePoint o PowerApps?

**R:** Si personaliza el formulario de una lista de SharePoint, no aparece como aplicación en PowerApps Studio ni PowerApps Mobile. Solo puede abrir el formulario desde la lista para la que lo ha creado.

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

**R:** Abra el formulario, seleccione **Copiar vínculo** y luego envíe el vínculo a cualquiera que quiera usar el formulario.

**P:** ¿Se puede actualizar un formulario sin que los cambios realizados sean visibles para otros usuarios?

**R:** Sí. Puede modificar el formulario y guardarlo tantas veces como quiera, pero los cambios no serán visibles para nadie a menos que seleccione **Publicar en SharePoint** dos veces.

**P:** Si se personaliza un formulario de lista y se comete un error, ¿se puede volver a la versión anterior?

**R:** Sí.

1. Abra la lista, seleccione **PowerApps** en la barra de comandos y luego seleccione **Personalizar formularios**.

1. En PowerApps Studio, seleccione **Archivo** y luego **Ver todas las versiones**. Se abre la página **Versiones** en una nueva pestaña de explorador.

    > [!NOTE]
    > Si no ve el botón **Ver todas las versiones**, seleccione **Guardar**. Debería aparecer el botón.

1. Sin cerrar la página **Versiones** ni la pestaña del explorador, vuelva a la página **Guardar** de la otra pestaña del explorador, pulse o haga clic en la flecha de la parte superior del panel de navegación izquierdo y, después, pulse o haga clic en **Volver a SharePoint** para desbloquear el formulario y cerrar PowerApps Studio.

1. Vuelva a la página **Versiones** de la otra pestaña del explorador, busque la versión que quiere restaurar y luego seleccione **Restaurar**.

    > [!NOTE]
    > Si recibe un mensaje de error que indica que la restauración no se pudo realizar porque otro usuario ha bloqueado el formulario, espere a que el usuario lo desbloquee y, a continuación, vuelva a intentarlo.

**P:** ¿Se puede mover un formulario de una lista a otra?

**A:** No.

### <a name="administer-your-custom-form"></a>Administrar el formulario personalizado

**P:** ¿Cómo se comparte un formulario?

**R:** No es necesario compartir el formulario, ya que este hereda los permisos de la lista de SharePoint. Cuando haya terminado de personalizarlo, solo tiene que [volver a publicarlo en SharePoint](customize-list-form.md#save-and-publish-the-list-form-back-to-sharepoint) para que otros usuarios puedan usarlo.

**P:** ¿Quién puede personalizar formularios?

**R:** Cualquier persona con permisos de SharePoint para administrar, diseñar o editar la lista asociada.

**P: ¿** ¿Se necesita una licencia de PowerApps para crear o utilizar formularios de lista personalizados?

**R:** Necesita un [plan de Office 365 que incluya PowerApps](../../administrator/pricing-billing-skus.md#licenses).

**P:** ¿Qué sucede cuando los usuarios invitados acceden a una lista que tiene un formulario personalizado?

**R:** Los usuarios invitados reciben un mensaje de error si intentan acceder a un formulario de lista que se ha personalizado mediante PowerApps.

**P:** ¿Cómo reciben los administradores una lista de todos los formularios personalizados de su organización?

**R:** Si es administrador de inquilinos de PowerApps o tiene permisos de administrador en el entorno predeterminado de PowerApps de la organización, haga lo siguiente:

1. En el [centro de administración de PowerApps](https://admin.powerapps.com), seleccione el entorno predeterminado de la organización en la lista de entornos.

1. En la parte superior de la página del entorno predeterminado, seleccione **Recursos**.

1. En la lista de aplicaciones, busque aplicaciones con un tipo de aplicación de **formulario de SharePoint**, que son los formularios personalizados.

    ![Lista de formularios personalizados](./media/customize-list-form/all-customized-forms.png)
