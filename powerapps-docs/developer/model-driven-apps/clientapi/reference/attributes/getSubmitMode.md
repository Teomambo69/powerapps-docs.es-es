---
title: getSubmitMode (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a3231438-3821-4dce-b118-d63e6ce85e01
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsubmitmode-client-api-reference"></a>getSubmitMode (referencia de la API de cliente)



Devuelve una cadena que indica cuándo se enviarán los datos del atributo al guardar el registro. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getSubmitMode()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena. 

**Descripción**: devuelve uno de los siguientes valores:
- siempre
- nunca
- modificado

### <a name="related-topic"></a>Tema relacionado
[setSubmitMode (referencia de API de cliente)](setSubmitMode.md)

