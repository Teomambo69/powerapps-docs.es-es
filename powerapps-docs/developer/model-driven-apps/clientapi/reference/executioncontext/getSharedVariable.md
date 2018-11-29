---
title: getSharedVariable (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 702a13c1-f4ae-4de2-9e8b-95360ad9240c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsharedvariable-client-api-reference"></a>getSharedVariable (referencia de la API de cliente)



Recupera un conjunto de variables que usa el método [setSharedVariable](setSharedVariable.md).

## <a name="syntax"></a>Sintaxis

`ExecutionContextObj.getSharedVariable(key)`

## <a name="parameters"></a>Parámetros

**key**

   **Tipo**: Cadena

   **Descripción**: nombre de la variable.

## <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: El tipo específico depende de cuál es el objeto del valor.

### <a name="related-topics"></a>Temas relacionados
[setSharedVariable](setSharedVariable.md)

[Contexto de ejecución](../execution-context.md)





