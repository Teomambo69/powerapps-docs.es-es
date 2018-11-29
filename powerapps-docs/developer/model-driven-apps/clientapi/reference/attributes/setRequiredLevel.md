---
title: setRequiredLevel (referencia de la API de cliente)| MicrosoftDocs
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
# <a name="setrequiredlevel-client-api-reference"></a>setRequiredLevel (referencia de la API de cliente)



Establece si los datos son requeridos o recomendados para el atributo antes de que el registro pueda ser guardado.

> [!IMPORTANT]
> Al reducir el nivel requerido de un atributo puede producirse un error al guardar la página. Si el atributo es requerido por el servidor se produce un error si no hay ningún valor para el atributo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).setRequiredLevel(requirementLevel)`

## <a name="parameters"></a>Parámetros

**Tipo**: Cadena. 

**Descripción**: Establecer el nivel de uno de los siguientes valores:
- ninguna
- obligatorio
- recomendada

### <a name="related-topic"></a>Tema relacionado
[getRequiredLevel (referencia de la API de cliente)](getRequiredLevel.md)


