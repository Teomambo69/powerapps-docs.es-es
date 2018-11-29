---
title: htmlDecode| MicrosoftDocs
description: El método de API de cliente convierte una cadena que se ha codificado con HTML en una cadena descodificada.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4ef7160b-ac01-4d08-8a98-f8e3012ef20b
author: KumarVivek
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="htmldecode-client-api-reference"></a>htmlDecode (referencia de cliente de API)



[!INCLUDE[./includes/htmlDecode-description.md](./includes/htmlDecode-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Encoding.htmlDecode(arg)`

## <a name="parameters"></a>Parámetros

|Nombre de parámetro        | Tipo           | Obligatoria  |Descripción  |
| ------------- |-------------| -----|-----|
|argumentos        | String           | Obligatoria  |Cadena codificada con HTML que se va a descodificar.  |


## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: cadena descodificada.

## <a name="related-topics"></a>Temas relacionados

[htmlEncode](htmlEncode.md)

[htmlAttributeEncode](htmlAttributeEncode.md)
