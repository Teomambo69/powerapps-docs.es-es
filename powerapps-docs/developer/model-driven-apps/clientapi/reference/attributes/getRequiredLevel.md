---
title: getRequiredLevel (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c0b6ea26-2a11-4a49-8ecf-fe700e782bf3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getrequiredlevel-client-api-reference"></a>getRequiredLevel (referencia de la API de cliente)



Devuelve un valor de cadena que indica si un valor del atributo es necesario o recomendado. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getRequiredLevel()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena. 

**Descripción**: devuelve uno de los siguientes valores:
- ninguna
- obligatorio
- recomendada

### <a name="related-topic"></a>Tema relacionado
[setRequiredLevel (referencia de la API de cliente)](setRequiredLevel.md)
