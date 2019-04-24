---
title: Función Choices | Microsoft Docs
description: Información de referencia, incluida sintaxis, de la función Choices de PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed555f5de4abc1e29b7d2a637413c440bd882f13
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61546827"
---
# <a name="choices-function-in-powerapps"></a>Función Choices de PowerApps
Devuelve una tabla de posibles valores para una columna de búsqueda.

## <a name="description"></a>Descripción
La función **Choices** devuelve una tabla de posibles valores para una columna de búsqueda.  

Use la función **Choices** para proporcionar una lista de opciones entre las que el usuario pueda seleccionar. Esta función se usa normalmente con el control [**Cuadro combinado**](../controls/control-combo-box.md) en formularios de edición.

En una búsqueda, la tabla que devuelve **Choices** coincide con la tabla externa asociada con la búsqueda. Si se usa **Choices**, ya no es necesario agregar la tabla externa como un origen de datos adicional. **Choices** devuelve todas las columnas de la tabla externa.

Dado que **Choices** devuelve una tabla, puede usar [**Filter**](function-filter-lookup.md), [**Sort**](function-sort.md), [**AddColumns**](function-table-shaping.md) y todas las demás funciones de manipulación de tablas para filtrar, ordenar y dar forma a la tabla. 

De momento no es posible [delegar](../delegation-overview.md) **Choices**. Si esta limitación plantea un problema en la aplicación, agregue la entidad externa como origen de datos y úsela directamente. 

**Choices** no exige que los nombres de columna sean cadenas ni se incluyan entre comillas dobles, a diferencia de [**ShowColumns**](function-table-shaping.md), [**Search**](function-filter-lookup.md) y otras funciones de tabla. Proporcione la fórmula como si estuviera haciendo referencia a la columna directamente.

Las referencias de columna deben ser directas al origen de datos. Por ejemplo, si el origen de datos es **Accounts** y la búsqueda es **SLA**, la referencia de columna sería **Accounts.SLA**. La referencia no se puede pasar a través de una función, una variable o un control. Para profundizar en este ejemplo, si **Accounts** se agrega a un control **Galería**, use la fórmula **Gallery.Selected.SLA** para hacer referencia al SLA de la cuenta seleccionada. Pero esta referencia se ha pasado a través de un control, por lo que no se puede pasar a la función **Columns**, sino que se debe seguir usando **Accounts.SLA**.

En este momento, puede usar las columnas de búsqueda sólo con SharePoint y Common Data Service.

## <a name="syntax"></a>Sintaxis
**Choices**( *column-reference* )

* *column-reference*: requerido.  Columna de búsqueda de un origen de datos. No incluya el nombre de columna entre comillas dobles. La referencia debe ser directa a la columna del origen de datos y no pasarse a través de una función o un control.

## <a name="examples"></a>Ejemplos

#### <a name="choices-for-a-lookup"></a>Choices para una búsqueda

1. [Crear una base de datos](../../../administrator/create-database.md) en Common Data Service y seleccione el **incluyen aplicaciones de ejemplo y datos** cuadro.

    Se crean muchas entidades, como **Accounts**.

    **Nota**: Los nombres de entidad son simples en web.powerapps.com y plural en PowerApps Studio.

    ![Lista parcial de los campos de la entidad Account en Commmon Data Service for Apps en la que se resalta que "Primary Contact" es un campo de búsqueda](media/function-choices/entity-account.png)

    La entidad **Accounts** tiene una columna **Primary Contact** que es una búsqueda en la entidad **Contacts**.  

    ![Lista parcial de los campos de la entidad Contact en Common Data Service](media/function-choices/entity-contact.png)

    En cada cuenta se designa un contacto como contacto principal o este está *blank*.

1. [Genere una aplicación](../data-platform-create-app.md) desde la entidad **Accounts**.

1. En la lista de pantallas y controles junto al borde izquierdo, desplácese hacia abajo hasta que aparezca **EditScreen1** y luego seleccione **EditForm1** justo debajo.

    ![En la barra de navegación izquierda, selección de EditForm1 en EditScreen1](media/function-choices/select-editform.png)

1. En el **propiedades** ficha del panel derecho, seleccione **editar campos**.

    ![Abra el panel de datos](media/function-choices/open-data-pane.png)

1. En el **campos** panel, seleccione **Agregar campo**.

1. Busque el **contacto principal** campo, seleccione su casilla de verificación y, a continuación, seleccione **agregar**.

    ![Selección de Accounts para abrir el panel Datos](media/function-choices/field-list.png)

    El **contacto principal** campo aparece en la parte inferior del formulario. Si el campo muestra un error, seleccione **orígenes de datos** en el **vista** pestaña, seleccione el botón de puntos suspensivos (...) para el **cuentas** origen de datos y, a continuación, seleccione **actualizar** .

1. (Opcional) Arrastre el campo **Primary Contact** desde la parte inferior a la parte superior de la lista de campos.

1. En la tarjeta de **Primary Contact**, seleccione el control **Cuadro combinado**.

    El **elementos** propiedad de ese control se establece en una fórmula que identifica la columna por su nombre para mostrar, como se muestra en el primer ejemplo, o su nombre lógico, como se muestra en el segundo ejemplo:

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![Pantalla de lienzo con un control de formulario. El cuadro combinado se selecciona el control de cuadro dentro de la tarjeta de contacto principal y la propiedad Items con las opciones de la fórmulas (cuentas. "Contacto principal") aparece](media/function-choices/accounts-primary-contact.png)

1. En la pestaña **Inicio**, seleccione **Nueva pantalla** y luego **En blanco**.

1. En la pestaña **Insertar**, seleccione **Tabla de datos**.

1. Establecer el **elementos** propiedad de la **tabla de datos** control en esta fórmula:

     **Choices( Accounts.'Primary Contact' )**

1. En el medio de la **tabla de datos** de control, seleccione el vínculo que se inicia **elija los campos...** y, a continuación, seleccione las casillas de verificación para el campo o campos que desea mostrar (por ejemplo, **firstname** y **lastname**).

     ![Pantalla de lienzo con un control de tabla de datos. La propiedad Items está establecida en la fórmula Choices( Accounts.'Primary Contact' ) y la tabla muestra las columnas firstname y lastname del primer conjunto de registros de la entidad Contacts](media/function-choices/full-accounts-pc.png)