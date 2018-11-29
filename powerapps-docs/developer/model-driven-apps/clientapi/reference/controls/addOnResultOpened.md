---
title: addOnResultOpened (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5f0eabe1-985a-4e89-b23a-72657208ae7e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonresultopened-client-api-reference"></a>addOnResultOpened (referencia de la API de cliente)



Agrega un controlador de eventos al evento [OnResultOpened](../events/onresultopened.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.addOnResultOpened(myFunction);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí|La función para agregar al evento **OnResultOpened**. El [contexto de ejecución](../../clientapi-execution-context.md) se pasa automáticamente como el primer parámetro a esta función.|

### <a name="related-topics"></a>Temas relacionados

[Evento OnResultOpened](../events/onresultopened.md)

[removeOnResultOpened](removeOnResultOpened.md)
