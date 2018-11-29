---
title: getFormType (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getformtype-client-api-reference"></a>getFormType (referencia de la API de cliente)



[!INCLUDE[./includes/getFormType-description.md](./includes/getFormType-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.getFormType();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: tipo de formulario. Devuelve uno de los siguientes valores 

|Value |Tipo de formulario |
|---|---|
|0|Sin definir|
|1|Crear|
|2|Actualizar|
|3|Solo lectura|
|4|Deshabilitada|
|6|Edición masiva|

>[!NOTE]
>Formularios de creación rápida devuelven 1.


### <a name="related-topics"></a>Temas relacionados

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

