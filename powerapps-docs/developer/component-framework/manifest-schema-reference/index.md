---
title: Referencia de esquema del manifiesto del Marco de componentes de PowerApps | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
manager: ''
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 7cf5f46fedc5708f4e2f30dc30140b8a8d9f3529
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63393863"
---
# <a name="manifest-schema-reference"></a>Referencia de esquema del manifiesto

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

Esta sección contiene documentación de referencia del esquema del manifiesto generado mediante la CLI de PowerApps.

> [!IMPORTANT]
> - Marco de componentes de PowerApps es una característica en vista previa.
> - [!INCLUDE[cc_preview_features_definition](../../../includes/cc-preview-features-definition.md)] 
> - [!INCLUDE[cc_preview_features_no_MS_support](../../../includes/cc-preview-features-no-ms-support.md)]

|Elemento|Descripción|
|----|-----------|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|
|[manifest](manifest.md)|El manifiesto es el archivo de metadatos que define un componente. Es un documento XML en el que se describe lo siguiente:<br/> - Espacio de nombres del componente.<br/> - Tipo de datos con el que se puede configurar, ya sea un campo o un conjunto de datos.<br/> - Cualquier propiedad que se puede configurar en la aplicación cuando se agrega el componente.<br/> - Lista de archivos de recursos que necesita el componente.<br/> - Uno de esos archivos debe ser un recurso web JavaScript. Este elemento JavaScript debe incluir una función que cree una instancia de un objeto. Así, se implementa una interfaz que expone los métodos que son necesarios para que el componente funcione. A esto se le denomina “biblioteca de implementación de componentes”.<br/> - Nombre de una función de JavaScript en la biblioteca de implementación de componentes que devolverá un objeto que se aplica a la interfaz necesaria.<br/> Cuando alguien configura un componente en la aplicación, los datos del manifiesto filtran los componentes disponibles para que solo los componentes válidos para el contexto estén disponibles para la configuración. Las propiedades definidas en el manifiesto para un componente se representan como campos de configuración para que el usuario que configure el control pueda especificar valores. A continuación, estos valores de propiedad están disponibles para la función del componente en tiempo de ejecución.|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|


### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema del manifiesto del Marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del Marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general del Marco de componentes de PowerApps](../overview.md)