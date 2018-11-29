---
title: removeOnSelection (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 3ca41e3e-af2b-4aa8-8233-64a8c276d0ef
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonselection-client-api-reference"></a>removeOnSelection (referencia de la API de cliente)



Quita un controlador de eventos del evento [OnSelection](../events/onselection.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda de knowledge base

## <a name="syntax"></a>Sintaxis

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.removeOnSelection(myFunction);
```

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí|La función que quitar del evento **OnSelection**.| 

### <a name="related-topics"></a>Temas relacionados

[addOnSelection](addOnSelection.md)


