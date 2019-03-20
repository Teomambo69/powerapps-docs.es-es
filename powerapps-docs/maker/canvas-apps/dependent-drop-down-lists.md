---
title: Crear una lista desplegable dependiente en una aplicación de lienzo | Microsoft Docs
description: En PowerApps, cree una lista desplegable que filtra otra lista desplegable en una aplicación de lienzo.
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 02/28/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: db511edd7e64f4d8ccd27cb59cae9a2c369e1a90
ms.sourcegitcommit: a06e3137e3cb36414f0d61825bbc687487ea6f8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "57804249"
---
# <a name="create-dependent-drop-down-lists-in-a-canvas-app"></a>Crear listas desplegables dependientes en una aplicación de lienzo

Al crear listas desplegables dependientes (o en cascada), los usuarios seleccionar una opción en una lista de opciones de filtrado de otra lista. Muchas organizaciones crean listas dependientes para ayudar a los usuarios a rellenar los formularios de forma más eficaz. Por ejemplo, los usuarios pueden seleccionar un país o región para filtrar una lista de ciudades o los usuarios pueden seleccionar una categoría para mostrar solo los códigos de esa categoría.

Como práctica recomendada, cree un origen de datos para los valores de la "principal" y "secundario" listas (por ejemplo, países o regiones y ciudades) que independiente del origen de datos que los usuarios se actualizan mediante el uso de la aplicación. Si adopta este enfoque, puede usar el mismo elemento primario y los datos secundarios en más de una aplicación y actualizar los datos sin volver a publicar la aplicación o aplicaciones que los usan. Puede lograr el mismo resultado mediante el uso de una colección o datos estáticos, pero no se recomienda para escenarios empresariales.

Para el escenario de este tema, almacén de problemas de los empleados enviar a un **incidentes** lista a través de un formulario. Los empleados especifican no solo la ubicación del almacén en que se produjo el incidente, sino también el departamento de esa ubicación. No todas las ubicaciones tienen los mismos departamentos, por lo que un **ubicaciones** lista garantiza que los empleados no pueden especificar un departamento para una ubicación que no tiene ese departamento.

En este tema usa las listas de SharePoint como orígenes de datos, pero todos los orígenes de datos tabulares funcionan del mismo modo.

## <a name="create-data-sources"></a>Crear orígenes de datos

Un **ubicaciones** lista muestra los departamentos en cada ubicación.

| Location | Departamento |
|----------------|------------------|
| Eganville      | Pastelería           |
| Eganville      | Deli             |
| Eganville      | Generar          |
| Renfrew        | Pastelería           |
| Renfrew        | Deli             |
| Renfrew        | Generar          |
| Renfrew        | Farmacia         |
| Renfrew        | Floral           |
| Pembroke       | Pastelería           |
| Pembroke       | Deli             |
| Pembroke       | Generar          |
| Pembroke       | Floral           |

Un **incidentes** lista muestra información de contacto y la información sobre cada incidente. Crear la columna de fecha como un **fecha** columna, pero crear las demás columnas como **una línea de texto** columnas para simplificar la configuración y evitar [delegación](./delegation-overview.md) advertencias en PowerApps.

| Nombre | Apellido | Número de teléfono     | Location | Departamento | Descripción       | Date      |
|------------|-----------|------------------|----------------|------------|-------------------------|-----------|
| Tonya       | Cortez   | (206) 555 - 1022 | Eganville      | Generar    | Había tenido un problema con...   | 2/12/2019 |
| Moses     | Laflamme     | (425) 555 - 1044 | Renfrew        | Floral     | Había experimentado un problema... | 2/13/2019 |

De forma predeterminada, las listas de SharePoint personalizadas incluyen un **título** columna que no se puede cambiar el nombre o quitar, y debe contener datos para poder guardar un elemento en la lista. Para configurar la columna para que no requiere datos:

1. Cerca de la esquina superior derecha, seleccione el icono de engranaje y, a continuación, seleccione **muestra las opciones**.
1. En el **configuración** página, seleccione **título** en la lista de columnas.
1. En **esta columna debe contener información**, seleccione **No**.

