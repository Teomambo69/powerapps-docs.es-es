---
title: RetrieveMultipleResponse | Microsoft Docs
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
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
ms.openlocfilehash: 0e5b2cad047bcf91b0c63e27c4a7ceb35c1ed538
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341320"
---
# <a name="retrievemultipleresponse"></a>RetrieveMultipleResponse

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos

## <a name="properties"></a>Propiedades

### <a name="entities"></a>jurídica

Matriz de objetos JSON, donde cada objeto representa el registro de entidad recuperado que contiene los atributos y sus valores.

**Tipo**: `Entity[]`

### <a name="nextlink"></a>nextLink

Si el número de registros que se recuperan es mayor que el valor especificado en el parámetro `maxPageSize` en la solicitud, este atributo devuelve la dirección URL para devolver el siguiente conjunto de registros.

**Tipo**: `string`


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)