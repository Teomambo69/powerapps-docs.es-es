---
title: removeOnResultOpened (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
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
# <a name="removeonresultopened-client-api-reference"></a>removeOnResultOpened (referencia de la API de cliente)



Quita un controlador de eventos del evento [OnResultOpened](../events/onresultopened.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.removeOnResultOpened(myFunction);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí|La función que quitar del evento **OnResultOpened**.|

### <a name="related-topics"></a>Temas relacionados

[Evento OnResultOpened](../events/onresultopened.md)

[addOnResultOpened](addOnResultOpened.md) 


