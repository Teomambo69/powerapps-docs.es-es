---
title: openForm | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
---

# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="syntax"></a>Sintaxis

`openForm(options, parameters)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|opciones|`EntityFormOptions`|sí|EntityFormOptions tiene los siguientes atributos:<br/>- **createFromEntity**: [EntityReference](../entityreference.md). Señala un registro que proporcionará valores predeterminados según los valores de atributo asignados. El objeto de búsqueda tiene las siguientes propiedades de cadena: entityType, identificador y nombre. <br/>- **entityId**: `string`. Identificador del registro de entidad para el que se va a mostrar el formulario.<br/>- **entityName**: `string`. Nombre lógico de la entidad para la que se va a mostrar el formulario.<br/>- **formId**: `string`. Identificador de la instancia de formulario que se va a mostrar.<br/>- **height**: `number`. Alto de la ventana de formulario que se mostrará, en píxeles.<br/>- **openInNewWindow**: `boolean`. si se debe mostrar el formulario en una nueva ventana.<br/>- **useQuickCreateForm**: `boolean`. si se abre un formulario de creación rápida. Si no especifica esto, se pasa `false` de forma predeterminada.<br/>- **width**: `number`. Ancho de la ventana de formulario que se mostrará, en píxeles.<br/>- **windowPosition**: `number`. Especifique uno de los siguientes valores para la posición del formulario de la ventana en la pantalla: `1:center` <br/> `2:side`|
|parámetros|`key`|sí|Parámetros del formulario de entidad|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise`

## <a name="remarks"></a>Comentarios

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)