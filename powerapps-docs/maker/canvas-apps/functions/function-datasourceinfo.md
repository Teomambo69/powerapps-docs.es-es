---
title: Función DataSourceInfo | Microsoft Docs
description: Información de referencia sobre la función DataSourceInfo de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/11/2015
ms.author: gregli
ms.openlocfilehash: 696da621bfc14cd2dfd36f4a03d7e1117e07e670
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022249"
---
# <a name="datasourceinfo-function-in-powerapps"></a>Función DataSourceInfo en PowerApps
Proporciona información sobre un [origen de datos](../working-with-data-sources.md).

## <a name="overview"></a>Información general
Los orígenes de datos pueden proporcionar una gran cantidad de información para optimizar la experiencia del usuario.

Puede usar información de nivel de [columna](../working-with-tables.md#columns) para validar entradas de usuario y proporcionar una respuesta inmediata al usuario antes de usar la función **[Revisión](function-patch.md)**. La función **[Validate](function-validate.md)**  usa esta misma información.

Puede usar información en el nivel de origen de datos para, por ejemplo, deshabilitar u ocultar los botones **Editar** y **Nuevo** de los usuarios que no tienen permisos para editar y crear [registros](../working-with-tables.md#records).

Los orígenes de datos varían en la cantidad de información que proporcionan; incluso pueden no ofrecer ninguna.  Las [colecciones](../working-with-data-sources.md#collections) no proporcionan ninguna información. Si no se proporciona una parte de la información, se utilizará el valor predeterminado o se devolverá *en blanco*.

## <a name="description"></a>Descripción
### <a name="column-information"></a>Información de columna
Puede usar **DataSourceInfo** para obtener información sobre una columna concreta de un origen de datos:  

| Argumento de información | Tipo de resultado | Descripción |
| --- | --- | --- |
| **DataSourceInfo.DisplayName** |Cadena |Nombre para mostrar de la columna. Si no se ha definido ningún nombre para mostrar, devolverá el nombre de la columna. |
| **DataSourceInfo.MaxLength** |Número |Número máximo de caracteres que puede contener la columna. Solo se aplica a las columnas que contienen cadenas. Si no se configura un máximo, devuelve *en blanco*. |
| **DataSourceInfo.MaxValue** |Número |Valor numérico máximo que puede contener una columna. Solo se aplica a las columnas que contienen números. Si no se configura un máximo, devuelve *en blanco*. |
| **DataSourceInfo.MinValue** |Número |Valor numérico mínimo que puede contener una columna. Solo se aplica a las columnas que contienen números. Si no se configura un mínimo, devuelve *en blanco*. |
| **DataSourceInfo.Required** |Booleano |¿Es un valor requerido para esta columna? Si no se establece mediante el origen de datos devuelve **false**. |

El tercer argumento es el nombre de una columna como una cadena.  Por ejemplo, la columna **Teléfono** de la colección **Personas** se pasaría como **"Teléfono"** incluidas las comillas dobles.

### <a name="data-source-information"></a>Información de origen de datos
Puede usar **DataSourceInfo** para obtener información sobre un origen de datos como un todo:  

| Argumento de información | Tipo de resultado | Descripción |
| --- | --- | --- |
| **DataSourceInfo.AllowedValues** |Booleano |¿Qué tipos de permisos se les pueden conceder a los usuarios para este origen de datos? Si no se establecen mediante el origen de datos, se devuelve *en blanco*. |
| **DataSourceInfo.CreatePermission** |Booleano |¿Tiene permiso el usuario actual para crear registros en este origen de datos? Si no se establece mediante el origen de datos, devuelve **true**. |
| **DataSourceInfo.DeletePermission** |Booleano |¿Tiene permiso el usuario actual para eliminar registros en este origen de datos? Si no se establece mediante el origen de datos, devuelve **true**. |
| **DataSourceInfo.EditPermission** |Booleano |¿Tiene permiso el usuario actual para editar registros en este origen de datos? Si no se establece mediante el origen de datos, devuelve **true**. |
| **DataSourceInfo.ReadPermission** |Booleano |¿Tiene permiso el usuario actual para leer registros en este origen de datos? Si no se establece mediante el origen de datos, devuelve **true**. |

## <a name="syntax"></a>Sintaxis
**DataSourceInfo**( *DataSource*, *Information*, *ColumnName* )

* *DataSource*: requerido. El origen de datos que se va a usar.
* *Information*: requerido. El tipo de información que desea recuperar.
* *ColumnName*: opcional. Para la información en el nivel de columna, el nombre de columna como una cadena. La columna **Teléfono** se pasaría como **"Teléfono"** incluidas las comillas dobles. Para la información en el nivel de origen de datos, el argumento *ColumnName* no se puede usar.
  
    > [!NOTE]
  > En el caso de orígenes de datos de SharePoint y Excel que contengan nombres de columna con espacios, especifique cada uno de ellos como **"\_x0020\_"**. Por ejemplo, especifique **"Nombre de columna"** como **"Nombre_x0020_de_columna"**.

## <a name="examples"></a>Ejemplos
Los ejemplos de esta sección usan este origen de datos, denominado **IceCream**:

![](media/function-datasourceinfo/icecream.png)

El origen de datos también ha proporcionado esta información:

* El nombre para mostrar para **Quantity** es "Cantidad disponible".
* La longitud máxima de **Flavor** es de 30 caracteres.
* La columna **Flavor** debe contener un valor. La columna **Quantity** no se requiere.
* La **cantidad** mínima es 0.
* La **cantidad** máxima es 100.
* El usuario actual puede leer y editar los registros del origen de datos **IceCream**, pero no se pueden crear ni eliminar registros.

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DisplayName,&nbsp;"Quantity"&nbsp;)** |Devuelve el nombre para mostrar de la columna **Quantity** del origen de datos **IceCream**. |"Cantidad disponible" |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxLength,&nbsp;"Flavor"&nbsp;)** |Devuelve la longitud máxima de la cadena para la columna **Flavor** del origen de datos **IceCream**. |30 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Flavor"&nbsp;)** |¿Se requiere la columna **Flavor** del origen de datos **IceCream**? |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.Required,&nbsp;"Quantity"&nbsp;)** |¿Se requiere la columna **Quantity** del origen de datos **IceCream**? |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MaxValue,&nbsp;"Quantity"&nbsp;)** |Devuelve el valor numérico máximo de la columna **Quantity** del origen de datos **IceCream**. |100 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.MinValue,&nbsp;"Quantity"&nbsp;)** |Devuelve el valor numérico mínimo de la columna **Quantity** del origen de datos **IceCream**. |0 |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.ReadPermission)** |¿Puede leer el usuario actual los registros del origen de datos **IceCream**? |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.EditPermission)** |¿Puede editar el usuario actual los registros del origen de datos **IceCream**? |**true** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.CreatePermission)** |¿Puede crear el usuario actual los registros del origen de datos **IceCream**? |**false** |
| **DataSourceInfo(&nbsp;IceCream, DataSourceInfo.DeletePermission)** |¿Puede eliminar el usuario actual los registros del origen de datos **IceCream**? |**false** |

