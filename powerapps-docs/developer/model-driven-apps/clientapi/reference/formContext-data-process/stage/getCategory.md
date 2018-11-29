---
title: getCategory (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2849a9e1-b2fb-464c-8fc7-90b0df027c86
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcategory-client-api-reference"></a>getCategory (referencia de la API de cliente)



[!INCLUDE[./includes/getCategory-description.md](./includes/getCategory-description.md)]

## <a name="syntax"></a>Sintaxis

`var stageCategoryNumber = stageObj.getCategory().getValue();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: número. 

**Descripción**: esta es la lista de valores posibles.

|Value |Descripción|
|--|--|
|0|Calificar|
|1|Desarrollar|
|2|Proponer|
|3|Cerrada|
|4|Identificar|
|5|Investigar|
|6|Resolver|

### <a name="related-topics"></a>Temas relacionados

[formContext.data.process](../../formContext-data-process.md)
 


