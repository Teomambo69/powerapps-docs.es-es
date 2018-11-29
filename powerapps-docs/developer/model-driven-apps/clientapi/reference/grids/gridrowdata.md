---
title: GridRowData (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8139c622-e4d9-478f-9510-414d140e5556
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridrowdata-client-api-reference"></a>GridRowData (referencia de la API de cliente)



El método [GridRow](gridrow.md).[getData](gridrow/getData.md) devuelve GridRowData.

GridRowData también proporciona métodos para recuperar información específica de un registro que se muestra en una fila de cuadrícula editable, incluida una colección de todos los atributos incluidos en la fila. Los datos del atributo se limitan a las columnas presentadas por la cuadrícula editable. Vea [Colecciones (referencia de la API de cliente)](../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

```JavaScript
var myRows = gridContext.getGrid().getRows();
var myRow = myRows.get(arg);
var gridRowData = myRow.getData();
```

## <a name="properties"></a>Propiedades

|Nombre|Descripción|Disponible para|
|--|--|--|
|entidad|Devuelve [GridEntity](gridentity.md) para GridRowData.|Cuadrículas editables y de solo lectura|


## <a name="methods"></a>Métodos

|Nombre|Descripción|Disponible para|
|--|--|--|
|[getEntity](gridrowdata/getEntity.md)|[!INCLUDE[gridrowdata/includes/getEntity-description.md](gridrowdata/includes/getEntity-description.md)]|Cuadrículas editables y de solo lectura|


