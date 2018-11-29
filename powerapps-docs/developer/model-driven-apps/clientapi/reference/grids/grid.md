---
title: Grid (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="grid-client-api-reference"></a>Grid (referencia de la API de cliente)



El método **gridContext**.[getGrid](gridcontrol/getGrid.md) devuelve una cuadrícula. Use los métodos Grid para tener acceso a la información acerca de los datos de la cuadrícula.

`var myGrid = gridContext.getGrid();`

## <a name="methods"></a>Métodos

|Nombre|Descripción|Disponible para|
|--|--|--|
|[getRows](grid/getRows.md)|[!INCLUDE[grid/includes/getRows-description.md](grid/includes/getRows-description.md)]|Cuadrículas editables y de solo lectura|
|[getSelectedRows](grid/getSelectedRows.md)|[!INCLUDE[grid/includes/getSelectedRows-description.md](grid/includes/getSelectedRows-description.md)]|Cuadrículas editables y de solo lectura|
|[getTotalRecordCount](grid/getTotalRecordCount.md)|[!INCLUDE[grid/includes/getTotalRecordCount-description.md](grid/includes/getTotalRecordCount-description.md)]|Cuadrículas editables y de solo lectura|

### <a name="related-topics"></a>Temas relacionados

[GridRow](gridrow.md)

[Cuadrículas y subcuadrículas en aplicaciones basadas en modelos](../grids.md)
