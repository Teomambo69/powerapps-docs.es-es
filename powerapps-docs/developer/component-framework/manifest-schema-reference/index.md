---
title: Referencia del esquema del manifiesto del marco de componentes de PowerApps | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 045a395b-4475-48dd-8f67-6bc2b33cd89c
ms.openlocfilehash: 8f58f10f6a3695615ddc3b58b540c59240af9641
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346380"
---
# <a name="manifest-schema-reference"></a>Referencia de esquema del manifiesto

Esta sección contiene documentación de referencia del esquema del manifiesto generado mediante la CLI de PowerApps.

> [!IMPORTANT]
> En la pestaña **disponible para** se muestran los elementos que son compatibles con las aplicaciones controladas por modelos y las aplicaciones de lienzo (versión preliminar experimental). Se recomienda comprobar la sección **disponible** para cada propiedad individual, ya sea compatible o no. Por ejemplo, el elemento de **código** es compatible con aplicaciones controladas por modelos y aplicaciones de lienzo, pero las propiedades **html** e **IMG** de los elementos de **código** no admiten aplicaciones de lienzo. 

|Elemento|Descripción|Disponible para|
|----|-----------|-----|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|Aplicaciones controladas por modelos|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|Aplicaciones controladas por modelos|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|Aplicaciones controladas por modelos|
|[manifest](manifest.md)|El manifiesto es el archivo de metadatos que define un componente. Es un documento XML en el que se describe lo siguiente:<br/> - Espacio de nombres del componente.<br/> - Tipo de datos con el que se puede configurar, ya sea un campo o un conjunto de datos.<br/> - Cualquier propiedad que se puede configurar en la aplicación cuando se agrega el componente.<br/> - Lista de archivos de recursos que necesita el componente.<br/> - Uno de esos archivos debe ser un recurso web JavaScript. Este elemento JavaScript debe incluir una función que cree una instancia de un objeto. Así, se implementa una interfaz que expone los métodos que son necesarios para que el componente funcione. A esto se le denomina “biblioteca de implementación de componentes”.<br/> - Nombre de una función de JavaScript en la biblioteca de implementación de componentes que devolverá un objeto que se aplica a la interfaz necesaria.<br/> Cuando alguien configura un componente en la aplicación, los datos del manifiesto filtran los componentes disponibles para que solo los componentes válidos para el contexto estén disponibles para la configuración. Las propiedades definidas en el manifiesto para un componente se representan como campos de configuración para que el usuario que configure el control pueda especificar valores. A continuación, estos valores de propiedad están disponibles para la función del componente en tiempo de ejecución.|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[property-set](property-set.md)|[!INCLUDE [property-set-description](includes/property-set-description.md)]|Aplicaciones controladas por modelos|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[uso de características](feature-usage.md)|El elemento de uso de características actúa como contenedor alrededor de los elementos de `uses-feature`, que a su vez permiten a los desarrolladores declarar qué características desea usar su componente. Si no hay ningún elemento use-Feature definido, el elemento de uso de características no es necesario.|Aplicaciones controladas por modelos|

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)