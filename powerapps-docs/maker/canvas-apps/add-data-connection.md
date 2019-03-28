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
ms.openlocfilehash: 28357a6187831e05fe27075b8b22514950215ab4
ms.sourcegitcommit: fc604f3e7f0399bdabee86ce94f67de49531a444
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545070"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-powerapps"></a>Agregar una conexión de datos a una aplicación de lienzo en PowerApps

En PowerApps, agregue una conexión de datos a una aplicación de lienzo existente o a una que se cree desde cero. La aplicación puede conectarse a SharePoint, Salesforce, OneDrive o [muchos otros orígenes de datos](connections-list.md).

Tras este artículo, el [próximo paso](#next-steps) será mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive y administre datos en un libro de Excel en su aplicación.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos

[Regístrese](../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para registrase.

## <a name="open-a-blank-app"></a>Abra una aplicación en blanco

1. En el **inicio** ficha, seleccione **desde cero una aplicación de lienzo**.

1. Especifique un nombre para la aplicación y, a continuación, seleccione **crear**.

1. Si aparece el cuadro de diálogo de **bienvenida a PowerApps Studio**, seleccione **Omitir**.

## <a name="add-data-source"></a>Agregar origen de datos

1. En el panel central, seleccione **conectarse a datos** para abrir el **datos** panel.

    Si se tratara de una aplicación existente y la pantalla ya contenía un control, seleccione **vista** > **orígenes de datos** para abrir el mismo panel.

1. Seleccione **agregar origen de datos**.

1. Si la lista de conexiones incluye la que desea, selecciónela para agregarla a la aplicación. De lo contrario, vaya al paso siguiente.

    ![Elija una conexión existente](./media/add-data-connection/choose-existing-connection.png)

1. Seleccione **nueva conexión** para mostrar una lista de conexiones.

    ![Añadir conexión](./media/add-data-connection/add-connection.png)

1. En la barra de búsqueda, escriba o pegue las primeras letras de la conexión que desee y, a continuación, seleccione, a continuación, conexión cuando aparezca.

    ![Búsqueda de una conexión](./media/add-data-connection/search-connections.png)

1. Seleccione **Crear** para crear la conexión y agregarla a la aplicación.

    Algunos conectores, como **Office 365 Outlook**, no requieren ningún paso adicional y puede mostrar datos procedentes de ellos inmediatamente. Otros conectores le pedirán que proporcione las credenciales, especifique un conjunto determinado de datos o que realice otros pasos. Por ejemplo, [SharePoint](connections/connection-sharepoint-online.md) y [SQL Server](connections/connection-azure-sqldatabase.md) requieren información adicional antes de poder utilizarlas.

## <a name="identify-or-change-a-data-source"></a>Identificar o cambiar un origen de datos
Si va a actualizar una aplicación, es posible que necesite identificar o cambiar el origen de datos que aparece en una galería, un formulario u otro control. Por ejemplo, podría tener que identificar un origen de datos cuando actualice una aplicación que otra persona ha creado o que usted creó hace tiempo.

1. Seleccione el control, como una galería, para el que desea identificar o cambiar el origen de datos.

    El nombre del origen de datos aparece en la pestaña **Propiedades** del panel derecho.

    ![Identificar una conexión](./media/add-data-connection/identify-connection.png)

1. Para mostrar más información sobre el origen de datos o para cambiarlo, seleccione la flecha abajo junto a su nombre.

    Aparece más información sobre el origen de datos actual, y puede seleccionar o crear otro origen.

    ![Cambiar una conexión](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>Pasos siguientes

* Para mostrar y actualizar datos en un origen como Excel, SharePoint o SQL Server, agregue [una galería](add-gallery.md) y [un formulario](add-form.md).
* Para datos de otros orígenes, utilice funciones específicas de conectores como los de [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) y [Microsoft Translator](connections/connection-microsoft-translator.md).
