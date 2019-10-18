---
title: openAlertDialog | Microsoft Docs
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
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
ms.openlocfilehash: f1f5a2a78faf3dd9c6a1d6d197fab61772969084
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342516"
---
# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|alertStrings|`AlertDialogStrings`|Sí|Cadenas que se van a usar en el cuadro de diálogo de alerta. AlertDialogStrings tiene los siguientes atributos:<br/>- **Text**: `string`. Mensaje que se va a mostrar en el cuadro de diálogo de alerta. <br/>- **confirmButtonLabel**: `string`. Etiqueta del botón confirmar. Si no especifica la etiqueta del botón, **Aceptar** (en el idioma preferido del usuario) se usa como etiqueta del botón.|
|Opciones|`AlertDialogOptions`|Sí|Opciones de diálogo. AlertDialogOptions tiene los siguientes atributos:<br/>- **alto**: `number`. Alto del cuadro de diálogo de alerta en píxeles. <br/>- **width**: `number`. Ancho del cuadro de diálogo de alerta en píxeles|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise`

## <a name="remarks"></a>Sección

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) and [File](https://developer.mozilla.org/docs/Web/API/File)

## <a name="example"></a>Ejemplo 

```TypeScript
context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
```

### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)