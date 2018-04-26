---
title: Función Actualizar | Microsoft Docs
description: Información de referencia de la función Refresh de PowerApps, con sintaxis y ejemplos
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/21/2015
ms.author: gregli
ms.openlocfilehash: 9ec2711c4a38f26fec2d44681b2606b4a8ecba29
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

