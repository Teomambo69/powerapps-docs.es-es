---
title: GridEntity (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: cc2b7eca-61f4-4949-8398-52c9fc36721c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridentity-client-api-reference"></a>GridEntity (referencia de la API de cliente)



GridEntity se devuelve por el método [GridRowData](gridrowdata.md).[getEntity](gridrowdata/getEntity.md) o accediendo directamente al objeto [GridRowData](gridrowdata.md).**entidad**. Use los métodos GridEntity para tener acceso a datos acerca de registros específicos en las filas.

```JavaScript
var myRows = gridContext.getGrid().getRows();
var myRow = myRows.get(arg);
var gridEntity = myRow.getData().getEntity();
```

GridEntity también admite la colección de **atributos** que proporcionan métodos para trabajar con una colección de atributos de una entidad en la cuadrícula editable. Cada atributo ([GridAttribute](gridattribute.md)) representa los datos en la celda de una cuadrícula editable y contiene una referencia a todas las celdas asociadas al atributo. Vea [Colecciones (referencia de la API de cliente)](../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

## <a name="methods"></a>Métodos

|Nombre|Descripción|Disponible para|
|--|--|--|
|[getEntityName](gridentity/getEntityName.md)|[!INCLUDE[gridentity/includes/getEntityName-description.md](gridentity/includes/getEntityName-description.md)]|Cuadrículas editables y de solo lectura|
|[getEntityReference](gridentity/getEntityReference.md)|[!INCLUDE[gridentity/includes/getEntityReference-description.md](gridentity/includes/getEntityReference-description.md)]|Cuadrículas editables y de solo lectura|
|[getId](gridentity/getId.md)|[!INCLUDE[gridentity/includes/getId-description.md](gridentity/includes/getId-description.md)]|Cuadrículas editables y de solo lectura|
|[getPrimaryAttributeValue](gridentity/getPrimaryAttributeValue.md)|[!INCLUDE[gridentity/includes/getPrimaryAttributeValue-description.md](gridentity/includes/getPrimaryAttributeValue-description.md)]|Cuadrícula de solo lectura|

### <a name="related-topics"></a>Temas relacionados

[GridAttribute](gridattribute.md)

[Cuadrículas y subcuadrículas en aplicaciones basadas en modelos](../grids.md)

[Atributos](../attributes.md)


