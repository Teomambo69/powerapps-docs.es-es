---
title: Función Defaults | Microsoft Docs
description: Información de referencia sobre la función Defaults de PowerApps, incluidos ejemplos y sintaxis
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b51d956f2c188e0b877530b28dec933d42c905a6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992840"
---
# <a name="defaults-function-in-powerapps"></a>Función Defaults en PowerApps
Devuelve los valores predeterminados para un [origen de datos](../working-with-data-sources.md).  

## <a name="description"></a>Descripción
Use la función **Defaults** para rellenar previamente un formulario de entrada de datos, lo cual facilita el rellenado.

Esta función devuelve un [registro](../working-with-tables.md#records) que contiene los valores predeterminados para el origen de datos.  Si una [columna](../working-with-tables.md#columns) dentro del origen de datos no tiene ningún valor predeterminado, esa propiedad no estará presente.

Los orígenes de datos varían en la cantidad de información predeterminada que proporcionan; incluso pueden no ofrecer ninguna.  Cuando trabaje con una [colección](../working-with-data-sources.md#collections) u otro origen de datos que no admita valores predeterminados, la función **Defaults** devolverá un registro [vacío](function-isblank-isempty.md).

Puede combinar la función **Defaults** con la función **[Patch](function-patch.md)** para [crear un registro](../working-with-data-sources.md).

## <a name="syntax"></a>Sintaxis
**Defaults**( *DataSource* )

* *DataSource*: requerido. El origen de datos para el que quiere valores predeterminados.

## <a name="examples"></a>Ejemplos

| Fórmula | Descripción | Resultado |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |Devuelve los valores predeterminados para el origen de datos **Scores**. |**{puntuación: 0}** |

