---
title: addPreSearch (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d69a432a-1d74-4782-bedd-f9f30d3d7d9c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addpresearch-client-api-reference"></a>addPreSearch (referencia de la API de cliente)



Aplica cambios a búsquedas basadas en valores actuales mientras el usuario está a punto de ver los resultados de la búsqueda.

## <a name="control-types-supported"></a>Tipos de control admitidos

Búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).addPreSearch(myFunction)`

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|myFunction |Función |Sí| La función que se ejecutará justo antes de que se produzca la búsqueda para proporcionar resultados para una búsqueda. Puede usar esta función para llamar a una de las otras funciones de control de búsqueda y mejorar los resultados que se mostrarán en la búsqueda. El [contexto de ejecución](../../clientapi-execution-context.md) se pasa automáticamente como el primer parámetro a esta función.|

### <a name="related-topics"></a>Temas relacionados

[Evento PreSearch](../events/PreSearch.md)

[removePreSearch](removePreSearch.md) 


