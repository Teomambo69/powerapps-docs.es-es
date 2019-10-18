---
title: openErrorDialog | Microsoft Docs
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
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
ms.openlocfilehash: c3371b7c3ea8bde869acc261ab7d4fc8f28ba7da
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342447"
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openErrorDialog(options)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|Opciones|`ErrorDialogOptions`|Sí|Opciones del cuadro de diálogo de error. ErrorDialogOptions tiene los siguientes atributos: <br/>**detalles**de - : `String`. Detalles sobre el error. Cuando se especifica, el botón **Descargar archivo de registro** está disponible en el mensaje de error y al hacer clic en él se permite a los usuarios descargar un archivo de texto con el contenido especificado en este atributo.<br/>- **ErrorCode**: `Number`. Código de error. Si acaba de establecer errorCode, el mensaje del código de error se recupera automáticamente del servidor y se muestra en el cuadro de diálogo de error. Si especifica un valor **ErrorCode** , se muestra un cuadro de diálogo de error con un mensaje de error predeterminado.<br/>- **mensaje**: `String`. Mensaje que se va a mostrar en el cuadro de diálogo de error. Debe establecer el atributo **ErrorCode** o **Message** .|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise`

## <a name="remarks"></a>Sección

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) and [File](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)