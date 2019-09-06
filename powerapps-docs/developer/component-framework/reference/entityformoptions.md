---
title: EntityFormOptions | Microsoft Docs
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
ms.assetid: 418871c0-59dc-4a7c-a8f9-9364a19f7662
---
# <a name="entityformoptions"></a>EntityFormOptions

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="properties"></a>Propiedades

## <a name="createfromentity-entityreference"></a>createFromEntity: EntityReference

Señala un registro que proporcionará valores predeterminados según el valor de atributo asignado. El objeto de búsqueda tiene las siguientes propiedades: tipo, identificador y nombre de entidad.

## <a name="entity"></a>Entidad

Identificador único del registro de entidad para el que se va a mostrar el formulario. 

**Tipo**: `string`

## <a name="entityname"></a>entityName

Nombre lógico de la entidad para la que se va a mostrar el formulario. 

**Tipo**: `string`

## <a name="formid"></a>formId

Identificador de la instancia de formulario que se va a mostrar.

**Tipo**: `string`

## <a name="height"></a>height

Alto de la ventana de formulario que se mostrará, en píxeles.

**Tipo**: `number`

## <a name="openinnewwindow"></a>openInNewWindow

Si se muestra el formulario en una nueva ventana

**Tipo**: `boolean`

## <a name="usequickcreateform"></a>useQuickCreateForm

Si se abre un formulario de creación rápida. Si no especifica esto, se pasa false de forma predeterminada. 

**Tipo**: `boolean`

## <a name="width"></a>width

Ancho de la ventana de formulario que se mostrará, en píxeles.

**Tipo**: `boolean`

## <a name="windowposition"></a>windowPosition

Especifica la posición de la ventana en la pantalla.

**Tipo**: `number`

El valor de windowPosition es un número con los siguientes valores posibles:

|Value|Puesto|
|---|---|
|1|Centrar|
|2|A un lado|


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)