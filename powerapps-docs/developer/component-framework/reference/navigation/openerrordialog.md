---
title: openErrorDialog | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="syntax"></a>Sintaxis

`openErrorDialog(options)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|opciones|`ErrorDialogOptions`|sí|Opciones del diálogo de error. ErrorDialogOptions tiene los siguientes atributos: <br/>- **detalles**: `string`. Detalles sobre el error. Cuando especifica esto, el botón Descargar archivo de registro botón está disponible en el mensaje de error y hacer clic en él permite que los usuarios descarguen un archivo de texto con el contenido especificado en este atributo.<br/>- **errorCode**: `number`. Si solo configurar errorCode, el mensaje para el código de error se recupera del servidor automáticamente y se muestra en el cuadro de diálogo de error. Si especifica un valor de errorCode, se muestra un cuadro de diálogo de error con un mensaje de error predeterminado.<br/>- **message**: `string`. El mensaje que se muestra en el cuadro de diálogo de error.|

## <a name="return-value"></a>Valor de retorno

Tipo: `Promise`

## <a name="remarks"></a>Comentarios

Consulte [Promesa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) y [Archivo](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)