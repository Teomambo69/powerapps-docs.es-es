---
title: Codificación de atributo xml | MicrosoftDocs
description: El método API de cliente codifica la cadena especificada para poder usarse en un atributo XML.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 909443cd-12b5-4a73-9904-8ae623d22c81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xmlattributeencode-client-api-reference"></a>Codificación de Atributo xml (referencia de la API de cliente)



[!INCLUDE[./includes/xmlAttributeEncode-description.md](./includes/xmlAttributeEncode-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Encoding.xmlAttributeEncode(arg)`

## <a name="parameters"></a>Parámetros

|Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|argumentos        | String           | Obligatoria  |Cadena para codificar.  |


## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: cadena codificada.

## <a name="related-topics"></a>Temas relacionados
[Codificación xml](xmlEncode.md)