---
title: getSearchQuery (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getsearchquery-client-api-reference"></a>getSearchQuery (referencia de la API de cliente)



Obtiene el texto usado como criterio de búsqueda para el control de administración de knowledge base. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
var searchQuery = kbSearchControl.getSearchQuery();
```

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: texto de la consulta de búsqueda.

### <a name="related-topics"></a>Temas relacionados

[setSearchQuery](setSearchQuery.md)

