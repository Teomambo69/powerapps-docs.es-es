---
title: DataSet | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0202d51f-e9a9-4a2e-b3e9-0bfd7f6afb86
---

# <a name="dataset"></a>DataSet

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="properties"></a>Propiedades

## <a name="addcolumn"></a>addColumn

El rol para agregar una columna al conjunto de datos

**Tipo**: `function`<br />
**Opcional**

### <a name="remarks"></a>Comentarios

Esta función debe aceptar dos parámetros.

|Nombre|Escriba|Requerido|Descripción|
|-|-|-|-|
|nombre|Cadena|Sí|Nombre de columna que se agregará al conjunto de datos|
|entityalias|Cadena|No| Alias para el que debe agregarse el nombre de columna|

## <a name="columns"></a>columns

El conjunto de columnas disponibles en este conjunto de datos.

**Tipo**: [Columna](column.md)[]

## <a name="error"></a>error

Si se ha producido un error en recuperación de datos.

**Tipo**: `boolean`

## <a name="errormessage"></a>errorMessage

El mensaje de error asociado al último error encontrado.

**Tipo**: `string`

## <a name="filtering"></a>filtering

Descripción del marcador: IDataSetExposedParameter.name
<!-- 
QUESTION: This description doesn't seem right
'The column sorting for the current query.' 
-->

**Tipo**: [Filtrado](filtering.md)

## <a name="linking"></a>linking

Descripción del marcador: IDataSetExposedParameter.name

**Tipo**: [Vinculación](linking.md)

## <a name="loading"></a>loading

Si el conjunto de datos se está cargando.

**Tipo**: `boolean`

## <a name="paging"></a>paginación

Estado y acciones de paginación.

**Tipo**: [Paginación](paging.md)

## <a name="records"></a>registros

Asignación de identificadores al objeto de registro completo.

**Tipo**: `object`

## <a name="sortedrecordids"></a>sortedRecordIds

Id. de los registros del conjunto de datos, en orden.

**Tipo**: `string[]`

## <a name="sorting"></a>sorting

El orden de columnas de la consulta actual.

**Tipo**: [Orden](sortstatus.md)

## <a name="methods"></a>Métodos

|Método | Descripción | 
| ------------- |-------------|
|[clearSelectedRecordIds](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[getSelectedRecordIds](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[getTargetEntityType](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[getViewId](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[openDatasetItem](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[actualizar](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[setSelectedRecordIds](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)