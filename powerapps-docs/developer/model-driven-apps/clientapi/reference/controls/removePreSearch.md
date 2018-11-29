---
title: removePreSearch (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2451c4ac-527c-4487-8f52-bde1690c5bde
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removepresearch-client-api-reference"></a>removePreSearch (referencia de la API de cliente)



Quita las funciones del controlador de eventos que se han establecido anteriormente para el evento [PreSearch](../events/PreSearch.md).

## <a name="control-types-supported"></a>Tipos de control admitidos

Búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).removePreSearch(myFunction)`

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí| Función a quitar. El [contexto de ejecución](../../clientapi-execution-context.md) se pasa automáticamente como el primer parámetro a esta función.|

### <a name="related-topics"></a>Temas relacionados

[Evento PreSearch](../events/PreSearch.md)

[addPreSearch](addPreSearch.md) 


