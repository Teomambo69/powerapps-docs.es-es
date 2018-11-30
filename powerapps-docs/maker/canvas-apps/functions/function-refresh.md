---
title: Función Refresh | Microsoft Docs
description: Información de referencia de la función Refresh de PowerApps, con sintaxis y ejemplos
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/21/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2999665e5882245b594468b6babe67be575c5c1e
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843606"
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

