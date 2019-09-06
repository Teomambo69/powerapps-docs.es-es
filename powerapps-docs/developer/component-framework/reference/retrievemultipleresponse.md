---
title: RetrieveMultipleResponse | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
---

# <a name="retrievemultipleresponse"></a>RetrieveMultipleResponse

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="properties"></a>Propiedades

## <a name="entities"></a>entities

Una matriz de objetos JSON, donde cada objeto representa el registro de entidad recuperada que contiene los atributos y sus valores.

**Tipo**: `Entity[]`

## <a name="nextlink"></a>nextLink

Si el número de registros que se están recuperando es mayor que el valor especificado en el parámetro 'maxPageSize' en la solicitud, este atributo devuelve la dirección URL para devolver el siguiente conjunto de registros.

**Tipo**: `string`


### <a name="related-topics"></a>Temas relacionados

[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)