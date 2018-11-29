---
title: getPrecision (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 610b9b53-9c29-4228-8ef3-0c05aae14a2b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getprecision-client-api-reference"></a>getPrecision (referencia de la API de cliente)



Devuelve el número de dígitos permitidos a la derecha de la coma decimal. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Money, decimal, double e integer

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getPrecision()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: número. 

**Descripción**: el número de dígitos permitidos a la derecha de la coma decimal.

### <a name="related-topics"></a>Temas relacionados

[setPrecision](setPrecision.md)

