---
title: getAllowedStatusTransitions (referencia de API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 28c36741-0070-435c-a42f-49f4dda2ef7f
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="getallowedstatustransitions-client-api-reference"></a>getAllowedStatusTransitions (referencia de la API de cliente)



[!INCLUDE[./includes/getAllowedStatusTransitions-description.md](./includes/getAllowedStatusTransitions-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.getAllowedStatusTransitions(entityName,stateCode).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parámetros

|Nombre |Tipo |Obligatoria |Descripción |
|---|---|---|---|
|entityName|String|Sí|El nombre lógico de la entidad.|
|stateCode|Número|Sí|El código de estado para saber los valores de transición de estado permitidos.|
|successCallback|Función|No|La función que se ejecuta cuando la operación es correcta.|
|errorCallback|Función|No|La función que se ejecuta cuando la operación produce un error.|


### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility](../xrm-utility.md)



