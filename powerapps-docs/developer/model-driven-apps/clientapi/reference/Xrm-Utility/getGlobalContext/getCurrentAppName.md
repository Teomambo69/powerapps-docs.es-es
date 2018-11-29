---
title: getCurrentAppName (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a8f83718-41a4-4958-a5ac-9b28cc2f8dba
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentappname-client-api-reference"></a>getCurrentAppName (referencia de la API de cliente)



Devuelve el nombre de la aplicación de negocio actual de las aplicaciones basadas en modelos.

## <a name="syntax"></a>Sintaxis

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getCurrentAppName().then(successCallback, errorCallback);
``` 

## <a name="parameters"></a>Parámetros

|Nombre |Escriba |Requerido |Descripción |
|---|---|---|---|
|successCallback |Función |Sí |Una función para llamar cuando se devuelve el nombre de la aplicación de negocio.  |
|errorCallback |Función |Sí |Una función para llamar cuando la operación tiene error.  |

## <a name="return-value"></a>Valor devuelto

Si se llama a este método en el contexto de una aplicación de negocio, devuelve el nombre de esa aplicación. De lo contrario, se produce un error.

### <a name="related-topics"></a>Temas relacionados

[Crear, administrar, y publicar aplicaciones basadas en modelos con código](../../../../create-manage-model-driven-apps-using-code.md)

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)


