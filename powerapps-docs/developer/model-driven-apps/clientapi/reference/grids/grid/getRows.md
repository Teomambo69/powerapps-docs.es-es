---
title: getRows (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getrows-client-api-reference"></a>getRows (referencia de la API de cliente)



[!INCLUDE[./includes/getRows-description.md](./includes/getRows-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`var allRows = gridContext.getGrid().getRows();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: colección

**Descripción**: una colección de filas de la cuadrícula.

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).

Vea [Colecciones (referencia de la API de cliente)](../../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

