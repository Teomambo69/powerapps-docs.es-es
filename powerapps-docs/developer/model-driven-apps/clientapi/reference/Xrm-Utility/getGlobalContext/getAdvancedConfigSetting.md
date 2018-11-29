---
title: getAdvancedConfigSetting (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getadvancedconfigsetting-client-api-reference"></a>getAdvancedConfigSetting (referencia de la API de cliente)



Devuelve información sobre las opciones de configuración avanzadas de la organización. 

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getAdvancedConfigSetting(setting);
```

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|configuración |String |Sí |Nombre de la opción de configuración. <br/>Se admiten únicamente las siguientes dos opciones de configuración: **"MaxChildIncidentNumber"** y **"MaxIncidentMergeNumber"** |

## <a name="return-value"></a>Valor devuelto

Devuelve el valor de la opción de configuración avanzada.

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)



