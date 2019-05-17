---
title: Biblioteca de implementación del componente | Microsoft Docs
description: Crear componentes personalizados con JavaScript o TypeScript
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
---

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Implementar la biblioteca de componentes es uno de los pasos clave cuando está desarrollando componentes personalizados con el marco de componentes de PowerApps. Los desarrolladores pueden implementar la biblioteca de componentes con TypeScript. Cada componente personalizado debe tener una biblioteca que incluya la definición de una función que devuelva un objeto que implemente los métodos descritos en la interfaz de componentes personalizados. 

> [!IMPORTANT]
> - El marco de componentes de PowerApps es una característica de vista previa.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 
> - [!INCLUDE[cc_preview_features_no_MS_support](../../includes/cc-preview-features-no-ms-support.md)]

El objeto implementa los siguientes métodos:

- [init](reference/control/init.md) (requerido)
- [updateView](reference/control/updateview.md) (requerido)
- [getOutputs](reference/control/getoutputs.md) (opcional)
- [destroy](reference/control/destroy.md) (requerido)

Estos métodos controlan el ciclo de vida del componente personalizado.

