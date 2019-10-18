---
title: openConfirmDialog | Microsoft Docs
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
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
ms.openlocfilehash: 8b7bda89b9c8d83614a4a95281853676db9cf568
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342493"
---
# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|confirmStrings|`ConfirmDialogStrings`|Sí|Cadenas usadas en el cuadro de diálogo. ConfirmDialogStrings tiene los siguientes atributos:<br/>**título**de - : `String`. Título que se va a mostrar en el cuadro de diálogo de confirmación. <br/>- **subtítulo**: `String`. El subtítulo que se va a utilizar en el cuadro de diálogo de confirmación.<br/>- **Text**: `String`. Mensaje que se va a mostrar en el cuadro de diálogo de confirmación.<br/>- **confirmButtonLabel**: `String`. Etiqueta del botón confirmar. Si no especifica la etiqueta del botón, **Aceptar** (en el idioma preferido del usuario) se usa como etiqueta del botón.<br/>- **cancelButtonLabel**: `String` la etiqueta del botón Cancelar. Si no especifica la etiqueta del botón Cancelar, se usa **Cancelar** como etiqueta del botón.|
|Opciones|`ConfirmDialogOptions`|No|Opciones del cuadro de diálogo. ConfirmDialogOptions tiene los siguientes atributos:<br/>- **alto**: `Number`. Alto del cuadro de diálogo de confirmación en píxeles. <br/>- **width**: `Number`. Ancho del cuadro de diálogo de confirmación en píxeles|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise<ConfirmDialogResponse>`

Descripción: devuelve un objeto con el atributo confirmado (booleano) que indica si se ha hecho clic en el botón confirmar para cerrar el cuadro de diálogo.

## <a name="remarks"></a>Sección

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)