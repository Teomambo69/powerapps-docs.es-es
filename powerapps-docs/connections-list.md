---
title: "Introducción a los conectores | Microsoft Docs"
description: "Información general de todas las conexiones disponibles que puede usar para crear aplicaciones"
services: 
suite: powerapps
documentationcenter: 
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 08/28/2017
ms.author: archanan
ms.openlocfilehash: e78cf64217d65ee90e9e463452ea62d7ee63df88
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="overview-of-connectors-for-powerapps"></a>Información general de los conectores de PowerApps
Los datos están el núcleo de la mayoría de las aplicaciones, entre las que se incluyen las que se compilan en PowerApps. Los datos se almacenan en un *origen de datos* y para enviarlos a una aplicación se crea una *conexión*. La conexión utiliza un *conector* concreto para comunicarse con el origen de datos. PowerApps tiene conectores para muchos de los servicios y orígenes de datos locales más usados, como SharePoint, SQL Server, Office 365, Salesforce, Twitter, etc. Para empezar a agregar datos a una aplicación, consulte [Adición de una conexión de datos en PowerApps](add-data-connection.md).

La tabla siguiente contiene vínculos a más información acerca de nuestro conectores más usados. Para ver una lista completa de conectores, consulte el apartado [Todos los conectores](#all-connectors).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive para la Empresa](./media/connections-list/onedrive.png) |[**OneDrive para la Empresa**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Usuarios de Office 365](./media/connections-list/office365.png) |[**Usuarios de Office 365**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="types-of-connectors"></a>Tipos de conectores
PowerApps tiene dos tipos de conectores: *conectores estándar*, como los que ya se han mencionado, y *conectores personalizados*. Si se va a conectar a un origen de datos que PowerApps admite con un conector estándar, use dicho conector. Si necesita conectarse a otro origen, como un servicio que ha creado, consulte [Registrar y usar conectores personalizados en PowerApps](register-custom-api.md).

Los conectores estándar se comportan de forma diferente según el tipo de origen de datos al que se conectan y la forma en que el origen de datos devuelve los datos:

* Algunos conectores usan orígenes de datos tabulares, como SharePoint, SQL Server y Excel. Cuando se trabaja con estos orígenes de datos, los datos se devuelven a PowerApps en forma de tabla. PowerApps utiliza sus propias funciones, como [Patch()](functions/function-patch.md), [Collect()](functions/function-clear-collect-clearcollect.md), [Update()](functions/function-update-updateif.md), entro otras, para interactuar con los datos. Los datos tabulares también son fáciles de usar en formularios y galerías, donde un campo de una tabla se muestra como un campo de una galería o un formulario. Para más información, consulte los siguientes artículos:
  
    [Información acerca de los orígenes de datos en PowerApps](working-with-data-sources.md)
  
    [Creación de una aplicación a partir de datos de Excel](get-started-create-from-data.md)
  
    [Crear una aplicación desde cero](get-started-create-from-blank.md)
  
    **Nota:** para conectarse a datos en Excel, el libro debe estar hospedado en un servicio de almacenamiento en la nube como OneDrive. Para más información, consulte [Conexiones de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).
* Otros conectores usan orígenes de datos basados en funciones, como Twitter, Facebook y Office 365 Outlook. Cuando se trabaja con estos orígenes de datos, los datos se devuelven a PowerApps cuando se llama a funciones específicas del servicio subyacente. Por ejemplo, con el conector de Twitter se llama a `Twitter.MyFollowers()` para devolver una lista de los seguidores. Estos datos también se pueden usar en un formulario o una galería, pero es preciso un esfuerzo algo mayor que con los datos tabulares. Para más información, consulte [Twitter](connections/connection-twitter.md).

## <a name="all-connectors"></a>Todos los conectores
En la tabla siguiente se enumeran todos nuestros conectores. Para más información acerca de cada conector, consulte la [referencia de los conectores de Microsoft](https://docs.microsoft.com/connectors/). Los conectores Premium requieren el plan 1 o el plan 2 de PowerApps. Para más información, consulte los [planes de PowerApps](https://powerapps.microsoft.com/pricing/).

| &nbsp; | &nbsp; |
| --- | --- |
| 10to8 Appointment Scheduling<br>Act!<br>Adobe Creative Cloud ![Conector Premium](./media/connections-list/premium.png)<br>Adobe Sign<br>Amazon Redshift ![Conector Premium](./media/connections-list/premium.png)<br>Apache Impala ![Conector Premium](./media/connections-list/premium.png)<br>AppFigures<br>Approvals<br>Asana<br>AWeber ![Conector Premium](./media/connections-list/premium.png)<br>Azure AD<br>Azure Application Insights<br>Azure Automation<br>Azure Blob Storage<br>Azure Cosmos DB<br>Azure Data Lake<br>Azure Event Grid<br>Azure Event Grid Publish<br>Azure File Storage<br>Azure Log Analytics<br>Azure Log Analytics Data Collector<br>Azure Queue<br>Azure Resource Manager<br>Azure Table Storage<br>Basecamp 2<br>Basecamp 3<br>Benchmark Email ![Conector Premium](./media/connections-list/premium.png)<br>Bing Maps<br>Bing Search<br>Bitbucket ![Conector Premium](./media/connections-list/premium.png)<br>Bitly<br>Bizzy (H3 Solutions, Inc.)<br>Blogger<br>Box<br>bttn<br>Buffer<br>Calendly ![Conector Premium](./media/connections-list/premium.png)<br>Campfire<br>Cápsula CRM ![Conector Premium](./media/connections-list/premium.png)<br>Chatter ![Conector Premium](./media/connections-list/premium.png)<br>Cognito Forms<br>Common Data Service ![Conector Premium](./media/connections-list/premium.png)<br>Computer Vision API<br>Content Conversion<br>Content Moderator<br>DB2 ![Conector Premium](./media/connections-list/premium.png)<br>Disqus<br>DocFusion365 – SP ![Conector Premium](./media/connections-list/premium.png)<br>DocuSign ![Conector Premium](./media/connections-list/premium.png)<br>Dropbox<br>Dynamics 365<br>Dynamics 365 for Financials<br>Dynamics for Operations<br>Dynamics NAV<br>Easy Redmine ![Conector Premium](./media/connections-list/premium.png)<br>Elastic Forms<br>Event Hubs<br>Eventbrite ![Conector Premium](./media/connections-list/premium.png)<br>Excel<br>API de reconocimiento facial<br>Facebook<br>Sistema de archivos<br>Flic<br>FlowForma ![Conector Premium](./media/connections-list/premium.png)<br>FreshBooks ![Conector Premium](./media/connections-list/premium.png)<br>Freshdesk<br>Freshservice ![Conector Premium](./media/connections-list/premium.png)<br>FTP<br>GitHub<br>Gmail<br>Google Calendar<br>Google Contacts<br>Google Drive<br>Google Sheets<br>Google Tasks<br>GoToMeeting ![Conector Premium](./media/connections-list/premium.png)<br>GoToTraining ![Conector Premium](./media/connections-list/premium.png)<br>GoToWebinar ![Conector Premium](./media/connections-list/premium.png)<br>Harvest ![Conector Premium](./media/connections-list/premium.png)<br>HelloSign ![Conector Premium](./media/connections-list/premium.png)<br>HipChat<br>HTTP con Azure AD ![Conector Premium](./media/connections-list/premium.png)<br>Informix ![Conector Premium](./media/connections-list/premium.png)<br>Infusionsoft ![Conector Premium](./media/connections-list/premium.png) |Inoreader<br>Insightly<br>Instagram<br>Instapaper<br>Intercom<br>JIRA ![Conector Premium](./media/connections-list/premium.png)<br>JotForm ![Conector Premium](./media/connections-list/premium.png)<br>LeanKit ![Conector Premium](./media/connections-list/premium.png)<br>LinkedIn<br>LiveChat ![Conector Premium](./media/connections-list/premium.png)<br>LUIS<br>Correo<br>MailChimp ![Conector Premium](./media/connections-list/premium.png)<br>Mandrill ![Conector Premium](./media/connections-list/premium.png)<br>Mediana<br>Microsoft Forms<br>Microsoft StaffHub<br>Microsoft Teams<br>Microsoft Translator<br>MSN El Tiempo<br>Muhimbi PDF<br>MySQL ![Conector Premium](./media/connections-list/premium.png)<br>Nexmo ![Conector Premium](./media/connections-list/premium.png)<br>Notificaciones<br>Office 365 Bookings<br>Office 365 Groups<br>Office 365 Outlook<br>Usuarios de Office 365<br>Office 365 Video<br>OneDrive<br>OneDrive para la Empresa<br>OneNote (empresas)<br>Oracle Database ![Conector Premium](./media/connections-list/premium.png)<br>Outlook Customer Manager<br>Tareas de Outlook<br>Outlook.com<br>PagerDuty<br>Parserr<br>Paylocity ![Conector Premium](./media/connections-list/premium.png)<br>Pinterest<br>Pipedrive ![Conector Premium](./media/connections-list/premium.png)<br>Pitney Bowes Data Validation ![Conector Premium](./media/connections-list/premium.png)<br>Pivotal Tracker<br>Planner<br>Plivo ![Conector Premium](./media/connections-list/premium.png)<br>PostgreSQL ![Conector Premium](./media/connections-list/premium.png)<br>Power BI<br>PowerApps Notification ![Conector Premium](./media/connections-list/premium.png)<br>Project Online<br>Redmine<br>RSS<br>Salesforce ![Conector Premium](./media/connections-list/premium.png)<br>SendGrid<br>Service Bus<br>SFTP<br>SharePoint<br>Skype Empresarial<br>Slack<br>SmartSheet<br>SMTP<br>SparkPost<br>SQL Server<br>Stripe ![Conector Premium](./media/connections-list/premium.png)<br>SurveyMonkey ![Conector Premium](./media/connections-list/premium.png)<br>Teamwork Projects ![Conector Premium](./media/connections-list/premium.png)<br>Teradata ![Conector Premium](./media/connections-list/premium.png)<br>Análisis de texto<br>Todoist<br>Toodledo<br>Trello<br>Twilio<br>Twitter<br>TypeForm<br>UserVoice ![Conector Premium](./media/connections-list/premium.png)<br>Video Indexer<br>Vimeo<br>Visual Studio Team Services<br>WebMerge<br>WordPress<br>Wunderlist<br>Yammer<br>YouTube<br>Zendesk ![Conector Premium](./media/connections-list/premium.png) |

Si tiene alguna duda acerca de un conector concreto, use los [foros de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1). Si tiene una idea para un nuevo conector o sugerencias sobre posibles mejoras, use [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).

