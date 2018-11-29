---
title: Xrm.Device| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: ce572df6-aae6-431a-aa95-73eee544c7e9
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getselectedoption-client-api-reference"></a>getSelectedOption (referencia de la API de cliente)



Devuelve el objeto de la opción o una matriz de objetos de la opción seleccionados en un atributo **optionset** o **multiselectoptionset** respectivamente. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

optionset, multiselectoptionset

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getSelectedOption()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto de opción para optionset; matriz de objetos de opción para multiselectoptionset. 

**Descripción**: devuelve el objeto con las propiedades de texto y de valor.

### <a name="related-topics"></a>Temas relacionados
[getInitialValue (referencia de la API de cliente)](getInitialValue.md)

[getOption (referencia de la API de cliente)](getOption.md)

[getOptions (referencia de la API de cliente)](getOptions.md)

[getText (referencia de la API de cliente)](getText.md)

