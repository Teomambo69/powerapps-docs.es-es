---
title: Crear una lista desplegable dependiente en una aplicación de lienzo | Microsoft Docs
description: En Power Apps, cree una lista desplegable que filtre otra lista desplegable en una aplicación de lienzo.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 233fd99eeba86151f616a22955cf28c2114de43e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679624"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>Crear listas desplegables dependientes en una aplicación de lienzo

Al crear listas desplegables dependientes (o en cascada), los usuarios seleccionan una opción en una lista para filtrar las opciones de otra lista. Muchas organizaciones crean listas dependientes para ayudar a los usuarios a rellenar formularios de forma más eficaz. Por ejemplo, los usuarios pueden seleccionar un país o región para filtrar una lista de ciudades, o bien los usuarios pueden seleccionar una categoría para mostrar solo los códigos de esa categoría.

Como procedimiento recomendado, cree un origen de datos para los valores de las listas "primario" y "secundario" (por ejemplo, países o regiones y ciudades) que sea independiente del origen de datos que los usuarios actualizan mediante la aplicación. Si adopta este enfoque, puede usar los mismos datos primarios y secundarios en más de una aplicación, y puede actualizar los datos sin volver a publicar la aplicación o aplicaciones que los usan. Puede lograr el mismo resultado mediante una colección o datos estáticos, pero no se recomienda para escenarios empresariales.

En el escenario de este tema, los empleados de la tienda envían problemas a una lista de **incidentes** a través de un formulario. Los empleados no solo especifican la ubicación del almacén en el que se produjo el incidente, sino también el departamento dentro de esa ubicación. No todas las ubicaciones tienen los mismos departamentos, por lo que una lista de **ubicaciones** garantiza que los empleados no puedan especificar un departamento para una ubicación que no tenga ese departamento.

En este tema se usan listas de Microsoft SharePoint como orígenes de datos, pero todos los orígenes de datos tabulares funcionan de la misma manera.

## <a name="create-data-sources"></a>Crear orígenes de datos

Una lista de **ubicaciones** muestra los departamentos de cada ubicación.

| Location | Departamento |
|----------------|------------------|
| Eganville      | Pastelería           |
| Eganville      | Nodos             |
| Eganville      | Crea          |
| Renfrew        | Pastelería           |
| Renfrew        | Nodos             |
| Renfrew        | Crea          |
| Renfrew        | Farmacia         |
| Renfrew        | Flor           |
| Pembroke       | Pastelería           |
| Pembroke       | Nodos             |
| Pembroke       | Crea          |
| Pembroke       | Flor           |

Una lista de **incidentes** muestra información de contacto e información sobre cada incidente. Cree la columna de fecha como una columna de **fecha** , pero cree las demás columnas como una **sola línea de columnas de texto** para simplificar la configuración y evitar las advertencias de [delegación](./delegation-overview.md) en Microsoft PowerApps.

| Nombre | Apellidos | Número de teléfono     | Location | Departamento | Descripción       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555-1022 | Eganville      | Crea    | Tengo un problema con...   | 2/12/2019 |
| , Moses,     | Laflamme     | (425) 555-1044 | Renfrew        | Flor     | Se produjo un problema... | 2/13/2019 |

De forma predeterminada, las listas personalizadas de SharePoint incluyen una columna de **título** que no puede cambiar de nombre o quitar, y que debe contener datos para poder guardar un elemento en la lista. Para configurar la columna de modo que no requiera datos:

1. Cerca de la esquina superior derecha, seleccione el icono de engranaje y, a continuación, seleccione Configuración de la **lista**.
1. En la página **configuración** , seleccione **título** en la lista de columnas.
1. En **requerir que esta columna contenga información**, seleccione **no**.

Después de ese cambio, puede omitir la columna **title** o [quitarla](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8) de la vista predeterminada si aparece al menos otra columna.

## <a name="open-the-form"></a>Abrir el formulario

