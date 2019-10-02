---
title: openConfirmDialog | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
---

# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="syntax"></a>Sintaxis

`openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|confirmStrings|`ConfirmDialogStrings`|sí|Cadenas usadas en el diálogo. ConfirmDialogStrings tiene los siguientes atributos:<br/>- **title**: `string`. Confirmar título del diálogo. <br/>- **subtitle**: `string`. Confirmar subtítulo del diálogo.<br/>- **text**: `string`. Confirmar texto/mensaje del diálogo.<br/>- **confirmButtonLabel**: `string`. Etiqueta del botón Confirmar. Si no especifica la etiqueta del botón, se utilizará Aceptar (en el idioma preferido del usuario) como etiqueta del botón.|
|opciones|`ConfirmDialogOptions`|sí|Opciones del diálogo. ConfirmDialogOptions tiene los siguientes atributos:<br/>- **height**: `number`. Alto del cuadro de diálogo de confirmación, en píxeles. <br/>- **width**:`number`. Ancho del cuadro de diálogo de confirmación, en píxeles|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise<ConfirmDialogResponse>`

Devuelve un objeto con el atributo confirmed (booleano) que indica si se hizo clic en el botón Confirmar para cerrar el cuadro de diálogo.

## <a name="remarks"></a>Comentarios

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)