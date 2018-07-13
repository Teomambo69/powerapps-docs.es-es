---
title: Conexión a Oracle Database | Microsoft Docs
description: Aprenda a conectarse a Oracle Database y a utilizarlo para compilar aplicaciones en PowerApps.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/14/2017
ms.author: lanced
ms.openlocfilehash: 6eea40490b7a41ae95445135fabbc33801386c4d
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021996"
---
# <a name="connect-to-an-oracle-database-from-powerapps"></a>Conectarse a una instancia de Oracle Database desde PowerApps
Enumere tablas y cree, lea, actualice y elimine filas de una tabla en una instancia de Oracle Database después de crear una conexión y compilar una aplicación en PowerApps. La conexión de Oracle Database admite la delegación completa del filtrado, ordenación y otras funciones, pero no los desencadenadores ni los procedimientos almacenados.

## <a name="prerequisites"></a>Requisitos previos
* Oracle 9 y versiones posteriores
* Software cliente de Oracle 8.1.7 y versiones posteriores
* Instalación de una puerta de enlace de datos local
* Instalación del SDK de cliente de Oracle

### <a name="install-an-on-premises-data-gateway"></a>Instalar una puerta de enlace de datos local
Para instalar una puerta de enlace, siga los pasos de [este tutorial](../gateway-management.md).

Una puerta de enlace de datos local actúa como un puente, proporcionando una transferencia de datos rápida y segura entre los datos locales (los datos que no se encuentran en la nube) y los servicios de Power BI, Microsoft Flow, Logic Apps y PowerApps. Puede usar la misma puerta de enlace con varios servicios y orígenes de datos. Para más información, consulte [Puertas de enlace](../gateway-reference.md).

### <a name="install-oracle-client"></a>Instalar el cliente de Oracle
En el mismo equipo que la puerta de enlace de datos local, instale [64-bit ODAC 12c Release 4 (12.1.0.2.4) for Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html). De lo contrario, aparecerá un error si intenta crear o usar la conexión, como se describe en la lista de problemas conocidos.

## <a name="create-an-app-from-a-table-in-an-oracle-database"></a>Crear una aplicación desde una tabla de una instancia de Oracle Database
1. En PowerApps Studio, pulse o haga clic en **Nuevo** en el menú **Archivo** (cerca del borde izquierdo).
   
   ![Nueva opción](./media/connection-oracledb/new-app.png)
2. En **Comenzar con los datos**, haga clic o pulse la flecha.
   
      Aparece una lista de conexiones que ya tiene.
3. Pulse o haga clic en **Nueva conexión**.
   
   ![Nueva conexión](./media/connection-oracledb/new-connection.png)
4. En la lista de conexiones, haga clic o pulse en **Oracle Database**.
   
   ![Base de datos nueva](./media/connection-oracledb/oracle-db.png)
5. Especifique el nombre de un servidor de Oracle, un nombre de usuario y una contraseña.
   
    Especifique un servidor en este formato si se requiere un SID:<br>
    *NombreServidor*/*SID*
   
   ![Parámetros de conexión](./media/connection-oracledb/connection-params.png)
6. Pulse o haga clic en la puerta de enlace que desea usar o instale una.
   
    Si la puerta de enlace no aparece después de instalarla, haga clic en **Actualizar lista de puertas de enlace**.
   
   ![Nueva puerta de enlace](./media/connection-oracledb/choose-gateway.png)
7. Pulse o haga clic en **Crear** para crear la conexión.
   
   ![Nuevo](./media/connection-oracledb/create-button.png)
8. Haga clic o pulse en el conjunto de datos **predeterminado**.
   
   ![Nuevo](./media/connection-oracledb/choose-dataset.png)
9. En la lista de tablas, haga clic o pulse en la tabla que desea utilizar.
   
   ![Nuevo](./media/connection-oracledb/choose-table.png)
10. Haga clic en **Conectar** para crear la aplicación.
    
    ![Nuevo](./media/connection-oracledb/connect-button.png)

PowerApps crea una aplicación que tiene tres pantallas y muestra los datos de la tabla que ha seleccionado:

* **BrowseScreen1**, que enumera todas las entradas de la tabla.
* **DetailScreen1**, que proporciona más información acerca de una sola entrada.
* **EditScreen1**, en la que los usuarios pueden actualizar o crear una entrada.

![Nuevo](./media/connection-oracledb/afd-app.png)

## <a name="next-steps"></a>Pasos siguientes
* Para guardar la aplicación que acaba de generar, presione Ctrl-S.
* Para personalizar la pantalla **BrowseScreen1** (que aparece de forma predeterminada), consulte [Personalizar un diseño](../customize-layout-sharepoint.md).
* Para personalizar **DetailsScreen1** o **EditScreen1**, consulte [Personalizar un formulario](../customize-forms-sharepoint.md).

## <a name="known-issues-tips-and-troubleshooting"></a>Problemas conocidos, sugerencias y solución de problemas
1. No se puede acceder a la puerta de enlace.
   
    Este error aparece si la puerta de enlace de datos local no se puede conectar a la nube. Para comprobar el estado de la puerta de enlace, inicie sesión en powerapps.microsoft.com, haga clic o pulse en **Puertas de enlace**y, a continuación, haga clic o pulse en la puerta de enlace que desea utilizar.
   
    Asegúrese de que la puerta de enlace se está ejecutando y puede conectarse a Internet. Evite la instalación de la puerta de enlace en un equipo que pueda estar apagado o suspendido. Intente también reiniciar el servicio de puerta de enlace de datos local (PBIEgwService).
2. System.Data.OracleClient requiere la versión 8.1.7 o posterior del software cliente de Oracle.
   
    Este error aparece si el SDK de cliente de Oracle no está instalado en el mismo equipo que la puerta de enlace de datos local. Para resolver este problema, [instale el proveedor oficial](https://go.microsoft.com/fwlink/p/?LinkID=272376).
3. La tabla '[Tablename]' no define ninguna columna de clave.
   
    Este error aparece si se está conectando a una tabla que no tiene una clave principal que necesita la conexión de Oracle Database.
4. En el momento de escribir este artículo, no se admiten los procedimientos almacenados, las tablas con claves compuestas ni los tipos de objeto anidados en tablas.

