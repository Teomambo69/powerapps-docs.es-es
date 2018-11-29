---
title: getVersion (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2fd5c43e-5a01-431d-ac2c-abefdb8d06ac
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getversion-client-api-reference"></a>getVersion (referencia de la API de cliente)



Devuelve el número de versión de la instancia de las aplicaciones basadas en modelos.

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getVersion();
``` 
## <a name="return-value"></a>Valor de retorno

**Tipo**: Cadena

**Descripción**: versión de la instancia de las aplicaciones basadas en modelos. Por ejemplo:

`"9.0.0.1103"`

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)
