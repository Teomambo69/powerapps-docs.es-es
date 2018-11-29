---
title: setActiveProcess (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0d4c2d8a-a2fb-4cdd-9153-041646068992
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setactiveprocess-client-api-reference"></a>setActiveProcess (referencia de la API de cliente)



[!INCLUDE[./includes/setActiveProcess-description.md](./includes/setActiveProcess-description.md)]

Si existe una instancia activa del proceso, el registro de entidad se carga con el Id. de instancia de proceso. Si no hay instancia activa del proceso actual, se crea una nueva instancia de proceso y el registro de entidad se carga con el Id. de instancia de proceso. Si hay varias instancias del proceso actual, el registro se carga con la primera instancia del proceso activo según la lógica predeterminada, que es la instancia de proceso usada más recientemente por usuario.

## <a name="syntax"></a>Sintaxis

`formContext.data.process.setActiveProcess(processId, callbackFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|processInstanceId|String|Sí|El identificador del proceso para establecer el proceso activo.|
|callbackFunction|Función|No|Una función para llamar una vez terminada la operación. A esta capacidad de devolución de llamada se le pasa uno de los siguientes valores de cadena para indicar si la operación se realizó correctamente:<br/>- **Correcto**: La operación se ha realizado correctamente.<br/>- **inválido**: El processId no es válido o el proceso no está habilitado.|

### <a name="related-topics"></a>Temas relacionados

[getActiveProcess](getActiveProcess.md)

[setActiveProcessInstance](../setActiveProcessInstance.md)

[formContext.data.process](../../formContext-data-process.md)
 


