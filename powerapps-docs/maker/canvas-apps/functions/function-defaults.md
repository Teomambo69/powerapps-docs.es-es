---
title: Función Valores predeterminados | Microsoft Docs
description: Información de referencia sobre la función Defaults de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 83021ff0d18eb5d7322ef40eaa2bc0839b56f452
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42835000"
---
# <a name="defaults-function-in-powerapps"></a>Función Defaults en PowerApps
Devuelve los valores predeterminados para un [origen de datos](../working-with-data-sources.md).  

## <a name="description"></a>Descripción
Use la función **Defaults** para rellenar previamente un formulario de entrada de datos, lo cual facilita el rellenado.

Esta función devuelve un [registro](../working-with-tables.md#records) que contiene los valores predeterminados para el origen de datos.  Si una [columna](../working-with-tables.md#columns) dentro del origen de datos no tiene ningún valor predeterminado, esa propiedad no estará presente.

Los orígenes de datos varían en la cantidad de información predeterminada que proporcionan; incluso pueden no ofrecer ninguna.  Cuando trabaje con una [colección](../working-with-data-sources.md#collections) u otro origen de datos que no admita valores predeterminados, la función **Defaults** devolverá un registro [vacío](function-isblank-isempty.md).

Puede combinar la función **Defaults** con la función **[Revisión](function-patch.md)** para [crear un registro](../working-with-data-sources.md).

## <a name="syntax"></a>Sintaxis
**Defaults**( *DataSource* )

* *DataSource*: requerido. El origen de datos para el que quiere valores predeterminados.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |Devuelve los valores predeterminados para el origen de datos **Scores**. |**{ Score: 0 }** |

