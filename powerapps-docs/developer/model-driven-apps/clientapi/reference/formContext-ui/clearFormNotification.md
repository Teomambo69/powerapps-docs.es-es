---
title: clearFormNotification (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6c57db71-a76d-404c-852e-9c36a1c549ee
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="clearformnotification-client-api-reference"></a>clearFormNotification (referencia de la API de cliente)



[!INCLUDE[./includes/clearFormNotification-description.md](./includes/clearFormNotification-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.clearFormNotification(uniqueId)`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|uniqueId|String|Sí|Un identificador único para el mensaje que se va a borrar que se ha establecido con el método [setFormNotification](setFormNotification.md).|

## <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: true si el método tiene éxito, false de lo contrario. 


### <a name="related-topics"></a>Temas relacionados

[setFormNotification](setFormNotification.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

