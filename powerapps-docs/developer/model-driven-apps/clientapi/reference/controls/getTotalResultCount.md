---
title: getTotalResultCount (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1f9169ce-cba3-4bb6-af20-f86140139cfe
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gettotalresultcount-client-api-reference"></a>getTotalResultCount (referencia de la API de cliente)



Obtenga el recuento de resultados que se encuentran en el control de búsqueda. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
var searchCount = kbSearchControl.getTotalResultCount();
```

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: número de resultados de la búsqueda.