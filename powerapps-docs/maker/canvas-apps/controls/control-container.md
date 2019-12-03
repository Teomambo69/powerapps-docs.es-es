---
title: 'Control contenedor: referencia | Microsoft Docs'
description: Información sobre el control contenedor, con propiedades y ejemplos
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 9/20/2019
ms.author: emcoope
ms.reviewer: tapanm-msft
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e22800dc929c32f0a605137b6dc94820b984459c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727334"
---
# <a name="container-control-in-power-apps-experimental"></a>Control de contenedor en Power apps (experimental)
Proporciona la capacidad de crear una jerarquía.

> [!IMPORTANT]
> Se trata de una característica experimental. Las características experimentales pueden cambiar radicalmente o desaparecer por completo en cualquier momento.
> Para obtener más información, lea [Descripción de las características experimentales y de vista previa en Power apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview).

## <a name="description"></a>Descripción
 El contenedor puede contener un conjunto de controles y tiene sus propias propiedades. 

Puede empezar por insertar un contenedor en blanco y, a continuación, personalizarlo agregando controles a él, cambiando su tamaño, moviéndolo, ocultándolo y realizando otros cambios. También puede empezar con una serie de controles, seleccionarlos y agregarlos a un contenedor mediante el menú contextual de la vista de árbol o hacer clic con el botón derecho en el lienzo. 

## <a name="properties"></a>Propiedades
**[BorderColor](properties-color-border.md)** : el color de un borde del control.

**[BorderStyle](properties-color-border.md)** : si el borde del control es **Solid**, **Dashed**, **Dotted** o **None**.

**[BorderThickness](properties-color-border.md)** : el grosor de un borde del control.

**[Fill](properties-color-border.md)** : el color de fondo de un control.

**[Height](properties-size-location.md)** : la distancia entre los bordes superior e inferior de un control.

**[Width](properties-size-location.md)** : la distancia entre los bordes derecho e izquierdo de un control.

**[Visible](properties-core.md)** : indica si un control aparece o está oculto.

**[X](properties-size-location.md)** : la distancia entre el borde izquierdo de un control y el borde izquierdo de su contenedor primario (la pantalla si no hay un contenedor primario). 

**[Y](properties-size-location.md)** : la distancia entre el borde superior de un control y el borde superior de su contenedor primario (la pantalla si no hay un contenedor primario). 


## <a name="known-limitations"></a>Limitaciones conocidas

Los contenedores no funcionan con componentes de canvas ni dentro de formularios. 

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

**¿Cuál es la diferencia entre un contenedor y un grupo?**
El grupo de creación es un concepto ligero que se usa para desplazarse por los controles y editar de forma masiva propiedades similares de los controles del grupo. El grupo de creación no afecta al diseño de la aplicación. 

El control contenedor enviado previamente en experimental como un reemplazo para el grupo de creación cambiado de nombre como grupo mejorado. Se cambió el nombre al control contenedor, ya que hay un valor en un grupo de creación ligero y un control contenedor strutured con propiedades adicionales. 

