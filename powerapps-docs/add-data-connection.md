---
title: "Adición de una conexión de datos en una aplicación | Microsoft Docs"
description: "Adición de una conexión de datos en una aplicación existente o en una aplicación en blanco"
services: 
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/02/2017
ms.author: archanan
ms.openlocfilehash: b4377bd869e2b8879fd95d0a6729664104cd1368
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="add-a-data-connection-in-powerapps"></a>Adición de una conexión de datos en PowerApps
En PowerApps, añada una conexión de datos a una aplicación existente o a una que se cree desde cero. En este tema se utiliza PowerApps Studio, pero también puede usar [powerapps.com](https://web.powerapps.com), como se describe en el tema [Administración de conexiones](add-manage-connections.md).

La conexión de datos de la aplicación puede conectarse a SharePoint, Salesforce, OneDrive o a [cualquiera de muchos otros orígenes de datos](connections-list.md).

Tras este artículo, el [próximo paso](#next-steps) será mostrar y administrar la información del origen de datos de la aplicación, como en estos ejemplos:

* Conéctese a OneDrive y administre datos en un libro de Excel en su aplicación.
* Conéctese a Twilio y envíe un mensaje SMS desde la aplicación.
* Conéctese a SQL Server y actualice una tabla desde la aplicación.

## <a name="prerequisites"></a>Requisitos previos
[Suscríbase](signup-for-powerapps.md) a PowerApps, [instálelo](http://aka.ms/powerappsinstall), ábralo e inicie sesión con las mismas credenciales que usó para suscribirse.

## <a name="background-on-data-connections"></a>Información general sobre las conexiones de datos
La mayoría de las aplicaciones de PowerApps utilizan información externa (lo que se denomina **orígenes de datos**) que está guardada en servicios en la nube. Uno de los ejemplos más frecuentes son tablas que pertenecen a archivos de Excel guardados en OneDrive para la Empresa. Las aplicaciones pueden acceder a estos orígenes de datos a través de los **conectores**.

Los orígenes de datos más frecuentes son las tablas, que se pueden usar tanto para recuperar como para guardar información. Puede utilizar los conectores con los orígenes de datos para leer y escribir información en libros de Microsoft Excel, listas de SharePoint, tablas SQL y muchos otros formatos, que pueden guardarse en servicios en la nube, como OneDrive para la Empresa, DropBox, SQL Server, etc.

Los orígenes de datos que no son tablas incluyen correo electrónico, calendarios, Twitter y notificaciones.

Con los controles **[Galería](controls/control-gallery.md)**, **[Formulario de presentación](controls/control-form-detail.md)** y **[Formulario de edición](controls/control-form-detail.md)**, resulta muy fácil crear una aplicación que lea y escriba datos en un origen de datos. Para empezar, lea el artículo [Understand data forms](working-with-forms.md) (Introducción a los formularios de datos).

## <a name="add-a-connection"></a>Agregar una conexión
1. Haga clic o pulse en **Nuevo** en el menú **Archivo** (cerca del borde izquierdo).

    ![Opción Nuevo en el menú Archivo](./media/add-data-connection/file-new.png)

2. En el icono **Aplicación vacía**, pulse o haga clic en **Diseño de teléfono**.

    ![Crear una aplicación desde cero](./media/add-data-connection/blank-app.png)

3. En el panel central, pulse o haga clic en **conectar a datos**.

4. Si la lista de conexiones del panel **Data** (Datos) incluye la que desea, haga clic en ella o púlsela para agregarla a la aplicación. De lo contrario, vaya al paso siguiente.

    ![Agregar origen de datos](./media/add-data-connection/choose-existing-connections.png)

5. Pulse o haga clic en **Nueva conexión** para mostrar una lista de conectores.

    ![Añadir conexión](./media/add-data-connection/new-connection.png)

6. Desplácese por la lista de conectores hasta el tipo de conexión que desea crear (por ejemplo, **Office 365 Outlook**) y, a continuación, haga clic en él o púlselo.

    ![Seleccionar conexión](./media/add-data-connection/choose-connection.png)

7. Pulse o haga clic en **Crear** para crear la conexión y agregarla a la aplicación.

    Algunos conectores, como **Microsoft Translator**, no requieren ningún paso adicional y puede mostrar datos procedentes de ellos inmediatamente. Otros conectores le pedirán que proporcione las credenciales, especifique un conjunto determinado de datos o que realice otros pasos. Por ejemplo, [SharePoint](connections/connection-sharepoint-online.md) y [SQL Server](connections/connection-azure-sqldatabase.md) requieren información adicional antes de poder utilizarlas.

## <a name="view-or-change-a-data-source"></a>Visualización o cambio de un origen de datos
Si va a actualizar una aplicación, es posible que necesite identificar o cambiar el origen de datos que aparece en una galería, un formulario u otro control que tenga una propiedad **Item**. Por ejemplo, puede trabajar en una aplicación creada por otra persona o puede desea que se le recuerde un origen de datos que configuró hace un tiempo.

1. Seleccione el control en el que desea identificar el origen de datos.

    Por ejemplo, seleccione una galería (no un control de la galería) pulsando o haciendo clic en la lista jerárquica de las pantallas y controles que está cerca del borde izquierdo.

    El nombre del origen de datos aparece en la pestaña **Propiedades** del panel derecho.

    ![Origen de datos en la pestaña Propiedades](./media/add-data-connection/properties-tab.png)

2. Para mostrar más información acerca del origen de datos o para cambiarlo, pulse o haga clic en **Data** (Datos) en el panel derecho.

    ![Panel Data (Datos)](./media/add-data-connection/data-pane.png)

3. Para cambiar el origen de datos, pulse o haga clic en la flecha abajo que hay junto al origen de datos y, a continuación, elija o cree otro origen.

## <a name="next-steps"></a>Pasos siguientes
* Para mostrar y actualizar datos en un origen como Excel, SharePoint o SQL Server, agregue [una galería](add-gallery.md) y [un formulario](add-form.md).
* Para datos de otros orígenes, utilice funciones específicas de conectores como los de [Office 365 Outlook](connections/connection-office365-outlook.md), [Twitter](connections/connection-twitter.md) y [Microsoft Translator](connections/connection-microsoft-translator.md).