1. Abra la lista **incidentes** y, a continuación, seleccione **PowerApps** > **personalizar formularios**.

    > [!div class="mx-imgBorder"]
    > ![Abra la lista incidentes y, a continuación, seleccione Power apps > personalizar formularios.](./media/dependent-drop-down-lists/open-form.png "Abra la lista incidentes y, a continuación, seleccione Power apps > personalizar formularios.")

    Se abre una pestaña del explorador con el formulario predeterminado en Power apps Studio.

1. opta En el panel **campos** , mantenga el mouse sobre el campo **título** , seleccione los puntos suspensivos (...) que aparecen y, a continuación, seleccione **quitar**.

    Si ha cerrado el panel **campos** , puede volver a abrirlo seleccionando **SharePointForm1** en la barra de navegación izquierda y, a continuación, seleccionando **Editar campos** en la pestaña **propiedades** del panel derecho.

1. opta Repita el paso anterior para quitar el campo de **datos adjuntos** del formulario.

    El formulario aparece solo con los campos que ha agregado.

    > [!div class="mx-imgBorder"]
    > ![formulario sin los campos título y datos adjuntos](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>Reemplazar los controles

1. En el panel **campos** , seleccione la flecha situada junto a **Ubicación**.

    Si ha cerrado el panel **campos** , puede volver a abrirlo seleccionando **SharePointForm1** en la barra de navegación izquierda y, a continuación, seleccionando **Editar campos** en la pestaña **propiedades** del panel derecho.

1. Abra la lista **tipo de control** y, a continuación, seleccione **valores permitidos**.

    > [!div class="mx-imgBorder"]
    > ![valores permitidos](./media/dependent-drop-down-lists/change-control.png)

    El mecanismo de entrada cambia a un control de **lista** desplegable.

1. Repita estos pasos para la tarjeta del **Departamento** .

## <a name="add-the-locations-list"></a>Agregar la lista de ubicaciones

1. Seleccione **ver** > **orígenes de datos** > **Agregar origen de datos**.

1. Seleccione o cree una conexión de SharePoint y, a continuación, especifique el sitio que contiene la lista de **ubicaciones** .

1. Active la casilla correspondiente a esa lista y, a continuación, seleccione **conectar**.

    > [!div class="mx-imgBorder"]
    > ![panel datos](./media/dependent-drop-down-lists/select-list.png)

    La lista de conexiones muestra la lista de **incidentes** , en la que se basa el formulario, y la lista de **ubicaciones** , que identificará las ubicaciones y los departamentos en el formulario.

    > [!div class="mx-imgBorder"]
    > ![orígenes de datos de SharePoint](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>Desbloquear las tarjetas

1. Seleccione la tarjeta de **Ubicación** , seleccione la pestaña **Opciones avanzadas** en el panel derecho y, a continuación, seleccione **desbloquear para cambiar las propiedades**.

1. Repita el paso anterior para la tarjeta del **Departamento** .

## <a name="rename-the-controls"></a>Cambiar el nombre de los controles

Si cambia el nombre de los controles, puede identificarlos más fácilmente y los ejemplos son más fáciles de seguir. Para descubrir otros procedimientos recomendados, revise las [notas del producto sobre estándares de codificación y directrices](https://aka.ms/powerappscanvasguidelines).

1. En la tarjeta **Ubicación** , seleccione el control **lista desplegable** .

1. Cerca de la parte superior del panel derecho, cambie el nombre del control seleccionado escribiendo o pegando **ddLocation**.

    > [!div class="mx-imgBorder"]
    > ![cambiar el nombre de un control](./media/dependent-drop-down-lists/rename-control.png)

1. Repita los dos pasos anteriores de la tarjeta **Department** para cambiar el nombre del control de **lista desplegable** a **ddDepartment**.

## <a name="configure-the-locations"></a>Configurar las ubicaciones

1. Establezca la propiedad **Items** de **ddlocation** en esta fórmula:

    `Distinct(Locations, Location)`

1. opta Mientras mantiene presionada la tecla Alt, Abra **ddLocation**y confirme que la lista muestra las tres ubicaciones.

## <a name="configure-the-departments"></a>Configurar los departamentos

1. Seleccione **ddDepartment**y, a continuación, en la pestaña **propiedades** del panel derecho, seleccione **depende de.**

1. En **control primario**, asegúrese de que **ddLocation** aparece en la lista superior y el **resultado** aparece en la lista inferior.

    > [!NOTE]
    > Si no desea buscar coincidencias en una cadena pero en el ID. real de la fila de datos, seleccione **ID** en lugar de **result**.

1. En **campo coincidente**, seleccione **ubicaciones** en la lista superior, seleccione **Ubicación** en la lista inferior y, a continuación, seleccione **aplicar**.

    > [!div class="mx-imgBorder"]
    > ![depende del vínculo](./media/dependent-drop-down-lists/depends-on.png)

    La propiedad **Items** de **ddDepartment** se establece en esta fórmula:

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    Esta fórmula filtra los elementos de **ddDepartment** en función de lo que seleccione el usuario en **ddLocation**. Esta configuración garantiza que la lista "secundaria" de departamentos refleje los datos para su ubicación "primaria", como la lista de **ubicaciones** de SharePoint especifica.

1. En la pestaña **propiedades** del panel derecho, abra la lista junto a **valor**y seleccione **Departamento**.

    Este paso establece el texto para mostrar en las opciones de la columna **Departamento** de la lista **ubicaciones** de SharePoint.

    > [!div class="mx-imgBorder"]
    > ![valor de Departamento](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>Prueba del formulario

Mientras mantiene presionada la tecla Alt, abra la lista de ubicaciones, seleccione una, abra la lista de departamentos y, a continuación, seleccione una.

Las listas de ubicaciones y departamentos reflejan la información de la lista **ubicaciones** de SharePoint.

> [!div class="mx-imgBorder"]
> ![abrir la lista de ubicaciones, cambie la selección de Renfrew a Pembroke y, a continuación, abra la lista de departamentos](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>Guardar y abrir el formulario (opcional)

1. Abra el menú **archivo** y, a continuación, seleccione **Guardar** > **publicar en SharePoint** > **publicar en SharePoint**.

1. En la esquina superior izquierda, seleccione la flecha Atrás y luego **Volver a SharePoint**.

1. En la barra de comandos, seleccione **Nuevo** para abrir el formulario personalizado.

## <a name="faq"></a>Preguntas más frecuentes

**No veo ningún dato: los orígenes están todos en blanco o tienen datos incorrectos.**
Confirme si está mostrando el campo correcto para el control de cualquiera de estas maneras:

- Seleccione una lista desplegable y, a continuación, seleccione la propiedad **valor** en la pestaña **propiedades** del panel derecho.

    > [!div class="mx-imgBorder"]
    > ![desplegable de cambio](./media/dependent-drop-down-lists/drop-down-display-field.png)

- Seleccione un cuadro combinado y, a continuación, asegúrese de que el texto principal es el campo que desea mostrar.

    > [!div class="mx-imgBorder"]
    > ![cambiar el cuadro combinado](./media/dependent-drop-down-lists/combo-box-display-field.png)

**La lista desplegable mi secundaria contiene elementos duplicados.**
Este síntoma es probable que se deba al uso de una columna de **búsqueda** en SharePoint o a una función de **elección** en Power apps. Para quitar la duplicación, ajuste una función **DISTINCT** alrededor de los datos que devuelven correctamente. Más información: [función DISTINCT](functions/function-distinct.md).

## <a name="known-limitations"></a>Limitaciones conocidas

Esta configuración está disponible en los controles desplegables, así **como en los** controles de **cuadro combinado** y **cuadro de lista** que permiten una selección a la vez. No se puede usar el **depende de** la configuración de ninguno de esos controles si permiten selecciones múltiples. No se recomienda este enfoque para trabajar con conjuntos de opciones en Common Data Service.

**Depende de** la configuración no es compatible con colecciones o datos estáticos. Para configurar listas desplegables dependientes con estos orígenes, edite la expresión directamente en la barra de fórmulas. Además, Power apps no admite el uso de dos campos de elección en SharePoint sin ninguna tabla de datos coincidente, y no se puede definir un **campo coincidente** dentro de esta interfaz de usuario.
