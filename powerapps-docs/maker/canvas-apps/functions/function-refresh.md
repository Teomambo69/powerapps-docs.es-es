---
title: "Función Actualizar | Microsoft Docs"
description: "Información de referencia de la función Refresh de PowerApps, con sintaxis y ejemplos"
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
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 631b0c8fbfc98d73cf1d944c2a0f3933f8f10c11
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="refresh-function-in-powerapps"></a>Función Refresh en PowerApps
Actualiza los [registros](../working-with-tables.md#records) de un [origen de datos](../working-with-data-sources.md).

## <a name="description"></a>Descripción
La función **Refresh** recupera una nueva copia de un origen de datos.  Verá los cambios que realizaron otros usuarios.

**Refresh** no tiene ningún valor devuelto y solo se puede usar en [fórmulas de comportamiento](../working-with-formulas-in-depth.md).

## <a name="syntax"></a>Sintaxis
**Refresh**( *DataSource* )

* *DataSource*: requerido. El origen de datos que desea actualizar.

## <a name="example"></a>Ejemplo
En este ejemplo, actualizará el origen de datos denominado **IceCream**, que empieza con estos datos:

![](media/function-refresh/icecream.png)

Un usuario de otro dispositivo cambia la columna **Quantity** en el registro **Strawberry** a **400**.  No verá este cambio hasta que se ejecuta esta fórmula:

**Refresh( IceCream )**

Una vez ejecutada la fórmula, las galerías que están enlazadas al origen de datos **IceCream** mostrarán el valor actualizado de **Strawberry**:

![](media/function-refresh/icecream-after.png)

