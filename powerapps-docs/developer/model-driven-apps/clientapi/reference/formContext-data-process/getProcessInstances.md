---
title: getProcessInstances (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4ed6c991-59c9-4a69-90d4-635f3f1d397b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getprocessinstances-client-api-reference"></a>getProcessInstances (referencia de la API de cliente)



[!INCLUDE[./includes/getProcessInstances-description.md](./includes/getProcessInstances-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.getProcessInstances(callbackFunction(object));`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|callbackFunction|Función|Sí|Se pasa un objeto a la función de devolución de llamada con los siguientes atributos y sus valores correspondientes como el par clave:valor. Todos los valores devueltos son de tipo de cadena excepto **CreatedOnDate**, que es de tipo [fecha](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date). <br/>- CreatedOn (obsoleto)<br/>- CreatedOnDate<br/>- ProcessDefinitionID<br/>- ProcessDefinitionName<br/>- ProcessInstanceID<br/>- ProcessInstanceName<br/>- StatusCodeName<br/><br/>Las instancias de proceso se filtran según los privilegios del usuario.|

### <a name="related-topics"></a>Temas relacionados

[setActiveProcessInstance](setActiveProcessInstance.md)

[formContext.data.process](../formContext-data-process.md)
 


