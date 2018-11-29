---
title: addOnPostSearch (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c398dbca-0ead-487a-8a92-35b1f2953bf6
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonpostsearch-client-api-reference"></a>removeOnPostSearch (referencia de la API de cliente)



Quita un controlador de eventos del evento [PostSearch](../events/postsearch.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>";
kbSearchControl.removeOnPostSearch(myFunction);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí|La función que quitar del evento **PostSearch**.| 

### <a name="related-topics"></a>Temas relacionados

[Evento postSearch](../events/postsearch.md)

[addOnPostSearch](addOnPostSearch.md) 


