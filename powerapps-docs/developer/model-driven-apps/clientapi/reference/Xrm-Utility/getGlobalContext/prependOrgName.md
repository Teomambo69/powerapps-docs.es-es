---
title: prependOrgName (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="prependorgname-client-api-reference"></a>prependOrgName (referencia de la API de cliente)



Agrega el nombre único de la organización actual como prefijo a una cadena, normalmente una dirección URL.

## <a name="syntax"></a>Sintaxis

 ```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.prependOrgName(sPath);
```

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|sPath |String |Sí |Una ruta local a un recurso. |

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: cadena de ruta con el nombre de la organización delante en el formato siguiente:

`"/"+ orgName + sPath`

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)


