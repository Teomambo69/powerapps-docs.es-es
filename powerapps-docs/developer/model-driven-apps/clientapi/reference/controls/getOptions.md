---
title: getOptions (referencia de la API de cliente)| MicrosoftDocs
ms.date: 08/13/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 83347491-68d2-4844-bda4-0cd0abde2edf
author: nkrb
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getoptions-client-api-reference"></a>getOptions (referencia de la API de cliente)

Devuelve una matriz de objetos de opción que representan opciones válidas disponibles para un control, incluida una opción en blanco y excluyendo cualquier opción que se haya quitado del control mediante [removeOption](removeOption.md). 

## <a name="control-types-supported"></a>Tipos de control admitidos

OptionSet, MultiSelectOptionSet

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getOptions()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: matriz de objetos de opción. 

**Descripción**: La matriz de objetos de opción que representa opciones válidas donde cada objeto de opción tiene los atributos siguientes:
- **text**: Cadena. Etiqueta de la opción.
- **value**: Número. Valor de enumeración de la opción.

