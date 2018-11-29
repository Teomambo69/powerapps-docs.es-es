---
title: setSearchQuery (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 99e82b80-b6c3-4ee8-83cc-637b13ed8498
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setsearchquery-client-api-reference"></a>setSearchQuery (referencia de la API de cliente)



Establece el texto utilizado como criterio de búsqueda para el control de búsqueda de la knowledge base.

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.setSearchQuery(searchString);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|searchString |String |Sí|El texto de la consulta de búsqueda.| 

### <a name="related-topics"></a>Temas relacionados

[getSearchQuery](getSearchQuery.md)


