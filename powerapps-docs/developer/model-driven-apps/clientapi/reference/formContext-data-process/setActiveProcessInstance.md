---
title: setActiveProcessInstance (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c01a9445-00b6-4152-a482-df830f91a3ea
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setactiveprocessinstance-client-api-reference"></a>setActiveProcessInstance (referencia de la API de cliente)



[!INCLUDE[./includes/setActiveProcessInstance-description.md](./includes/setActiveProcessInstance-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.setActiveProcessInstance(processInstanceId, callbackFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|processInstanceId|String|Sí|El identificador de la instancia de proceso para establecer como instancia activa.|
|callbackFunction|Función|No|Una función para llamar una vez terminada la operación. A esta capacidad de devolución de llamada se le pasa uno de los siguientes valores de cadena para indicar si la operación se realizó correctamente:<br/>- **Correcto**: La operación se ha realizado correctamente.<br/>- **inválido**: El processInstanceId no es válido o el proceso no está habilitado.|

### <a name="related-topics"></a>Temas relacionados

[getProcessInstances](getProcessInstances.md)

[formContext.data.process](../formContext-data-process.md)
 


