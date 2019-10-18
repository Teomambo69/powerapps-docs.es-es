---
title: lookupObjects | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
ms.openlocfilehash: 0dca29df3537389decefe2584d2fc931cea8979c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341159"
---
# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.utils.lookupObjects(lookupOptions)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|LookupOptions|`UtilityApi.LookupOptions`|Sí|Define las opciones para abrir el cuadro de diálogo de búsqueda. LookupOptions tiene los siguientes atributos:<br/>- **allowMultiSelect**: `Boolean`. Indica si la búsqueda permite seleccionar más de un elemento.<br/>- **defaultEntityType**: `String`. Tipo de entidad predeterminado que se va a usar.<br/>- **defaultViewId**: `String`. Vista predeterminada que se va a usar.<br/>- **entityTypes**: `String[]`. Tipos de entidad que se van a mostrar.<br/>- **viewid controles**: `String[]`. Vistas que estarán disponibles en el selector de vistas. Solo se admiten vistas del sistema (no vistas de usuario).|

## <a name="return-value"></a>Valor devuelto

Tipo: [promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[Entityreference](../entityreference.md)[] >


### <a name="related-topics"></a>Temas relacionados

[Utility](../utility.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)