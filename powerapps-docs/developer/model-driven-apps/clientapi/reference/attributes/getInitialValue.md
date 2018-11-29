---
title: getInitialValue (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 56fb62e6-d357-4096-bf4c-f4c1b543d633
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getinitialvalue-client-api-reference"></a>getInitialValue (referencia de la API de cliente)



Devuelve un valor que representa el valor establecido para un atributo **booleano**, **OptionSet** o **MultiSelectOptionSet** cuando se abre el formulario.

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Booleano, OptionSet, MultiSelectOptionSet 

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getInitialValue()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: el valor inicial para el atributo.


