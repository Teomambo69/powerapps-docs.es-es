---
title: getFormat (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e5f97552-4a48-4bf9-b460-6105442e2e6b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getformat-client-api-reference"></a>getFormat (referencia de la API de cliente)



Devuelve un valor de cadena que representa las opciones de formato del atributo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getFormat()`

## <a name="return-value"></a>Valor devuelto

Este método devolverá uno de los siguientes valores **string** o "null":

- fecha
- datetime
- duración
- correo electrónico
- language
- ninguna
- Teléfono
- texto
- textarea
- tickersymbol
- timezone
- url

> [!NOTE]
> Esta información de formato representa normalmente las opciones de formato del campo de la aplicación. Las opciones de formato de los campos booleanos no se proporcionan.

La siguiente tabla enumera los valores de cadena de formato que se pueden esperar para cada tipo de opción de formato y tipo de esquema de atributo.

| Tipo de campo de aplicación | Opción de formato | Tipo de atributo | Valor de formato|
|----------------------------|-------------------|--------------------|------------------|
| Fecha y hora              | Sólo fecha         | datetime           | fecha             |
| Fecha y hora              | Fecha y hora     | datetime           | datetime         |
| Número entero               | Duración          | entero            | duración         |
| Línea única de texto        | Correo electrónico            | cadena             | Correo electrónico            |
| Número entero               | Idioma          | optionset          | language         |
| Número entero               | Ninguna              | entero            | ninguna             |
| Línea única de texto        | Área de texto         | cadena             | textarea         |
| Línea única de texto        | Texto              | cadena             | texto             |
| Línea única de texto        | Símbolo del valor     | cadena             | tickersymbol     |
| Línea única de texto        | Teléfono             | cadena             | Teléfono            |
| Número entero               | Zona horaria         | optionset          | timezone         |
| Línea de texto única        | URL               | cadena             | dirección url 
