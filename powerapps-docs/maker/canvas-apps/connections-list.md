---
title: Introducción a los conectores para aplicaciones de lienzo | Microsoft Docs
description: Información general sobre todas las conexiones de que dispone para compilar aplicaciones de lienzo
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/19/2019
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6cda843ea95f79e907aa738a6546d63a6a3be270
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74678865"
---
# <a name="overview-of-canvas-app-connectors-for-powerapps"></a>Introducción a los conectores para aplicaciones de lienzo de PowerApps
Los datos son el núcleo de la mayoría de las aplicaciones, incluidas las que se crean en Power apps. Los datos se almacenan en un *origen de datos* y para enviarlos a una aplicación se crea una *conexión*. La conexión utiliza un *conector* concreto para comunicarse con el origen de datos. Power apps tiene conectores para muchos servicios populares y orígenes de datos locales, entre los que se incluyen SharePoint, SQL Server, Office 365, Salesforce y Twitter. Para empezar a agregar datos a una aplicación de lienzo, vea [Adición de una conexión de datos en PowerApps](add-data-connection.md).

Un conector puede proporcionar **tablas** de datos o **acciones**. Algunos conectores solo ofrecen tablas, algunos solo ofrecen acciones y otros ofrecen ambas. Además, el conector puede ser un conector estándar o personalizado.

## <a name="tables"></a>Tablas

Si el conector ofrece tablas, agregue el origen de datos y luego seleccione la tabla en el origen de datos que quiere administrar. Power apps recupera datos de la tabla en la aplicación y actualiza los datos en el origen de datos. Por ejemplo, puede agregar un origen de datos que contenga una tabla denominada **Lecciones** y luego establecer la propiedad **Items** de un control, como una galería o un formulario, en este valor en la barra de fórmulas:

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
>  **Power apps no funciona con el esquema dinámico**. La frase esquema dinámico hace referencia a la posibilidad de que la misma acción pueda devolver una tabla diferente con columnas diferentes. Entre otras, las condiciones que pueden hacer que las columnas de las tablas difieran son los parámetros de entrada de la acción, el usuario o el rol que ejecuta la acción y el grupo en el que está trabajando el usuario. Por ejemplo, SQL Server procedimientos almacenados pueden devolver diferentes columnas si se ejecutan con diferentes entradas. En el caso de las acciones con esquema dinámico, la documentación del conector muestra **que las salidas de esta operación son dinámicas.** como valor devuelto. Por el contrario, Power automatizate funciona con el esquema dinámico y podría proporcionar una solución alternativa para su escenario.

## <a name="popular-connectors"></a>Conectores populares

La tabla siguiente contiene vínculos a más información sobre nuestros conectores más utilizados. Para ver una lista completa de conectores, consulte el apartado [Todos los conectores](https://docs.microsoft.com/connectors/).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![Almacenamiento en nube](./media/connections-list/onedrive.png) | ** de [**almacenamiento en la nube**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Traductor de Microsoft](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |&nbsp; | ![Usuarios de Office 365](./media/connections-list/office365.png) |[**Usuarios de Office 365**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**Oracle**](connections/connection-oracledb.md) |&nbsp; | ![Power BI](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

\* * Se aplica a Azure BLOB, Box, Dropbox, Google Drive, OneDrive y OneDrive para la empresa

## <a name="standard-and-custom-connectors"></a>Conectores estándar y personalizados
Power apps proporciona conectores *estándar* para muchos orígenes de datos de uso común, como los mencionados anteriormente. Si Power apps tiene un conector estándar para el tipo de origen de datos que desea usar, debe usar dicho conector. Si tiene que conectarse a otros tipos de orígenes de datos, como un servicio que haya creado, vea [Conectores personalizados en PowerApps](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Todos los conectores estándar
Vea la [referencia de conectores de Microsoft](https://docs.microsoft.com/connectors/) para obtener una lista de todos los conectores estándar. Los conectores premium requieren Power apps plan 1 o plan 2. Para obtener más información, consulte [planes de Power apps](https://powerapps.microsoft.com/pricing/).

Puede formular preguntas sobre un conector específico en los [foros de Power apps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)y puede sugerir conectores para agregar o realizar otras mejoras en las [ideas de Power apps](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).
