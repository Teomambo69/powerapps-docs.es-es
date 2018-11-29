---
title: refresh (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="refresh-client-api-reference"></a>refresh (referencia de la API de cliente)



[!INCLUDE[./includes/refresh-description.md](./includes/refresh-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.refresh(save).then(successCallback, errorCallback);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|guardar|Boolean|No|verdadero si los datos se deben guardar después de que se actualicen, si no falso.|
|successCallback|Función|No|Una función para llamar a la operación es correcta.|
|errorCallback|Función|No|Una función para llamar cuando la operación tiene error.|

### <a name="related-topics"></a>Temas relacionados

[formContext](../../clientapi-form-context.md)

