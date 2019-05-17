---
title: openUrl | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
---

# <a name="openurl"></a>Abrir Url

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="syntax"></a>Sintaxis

`openUrl(url, options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|dirección url|`string`|sí|URL que se abrirá.|
|opciones|`OpenUrlOptions`|sí|Opciones de ventana para la dirección URL. OpenUrlOptions tienen los parámetros siguientes: <br/>- **height**: `number`. Alto de la ventana para mostrar la página resultante, en píxeles.<br/>- **width**: `number`. Ancho de la ventana para mostrar la página resultante, en píxeles.|


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)