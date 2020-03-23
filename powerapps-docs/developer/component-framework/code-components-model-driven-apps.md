---
title: Componentes de código para aplicaciones basadas en modelo | Microsoft Docs
description: Crear componentes de código para aplicaciones de lienzo
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 02/24/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: 4380d99439b9103ea40800ea8a5a20e1e13768d8
ms.sourcegitcommit: 27cb5ad024d43f208ef6acfbea456a05df3edf8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "3082825"
---
# <a name="code-components-for-model-driven-apps"></a>Componentes de código para aplicaciones basadas en modelo

Power Apps component framework ofrece a los desarrolladores la capacidad de ampliar las visualizaciones en aplicaciones basadas en modelo. Los desarrolladores profesionales pueden crear, depurar, importar y agregar componentes de código a aplicaciones basadas en modelo utilizando [Power Apps CLI](get-powerapps-cli.md). Puede agregar componentes de código a campos, cuadrículas y subcuadrículas en aplicaciones basadas en modelo. 

> [!IMPORTANT]
> Power Apps component framework está habilitado para aplicaciones basadas en modelo de forma predeterminada. Vea [Componentes de código para aplicaciones de lienzo](component-framework-for-canvas-apps.md) para aprender a habilitar Power Apps component framework para aplicaciones de lienzo.

## <a name="implementing-code-components"></a>Implementar componente de código

Antes de comenzar a crear componentes de código, asegúrese de que ha instalado todos los requisitos previos necesarios para desarrollar componentes utilizando el Power Apps component framework. 

El tema [Cree su primer componente de código](implementing-controls-using-typescript.md) demuestra el proceso paso a paso para crear componentes de código.

## <a name="add-code-components-to-model-driven-apps"></a>Agregar componentes de código a aplicaciones basadas en modelo

Para agregar componentes de código a un campo o una entidad en aplicaciones basadas en modelo, vea [Agregar componentes de código a aplicaciones basadas en modelo](add-custom-controls-to-a-field-or-entity.md).

> [!div class="mx-imgBorder"] 
> ![Agregar control deslizante lineal](../../maker/model-driven-apps/media/add-slider.PNG "Agregar control deslizante lineal")

> [!div class="mx-imgBorder"]
> ![Componente de cuadrícula de conjunto de datos](media/add-dataset-component.png "Componente de cuadrícula de conjunto de datos")

## <a name="update-existing-code-components"></a>Actualizar componentes de código existentes

Cada vez que actualice los componentes del código y desee ver los cambios en tiempo de ejecución, deberá colocar el atributo de versión en el archivo de manifiesto. Se recomienda saltar siempre la versión del componente cada vez que haga cambios.

## <a name="see-also"></a>Vea también

[Información general sobre Power Apps component framework](overview.md)<br/>
[Crear el primer componente de código](implementing-controls-using-typescript.md)
