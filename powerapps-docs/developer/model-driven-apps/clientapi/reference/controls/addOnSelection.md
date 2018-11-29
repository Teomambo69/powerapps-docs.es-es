---
title: addOnSelection (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 66cfb2ff-4d78-4bb9-8dc0-e214ae1d2880
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonselection-client-api-reference"></a>addOnSelection (referencia de la API de cliente)



Agrega un controlador de eventos al evento [OnSelection](../events/onselection.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.addOnSelection(myFunction);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí|La función para agregar al evento **OnSelection**. El [contexto de ejecución](../../clientapi-execution-context.md) se pasa automáticamente como el primer parámetro a esta función.|

### <a name="related-topics"></a>Temas relacionados

[Evento OnSelection](../events/onselection.md)

[removeOnSelection](removeOnSelection.md)