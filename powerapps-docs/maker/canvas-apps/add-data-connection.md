---
title: Agregar una conexión de datos en una aplicación de lienzo | Microsoft Docs
description: Agregue una conexión de datos en una aplicación de lienzo existente o en una aplicación en blanco.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/06/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d1397f9fd2859611a3cd54023210a27cd5977834
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404595"
---
# <a name="add-a-data-connection-to-a-canvas-app-in-power-apps"></a>Agregar una conexión de datos a una aplicación de lienzo en Power apps

En Power Apps, agregue una conexión de datos a una aplicación de lienzo existente o a una aplicación que vaya a crear desde cero. La aplicación puede conectarse a SharePoint, Common Data Service, Salesforce, OneDrive o [muchos otros orígenes de datos](connections-list.md).

Tras este artículo, el [próximo paso](#next-steps) será mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive y administre datos en un libro de Excel en su aplicación.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.
* Conéctese a Common Data Service y actualice una entidad desde la aplicación.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos

[Regístrese](../signup-for-powerapps.md) en Power apps y, a continuación, [inicie sesión](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para suscribirse.

## <a name="open-a-blank-app"></a>Abra una aplicación en blanco

1. En la pestaña **Inicio** , seleccione **aplicación de lienzo en blanco**.

1. Especifique un nombre para la aplicación y, a continuación, seleccione **crear**.

1. Si aparece el cuadro de diálogo **Bienvenido a Power apps Studio** , seleccione **omitir**.

## <a name="add-data-source"></a>Agregar origen de datos

1. En el panel central, seleccione **conectarse a los datos** para abrir el panel **datos** .

    Si se tratara de una aplicación existente y la pantalla ya contenía un control, seleccione **ver** > **orígenes de datos** para abrir el mismo panel.

1. Seleccione **Agregar origen de datos**.

1. Si la lista de conexiones incluye la que desea, selecciónela para agregarla a la aplicación. De lo contrario, vaya al paso siguiente.

    ![Elegir una conexión existente](./media/add-data-connection/choose-existing-connection.png)

1. Seleccione **nueva conexión** para mostrar una lista de conexiones.

    ![Añadir conexión](./media/add-data-connection/add-connection.png)

1. En la barra de búsqueda, escriba o pegue las primeras letras de la conexión que desee y, a continuación, seleccione la conexión cuando aparezca.

    ![Buscar una conexión](./media/add-data-connection/search-connections.png)

1. Seleccione **Crear** para crear la conexión y agregarla a la aplicación.

    Algunos conectores, como **Office 365 Outlook**, no requieren ningún paso adicional y puede mostrar datos procedentes de ellos inmediatamente. Otros conectores le pedirán que proporcione las credenciales, especifique un conjunto determinado de datos o que realice otros pasos. Por ejemplo, [SharePoint](connections/connection-sharepoint-online.md) y [SQL Server](connections/connection-azure-sqldatabase.md) requieren información adicional antes de poder utilizarlas. Con [Common Data Service](connections/connection-common-data-service.md), puede cambiar el entorno antes de seleccionar una entidad.

## <a name="identify-or-change-a-data-source"></a>Identificar o cambiar un origen de datos
Si va a actualizar una aplicación, es posible que necesite identificar o cambiar el origen de datos que aparece en una galería, un formulario u otro control. Por ejemplo, es posible que necesite identificar un origen de datos a medida que actualice una aplicación creada por otra persona o que haya creado hace mucho tiempo.

1. Seleccione el control, como una galería, para el que desea identificar o cambiar el origen de datos.

    El nombre del origen de datos aparece en la pestaña **Propiedades** del panel derecho.

    ![Identificar una conexión](./media/add-data-connection/identify-connection.png)

1. Para mostrar más información acerca del origen de datos o para cambiarlo, seleccione la flecha hacia abajo situada junto a su nombre.

    Aparece más información sobre el origen de datos actual y puede seleccionar o crear otro origen.

    ![Cambiar una conexión](./media/add-data-connection/change-connection.png)

## <a name="next-steps"></a>Pasos siguientes

* Para mostrar y actualizar datos en un origen como Excel, SharePoint, Common Data Service o SQL Server, [agregue una galería](add-gallery.md)y [agregue un formulario](add-form.md).
* Para datos de otros orígenes, utilice funciones específicas de conectores como los de [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) y [Microsoft Translator](connections/connection-microsoft-translator.md).
