---
title: setPrecision (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 580aebec-c1d1-4e4a-8c20-ced859569fb2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setprecision-client-api-reference"></a>setPrecision (referencia de la API de cliente)



Establece el número de dígitos permitidos a la derecha de la coma decimal. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Dinero, decimal, doble y entero

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).setPrecision(value);`

## <a name="parameter"></a>Parámetro

 Nombre de parámetro| Tipo| Descripción  |
| --------|-----------| -----|
|valor| Número| Número de dígitos permitidos a la derecha de la coma decimal.|

### <a name="related-topics"></a>Temas relacionados

[getPrecision](getPrecision.md)

