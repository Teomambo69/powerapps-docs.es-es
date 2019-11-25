---
title: 'Característica de vista previa: Utilizar Azure Cosmos DB para el proveedor de datos de la API de SQL con Common Data Service | MicrosoftDocs'
description: Aprenda a configurar el proveedor de datos de Azure Cosmos DB para el proveedor de datos de la API de SQL para usar con entidades virtuales.
keywords: API SQL
ms.date: 02/15/2019
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3e9594ada54fb89f77298a4077281dcedbb8c656
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705687"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>Característica de vista previa: Requisitos del proveedor de datos de Azure Cosmos DB para la API SQL

En este tema se describen los requisitos para el proveedor de datos de Azure Cosmos DB para la API de SQL y también cómo configurar y las prácticas recomendadas cuando se usa el proveedor de datos de Azure Cosmos DB para la API de SQL con entidades virtuales. 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>¿Qué es Azure Cosmos DB?

Azure Cosmos DB es el servicio de la base de datos de varios modelos global distribuido de Microsoft para aplicaciones críticas. Proporciona capacidades de consulta SQL enriquecidas y familiares con latencias bajas homogéneas en datos JSON sin esquema. Más información: [Introducción a Azure Cosmos DB: API SQL](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>Requisitos

- Suscripción de Azure que incluye Azure Cosmos DB.
- Una colección de la API SQL de Azure Cosmos DB.
- El tipo de base de datos Azure Cosmos DB debe ser SQL. 

## <a name="data-type-mapping"></a>Asignaciones de tipos de datos

Supongamos que tiene un documento Azure Cosmos DB en una colección denominada *pedidos* que tiene la siguiente estructura JSON.

![JSON de ejemplo para documento de API de SQL](media/documentdbexample.png)

Esta tabla indica las asignaciones de tipo de datos para el documento de la API SQL en la colección *pedidos* con Common Data Service.

|Datos de la API de SQL|Common Data Service|
|--|--|
|`id`|Clave principal|
|`name`|Línea de texto única|
|`quantity`|Número entero|
|`orderid`|Línea de texto única|
|`ordertype`|Conjunto de opciones|
|`amount`|Número decimal o divisa|
|`delivered`|Dos opciones|
|`datetimeoffset`|Fecha y hora|

> [!NOTE]
> - Los atributos con un prefijo de subrayado (_) se generan mediante la API de SQL.
> - Los atributos que están configurados como opcionales en el documento de la API SQL y se asignan en Common Data Service como **necesario para la empresa** generarán un error de tiempo de ejecución.
> - los valores de atributo de identificador deben ser guids.
> - Para obtener más información sobre el uso de fechas en la API SQL, consulte [Trabajar con fechas en Azure Cosmos DB](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/).

## <a name="supported-sql-query-filtering"></a>Filtro de consultas SQL admitido

El filtro de consultas SQL admite los siguientes operadores. 

- Operadores de comparación:`<`,`>`,`<=`, `>=`,`!=`
- Operadores lógicos: `and`, `or` 
- Operadores de conjuntos: `in`, `not in`
- Operadores de cadena: `like`, `contains`, `begins with`, `ends with`

> [!NOTE]
> El uso del operador like se traduce en el equivalente a los operadores `contains`/`begins with`/`ends with`. La API de SQL no admite argumentos de patrón como se explica en el tema [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql). El proveedor de datos de Azure Cosmos DB para la API de SQL puede traducir el caso único especial `Like('[aA]%')` a `BeginsWith('a')` O `BeginsWith('A')`. Tenga en cuenta que la comparación de cadenas en la API de SQL distingue entre mayúsculas y minúsculas.

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>Añadir un origen de datos con Azure Cosmos DB para el proveedor de datos API SQL

1. Vaya a [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview), seleccione **OBTENERLO AHORA** y siga las instrucciones para agregar la aplicación a su entorno usando v9x o una versión posterior.
2. Después de que la solución esté instalada, inicie sesión en en entorno y vaya a **Configuración** > **Administración** > **Orígenes de datos de entidades virtuales**.
3. En la barra de herramientas Acciones, seleccione **NUEVO** y, en el cuadro de diálogo **Seleccionar proveedor de datos**, seleccione **Azure Cosmos DB para proveedor de datos API SQL** y seleccione **Aceptar**.
![Seleccione Azure Cosmos DB para el proveedor de datos de la API de SQL.](media/createdatasource.png)
1. Especifique la siguiente información y luego seleccione **GUARDAR Y CERRAR**.

    |Campo|Descripción|
    |--|--|
    |**Nombre**|Escriba un nombre para describir el origen de datos.|
    |**Nombre de recopilación**|El nombre de la *base de datos* de Azure Cosmos DB que contiene la colección que desea que se muestre en una entidad virtual.  |
    |**Clave de autorización**|La clave principal o secundaria para la cuenta de Azure Cosmos DB. Puede encontrar la clave en el portal de administración de Azure en la opción **claves** en su cuenta de Azure Cosmos DB.|
    |**Uri**|El URI del grupo de recursos donde se encuentra la colección de Azure Cosmos DB. La dirección URI se forma como `https://contoso/documents.azure.com:443`. Puede encontrar el URI del portal de administración de Azure en la opción **claves** de la cuenta de Azure Cosmos DB. |
    |**Tiempo de espera en segundos**|Escriba la cantidad de segundos que se debe esperar a una respuesta del servicio Azure Cosmos DB antes de agotar el tiempo de espera de una solicitud de datos. Por ejemplo, escriba 30 para esperar un máximo de treinta segundos antes de que se agote el tiempo de espera. El tiempo de espera predeterminado es de 120 segundos.|

    > [!div class="mx-imgBorder"] 
    > ![Crear el origen de datos con el proveedor de datos de la API de SQL.](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>Recomendaciones y limitaciones

- Tenga en cuenta lo siguiente cuando utilice Azure Cosmos DB como origen de datos:
   - Cada origen de datos Azure Cosmos DB solo se puede asociar a una sola entidad virtual.
   - Puede conectar varios orígenes de datos a la misma colección en el Azure Cosmos DB.
- No se puede segmentar los datos de una colección por entidad.
- Las bases de datos Azure Cosmos DB no requieren un esquema; sin embargo los datos de la Azure Cosmos DB se deben estructurar mediante un esquema predecible. 
- Aunque el proveedor de datos de Azure Cosmos DB para la API de SQL implementa la traducción de consultas de operadores de proyección, filtro y ordenación, no admite las operaciones join.
- Solo puede filtrar por una sola columna con la API de SQL.

## <a name="see-also"></a>Vea también

[Crear y editar entidades virtuales que contienen datos desde un origen de datos externo](create-edit-virtual-entities.md)
