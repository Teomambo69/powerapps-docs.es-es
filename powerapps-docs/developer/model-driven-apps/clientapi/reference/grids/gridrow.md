---
title: GridRow (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 02fef0b4-b895-4277-b604-3f525c29dca3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridrow-client-api-reference"></a>GridRow (referencia de la API de cliente)



Los métodos [Grid](grid.md).[getRows](grid/getRows.md) y [Grid](grid.md).[getSelectedRows](grid/getSelectedRows.md) devuelven una colección de GridRow.

```JavaScript
var myRows = gridContext.getGrid().getRows();
var gridRow = myRows.get(arg);
```

## <a name="properties"></a>Propiedades

|Nombre|Descripción|Disponible para|
|--|--|--|
|Datos de |Una colección que contiene [GridRowData](gridrowdata.md) para GridRow. Vea [Colecciones (referencia de la API de cliente)](../collections.md) para obtener información sobre los métodos disponibles para el acceso a los datos de una colección.|Cuadrículas editables y de solo lectura|


## <a name="methods"></a>Métodos

|Nombre|Descripción|Disponible para|
|--|--|--|
|[getData](gridrow/getData.md)|[!INCLUDE[gridrow/includes/getData-description.md](gridrow/includes/getData-description.md)]|Cuadrículas editables y de solo lectura|

### <a name="related-topics"></a>Temas relacionados

[GridRowData](gridrowdata.md)

[Cuadrículas y subcuadrículas en aplicaciones basadas en modelos](../grids.md)


