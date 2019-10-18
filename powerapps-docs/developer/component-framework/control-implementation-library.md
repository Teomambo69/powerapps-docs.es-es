---
title: Biblioteca de implementación de componentes | Microsoft Docs
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
ms.openlocfilehash: 31b7d2b30a1ef83ca4400011d50854713cb260f6
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347254"
---
# <a name="component-implementation-library"></a>Biblioteca de implementación de componentes

La implementación de la biblioteca de componentes es uno de los pasos clave para desarrollar componentes de código mediante el marco de componentes de PowerApps. Los desarrolladores pueden implementar la biblioteca de componentes mediante TypeScript. Cada componente de código debe tener una biblioteca que incluya la definición de una función que devuelva un objeto que implemente los métodos descritos en la interfaz del componente de código. 

El objeto implementa los métodos siguientes:

- [init](reference/control/init.md) (obligatorio)
- [updateView](reference/control/updateview.md) (obligatorio)
- [getOutputs](reference/control/getoutputs.md) (opcional)
- [destruir](reference/control/destroy.md) (obligatorio)

Estos métodos controlan el ciclo de vida del componente de código.

