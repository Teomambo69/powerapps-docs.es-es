---
title: getSelectedRows (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 49f39f0f-33ef-41d1-9ab3-14966ae075b5
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getselectedrows-client-api-reference"></a>getSelectedRows (referencia de la API de cliente)



[!INCLUDE[./includes/getSelectedRows-description.md](./includes/getSelectedRows-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`var allSelectedRows = gridContext.getGrid().getSelectedRows();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: colección

**Descripción**: una colección de filas seleccionadas de la cuadrícula.

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).

Vea [Colecciones (referencia de la API de cliente)](../../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

