---
title: Adición y administración de conexiones en aplicaciones de lienzo | Microsoft Docs
description: Agregue, elimine y actualice las conexiones de aplicaciones de lienzo con orígenes de datos tales como SharePoint, SQL Server y OneDrive para la Empresa.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/05/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9b25eef7460098139c32fba5606b682baae2ada9
ms.sourcegitcommit: dc379bede57da58b5787eda5437eb94b662e21ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2020
ms.locfileid: "77037505"
---
# <a name="manage-canvas-app-connections-in-power-apps"></a>Administración de conexiones de la aplicación de lienzo en Power apps
En [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), cree una conexión con uno o varios orígenes de datos, elimine una conexión o actualice las credenciales.

La conexión de datos de la aplicación de lienzo puede establecerse con SharePoint, SQL Server, Office 365, OneDrive para la Empresa, Salesforce, Excel y muchos otros [orígenes de datos](connections-list.md).

Lo siguiente que haremos en este artículo es mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive para la Empresa y administre los datos de un libro de Excel en la aplicación.
* Actualizar una lista en un sitio de SharePoint.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.
* Enviar correo electrónico en Office 365.
* Enviar un tweet.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos
1. [Regístrese](../signup-for-powerapps.md) en Power apps.
2. Inicie sesión en [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) con las mismas credenciales que usó para suscribirse.

## <a name="background-on-data-connections"></a>Información general sobre las conexiones de datos
La mayoría de las aplicaciones de Power apps usan información externa denominada **orígenes de datos** que se almacenan en Cloud Services. Uno de los ejemplos más frecuentes son tablas que pertenecen a archivos de Excel guardados en OneDrive para la Empresa. Las aplicaciones pueden acceder a estos orígenes de datos a través de las **conexiones**.

El tipo más común de origen de datos son las tablas, que pueden usarse tanto para recuperar como para guardar información. Puede utilizar las conexiones con los orígenes de datos para leer y escribir información en libros de Microsoft Excel, listas de SharePoint, tablas SQL y muchos otros formatos, que pueden guardarse en servicios en la nube, como OneDrive para la Empresa, DropBox, SQL Server, etc.

Hay otros tipos de orígenes de datos que no son tablas, como correo electrónico, calendarios, Twitter y notificaciones.

Con los controles **[Galería](controls/control-gallery.md)** , **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)** , resulta muy fácil crear una aplicación que lea y escriba datos en un origen de datos. Para empezar, lea el artículo [Understand data forms](working-with-forms.md) (Introducción a los formularios de datos).

Además de crear y administrar conexiones en [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc), también puede crearlas realizando estas tareas:

* Generar automáticamente un [aplicación de datos](app-from-sharepoint.md), como una lista de SharePoint personalizada.
* Actualizar una aplicación existente o crear una desde cero como se describe en [Agregar una conexión](add-data-connection.md).
* Abrir una aplicación que otro usuario ha creado y [compartido con usted](share-app.md).

> [!NOTE]
> Si desea usar Power apps Studio en su lugar, abra el menú **archivo** y, a continuación, haga clic o pulse en **conexiones**, [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) se abrirá para que pueda crear y administrar las conexiones allí.

## <a name="create-a-new-connection"></a>Creación de una nueva conexión
1. Si todavía no lo ha hecho, inicie sesión en [make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
2. En el panel de navegación izquierdo, expanda **datos** y seleccione **conexiones**.
   
    ![Administración de conexiones](./media/add-manage-connections/open-connections.png)
3. Seleccione **nueva conexión**.
   
    ![Adición de conexiones](./media/add-manage-connections/add-connection.png)
4. Seleccione un conector en la lista que aparece y, a continuación, siga las indicaciones.
   
   ![Adición de conexiones](./media/add-manage-connections/choose-connection.png)
5. Seleccione el botón **crear** .
   
   ![Adición de conexiones](./media/add-manage-connections/create-connection.png)
6. Siga las instrucciones. Algunos conectores le solicitarán que escriba las credenciales, que especifique un conjunto de datos o que realice otros pasos. Esto no ocurre con otros conectores, como **Microsoft Translator**.
   
   Por ejemplo, estos conectores requieren información adicional antes de usarlos.
   
   * [SharePoint](connections/connection-sharepoint-online.md)
   * [SQL Server](connections/connection-azure-sqldatabase.md)

Aparecerá el nuevo conector en **Conexiones** y podrá [agregarlo a una aplicación](add-data-connection.md).

## <a name="update-or-delete-a-connection"></a>Actualizar o eliminar una conexión
En la lista de conexiones, busque la conexión que desea actualizar o eliminar y, a continuación, seleccione los puntos suspensivos (...) a la derecha de la conexión.

![Actualización de la conexión](./media/add-manage-connections/auth-or-delete.png)

* Para actualizar las credenciales de una conexión, seleccione el icono de clave y, a continuación, proporcione las credenciales para esa conexión.
* Para eliminar la conexión, seleccione eliminar.
* Seleccione el icono de información para ver los detalles de la conexión.

