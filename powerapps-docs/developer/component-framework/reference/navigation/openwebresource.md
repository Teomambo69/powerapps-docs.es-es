---
title: openWebResource | Microsoft Docs
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
---

# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="syntax"></a>Sintaxis

`openWebResource(name, options, data)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|nombre|`string`|sí|El nombre del recurso web HTML para abrir.|
|opciones|`OpenWebResourceOptions`|sí|Opciones de ventana para el recurso web. OpenWebResourceOptions tiene los siguientes atributos:<br/>- **height**: `number`. Alto de la ventana para mostrar la página resultante, en píxeles.<br/>- **width**: `number`. Ancho de la ventana para mostrar la página resultante, en píxeles.<br/>- **openInNewWindow**: `boolean`. si se abre el recurso web en una nueva ventana.|
|Datos de |`string`|no|Datos que se pasarán al parámetro de datos.


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)