---
title: Función Validar | Microsoft Docs
description: Información de referencia para la función Validate en PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: 6a8bff341484139e6d16092fc2ea3cbacb384777
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022847"
---
# <a name="validate-function-in-powerapps"></a>Función Validate en PowerApps
La función **Validate** comprueba si el valor de una única [columna](../working-with-tables.md#columns) o un [registro](../working-with-tables.md#records) completo es válido para un [origen de datos](../working-with-data-sources.md).  

## <a name="description"></a>Descripción
Antes de que un usuario envíe un cambio de datos, puede proporcionar información inmediata sobre la validez de ese envío, lo que se traduce en una mejor experiencia de usuario.

Los orígenes de datos pueden proporcionar información sobre qué constituyen valores válidos en un registro. Esta información puede incluir muchas restricciones, como en estos ejemplos:

* si una columna requiere un valor
* qué longitud puede tener una cadena de texto
* cuál puede ser el valor más alto y más bajo de un número
* cuál puede ser la fecha más temprana y la más tardía

La función **Validate** usa esta información para determinar si un valor es válido y para devolver el correspondiente mensaje de error si no lo es. Puede usar la función **[DataSourceInfo](function-datasourceinfo.md)** para ver la misma información que usa **Validate**.

Los orígenes de datos varían en la cantidad de información de validación que proporcionan; incluso pueden no ofrecer ninguna. **Validate** solo puede verificar valores basándose en esta información. Incluso si **Validate** no detecta ningún problema, es posible que se siga produciendo un error al aplicar el cambio de datos. Puede usar la función **[Errors](function-errors.md)** para obtener información sobre el error.

Si **Validate** encuentra un problema, la función devuelve un mensaje de error que puede mostrar al usuario de la aplicación. Si todos los valores son válidos, **Validate** devuelve [blank](function-isblank-isempty.md). Cuando trabaja con una [colección](../working-with-data-sources.md#collections) que no tiene ninguna información de validación, los valores siempre son válidos.

## <a name="syntax"></a>Sintaxis
**Validate**( *DataSource*, *Column*, *Value* )

* *DataSource*: requerido. El origen de datos con el que realizar la validación.
* *Column*: requerido. La columna que se va a validar.
* *Value*: requerido. El valor de la columna seleccionada que se debe validar.

**Validate**( *DataSource*, *OriginalRecord*, *Updates* )

* *DataSource*: requerido. El origen de datos con el que realizar la validación.
* *OriginalRecord*: requerido.  El registro con el que se van a validar las actualizaciones.
* *Updates*: requerido.  Los cambios que se van a aplicar al registro original.

## <a name="examples"></a>Ejemplos
Para estos ejemplos, los valores de la columna **Percentage** del origen de datos **Scores** deben estar comprendidos entre 0 y 100, ambos incluidos. Si los datos pasan la validación, la función devuelve *blank*. En caso contrario, la función devuelve un mensaje de error.

### <a name="validate-with-a-single-column"></a>Validar con una sola columna

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Validate( Scores, Percentage, 10 )** |Comprueba si **10** es un valor válido para la columna **Percentage** del origen de datos **Scores**. |*blank* |
| **Validate( Scores, Percentage, 120 )** |Comprueba si **120** es un valor válido para la columna **Percentage** del origen de datos **Scores**. |"Los valores deben estar comprendidos entre 0 y 100". |

### <a name="validate-with-a-complete-record"></a>Validar con un registro completo

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Validate( Scores, EditRecord, Gallery.Updates )** |Comprueba si **10** es un valor válido para la columna **Percentage** del origen de datos **Scores**. |*blank* |
| **Validate( Scores, EditRecord, Gallery.Updates )** |Comprueba si **120** es un valor válido para la columna **Percentage** del origen de datos **Scores**. |"Los valores deben estar comprendidos entre 0 y 100". |

