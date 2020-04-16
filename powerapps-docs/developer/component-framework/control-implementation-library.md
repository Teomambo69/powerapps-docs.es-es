---
title: Biblioteca de implementación del componente | Microsoft Docs
description: Crear componentes de código con JavaScript o TypeScript
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: febda5c1c52b482db449b370d114c771cb2984eb
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162173"
---
# <a name="component-implementation-library"></a>Biblioteca de implementación del componente

Implementar la biblioteca de componentes es uno de los pasos clave cuando está desarrollando componentes personalizados con Power Apps component framework. Los desarrolladores pueden implementar la biblioteca de componentes con TypeScript.

Cada componente de código debe tener una biblioteca que incluya la definición de una función que devuelva un objeto que implemente los métodos descritos en la interfaz de componentes de código. 

El objeto implementa los siguientes métodos:

- [init](reference/control/init.md) (requerido)
- [updateView](reference/control/updateview.md) (requerido)
- [getOutputs](reference/control/getoutputs.md) (opcional)
- [destroy](reference/control/destroy.md) (requerido)

Estos métodos controlan el ciclo de vida del componente de código.

