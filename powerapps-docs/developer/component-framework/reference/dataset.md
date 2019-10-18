---
title: DataSet | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0202d51f-e9a9-4a2e-b3e9-0bfd7f6afb86
ms.openlocfilehash: 5e9408c81fc9587b9dec30f18fc68c3112ba6125
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345322"
---
# <a name="dataset"></a>DataSet

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="addcolumn"></a>addColumn ()

Agrega una columna a columnset

### <a name="remarks"></a>Sección

Este método acepta dos parámetros.

|Nombre|Tipo|Requerido|Descripción|
|------|-----|------|-----|
|Name|`string`|Sí|Nombre de columna que se va a agregar al conjunto de DataSet.|
|entityAlias|`string`|No| Alias de entidad para el que se debe agregar el nombre de columna.|

### <a name="columns"></a>Columnas

Conjunto de columnas disponibles en este conjunto de los

**Tipo**: [columna](column.md)[]

### <a name="error"></a>Error

Indica si se produjo un error en la recuperación de datos.

**Tipo**: `boolean`

### <a name="errormessage"></a>errorMessage

Mensaje de error asociado al último error encontrado, si procede.

**Tipo**: `string`

### <a name="filtering"></a>filtra

El filtrado de columnas para la consulta actual.

**Tipo**: [filtrado](filtering.md)

### <a name="linking"></a>unir

Define la información de la entidad vinculada.

**Tipo**: [vinculación](linking.md)

### <a name="loading"></a>cargarla

Indica si el conjunto de DataSet se está cargando o no.

**Tipo**: `boolean`

### <a name="paging"></a>buscapersona

Estado y acciones de paginación.

**Tipo**: [paginación](paging.md)

### <a name="records"></a>Informes

Asignación de identificadores al objeto de registro completo.

**Tipo**: [EntityRecord](entityrecord.md)

### <a name="sortedrecordids"></a>sortedRecordIds

Identificadores de los registros del conjunto de registros, ordenados por el resultado de la respuesta de la consulta.

**Tipo**: `string[]`

### <a name="sorting"></a>ordenación

El estado de ordenación de la consulta actual.

**Tipo**: [SortStatus](sortstatus.md)

## <a name="methods"></a>Modalidades

|Forma | Descripción | 
| ------------- |-------------|
|[clearSelectedRecordIds](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[getSelectedRecordIds](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[getTargetEntityType](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[getViewId](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[openDatasetItem](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[actualizaciones](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[setSelectedRecordIds](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 

## <a name="example"></a>Ejemplo

Para obtener más información sobre cómo implementar los métodos del conjunto de elementos, vea [DataSet Grid Component](../sample-controls/data-set-grid-control.md) .

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)