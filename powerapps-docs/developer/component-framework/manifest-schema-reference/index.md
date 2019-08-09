---
title: Referencia de esquema de manifiesto del marco de componentes de PowerApps | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: null
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
---

# <a name="manifest-schema-reference"></a>Referencia de esquema de manifiesto

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Esta sección contiene la documentación de referencia del esquema de manifiesto generado con el PowerApps CLI.

|Elemento|Descripción|
|----|-----------|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|
|[manifiesto](manifest.md)|El manifiesto es el archivo de metadatos que define un componente. Es un documento XML que describe<br/> - El espacio de nombres del componente.<br/> - El tipo de datos que se puede configurar, un campo o un conjunto de datos.<br/> - Las propiedades que se pueden configurar en la aplicación cuando se agrega el componente.<br/> - Una lista de archivos de recursos que el componente necesita.<br/> - Uno de ellos debe ser un recurso web de JavaScript. Este JavaScript debe incluir una función que creará instancias de un objeto. Esto implementa una interfaz que expone métodos que son necesarios para que funcione el componente. Esto se llama la biblioteca de implementación de componentes.<br/> - El nombre de una función JavaScript en la biblioteca de implementación del componente que devolverá un objeto que aplica la interfaz requerida.<br/> Cuando alguien configura un componente en la aplicación, los datos del manifiesto filtran los componentes disponibles para que sólo los componentes válidos para el contexto estén disponibles para configuración. Las propiedades definidas en el manifiesto para un componente se generan como campos de configuración para que la persona que configura el control pueda especificar valores. Estos valores de propiedad están disponibles entonces para la función de componente en tiempo de ejecución.|
|[propiedad](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|
|[recursos](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|


### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)