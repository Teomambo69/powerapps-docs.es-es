---
title: getMaxLength (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 67a96fc4-4d65-4858-90da-f41eeba0365a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getmaxlength-client-api-reference"></a>getMaxLength (referencia de la API de cliente)



Devuelve un número que indica la longitud máxima de un atributo de cadena o de memo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

string, memo

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getMaxLength()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: número. 

**Descripción**: la longitud máxima permitida de una cadena para este atributo.

> [!NOTE]
> El atributo de descripción del formulario de correo electrónico es un atributo memo, pero no tiene un método `getMaxLength` .