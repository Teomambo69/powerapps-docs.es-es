---
title: getOption (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e334d2d9-91c0-4953-956d-444a84dc9da2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getoption-client-api-reference"></a>getOption (referencia de la API de cliente)



Devuelve un objeto de opción con el valor que coincide con el argumento (etiqueta o valor de enumeración) pasado al método. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

OptionSet, MultiSelectOptionSet

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getOption(value)`

## <a name="parameters"></a>Parámetros

**Cadena** (etiqueta de la opción) o **número** (valor de enumeración de la opción).

## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto de opción. 

**Descripción**: el nombre lógico del atributo.

