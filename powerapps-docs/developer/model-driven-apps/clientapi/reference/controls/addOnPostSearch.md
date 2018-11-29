---
title: addOnPostSearch (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9d000628-5dbe-45bd-9c47-e19187ffdae7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonpostsearch-client-api-reference"></a>addOnPostSearch (referencia de la API de cliente)



Agrega un controlador de eventos al evento [PostSearch](../events/postsearch.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>";
kbSearchControl.addOnPostSearch(myFunction);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí|La función para agregar al evento **PostSearch**. El [contexto de ejecución](../../clientapi-execution-context.md) se pasa automáticamente como el primer parámetro a esta función.| 

### <a name="related-topics"></a>Temas relacionados

[Evento postSearch](../events/postsearch.md)

[removeOnPostSearch](removeOnPostSearch.md)