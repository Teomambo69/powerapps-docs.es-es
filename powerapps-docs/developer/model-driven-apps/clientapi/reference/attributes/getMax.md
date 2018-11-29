---
title: getMax (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6bcd4b47-b3b6-4a9c-899f-a5dce4cbab51
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getmax-client-api-reference"></a>getMax (referencia de la API de cliente)



Devuelve un número que indica el valor máximo permitido para un atributo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

decimal, integer, double y money

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getMax()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: número. 

**Descripción**: el valor máximo permitido para el atributo.

