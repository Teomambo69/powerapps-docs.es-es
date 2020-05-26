---
title: Usar SQL para consultar datos (Common Data Service) | Microsoft Docs
description: Aprenda a consultar datos de entidad Common Data Service utilizando SQL.
ms.custom: ''
ms.date: 05/05/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b464b1cd4a64e9f33919567da15d10d7e50d9dd2
ms.sourcegitcommit: 0ede8e3bc795e151aa94ffcbce15cff7a949c57a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "3335344"
---
# <a name="use-sql-to-query-data-preview"></a>Usar SQL para consultar datos (Vista previa)

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Una conexión de datos SQL está disponible en el punto de conexión Common Data Service. La conexión SQL proporciona acceso de solo lectura a los datos de entidad del entorno de destino Common Data Service. Esto le permite escribir y ejecutar consultas SQL en la tabla de datos de la entidad. Las columnas de la tabla proporcionan los datos de atributos de la entidad. No se han proporcionado vistas personalizadas de los datos.

> [!IMPORTANT]
> - Esta es una característica en vista previa y no está disponible en todas las regiones.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

## <a name="applications-support"></a>Soporte de aplicaciones

Puede usar la opción **Analizar en Power BI** (**Datos** > **Entidades** > **Analizar en Power BI**) en Power Apps (https://make.powerapps.com) para usar la función de conexión SQL para analizar datos en Power BI Desktop. Más información: [Ver datos de entidad en Power BI Desktop](/powerapps/maker/common-data-service/view-entity-data-power-bi)

> [!NOTE]
> Si no tiene la opción **Analizar en Power BI** en su entorno de Power Apps, aún no tiene acceso a la característica de conexión de SQL.

También puedes usar [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) (SSMS) versión 18.4 o posterior con la conexión SQL del punto de conexión Common Data Service. A continuación se proporcionan ejemplos de uso de SSMS con la conexión de datos SQL.

![Tabla expandida de cuentas](media/ssms-table-expanded.PNG)

## <a name="security-and-authentication"></a>Seguridad y autenticación

El punto de conexión Common Data Service de la conexión SQL usa el modelo de seguridad de Common Data Service para acceso a datos. Se pueden obtener datos para todas las entidades a las que un usuario tiene acceso en Common Data Service.

Sólo se admite la autenticación Azure Active Directory. La autenticación de SQL y la autenticación de Windows no son compatibles. A continuación se muestra un ejemplo de cómo iniciar sesión en la conexión SQL en SSMS. Observe que el nombre del servidor es la dirección URL de la organización seguida de una coma y el valor del puerto de 5558.

![Diálogo de conexión](media/ssms-connect-dialog.PNG)

## <a name="example-entity-data-queries"></a>Ejemplos de consultas de datos de entidad

A continuación hay un par de consultas de ejemplo compuestas en SSMS. La primera imagen muestra una consulta simple usando alias y ordenamiento de resultados.

```tsql
select top 5 a.name as [VIP customer], a.address1_postalcode as [ZIP code] from account a order by a.address1_postalcode desc
```

![Consulta simple usando alias y ordenando](media/ssms-simple-query.PNG)

La siguiente consulta muestra un JOIN.

```tsql
select name, fullname from account a inner join contact c on a.primarycontactid = c.contactid
```

![Otra consulta usando un JOIN](media/ssms-join-query.PNG)

## <a name="supported-operations-and-data-types"></a>Tipos de datos y operaciones compatibles

La lista de operaciones SQL compatibles incluyen:

- Operaciones por lotes
- SELECCIONAR
- Funciones de agregación (es decir, funciones Count() y Max())
- UNION y JOIN
- Filtrado

Cualquier operación que intente modificar datos (es decir, INSERTAR, ACTUALIZAR) no funcionará, ya que esta es una conexión de datos SQL de solo lectura. los conjuntos de opciones de Common Data Service se representan como \<OptionSet\>Nombre y \<OptionSet\>Etiqueta en un conjunto de resultados.

Los siguientes tipos de datos de Common Data Service no son compatibles con la conexión SQL: binario, imagen, ntext, sql_variant, varbinary, virtual, HierarchyId, propiedad administrada, archivo, xml, partylist, marca de tiempo.

### <a name="see-also"></a>Vea también

[Usar FetchXML para crear una consulta](use-fetchxml-construct-query.md)
