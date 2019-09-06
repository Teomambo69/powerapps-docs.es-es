---
title: lookupObjects | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
---

# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="syntax"></a>Sintaxis

`lookupObjects(lookupOptions)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|lookupOptions|`UtilityApi.LookupOptions`|sí|Opciones para abrir el cuadro de diálogo de búsqueda. LookupOptions tiene los siguientes atributos:<br/>- **allowMultiSelect**: `boolean`. Si la búsqueda permite que se seleccione más de un elemento.<br/>- **defaultEntityType**: `string`. El tipo de entidad predeterminada.<br/>- **defaultViewId**: `string`. La vista predeterminada que se usa.<br/>- **entityTypes**: `string[]`. Los tipos de entidad que se muestran.<br/>- **viewIds**: `string[]`. Las vistas que están disponibles en el selector de vistas. Solo las vistas del sistema son compatibles (no las vistas de usuario).|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise`

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Temas relacionados

[Utilidad](../utility.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)