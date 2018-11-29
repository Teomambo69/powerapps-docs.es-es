---
title: setStatus (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setstatus-client-api-reference"></a>setStatus (referencia de la API de cliente)



[!INCLUDE[./includes/setStatus-description.md](./includes/setStatus-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.process.setStatus(status, callbackFunction);`

## <a name="parameters"></a>Parámetros

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|estado|String|Sí|El nuevo estado. Los valores pueden ser **activo**, **anulado**, o **finalizado**.|
|callbackFunction|Función|No|Una función para llamar una vez terminada la operación. A esta función de devolución de llamada se pasa el nuevo estado como valor de cadena.|

**Tipo**: Cadena. 

**Descripción**: Devuelve uno de los siguientes valores: **activo**, **anulado** o **finalizado**.

### <a name="related-topics"></a>Temas relacionados

[formContext.data.process](../../formContext-data-process.md)
 


