---
title: Introducción a la conexión de SQL Server | Microsoft Docs
description: Instrucciones paso a paso sobre cómo conectarse a Azure SQL o una base de datos de SQL Server local
author: lancedMicrosoft
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.openlocfilehash: e11521219fcd368801a6e943f45dbc713309ec36
ms.sourcegitcommit: 7354a0c61578fcc0b9965bf557b9d7c553c73e96
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34803429"
---
# <a name="connect-to-sql-server-from-powerapps"></a>Conexión a SQL Server desde PowerApps
![Icono de SQL Server](./media/connection-azure-sqldatabase/sqlicon.png)

Conéctese a SQL Server, bien en Azure o en una base de datos local, para poder mostrar la información del servidor en PowerApps.

## <a name="prerequisites"></a>Requisitos previos

* [Regístrese](../../signup-for-powerapps.md) en PowerApps y, luego, [inicie sesión](http://web.powerapps.com) con las mismas credenciales que usó para registrase.
* Recopile la siguiente información para una base de datos que contenga al menos una tabla con una clave principal:
  
  * el nombre de la base de datos
  * el nombre del servidor donde se aloja la base de datos
  * un nombre de usuario válido y una contraseña para conectarse a la base de datos
  * el tipo de autenticación necesaria para conectarse a la base de datos
    
    Si no tiene esta información, solicítela al administrador de la base de datos que desea usar.
* Para una base de datos local, identifique una [puerta de enlace de datos](../gateway-management.md) que se haya compartido con usted (o cree una).
  
    > [!NOTE]
> Las puertas de enlace y las conexiones locales solo se pueden crear y usar en el [entorno predeterminado](../working-with-environments.md) del usuario.

## <a name="generate-an-app-automatically"></a>Generar una aplicación automáticamente
1. En PowerApps Studio, pulse o haga clic en **Nuevo** en el menú **Archivo** (en el borde izquierdo).
   
    ![Opción Nuevo en el menú Archivo](./media/connection-azure-sqldatabase/file-new.png)
2. En **Comenzar con los datos**, pulse o haga clic en la flecha derecha al final de la fila de conectores.
3. Si ya tiene una conexión a la base de datos que desea usar, pulse o haga clic en ella y, después, vaya al paso 7 de este procedimiento.
4. Pulse o haga clic en **Nueva conexión** y, después, pulse o haga clic en **SQL Server**.
   
    ![Agregar conexión de SQL Server](./media/connection-azure-sqldatabase/add-sql-connection.png)
5. Realice uno de estos pasos:
   
   * Especifique **Conectar directamente (servicios en la nube)** y, después, escriba o pegue el nombre del servidor, el nombre de la base de datos, el nombre de usuario y la contraseña de la base de datos que desea usar.
     
       ![Conexión a una base de datos en Azure](./media/connection-azure-sqldatabase/connect-azure.png)
   * Especifique **Conectar mediante una puerta de enlace de datos local**, escriba o pegue el nombre del servidor, el nombre de la base de datos, el nombre de usuario y la contraseña de la base de datos que desea usar, y especifique el tipo de autenticación y la puerta de enlace.
     
       ![Conexión a un recurso local](./media/connection-azure-sqldatabase/connect-onprem.png)
     
       > [!NOTE]
> Si no tiene una puerta de enlace, [instálela](../gateway-reference.md)y, después, haga clic o pulse **Actualizar lista de puertas de enlace**.
6. Pulse o haga clic en **Conectar**.
7. Pulse o haga clic en una opción en **Elegir un conjunto de datos**, pulse o haga clic en una opción en **Elegir una tabla** y, después, pulse o haga clic en **Conectar**.
   
    PowerApps crea una aplicación que muestra los datos en tres pantallas. La heurística sugiere el tipo de datos que se van a mostrar, pero tendrá que personalizar la interfaz de usuario para adecuarla a sus necesidades.
8. Personalice la aplicación mediante el uso de técnicas que son similares a las que se describe en [Create an app from Excel](../get-started-create-from-data.md) (Creación de una aplicación de Excel), a partir de cambiar el diseño de la aplicación.

## <a name="build-an-app-from-scratch"></a>Crear una aplicación desde cero
1. Inicie sesión en [powerapps.com](https://web.powerapps.com) con la misma cuenta que usó para suscribirse a PowerApps.
2. En la barra de navegación izquierda, pulse o haga clic en **Conexiones**:  
   
    ![Administrar conexiones](./media/connection-azure-sqldatabase/manage-connections.png)
3. Cerca de la esquina superior derecha, pulse o haga clic en **Nueva conexión** y, después, pulse o haga clic en **SQL Server**.
4. Realice uno de estos pasos:
   
   * Especifique **Conectar directamente (servicios en la nube)** y, después, escriba o pegue el nombre del servidor, el nombre de la base de datos, el nombre de usuario y la contraseña de la base de datos que desea usar.
     
       ![Conexión a una base de datos en Azure](./media/connection-azure-sqldatabase/connect-azure-portal.png)
   * Especifique **Conectar mediante una puerta de enlace de datos local**, escriba o pegue el nombre del servidor, el nombre de la base de datos, el nombre de usuario y la contraseña de la base de datos que desea usar, y especifique el tipo de autenticación y la puerta de enlace.
     
       ![Conexión a una base de datos en Azure](./media/connection-azure-sqldatabase/connect-onprem-portal.png)
     
       > [!NOTE]
> Si no tiene una puerta de enlace, [instálela](../gateway-reference.md)y, después, haga clic o pulse el icono del reloj para actualizar la lista.
5. Pulse o haga clic en **Crear** para crear la conexión.
6. Cree una aplicación mediante técnicas que son similares a las que describen en [Crear una aplicación desde cero](../get-started-create-from-blank.md).

## <a name="update-an-existing-app"></a>Actualizar una aplicación existente
1. En PowerApps Studio, abra la aplicación que desea actualizar.
2. Pulse o haga clic en **Orígenes de datos** en la pestaña **Vista** de la cinta de opciones.
3. En el panel de la derecha, pulse o haga clic en **Agregar origen de datos**.
   
    ![Agregar origen de datos](./media/connection-azure-sqldatabase/add-data-source.png)
4. Pulse o haga clic en **Nueva conexión**, pulse o haga clic en **SQL Server** y, finalmente, pulse o haga clic en **Conectar**.
5. Realice uno de estos pasos:
   
   * Especifique **Conectar directamente (servicios en la nube)** y, después, escriba o pegue el nombre del servidor, el nombre de la base de datos, el nombre de usuario y la contraseña de la base de datos que desea usar.
     
       ![Conexión a una base de datos en Azure](./media/connection-azure-sqldatabase/connect-azure-fromblank.png)
   * Especifique **Conectar mediante una puerta de enlace de datos local**, escriba o pegue el nombre del servidor, el nombre de la base de datos, el nombre de usuario y la contraseña de la base de datos que desea usar, y especifique el tipo de autenticación y la puerta de enlace.
     
       ![Conexión a una base de datos en Azure](./media/connection-azure-sqldatabase/connect-onprem-fromblank.png)
     
       > [!NOTE]
> Si no tiene una puerta de enlace, [instálela](../gateway-reference.md)y, después, haga clic o pulse el icono circular para actualizar la lista.
6. Pulse o haga clic en **Conectar**.
7. En **Elegir un conjunto de datos**, pulse o haga clic en opción.
8. En **Elegir una tabla**, seleccione una o varias casillas y, después, pulse o haga clic en **Conectar**.

## <a name="next-steps"></a>Pasos siguientes
* Más información sobre cómo [mostrar datos a partir de un origen de datos](../add-gallery.md).
* Más información sobre cómo [ver detalles y crear o actualizar registros](../add-form.md).
* Consulte otros tipos de [orígenes de datos](../connections-list.md) a los que se puede conectar.  
* [Comprenda las tablas y los registros](../working-with-tables.md) con orígenes de datos tabulares.

<!--NotAvailableYet
## View the available functions ##
This connection includes the following functions:

| Function Name |  Description |
| --- | --- |
|[GetItems](connection-azure-sqldatabase.md#getitems) | Retrieves rows from a SQL table |
|[PostItem](connection-azure-sqldatabase.md#postitem) | Inserts a new row into a SQL table |
|[GetItem](connection-azure-sqldatabase.md#getitem) | Retrieves a single row from a SQL table |
|[DeleteItem](connection-azure-sqldatabase.md#deleteitem) | Deletes a row from a SQL table |
|[PatchItem](connection-azure-sqldatabase.md#patchitem) | Updates an existing row in a SQL table |
|[GetTables](connection-azure-sqldatabase.md#gettables) | Retrieves tables from a SQL database |

### GetItems
Get rows: Retrieves rows from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|$skip|integer|no|Number of entries to skip (default = 0)|
|$top|integer|no|Maximum number of entries to retrieve (default = 256)|
|$filter|string|no|An ODATA filter query to restrict the number of entries|
|$orderby|string|no|An ODATA orderBy query for specifying the order of entries|

### PostItem
Insert row: Inserts a new row into a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|item| |yes|Row to insert into the specified table in SQL|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | |


### GetItem
Get row: Retrieves a single row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to retrieve|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | |


### DeleteItem
Delete row: Deletes a row from a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to delete|

#### Output properties
None.

### PatchItem
Update row: Updates an existing row in a SQL table

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|table|string|yes|Name of SQL table|
|id|string|yes|Unique identifier of the row to update|
|item| |yes|Row with updated values|

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|ItemInternalId|string|No | &nbsp; |


### GetTables
Get tables: Retrieves tables from a SQL database

#### Input properties
None.

#### Output properties

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|value|array|No | Can output the Name and DisplayName properties |

### ExecuteProcedure
Execute stored procedure: Executes a stored procedure in SQL

#### Input properties

| Name| Data Type|Required|Description|
| ---|---|---|---|
|procedure|string|yes|Procedure name|
|parameters| |yes|Input parameters|

#### Output properties
Result of the stored procedure execution.

| Property Name | Data Type | Required | Description |
|---|---|---|---|
|OutputParameters|object|No | Output parameter values |
|ReturnCode|integer|No | Return code of a procedure |
|ResultSets|object|No | Result sets|

-->
