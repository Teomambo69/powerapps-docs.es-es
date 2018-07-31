---
title: Introducción a los conectores | Microsoft Docs
description: Información general de todas las conexiones disponibles que puede usar para crear aplicaciones
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/28/2017
ms.author: lanced
ms.openlocfilehash: 15da6ed2ce6b44c17645ac11d1b049b95e157703
ms.sourcegitcommit: 47be38a23c96ba7478fd777065f5db41181af40b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39164757"
---
# <a name="overview-of-connectors-for-powerapps"></a>Información general de los conectores de PowerApps
Los datos están el núcleo de la mayoría de las aplicaciones, entre las que se incluyen las que se compilan en PowerApps. Los datos se almacenan en un *origen de datos* y para enviarlos a una aplicación se crea una *conexión*. La conexión utiliza un *conector* concreto para comunicarse con el origen de datos. PowerApps tiene conectores para muchos de los servicios y orígenes de datos locales más usados, como SharePoint, SQL Server, Office 365, Salesforce, Twitter, etc. Para empezar a agregar datos a una aplicación, consulte [Adición de una conexión de datos en PowerApps](add-data-connection.md).

La tabla siguiente contiene vínculos a más información acerca de nuestro conectores más usados. Para ver una lista completa de conectores, consulte el apartado [Todos los conectores](#all-connectors).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive para la Empresa](./media/connections-list/onedrive.png) |[**OneDrive para la Empresa**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Usuarios de Office 365](./media/connections-list/office365.png) |[**Usuarios de Office 365**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="types-of-connectors"></a>Tipos de conectores
PowerApps tiene dos tipos de conectores: *conectores estándar*, como los que ya se han mencionado, y *conectores personalizados*. Si se va a conectar a un origen de datos que PowerApps admite con un conector estándar, use dicho conector. Si necesita conectarse a otro origen, como un servicio que ha creado, consulte [Registrar y usar conectores personalizados en PowerApps](../canvas-apps/register-custom-api.md).

Los conectores estándar se comportan de forma diferente según el tipo de origen de datos al que se conectan y la forma en que el origen de datos devuelve los datos:

* Algunos conectores usan orígenes de datos tabulares, como SharePoint, SQL Server y Excel. Cuando se trabaja con estos orígenes de datos, los datos se devuelven a PowerApps en forma de tabla. PowerApps utiliza sus propias funciones, como [Patch()](functions/function-patch.md), [Collect()](functions/function-clear-collect-clearcollect.md), [Update()](functions/function-update-updateif.md), entro otras, para interactuar con los datos. Los datos tabulares también son fáciles de usar en formularios y galerías, donde un campo de una tabla se muestra como un campo de una galería o un formulario. Para más información, consulte los siguientes artículos:

    [Información acerca de los orígenes de datos en PowerApps](working-with-data-sources.md)

    [Creación de una aplicación a partir de datos de Excel](get-started-create-from-data.md)

    [Crear una aplicación desde cero](get-started-create-from-blank.md)

    > [!NOTE]
  > Para conectarse a datos en Excel, el libro debe estar hospedado en un servicio de almacenamiento en la nube como OneDrive. Para más información, consulte [Conexiones de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).

* Otros conectores usan orígenes de datos basados en funciones, como Twitter, Facebook y Office 365 Outlook. Cuando se trabaja con estos orígenes de datos, los datos se devuelven a PowerApps cuando se llama a funciones específicas del servicio subyacente. Por ejemplo, con el conector de Twitter se llama a `Twitter.MyFollowers()` para devolver una lista de los seguidores. Estos datos también se pueden usar en un formulario o una galería, pero es preciso un esfuerzo algo mayor que con los datos tabulares. Para más información, consulte [Twitter](connections/connection-twitter.md).

## <a name="all-connectors"></a>Todos los conectores
Consulte la [referencia de conectores de Microsoft](https://docs.microsoft.com/connectors/) para ver una lista de los conectores. Los conectores Premium requieren el plan 1 o el plan 2 de PowerApps. Para más información, consulte los [planes de PowerApps](https://powerapps.microsoft.com/pricing/).


Si tiene alguna duda acerca de un conector concreto, use los [foros de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1). Si tiene una idea para un nuevo conector o sugerencias sobre posibles mejoras, use [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).
