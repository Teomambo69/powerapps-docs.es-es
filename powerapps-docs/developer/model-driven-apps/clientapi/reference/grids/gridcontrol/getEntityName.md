---
title: getEntityName (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1ead9dc0-7511-4b41-bd7d-23b8bb3b4e43
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentityname-client-api-reference"></a>getEntityName (referencia de la API de cliente)



[!INCLUDE[./includes/getEntityName-description.md](./includes/getEntityName-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`gridContext.getEntityName();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: el nombre lógico de los datos de entidad que se muestran en la cuadrícula.

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext). 


