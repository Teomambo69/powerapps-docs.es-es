---
title: Introducción a los conectores para aplicaciones de lienzo | Microsoft Docs
description: Información general sobre todas las conexiones de que dispone para compilar aplicaciones de lienzo
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/28/2017
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 907ac3cf53709edd5a8b523479ec99816c6eec9c
ms.sourcegitcommit: 0f0b26122be28d674af0833247b491e9367c4932
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "73897831"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>Introducción a los conectores para aplicaciones de lienzo de PowerApps
Los datos están el núcleo de la mayoría de las aplicaciones, entre las que se incluyen las que se compilan en PowerApps. Los datos se almacenan en un *origen de datos* y para enviarlos a una aplicación se crea una *conexión*. La conexión utiliza un *conector* concreto para comunicarse con el origen de datos. PowerApps tiene conectores para muchos de los servicios y orígenes de datos locales más usados, como SharePoint, SQL Server, Office 365, Salesforce y Twitter. Para empezar a agregar datos a una aplicación de lienzo, vea [Adición de una conexión de datos en PowerApps](add-data-connection.md).

Un conector puede proporcionar **tablas** de datos o **acciones**. Algunos conectores solo ofrecen tablas, algunos solo ofrecen acciones y otros ofrecen ambas. Además, el conector puede ser un conector estándar o personalizado.

## <a name="tables"></a>Tablas

Si el conector ofrece tablas, agregue el origen de datos y luego seleccione la tabla en el origen de datos que quiere administrar. PowerApps recupera los datos de la tabla en la aplicación y actualiza automáticamente los datos en el origen de datos. Por ejemplo, puede agregar un origen de datos que contenga una tabla denominada **Lecciones** y luego establecer la propiedad **Items** de un control, como una galería o un formulario, en este valor en la barra de fórmulas:

 ![Propiedad Items en orígenes de datos sin formato](./media/connections-list/ItemPropertyPlain.png)

Puede especificar los datos que recupera la aplicación personalizando la propiedad **elementos** del control que muestra los datos. Retomando el ejemplo anterior, puede ordenar o filtrar los datos de la tabla **Lecciones** utilizando ese nombre como argumento para las funciones **Search** y **SortByColumn**. En este gráfico, la fórmula en la que se establece la propiedad **Items** especifica que los datos se ordenan y filtran según el texto de **TextSearchBox1**. 

 ![Propiedad Items en orígenes de datos expandidos](./media/connections-list/ItemPropertyExpanded.png)

Para obtener más información sobre cómo personalizar la fórmula con tablas, vea estos temas:

  [Información acerca de los orígenes de datos en PowerApps](working-with-data-sources.md)<br> 
  [Creación de una aplicación a partir de datos de Excel](get-started-create-from-data.md)<br> 
  [Crear una aplicación desde cero](get-started-create-from-blank.md)<br>
  [Información sobre tablas y registros de PowerApps](working-with-tables.md)

  > [!NOTE]
  > Para conectarse a datos en un libro de Excel, este ha de estar hospedado en un servicio de almacenamiento en la nube como OneDrive. Para más información, consulte [Conexiones de almacenamiento en la nube](connections/cloud-storage-blob-connections.md).

## <a name="actions"></a>Operaciones

Si el conector facilita acciones, tiene que seleccionar el origen de datos del mismo modo que antes. En lugar de seleccionar una tabla como siguiente paso, conecte manualmente un control a una acción editando la propiedad **Items** del control que va a mostrar los datos. La fórmula en la que se establece la propiedad **Items** especifica la acción que recupera los datos. Por ejemplo, la aplicación no recuperará los datos si se conecta a Yammer y luego establece la propiedad **Items** en el nombre del origen de datos. Para rellenar un control con datos, especifique una acción como **GetMessagesInGroup(5033622).messages**.

![Propiedad Items en orígenes de datos de acción](./media/connections-list/ItemPropertyAction.png)

Si tiene que controlar actualizaciones de datos personalizadas con conectores de acción, cree una fórmula que incluya la función **Patch**. En la fórmula, identifique la acción y los campos que quiere enlazar a la acción.  

Para obtener más información sobre cómo personalizar la fórmula para las actualizaciones personalizadas, vea estos temas:

[Patch](functions/function-patch.md)<br>[Collect](functions/function-clear-collect-clearcollect.md)<br>[Update](functions/function-update-updateif.md)

> [!NOTE]
>  **PowerApps no funciona con el esquema dinámico**. La frase esquema dinámico hace referencia a la posibilidad de que la misma acción pueda devolver una tabla diferente con columnas diferentes. Entre otras, las condiciones que pueden hacer que las columnas de las tablas difieran son los parámetros de entrada de la acción, el usuario o el rol que ejecuta la acción y el grupo en el que está trabajando el usuario. Por ejemplo, SQL Server procedimientos almacenados pueden devolver diferentes columnas si se ejecutan con diferentes entradas. En el caso de las acciones con esquema dinámico, la documentación del conector muestra **que las salidas de esta operación son dinámicas.** como valor devuelto. Por el contrario, Power automatizate funciona con el esquema dinámico y podría proporcionar una solución alternativa para su escenario.

## <a name="popular-connectors"></a>Conectores populares

La tabla siguiente contiene vínculos a más información sobre nuestros conectores más utilizados. Para ver una lista completa de conectores, consulte el apartado [Todos los conectores](https://docs.microsoft.com/connectors/).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive para la Empresa](./media/connections-list/onedrive.png) |[**OneDrive para la Empresa**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Usuarios de Office 365](./media/connections-list/office365.png) |[**Usuarios de Office 365**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="standard-and-custom-connectors"></a>Conectores estándar y personalizados
PowerApps ofrece conectores *estándar* para muchos orígenes de datos de uso común, como los indicados anteriormente. Si PowerApps tiene un conector estándar para el tipo de origen de datos que quiere utilizar, ha de usar dicho conector. Si tiene que conectarse a otros tipos de orígenes de datos, como un servicio que haya creado, vea [Conectores personalizados en PowerApps](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Todos los conectores estándar
Vea la [referencia de conectores de Microsoft](https://docs.microsoft.com/connectors/) para obtener una lista de todos los conectores estándar. Los conectores Premium requieren el plan 1 o el plan 2 de PowerApps. Para más información, consulte los [planes de PowerApps](https://powerapps.microsoft.com/pricing/).

Puede formular preguntas sobre un conector específico en los [foros de PowerApps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1), así como sugerir que se agreguen conectores o se realicen otras mejoras en [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas) (Ideas para PowerApps).
