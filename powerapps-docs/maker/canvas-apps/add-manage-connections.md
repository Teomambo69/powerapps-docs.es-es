---
title: Incorporación y administración de conexiones con orígenes de datos en servicios en la nube | Microsoft Docs
description: Agregue, elimine y actualice conexiones con orígenes de datos, como SharePoint, SQL Server, OneDrive para la Empresa, Salesforce y Office 365.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/09/2017
ms.author: lanced
ms.openlocfilehash: 40b215e0f7e8d681b5d857d08ce2677f2d271ef1
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39019846"
---
# <a name="manage-your-connections-in-powerapps"></a>Administración de las conexiones en PowerApps
En [powerapps.com](https://web.powerapps.com), puede crear una conexión entre PowerApps y uno o varios orígenes de datos, eliminar conexiones o actualizar las credenciales.

La conexión de datos de la aplicación puede establecerse con SharePoint, SQL Server, Office 365, OneDrive para la Empresa, Salesforce, Excel y otros muchos [orígenes de datos](connections-list.md).

Lo siguiente que haremos en este artículo es mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive para la Empresa y administre los datos de un libro de Excel en la aplicación.
* Actualice una lista en un sitio de SharePoint.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.
* Envíe correo electrónico en Office 365.
* Envíe un tweet.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos
1. [Inicie sesión](../signup-for-powerapps.md) en PowerApps.
2. Inicie sesión en [powerapps.com](https://web.powerapps.com) con las mismas credenciales que utilizó para suscribirse.

## <a name="background-on-data-connections"></a>Información general sobre las conexiones de datos
La mayoría de las aplicaciones de PowerApps utilizan información externa (lo que se denomina **orígenes de datos**) que está guardada en servicios en la nube. Uno de los ejemplos más frecuentes son tablas que pertenecen a archivos de Excel guardados en OneDrive para la Empresa. Las aplicaciones pueden acceder a estos orígenes de datos a través de las **conexiones**.

El tipo más común de origen de datos son las tablas, que pueden usarse tanto para recuperar como para guardar información. Puede utilizar las conexiones con los orígenes de datos para leer y escribir información en libros de Microsoft Excel, listas de SharePoint, tablas SQL y muchos otros formatos, que pueden guardarse en servicios en la nube, como OneDrive para la Empresa, DropBox, SQL Server, etc.

También existen otros tipos de orígenes de datos que no son tablas, como correos electrónicos, calendarios, Twitter y (próximamente) notificaciones.

Con los controles **[Galería](controls/control-gallery.md)**, **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)**, resulta muy fácil crear una aplicación que lea y escriba datos en un origen de datos. Para empezar, lea el artículo [Understand data forms](working-with-forms.md) (Introducción a los formularios de datos).

Además de crear y administrar conexiones en [powerapps.com](https://web.powerapps.com), también puede crearlas realizando estas tareas:

* Generar automáticamente un [aplicación de datos](app-from-sharepoint.md), como una lista de SharePoint personalizada.
* Actualizar una aplicación existente o crear una desde cero como se describe en [Agregar una conexión](add-data-connection.md).
* Abrir una aplicación que otro usuario ha creado y [compartido con usted](share-app.md).

> [!NOTE]
> Si desea usar PowerApps Studio en su lugar, abra el menú **Archivo** y haga clic o pulse **Conexiones**, y se abre [powerapps.com](https://web.powerapps.com), donde puede crear y administrar las conexiones de allí.

## <a name="create-a-new-connection"></a>Creación de una nueva conexión
1. Si aún no lo ha hecho, inicie sesión en [powerapps.com](https://web.powerapps.com).
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

