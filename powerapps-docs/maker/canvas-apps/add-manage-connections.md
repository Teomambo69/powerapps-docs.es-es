---
title: Adición y administración de conexiones en aplicaciones de lienzo | Microsoft Docs
description: Agregue, elimine y actualice las conexiones de aplicaciones de lienzo con orígenes de datos tales como SharePoint, SQL Server y OneDrive para la Empresa.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/09/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d230d38c8393540bc78fd003ecb167f1f3978b97
ms.sourcegitcommit: fe18d82dbbd3972c472fd69f7feb3a35c3a31153
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150235"
---
# <a name="manage-canvas-app-connections-in-powerapps"></a>Administración de conexiones de aplicaciones de lienzo en PowerApps
En [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), cree una conexión con uno o varios orígenes de datos, elimine una conexión o actualice las credenciales.

La conexión de datos de la aplicación de lienzo puede establecerse con SharePoint, SQL Server, Office 365, OneDrive para la Empresa, Salesforce, Excel y muchos otros [orígenes de datos](connections-list.md).

Lo siguiente que haremos en este artículo es mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive para la Empresa y administre los datos de un libro de Excel en la aplicación.
* Actualice una lista en un sitio de SharePoint.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.
* Envíe correo electrónico en Office 365.
* Envíe un tweet.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos
1. [Inicie sesión](../signup-for-powerapps.md) en PowerApps.
2. Inicie sesión en [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que utilizó para suscribirse.

## <a name="background-on-data-connections"></a>Información general sobre las conexiones de datos
La mayoría de las aplicaciones de PowerApps utilizan información externa (lo que se denomina **orígenes de datos**) que está guardada en servicios en la nube. Uno de los ejemplos más frecuentes son tablas que pertenecen a archivos de Excel guardados en OneDrive para la Empresa. Las aplicaciones pueden acceder a estos orígenes de datos a través de las **conexiones**.

El tipo más común de origen de datos son las tablas, que pueden usarse tanto para recuperar como para guardar información. Puede utilizar las conexiones con los orígenes de datos para leer y escribir información en libros de Microsoft Excel, listas de SharePoint, tablas SQL y muchos otros formatos, que pueden guardarse en servicios en la nube, como OneDrive para la Empresa, DropBox, SQL Server, etc.

Hay otros tipos de orígenes de datos que no son tablas, como correo electrónico, calendarios, Twitter y notificaciones.

Con los controles **[Galería](controls/control-gallery.md)** , **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)** , resulta muy fácil crear una aplicación que lea y escriba datos en un origen de datos. Para empezar, lea el artículo [Understand data forms](working-with-forms.md) (Introducción a los formularios de datos).

Además de crear y administrar conexiones en [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), también puede crearlas realizando estas tareas:

* Generar automáticamente un [aplicación de datos](app-from-sharepoint.md), como una lista de SharePoint personalizada.
* Actualizar una aplicación existente o crear una desde cero como se describe en [Agregar una conexión](add-data-connection.md).
* Abrir una aplicación que otro usuario ha creado y [compartido con usted](share-app.md).

> [!NOTE]
> Si desea usar PowerApps Studio en su lugar, abra el menú **Archivo** y haga clic o pulse **Conexiones**, y se abre [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), donde puede crear y administrar las conexiones de allí.

## <a name="create-a-new-connection"></a>Creación de una nueva conexión
1. Si aún no lo ha hecho, inicie sesión en [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. En la barra de navegación izquierda, pulse o haga clic en **Conexiones**.
   
    ![Administración de conexiones](./media/add-manage-connections/open-connections.png)
3. En la esquina superior derecha, pulse o haga clic en **Nueva conexión**.
   
    ![Adición de conexiones](./media/add-manage-connections/add-connection.png)
4. Pulse o haga clic en un conector de la lista que aparece y siga las instrucciones.
   
   ![Adición de conexiones](./media/add-manage-connections/choose-connection.png)
5. Pulse o haga clic en el botón **Crear**.
   
   ![Adición de conexiones](./media/add-manage-connections/create-connection.png)
6. Siga las instrucciones. Algunos conectores le solicitarán que escriba las credenciales, que especifique un conjunto de datos o que realice otros pasos. Esto no ocurre con otros conectores, como **Microsoft Translator**.
   
   Por ejemplo, estos conectores requieren información adicional antes de usarlos.
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

Aparecerá el nuevo conector en **Conexiones** y podrá [agregarlo a una aplicación](add-data-connection.md).

## <a name="update-or-delete-a-connection"></a>Actualizar o eliminar una conexión
En la lista de conexiones, pulse o haga clic en la conexión que desea actualizar o eliminar y en el botón de puntos suspensivos (tres puntos) que encontrará a la derecha de la conexión.

![Actualización de la conexión](./media/add-manage-connections/auth-or-delete.png)

* Para actualizar las credenciales de una conexión, pulse o haga clic en el icono con forma de llave y especifique las credenciales de dicha conexión.
* Para eliminar la conexión, pulse o haga clic en el icono de papelera.
* Pulse o haga clic en el icono de información para ver los detalles de la conexión.

