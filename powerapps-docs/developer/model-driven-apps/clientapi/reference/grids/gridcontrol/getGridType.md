---
title: getGridType (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a441c08c-df32-433e-b666-4253f2cf878c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getgridtype-client-api-reference"></a>getGridType (referencia de la API de cliente)



[!INCLUDE[./includes/getGridType-description.md](./includes/getGridType-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`var gridType = gridContext.getGridType();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: devuelve uno de los siguientes valores:

|Value |Descripción |
|--|--|
|1|HomePageGrid|
|2|Subcuadrícula|

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext). 


