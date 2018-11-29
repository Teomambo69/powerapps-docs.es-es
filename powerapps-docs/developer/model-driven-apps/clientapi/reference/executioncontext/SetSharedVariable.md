---
title: setSharedVariable (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Obtenga más información sobre el método getEventSource que devuelve una referencia al formulario o a un elemento del formulario dependiendo de dónde se haya llamado el método.
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
# <a name="setsharedvariable-client-api-reference"></a>setSharedVariable (referencia de la API de cliente)



Establece el valor de una variable que será usada por un controlador una vez que se complete el controlador actual.

## <a name="syntax"></a>Sintaxis

`ExecutionContextObj.setSharedVariable(key, value)`

## <a name="parameters"></a>Parámetros

- **key**: Cadena: El nombre de la variable
- **Valor**: Objeto. Los valores a establecer



## <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: El tipo específico depende de cuál es el objeto del valor.

### <a name="related-topics"></a>Temas relacionados
[getSharedVariable](getSharedVariable.md)

[Contexto de ejecución](../execution-context.md)





