---
title: 'Característica en vista previa: uso de Azure Cosmos DB para el proveedor de datos de la API de SQL con Common Data Service para aplicaciones | Microsoft Docs'
description: Obtenga información sobre cómo configurar Azure Cosmos DB para que el proveedor de datos de la API de SQL la use con entidades virtuales.
keywords: API de SQL
ms.date: 06/27/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
ms.openlocfilehash: fa45376dff85205a0dfbf28334c678293528d00e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711522"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>Característica en vista previa: requisitos del proveedor de datos de la API de SQL de Azure Cosmos DB

En este tema se describen los requisitos de Azure Cosmos DB para el proveedor de datos de la API de SQL, además de cómo configurar y recomendar procedimientos recomendados al usar Azure Cosmos DB para el proveedor de datos de la API de SQL con entidades virtuales. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>¿Qué es Azure Cosmos DB?

Azure Cosmos DB es un servicio de base de datos con varios modelos y distribución global de Microsoft para aplicaciones críticas. Proporciona un gran número de funcionalidades de consulta SQL conocidas con latencias bajas coherentes sobre datos JSON sin esquemas. Más información: [Introducción a Azure Cosmos DB: API de SQL](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>Requisitos

- Suscripción de Azure que incluye Azure Cosmos DB.
- Una colección de la API de SQL de Azure Cosmos DB.
- El tipo de base de datos Azure Cosmos DB debe ser SQL. 

## <a name="data-type-mapping"></a>Asignación de tipos de datos

Imagine que tiene un documento de Azure Cosmos DB en una colección llamada *Pedidos* con la siguiente estructura JSON.

![JSON de ejemplo para el documento de la API de SQL.](media/documentdbexample.png)

En esta tabla se indican las asignaciones de tipos de datos para el documento de la API de SQL en la colección *Pedidos* con Common Data Service para aplicaciones.

|Datos de la API de SQL|CDS para aplicaciones|
|--|--|
|`id`|Clave principal|
|`name`|Una línea de texto|
|`quantity`|Número entero|
|`orderid`|Una línea de texto|
|`ordertype`|Conjunto de opciones|
|`amount`|Número decimal o moneda|
|`delivered`|Dos opciones|
|`datetimeoffset`|Fecha y hora|

> [!NOTE]
> - La API de SQL genera los atributos con un guion bajo (_) como prefijo.
> - Los atributos configurados como opcionales en el documento de la API de SQL y asignados en CDS para aplicaciones como **Requerido por la empresa** darán lugar a un error de tiempo de ejecución.
> - Los valores de atributo de identificador deben ser GUID.
> - Para obtener más información sobre cómo usar las fechas en la API de SQL, consulte [Working with Dates in Azure Cosmos DB](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/) (Trabajo con fechas en Azure Cosmos DB).

## <a name="supported-sql-query-filtering"></a>Filtrado de consultas de SQL admitido

El filtrado de consultas de SQL admite los siguientes operadores. 

- Operadores de comparación: `<`,`>`,`<=`, `>=` y `!=`
- Operadores lógicos: `and` y `or` 
- Operadores establecidos: `in` y `not in`
- Operadores de cadena: `like`, `contains`, b`egins with` y `ends with`

> [!NOTE]
> El uso del operador like se traduce a los operadores `contains`/`begins with`/`ends with` equivalentes. La API de SQL no admite argumentos de patrón como se describe en el tema [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql). Azure Cosmos DB para el proveedor de datos de la API de SQL puede traducir el caso especial único `Like('[aA]%')` a `BeginsWith('a')` O `BeginsWith('A')`. Tenga en cuenta que la comparación de cadena en la API de SQL distingue mayúsculas de minúsculas.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>Agregar un origen de datos mediante Azure Cosmos DB para el proveedor de datos de la API de SQL

1. Vaya a [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview), seleccione **OBTENERLA AHORA** y siga las instrucciones para agregar la aplicación a su entorno mediante v9x o posterior.
2. Una vez instalada la solución, inicie sesión en el entorno y vaya a **Configuración** > **Administración** > **Orígenes de datos de entidades virtuales**.
3. En la barra de herramientas Acciones, seleccione **NUEVO** y, en el cuadro de diálogo **Seleccionar proveedor de datos**, seleccione **Azure Cosmos DB para el proveedor de datos de la API de SQL** y, a continuación, **Aceptar**.
![Seleccione Azure Cosmos DB para el proveedor de datos de la API de SQL.](media/createdatasource.png)
1. Escriba la siguiente información y, a continuación, seleccione **GUARDAR Y CERRAR**.

    |Campo|Descripción|
    |--|--|
    |**Nombre**|Escriba un nombre que describa el origen de datos.|
    |**Nombre de la colección**|El identificador de la colección de bases de datos Azure Cosmos DB en las que se incluyen los datos que desea que aparezcan en una entidad virtual.  |
    |**Clave de autorización**|La clave principal o secundaria para la cuenta de Azure Cosmos DB. Puede encontrar la clave del portal de administración de Azure en la configuración **Claves** en su cuenta de Azure Cosmos DB.|
    |**Uri**|El URI del grupo de recursos donde se encuentra la colección de Azure Cosmos DB. El URI se forma de manera similar a `https://contoso/documents.azure.com:443`. Puede encontrar el URI del portal de administración de Azure en la configuración **Claves** en la cuenta de Azure Cosmos DB. |
    |**Tiempo de espera en segundos**|Escriba el número de segundos que se esperará una respuesta del servicio de Azure Cosmos DB antes de que se agote el tiempo de espera de solicitud de datos. Por ejemplo, escriba 30 para esperar un máximo de treinta segundos antes de que se agote el tiempo de espera. El tiempo de espera predeterminado es de 120 segundos.|

    ![Cree el origen de datos mediante el proveedor de datos de la API de SQL.](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>Procedimientos recomendados y limitaciones

- Tenga en cuenta lo siguiente al usar Azure Cosmos DB como origen de datos:
   - Cada origen de datos de Azure Cosmos DB puede asociarse únicamente a una sola entidad virtual.
   - Puede conectar varios orígenes de datos a la misma colección en Azure Cosmos DB.
- No puede segmentar los datos en una colección por entidad.
- Las bases de datos Azure Cosmos DB no requieren un esquema. No obstante, los datos de Azure Cosmos DB deben estructurarse mediante un esquema predecible. 
- Aunque Azure Cosmos DB para el proveedor de datos de la API de SQL implementa la traducción de consulta de los operadores de proyección, filtrado y ordenación, no admite las operaciones de combinación.
- Solo puede filtrar por una sola columna con la API de SQL.

## <a name="see-also"></a>Vea también

[Crear y editar entidades virtuales que contienen datos de un origen de datos externo](create-edit-virtual-entities.md)
