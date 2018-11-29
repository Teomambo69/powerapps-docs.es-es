---
title: getTotalRecordCount (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8305f0cb-9959-4429-a721-a864ade4cd35
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gettotalrecordcount-client-api-reference"></a>getTotalRecordCount (referencia de la API de cliente)



[!INCLUDE[./includes/getTotalRecordCount-description.md](./includes/getTotalRecordCount-description.md)]

- Cuando el cliente de Dynamics 365 para Outlook no está conectado al servidor, este número está limitado a aquellos registros que el usuario ha seleccionado para trabajar sin conexión.
- Para los clientes móviles Dynamics 365, este método devolverá el número de registros de la subcuadrícula.

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`var filteredRecordCount = gridContext.getGrid().getTotalRecordCount();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: número total de registros que coinciden con los criterios de filtro de la vista.

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).

Vea [Colecciones (referencia de la API de cliente)](../../collections.md) para obtener información sobre los métodos disponibles para obtener acceso a los datos de una colección.

