---
title: openAlertDialog | Microsoft Docs
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
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
---

# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="syntax"></a>Sintaxis

`openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|alertStrings|`AlertDialogStrings`|sí|Cadenas que se usará en el diálogo de alerta. AlertDialogStrings tiene los siguientes atributos:<br/>- **text**: `string`. Mensaje que se mostrará en el cuadro de diálogo de alerta. <br/>- **confirmButtonLabel**:`string`. Etiqueta del botón Confirmar. si no especifica la etiqueta del botón, se utilizará Aceptar (en el idioma preferido del usuario) como etiqueta del botón.|
|opciones|`AlertDialogOptions`|sí|Opciones del diálogo AlertDialogOptions tiene los siguientes atributos:<br/>- **height**: `number`. Alto del cuadro de diálogo de alerta, en píxeles. <br/>- **width**: `number`. Ancho del cuadro de diálogo de alerta en píxeles.|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise`

## <a name="remarks"></a>Comentarios

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)

### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)