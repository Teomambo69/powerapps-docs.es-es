---
title: "Función Valores predeterminados | Microsoft Docs"
description: "Información de referencia sobre la función Defaults de PowerApps, incluidos ejemplos y sintaxis"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/01/2015
ms.author: gregli
ms.openlocfilehash: eb1c6b802eff4aa5bd02a2ec52626b8788c42b73
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
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
