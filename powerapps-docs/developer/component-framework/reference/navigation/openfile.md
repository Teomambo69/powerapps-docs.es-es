---
title: openFile | Microsoft Docs
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
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
ms.openlocfilehash: 5de6eefb37450fde50127829f2a922252d08a4fb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342700"
---
# <a name="openfile"></a>openFile

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openFile(file, options)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|Filesystem|`FileObject`|Sí|Objeto que describe el archivo que se va a abrir. FileObject tiene los siguientes atributos: <br/>- **fileContent**: `String`. Contenido del archivo. <br/>- **nombre de archivo**: `String`. Nombre del archivo.<br/>- **archivo**: `Number`. Tamaño del archivo en KB. <br/>- **Mimetype**: `String`. Tipo MIME del archivo.|
|Opciones|`Object`|No|Objeto que describe si se va a abrir o guardar el archivo. El objeto tiene el atributo siguiente: <br/>- **openMode**: especifique 1 para abrirlo; 2 para guardar. 
Si no se especifica este parámetro, se pasa de forma predeterminada 1 (abrir). Este parámetro solo se admite en la interfaz unificada.|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise`

## <a name="remarks"></a>Sección

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) and [FileObject](../fileobject.md)


### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)