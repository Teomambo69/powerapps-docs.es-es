---
title: Función Valores predeterminados | Microsoft Docs
description: Información de referencia sobre la función Defaults de PowerApps, incluidos ejemplos y sintaxis
services: ''
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: b62b2b8575d1ff0e5a55a97db6e6650af5a593c1
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

