---
title: Agregar una conexión de datos en una aplicación de lienzo | Microsoft Docs
description: Agregue una conexión de datos en una aplicación de lienzo existente o en una aplicación en blanco.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 33ca717967989a202fabbf8281b93f8b8263b79d
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42853213"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-powerapps"></a>Agregar una conexión de datos a una aplicación de lienzo en PowerApps

En PowerApps, agregue una conexión de datos a una aplicación de lienzo existente o a una que se cree desde cero. La aplicación puede conectarse a SharePoint, Salesforce, OneDrive o [muchos otros orígenes de datos](connections-list.md).

Tras este artículo, el [próximo paso](#next-steps) será mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive y administre datos en un libro de Excel en su aplicación.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos

[Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.

## <a name="add-a-data-source"></a>Agregar un origen de datos
1. En la pestaña **Inicio**, mantenga el mouse sobre el icono **Start from blank** (Empezar desde cero) y, luego, seleccione **Make this app.** (Crear esta aplicación).

    ![Crear una aplicación desde cero](./media/add-data-connection/blank-app-tile.png)

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

3. En el panel central, pulse o haga clic en **conectar a datos**.

4. Si la lista de conexiones del panel **Datos** incluye la que desea, selecciónela para agregarla a la aplicación. De lo contrario, vaya al paso siguiente.

    ![Agregar origen de datos](./media/add-data-connection/choose-existing-connections.png)

5. Seleccione **New connection** (Nueva conexión) para mostrar una lista de conectores.

    ![Añadir conexión](./media/add-data-connection/new-connection.png)

6. Desplácese por la lista de conectores hasta que aparezca el tipo de conexión que desea crear (por ejemplo, **Office 365 Outlook**) y, luego, selecciónelo.

    ![Seleccionar conexión](./media/add-data-connection/choose-connection.png)

7. Seleccione **Crear** para crear la conexión y agregarla a la aplicación.

    Algunos conectores, como **Office 365 Outlook**, no requieren ningún paso adicional y puede mostrar datos procedentes de ellos inmediatamente. Otros conectores le pedirán que proporcione las credenciales, especifique un conjunto determinado de datos o que realice otros pasos. Por ejemplo, [SharePoint](connections/connection-sharepoint-online.md) y [SQL Server](connections/connection-azure-sqldatabase.md) requieren información adicional antes de poder utilizarlas.

## <a name="add-another-data-source"></a>Agregar otro origen de datos
1. Agregue un control al que desee agregar un origen de datos.

    El control debe tener una propiedad **Items**, como tienen las galerías y los cuadros de lista, o una propiedad **Item**, como tiene un formulario.

1. En el panel **Datos** (que se abre automáticamente), abra la lista que aparece debajo de **Origen de datos** y, luego, seleccione **Agregar un origen de datos**.

1. Siga el procedimiento anterior, comenzando con el paso 4.

## <a name="identify-or-change-a-data-source"></a>Identificar o cambiar un origen de datos
Si va a actualizar una aplicación, es posible que necesite identificar o cambiar el origen de datos que aparece en una galería, un formulario u otro control. Por ejemplo, podría tener que identificar un origen de datos cuando actualice una aplicación que otra persona ha creado o que usted creó hace tiempo.

1. Seleccione el control para el que desea identificar o cambiar el origen de datos.

    Por ejemplo, seleccione una galería (no un control de la galería) pulsando o haciendo clic en la lista jerárquica de las pantallas y controles que está cerca del borde izquierdo.

    El nombre del origen de datos aparece en la pestaña **Propiedades** del panel derecho.

2. Seleccione el origen de datos para cambiarlo o para mostrar más información sobre él.

    ![Panel Data (Datos)](./media/add-data-connection/data-pane.png)

3. Para cambiar el origen de datos, abra la lista de orígenes de datos y, luego, seleccione o cree otro origen.

     ![Panel Data (Datos)](./media/add-data-connection/datasource-list.png)

## <a name="next-steps"></a>Pasos siguientes
* Para mostrar y actualizar datos en un origen como Excel, SharePoint o SQL Server, agregue [una galería](add-gallery.md) y [un formulario](add-form.md).
* Para datos de otros orígenes, utilice funciones específicas de conectores como los de [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) y [Microsoft Translator](connections/connection-microsoft-translator.md).
