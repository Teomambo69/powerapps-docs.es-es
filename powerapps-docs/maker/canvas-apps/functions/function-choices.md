---
title: Función Choices | Microsoft Docs
description: Información de referencia, incluida sintaxis, de la función Choices de PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7adf3391ef418a2b42861df63bc8396adc22f93a
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679463"
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

En este momento, solo puede usar las columnas de búsqueda con SharePoint y Common Data Service.

## <a name="syntax"></a>Sintaxis
**Choices**( *column-reference* )

* *column-reference*: requerido.  Columna de búsqueda de un origen de datos. No incluya el nombre de columna entre comillas dobles. La referencia debe ser directa a la columna del origen de datos y no pasarse a través de una función o un control.

## <a name="examples"></a>Ejemplos

#### <a name="choices-for-a-lookup"></a>Choices para una búsqueda

1. [Cree una base](../../../administrator/create-database.md) de datos en Common Data Service y seleccione el cuadro **incluir aplicaciones y datos de ejemplo** .

    Se crean muchas entidades, como **Accounts**.

    **Nota**: los nombres de entidad son singulares en make.powerapps.com y plural en Power apps Studio.

    ![Una lista parcial de los campos de la entidad cuenta en Common Data Service para aplicaciones, resaltando que "contacto principal" es un campo de búsqueda](media/function-choices/entity-account.png)

    La entidad **Accounts** tiene una columna **Primary Contact** que es una búsqueda en la entidad **Contacts**.  

    ![Una lista parcial de los campos de la entidad Contact en el Common Data Service](media/function-choices/entity-contact.png)

    En cada cuenta se designa un contacto como contacto principal o este está *blank*.

1. [Genere una aplicación](../data-platform-create-app.md) desde la entidad **Accounts**.

1. En la lista de pantallas y controles junto al borde izquierdo, desplácese hacia abajo hasta que aparezca **EditScreen1** y luego seleccione **EditForm1** justo debajo.

    ![En la barra de navegación izquierda, selección de EditForm1 en EditScreen1](media/function-choices/select-editform.png)

1. En la pestaña **propiedades** del panel derecho, seleccione **Editar campos**.

    ![Abrir el panel datos](media/function-choices/open-data-pane.png)

1. En el panel **campos** , seleccione **Agregar campo**.

1. Busque el campo de **contacto principal** , Active su casilla y, a continuación, seleccione **Agregar**.

    ![Selección de Accounts para abrir el panel Datos](media/function-choices/field-list.png)

    El campo **contacto principal** aparece en la parte inferior del formulario. Si el campo muestra un error, seleccione **orígenes de datos** en la pestaña **Ver** , seleccione los puntos suspensivos (...) para el origen de datos **cuentas** y, a continuación, seleccione **Actualizar**.

1. (Opcional) Arrastre el campo **Primary Contact** desde la parte inferior a la parte superior de la lista de campos.

1. En la tarjeta de **Primary Contact**, seleccione el control **Cuadro combinado**.

    La propiedad **Items** de ese control se establece en una fórmula que identifica la columna por su nombre para mostrar, como en el primer ejemplo, o su nombre lógico, como en el segundo ejemplo:

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![Pantalla de lienzo con un control de formulario. Se selecciona el control de cuadro combinado dentro de la tarjeta de contacto principal y aparece la propiedad items con las opciones de la fórmula (accounts. ' Primary contact ')](media/function-choices/accounts-primary-contact.png)

1. En la pestaña **Inicio**, seleccione **Nueva pantalla** y luego **En blanco**.

1. En la pestaña **Insertar**, seleccione **Tabla de datos**.

1. Establezca la propiedad **elementos** del control **tabla de datos** en esta fórmula:

     **Choices( Accounts.'Primary Contact' )**

1. En el centro del control **tabla de datos** , seleccione el vínculo que comienza **a elegir los campos...** y, a continuación, active las casillas correspondientes al campo o los campos que desea mostrar (por ejemplo, **FirstName** y **LastName**).

     ![Pantalla de lienzo con un control de tabla de datos. La propiedad Items está establecida en la fórmula Choices( Accounts.'Primary Contact' ) y la tabla muestra las columnas firstname y lastname del primer conjunto de registros de la entidad Contacts](media/function-choices/full-accounts-pc.png)