Después de este cambio, puede omitir el **título** columna, o puede [quitarlo](https://support.office.com/article/edit-a-list-column-in-sharepoint-online-77130c2e-76d1-4f80-af8b-4c6f47b264b8) desde la vista predeterminada, si aparece al menos otra columna.

## <a name="open-the-form"></a>Abra el formulario

1. Abra el **incidentes** lista y, a continuación, seleccione **PowerApps** > **personalizar formularios**.

    > [!div class="mx-imgBorder"]
    > ![Abra la lista de incidentes y, a continuación, seleccione PowerApps > Personalizar formularios. ](./media/dependent-drop-down-lists/open-form.png "Abra la lista de incidentes y, a continuación, seleccione PowerApps > Personalizar formularios.")

    Se abre una pestaña del explorador con el formulario predeterminado en PowerApps Studio.

1. (opcional) En el **campos** panel, mantenga el puntero sobre el **título** , seleccione el botón de puntos suspensivos (...) que aparece y, a continuación, seleccione **quitar**.

    Si ha cerrado el **campos** panel, puede abrirlo de nuevo seleccionando **SharePointForm1** en la barra de navegación izquierda y seleccione **editar campos** en el **Propiedades** ficha del panel derecho.

1. (opcional) Repita el paso anterior para quitar el **datos adjuntos** arrastrándolo desde el formulario.

    El formulario aparece con solo los campos que ha agregado.

    > [!div class="mx-imgBorder"]
    > ![Sin título y los datos adjuntos de los campos de formulario](./media/dependent-drop-down-lists/default-form.png)

## <a name="replace-the-controls"></a>Reemplace los controles

1. En el **campos** panel, seleccione la flecha abajo junto a **ubicación**.

    Si ha cerrado el **campos** panel, puede abrirlo de nuevo seleccionando **SharePointForm1** en la barra de navegación izquierda y seleccione **editar campos** en el **Propiedades** ficha del panel derecho.

1. Abra el **tipo de Control** lista y, a continuación, seleccione **permiten valores**.

    > [!div class="mx-imgBorder"]
    > ![Valores permitidos](./media/dependent-drop-down-lists/change-control.png)

    El mecanismo de entrada cambia a un **desplegable** control.

1. Repita estos pasos para la **departamento** tarjeta.

## <a name="add-the-locations-list"></a>Agregar la lista de ubicaciones

1. Seleccione **vista** > **orígenes de datos** > **agregar origen de datos**.

1. Seleccione o cree una conexión de SharePoint y, a continuación, especifique el sitio que contiene el **ubicaciones** lista.

1. Seleccione la casilla de verificación para esa lista y, a continuación, seleccione **Connect**.

    > [!div class="mx-imgBorder"]
    > ![Panel de datos](./media/dependent-drop-down-lists/select-list.png)

    La lista de conexiones, se muestra el **incidentes** lista, en el que se basa el formulario, y el **ubicaciones** lista, que identificará las ubicaciones y departamentos en el formulario.

    > [!div class="mx-imgBorder"]
    > ![Orígenes de datos de SharePoint](./media/dependent-drop-down-lists/data-sources.png)

## <a name="unlock-the-cards"></a>Desbloquear las tarjetas

1. Seleccione el **ubicación** tarjeta, seleccione el **avanzadas** pestaña en el panel derecho y, a continuación, seleccione **Unlock para cambiar las propiedades**.

1. Repita el paso anterior para el **departamento** tarjeta.

## <a name="rename-the-controls"></a>Cambiar el nombre de los controles

Si cambia el nombre de los controles, puede identificar más fácilmente y son más fáciles de seguir los ejemplos. Para detectar otros procedimientos recomendados, revise el [notas del producto de instrucciones y estándares de codificación](https://aka.ms/powerappscanvasguidelines).

1. En el **ubicación** tarjeta, seleccione el **desplegable** control.

1. Cerca de la parte superior del panel derecho, cambie el nombre del control seleccionado escribiendo o pegando **ddLocation**.

    > [!div class="mx-imgBorder"]
    > ![Cambiar el nombre de un control](./media/dependent-drop-down-lists/rename-control.png)

1. Repita los dos pasos anteriores en el **departamento** tarjeta para cambiar el nombre de la **desplegable** el control a **ddDepartment**.

## <a name="configure-the-locations"></a>Configurar las ubicaciones

1. Establecer el **elementos** propiedad de **ddlocation** en esta fórmula:

    `Distinct(Locations, Location)`

1. (opcional) Mientras mantiene presionada la tecla Alt, abra **ddLocation**y confirme que la lista muestra las tres ubicaciones.

## <a name="configure-the-departments"></a>Configurar los departamentos

1. Seleccione **ddDepartment** y, a continuación, en el **propiedades** ficha del panel derecho, seleccione **depende.**

1. En **principal control**, asegúrese de que **ddLocation** aparece en la lista superior y **resultado** aparece en la lista inferior.

    > [!NOTE]
    > Si no desea hacer coincidir en una cadena, pero en el identificador real de la fila de datos, seleccione **ID** en lugar de **resultado**.

1. En **campo coincidencia**, seleccione **ubicaciones** en la lista superior, seleccione **ubicación** en la lista inferior y, a continuación, seleccione **aplicar**.

    > [!div class="mx-imgBorder"]
    > ![Depende de vínculo](./media/dependent-drop-down-lists/depends-on.png)

    El **elementos** propiedad de **ddDepartment** está establecida en esta fórmula:

    `Filter(Locations, Location = ddLocation.Selected.Result)`

    Esta fórmula filtra los elementos en **ddDepartment** según lo que el usuario selecciona en **ddLocation**. Dicha configuración garantiza que la lista "secundarios" de los departamentos de TI refleja los datos de su ubicación "principal", como el **ubicaciones** especifica la lista de SharePoint.

1. En el **propiedades** ficha del panel derecho, abra la lista junto a **valor**y, a continuación, seleccione **departamento**.

    Este paso establece el texto para mostrar las opciones de la **departamento** columna de la **ubicaciones** lista de SharePoint.

    > [!div class="mx-imgBorder"]
    > ![Valor de departamento](./media/dependent-drop-down-lists/dept-value.png)

## <a name="test-the-form"></a>Comprobar el formulario

Mientras mantiene presionada la tecla Alt, abra la lista de ubicaciones, seleccione uno, abra la lista de los departamentos de TI y, a continuación, seleccione uno.

Las listas de ubicaciones y departamentos refleja la información de la **ubicaciones** lista de SharePoint.

> [!div class="mx-imgBorder"]
> ![Abra la lista de ubicaciones, cambie la selección de Renfrew a Pembroke y, a continuación, abra la lista de los departamentos de TI](./media/dependent-drop-down-lists/dropdowns.gif)

## <a name="save-and-open-the-form-optional"></a>Guardar y abrir el formulario (opcional)

1. Abra el **archivo** menú y, a continuación, seleccione **guardar** > **publicar en SharePoint** > **publicar en SharePoint**.

1. En la esquina superior izquierda, seleccione la flecha Atrás y luego **Volver a SharePoint**.

1. En la barra de comandos, seleccione **Nuevo** para abrir el formulario personalizado.

## <a name="faq"></a>PREGUNTAS MÁS FRECUENTES

**No puedo ver todos los datos: los orígenes están todas en blanco o datos incorrecto.**
Confirme si se muestra el campo correcto para el control de cualquiera de estas maneras:

- Seleccione una lista desplegable y, a continuación, seleccione el **valor** propiedad en el **propiedades** ficha del panel derecho.

    > [!div class="mx-imgBorder"]
    > ![Menú desplegable de cambio](./media/dependent-drop-down-lists/drop-down-display-field.png)

- Seleccione un cuadro combinado y, a continuación, asegúrese de que el texto principal es el campo que desea mostrar.

    > [!div class="mx-imgBorder"]
    > ![Cuadro combinado de cambio](./media/dependent-drop-down-lists/combo-box-display-field.png)

**Mi lista de desplegable secundaria contiene elementos duplicados.**
Este síntoma suele debido al uso de un **búsqueda** columna de SharePoint o un **opciones** función en PowerApps. Para quitar la duplicación, encapsular una **Distinct** función alrededor de los datos correctamente. Más información: [Función DISTINCT](functions/function-distinct.md)

## <a name="known-limitations"></a>Limitaciones conocidas

Esta configuración está disponible en **desplegable** controles, así como **cuadro combinado** y **cuadro de lista** controles que permiten una selección a la vez. No puede usar el **depende** configuración para cualquiera de esos controles si permiten varias selecciones. No se recomienda este enfoque para trabajar con conjuntos de opciones en común Data Service for Apps.

El **depende** configuración no es compatible con datos estáticos o colecciones. Para configurar listas desplegables dependientes con estos orígenes, edite la expresión directamente en la barra de fórmulas. Además, PowerApps no admite el uso de dos campos choice en SharePoint sin ninguna tabla de búsqueda de coincidencias de datos y no se puede definir **campo coincidencia** dentro de esta interfaz de usuario.