---
title: Introducción a los conectores para aplicaciones de lienzo | Microsoft Docs
description: Información general sobre todas las conexiones de que dispone para compilar aplicaciones de lienzo
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/19/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c0710f36b5c49037d5104ab1085d1c990290b967
ms.sourcegitcommit: 1b29cd1fa1492037ef04188dd857a911edeb4985
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80122876"
---
# <a name="overview-of-canvas-app-connectors-for-power-apps"></a>Información general de los conectores de canvas-app para Power apps
Los datos son el núcleo de la mayoría de las aplicaciones, incluidas las que se crean en Power apps. Los datos se almacenan en un *origen de datos* y para enviarlos a una aplicación se crea una *conexión*. La conexión utiliza un *conector* concreto para comunicarse con el origen de datos. Power apps tiene conectores para muchos servicios populares y orígenes de datos locales, entre los que se incluyen SharePoint, SQL Server, Office 365, Salesforce y Twitter. Para empezar a agregar datos a una aplicación de lienzo, consulte [Agregar una conexión de datos en Power apps](add-data-connection.md).

Un conector puede proporcionar **tablas** de datos o **acciones**. Algunos conectores solo ofrecen tablas, algunos solo ofrecen acciones y otros ofrecen ambas. Además, el conector puede ser un conector estándar o personalizado.

## <a name="tables"></a>Tablas

Si el conector ofrece tablas, agregue el origen de datos y luego seleccione la tabla en el origen de datos que quiere administrar. Power apps recupera datos de la tabla en la aplicación y actualiza los datos en el origen de datos. Por ejemplo, puede agregar un origen de datos que contenga una tabla denominada **Lecciones** y luego establecer la propiedad **Items** de un control, como una galería o un formulario, en este valor en la barra de fórmulas:

 ![Propiedad Items en orígenes de datos sin formato](./media/connections-list/ItemPropertyPlain.png)

Puede especificar los datos que recupera la aplicación personalizando la propiedad **elementos** del control que muestra los datos. Retomando el ejemplo anterior, puede ordenar o filtrar los datos de la tabla **Lecciones** utilizando ese nombre como argumento para las funciones **Search** y **SortByColumn**. En este gráfico, la fórmula en la que se establece la propiedad **Items** especifica que los datos se ordenan y filtran según el texto de **TextSearchBox1**. 

 ![Propiedad Items en orígenes de datos expandidos](./media/connections-list/ItemPropertyExpanded.png)

Para obtener más información sobre cómo personalizar la fórmula con tablas, vea estos temas:

  [Descripción de los orígenes de datos en Power apps](working-with-data-sources.md)<br> 
  [Creación de una aplicación a partir de datos de Excel](get-started-create-from-data.md)<br> 
  [Crear una aplicación desde cero](get-started-create-from-blank.md)<br>
  [Descripción de las tablas y los registros de Power apps](working-with-tables.md)

  > [!NOTE]
  > Para conectarse a datos en un libro de Excel, este ha de estar hospedado en un servicio de almacenamiento en la nube como OneDrive. Para más información, consulte [conexión a almacenamiento en la nube desde Power apps](connections/cloud-storage-blob-connections.md).

