---
title: AbrirFormulario | Microsoft Docs
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
ms.assetid: bea56947-d976-4974-9ac7-2d5f5c7b6732
ms.openlocfilehash: d0754030de4880f0ad693105e96b47d785f1561b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342378"
---
# <a name="openform"></a>openForm

[!INCLUDE [openform-description](includes/openform-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.navigation.openForm(options, parameters)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|Opciones|`EntityFormOptions`|Sí|Opciones de formulario de la entidad para abrir el formulario. EntityFormOptions tiene los siguientes atributos:<br/>- **createFromEntity**: `Lookup`. Designa un registro que proporcionará los valores predeterminados basados en los valores de atributo asignados. El objeto de búsqueda tiene las siguientes propiedades de cadena: `entityType`, `id` y `name`. <br/>- **entityId**: `String`. IDENTIFICADOR del registro de entidad para el que se va a mostrar el formulario.<br/>- **entityName**: `String`. Nombre lógico de la entidad para la que se va a mostrar el formulario.<br/>- **FormId**: `String`. IDENTIFICADOR de la instancia del formulario que se va a mostrar.<br/>- **alto**: `Number`. Alto de la ventana del formulario que se va a mostrar en píxeles.<br/>- **openInNewWindow**: `boolean`. indica si se va a mostrar el formulario en una nueva ventana.<br/>- **useQuickCreateForm**: `Boolean`. Si se va a abrir un formulario de creación rápida. Si no se especifica, se pasa de forma predeterminada `false`.<br/>- **width**: `Number`. Ancho de la ventana del formulario que se va a mostrar en píxeles.<br/>- **windowPosition**: `Number`. Especifique uno de los siguientes valores para la posición de la ventana del formulario en la pantalla: `1:center` <br/> `2:side`|
|Los|`Object`|No|Objeto de diccionario que pasa parámetros adicionales al formulario. Los parámetros no válidos producirán un error. Más información, [ver valores de campo usar parámetros pasados a un formulario](https://docs.microsoft.com/en-us/powerapps/developer/model-driven-apps/set-field-values-using-parameters-passed-form) y [configurar un formulario para aceptar parámetros de cadena de consulta personalizada](https://docs.microsoft.com/en-us/powerapps/developer/component-framework/sample-controls/navigation-api-control)|

## <a name="return-value"></a>Valor devuelto

Tipo: `Promise<OpenFormSuccessResponse>`

## <a name="remarks"></a>Sección

Vea [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)

### <a name="related-topics"></a>Temas relacionados

[Navegación](../navigation.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)