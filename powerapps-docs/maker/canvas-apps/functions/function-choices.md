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
ms.openlocfilehash: 531a614493ef739acd7be71f396dfc2f7e1ada1c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42832805"
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

De momento solo puede usar columnas de búsqueda con SharePoint y Common Data Service for Apps.

## <a name="syntax"></a>Sintaxis
**Choices**( *column-reference* )

* *column-reference*: requerido.  Columna de búsqueda de un origen de datos. No incluya el nombre de columna entre comillas dobles. La referencia debe ser directa a la columna del origen de datos y no pasarse a través de una función o un control.

## <a name="examples"></a>Ejemplos

#### <a name="choices-for-a-lookup"></a>Choices para una búsqueda

1. [Cree una base de datos](../../../administrator/create-database.md) en Common Data Service for Apps y seleccione el cuadro **Incluir datos y aplicaciones de ejemplo**.

    Se crean muchas entidades, como **Accounts**.

    **Nota**: Los nombres de entidad son singulares en web.powerapps.com y plurales en PowerApps Studio.

    ![Lista parcial de los campos de la entidad Account en Commmon Data Service for Apps en la que se resalta que "Primary Contact" es un campo de búsqueda](media/function-choices/entity-account.png)

    La entidad **Accounts** tiene una columna **Primary Contact** que es una búsqueda en la entidad **Contacts**.  

    ![Lista parcial de los campos de la entidad Contact en Common Data Service](media/function-choices/entity-contact.png)

    En cada cuenta se designa un contacto como contacto principal o este está *blank*.

2. [Genere una aplicación](../data-platform-create-app.md) desde la entidad **Accounts**.

3. En la lista de pantallas y controles junto al borde izquierdo, desplácese hacia abajo hasta que aparezca **EditScreen1** y luego seleccione **EditForm1** justo debajo.

    ![En la barra de navegación izquierda, selección de EditForm1 en EditScreen1](media/function-choices/select-editform.png)

4. En la pestaña **Propiedades** del panel derecho, seleccione **Accounts**.

    ![Selección de Accounts para abrir el panel Datos](media/function-choices/open-data-pane.png)

5. En el panel **Datos**, desplácese hacia abajo hasta la lista de campos.

    ![Selección de Accounts para abrir el panel Datos](media/function-choices/field-list.png)

6. Busque la casilla **Primary Contact** y actívela si está desactivada.

7. (Opcional) Arrastre el campo **Primary Contact** desde la parte inferior a la parte superior de la lista de campos.

8. En la tarjeta de **Primary Contact**, seleccione el control **Cuadro combinado**.

    La propiedad **Items** de ese control se establece en una de dos fórmulas en función del estado de la casilla **Usar nombres de columna para mostrar** de Configuración avanzada.

   - Si la casilla está activada, la propiedad se establece en esta fórmula:<br>**Choices( Accounts.'Primary Contact' )**
   - Si la casilla está desactivada, la propiedad se establece en esta fórmula:<br>**Choices( Accounts.primarycontactid )**

     ![Pantalla de lienzo con un control de formulario. El control **Cuadro combinado** de la tarjeta **Primary Contact** está seleccionado y aparece la propiedad Items con la fórmula Choices( Accounts.'Primary Contact' )](media/function-choices/accounts-primary-contact.png)

9. En la pestaña **Inicio**, seleccione **Nueva pantalla** y luego **En blanco**.

10. En la pestaña **Insertar**, seleccione **Tabla de datos**.

11. Establezca la propiedad **Items** del control **Tabla de datos** en una de estas fórmulas:

     - Si la casilla **Usar nombres de columna para mostrar** de Configuración avanzada está activada, use esta fórmula:<br>**Choices( Accounts.'Primary Contact' )**
     - De lo contrario, use esta fórmula:<br>**Choices( Accounts.primarycontactid )**

12. Abra el panel **Datos** y luego active las casillas de **firstname**, **lastname** o cualquier otro campo que quiera mostrar.

     ![Pantalla de lienzo con un control de tabla de datos. La propiedad Items está establecida en la fórmula Choices( Accounts.'Primary Contact' ) y la tabla muestra las columnas firstname y lastname del primer conjunto de registros de la entidad Contacts](media/function-choices/full-accounts-pc.png)
