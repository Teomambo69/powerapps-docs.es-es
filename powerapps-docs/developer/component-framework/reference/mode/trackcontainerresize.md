---
title: TrackContainerResize | Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: c5f482c2-dde2-460b-89a7-39e0efcc5704
ms.openlocfilehash: 8f9bc1ef17bdcb762e992d9f77dcdcd7ba1e8c50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342562"
---
# <a name="trackcontainerresize"></a>trackContainerResize

[!INCLUDE [trackcontainerresize-description](includes/trackcontainerresize-description.md)].

Si el contexto primario que hospeda el componente proporciona un límite en el alto de las aplicaciones controladas por modelos, lo mismo se aplica correctamente al componente secundario. Sin embargo, en la mayoría de los escenarios, el contexto primario no restringe el alto del componente, por lo que recibe "-1" para indicar que puede crecer más.

En las aplicaciones de Canvas, el contexto primario siempre proporciona el alto y el ancho al componente por naturaleza del editor de arrastrar y colocar.

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="syntax"></a>Sintaxis

`context.mode.trackContainerResize(value)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|value|`Boolean`|Sí|`True` si los controles necesitan realizar un seguimiento del tamaño del contenedor, el componente obtendrá allocatedWidth o allocatedHeight.|


### <a name="related-topics"></a>Temas relacionados

[Mode](../mode.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)
