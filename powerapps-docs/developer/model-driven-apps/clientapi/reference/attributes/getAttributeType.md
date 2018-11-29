---
title: getAttribute (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9ef1c886-a0b8-4ba9-bb9f-e6ecfa9d6dff
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getattribute-client-api-reference"></a>getAttribute (referencia de la API de cliente)



Devuelve un valor de cadena que representa el tipo de atributo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getAttributeType()`

## <a name="return-value"></a>Valor devuelto

Este método devolverá uno de los siguientes valores de **cadena**:

- Booleano
- datetime
- decimal
- doble
- entero
- búsqueda
- memo
- money
- multioptionset
- optionset
- cadena