## <a name="actions"></a>Acciones

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
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](connections/connection-common-data-service.md) |&nbsp; |![El almacenamiento en la nube](./media/connections-list/onedrive.png) | ** de [**almacenamiento en la nube**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; | ![Dynamics AX](./media/connections-list/dynamics-ax.png) |[**Dynamics AX**](connections/connection-dynamicsax.md) |
|![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |&nbsp; |![Traductor de Microsoft](./media/connections-list/microsoft-translator.png) |[**Microsoft Translator**](connections/connection-microsoft-translator.md) |
|![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |&nbsp; | ![Usuarios de Office 365](./media/connections-list/office365.png) |[**Usuarios de Office 365**](connections/connection-office365-users.md) |
| ![Oracle](./media/connections-list/oracle-icon.png) |[**Oracle**](connections/connection-oracledb.md) |&nbsp; | ![Aplicación](./media/connections-list/powerbi.png) |[**Power BI**](connections/connection-powerbi.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; | ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) 
|![Twitter](./media/connections-list/twitter.png) |[**Twitter**](connections/connection-twitter.md)

\* * Se aplica a Azure BLOB, Box, Dropbox, Google Drive, OneDrive y OneDrive para la empresa

## <a name="standard-and-custom-connectors"></a>Conectores estándar y personalizados
Power apps proporciona conectores *estándar* para muchos orígenes de datos de uso frecuente. Si Power apps tiene un conector estándar para el tipo de origen de datos que desea usar, debe usar dicho conector. Si tiene que conectarse a otros tipos de orígenes de datos, como un servicio que haya creado, vea [Conectores personalizados en PowerApps](../canvas-apps/register-custom-api.md).

## <a name="all-standard-connectors"></a>Todos los conectores estándar
Los conectores estándar no requieren licencias especiales. Para obtener más información, consulte [planes de Power apps](https://powerapps.microsoft.com/pricing/).

Puede formular preguntas sobre un conector específico en los [foros de Power apps](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)y puede sugerir conectores para agregar o realizar otras mejoras en las [ideas de Power apps](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).

## <a name="security-and-types-of-authentication"></a>Seguridad y tipos de autenticación

Cuando cree la aplicación y cree una conexión a un origen de datos, puede ver que su elección de conector le permite usar diferentes maneras de autenticarse. Por ejemplo, el conector de SQL Server permite usar Azure AD la autenticación integrada, SQL Server y la autenticación de Windows. Cada tipo de autenticación tiene diferentes niveles de seguridad asociados.  Es importante comprender qué información y qué derechos se comparten con los usuarios que usan la aplicación. El ejemplo principal de este artículo es SQL Server, sin embargo, los principios se aplican a todos los tipos de conexiones.

### <a name="azure-ad-integrated"></a>Azure AD integrado

Se trata de un tipo de conexión seguro.  Por ejemplo, SharePoint usa este tipo de autenticación.  SQL Server también permite este tipo de autenticación.  Al conectarse, el servicio de Azure AD identifica a SharePoint por separado en su nombre.  No es necesario proporcionar un nombre de usuario o una contraseña.  Como autor, puede crear y trabajar con el origen de datos con sus credenciales.  Al publicar la aplicación y el usuario de la aplicación inicia sesión, lo hacen con sus credenciales. Si los datos están protegidos correctamente en un back-end, los usuarios solo pueden ver lo que están autorizados para verlos en función de sus credenciales.   Este tipo de seguridad permite cambiar los derechos de usuarios específicos de la aplicación en el origen de datos back-end una vez publicada la aplicación.  Por ejemplo, puede conceder acceso, denegar el acceso o restringir lo que un usuario o un conjunto de usuarios pueden ver en el origen de datos back-end.

### <a name="open-standard-authorization-oauth"></a>Autorización de Open-Standard (OAuth)

Este tipo de conexión también es seguro.  Por ejemplo, Twitter usa este tipo de autenticación.  Cuando se conecte, debe proporcionar su nombre de usuario y contraseña.  Como autor, puede crear y trabajar con el origen de datos con sus credenciales.  Al publicar la aplicación y el usuario de la aplicación inicia sesión, también deben proporcionar sus credenciales.  Por lo tanto, este tipo de conexión es seguro, ya que los usuarios deben usar sus propias credenciales para tener acceso al servicio de origen de datos. 

### <a name="sql-user-name-and-password-authentication"></a>Autenticación de nombre de usuario y contraseña de SQL

Este tipo de conexión no es muy seguro porque no se basa en la autenticación de usuario final.  SQL Server también permite este tipo de autenticación.  En SQL Server este tipo de autenticación se denomina **SQL Server autenticación**.  Muchos otros orígenes de datos de base de datos ofrecen una funcionalidad similar.  Al publicar la aplicación, no es necesario que los usuarios proporcionen un nombre de usuario y una contraseña únicos.  Están usando el nombre de usuario y la contraseña que se proporcionan al crear la aplicación.  La autenticación de la conexión con el origen de datos se **comparte implícitamente** con los usuarios.  Una vez publicada la aplicación, la conexión también se publica y está disponible para los usuarios.  Los usuarios finales también pueden crear aplicaciones con cualquier conexión mediante SQL Server autenticación que se comparta con ellas.  Los usuarios no pueden ver el nombre de usuario de la contraseña, pero la conexión estará disponible.  Existen escenarios válidos para este tipo de conexión.  Por ejemplo, si tiene una base de datos de solo lectura que está disponible para todos los usuarios de la empresa, este tipo de conexión puede ser válido. 

### <a name="windows-authentication"></a>Autenticación de Windows

Este tipo de conexión no es muy seguro porque no se basa en la autenticación de usuario final. Use la autenticación de Windows cuando necesite conectarse a un origen **de datos local**. Un ejemplo de este tipo de conexión es a un servidor local que tiene una SQL Server. La conexión debe pasar a través de una puerta de enlace. Dado que pasa a través de una puerta de enlace, el conector tiene acceso a todos los datos de ese origen de datos. Como resultado, cualquier información a la que se pueda tener acceso con las credenciales de Windows que suministre está disponible para el conector. Una vez publicada la aplicación, la conexión también se publica y está disponible para los usuarios.  Esto significa que los usuarios finales también pueden crear aplicaciones con esta misma conexión y acceder a los datos de esa máquina. Las conexiones al origen de datos también se **comparten implícitamente** con los usuarios con los que se comparte la aplicación. Este tipo de conexión puede ser válido cuando el origen de datos solo reside en un servidor local y los datos de ese origen se pueden compartir libremente.
