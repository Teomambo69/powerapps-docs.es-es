---
title: getClient | Microsoft Docs
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
ms.assetid: 4b7c18f8-cd00-4f39-8f88-ed9306d6a055
ms.openlocfilehash: 503d24d97061548132f912351a58fbce68082d18
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345759"
---
# <a name="getclient"></a>getClient

[!INCLUDE [getclient-description](includes/getclient-description.md)]

## <a name="syntax"></a>Sintaxis

`context.client.getClient()`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental) 



## <a name="return-value"></a>Valor devuelto

Tipo: `String`

Devuelve un valor que indica en qué cliente se está ejecutando el script.

|||
|-----|-----|
|Web| Aplicación web o interfaz unificada|
|Outlook| Outlook|
|Movilidad| Aplicación móvil|



### <a name="related-topics"></a>Temas relacionados

[Cliente](../client.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)