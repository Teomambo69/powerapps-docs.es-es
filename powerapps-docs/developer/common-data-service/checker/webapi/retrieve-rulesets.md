---
title: Recuperar la lista de conjuntos de reglas | Microsoft Docs
description: Lea cómo formar una solicitud GET mediante la API web del comprobador de PowerApps para recuperar conjuntos de reglas disponibles.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 23c9391c-1697-47a3-a8f2-eedd5c862874
caps.latest.revision: 21
author: mhuguet
ms.author: mhuguet
ms.reviewer: pehecke
manager: maustinjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e575ca1eaf1c468d8f090bba7e4b84ea767b773c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749582"
---
# <a name="retrieve-the-list-of-rulesets"></a>Recuperar la lista de conjuntos de reglas

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Las reglas se agrupan mediante un conjunto de reglas. Los conjuntos de reglas pueden tener runa o varias reglas sin límite. Una regla puede no estar en ningún conjunto de reglas o en varios. Use una solicitud `GET` para obtener una lista de todos los conjuntos de reglas disponibles, a la API, [URI geográfica]/api/ruleset.

> [!NOTE]
>  Esta API no requiere un símbolo OAuth, pero puede aceptar uno si se proporciona.

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Respuestas esperadas

|Código de estado HTTP|Escenario|Resultado|
|---|---|---|
|200|Uno o varios resultados se encontraron|Vea el ejemplo siguiente. Se pueden devolver uno o varios resultados.|
|204|No se encontraron resultados|No se devuelve ningún cuerpo de respuesta de resultados.|

### <a name="expected-response-body"></a>Cuerpo de la respuesta esperada

En la siguiente tabla se esboza la estructura de la respuesta para cada solicitud (respuesta HTTP 200 solo).

|Propiedad|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|id.|Guid|Identificador del conjunto de reglas|Sí|
|nombre|Cadena|Nombre descriptivo del conjunto de reglas|Sí|

<a name="bkmk_retrieve"></a>

## <a name="example-retrieve-all-rulesets"></a>Ejemplo: recuperar todos los conjuntos de reglas

Este ejemplo devuelve los datos de todos los conjuntos de reglas disponibles.

**Solicitud**

```http
GET [Geographical URI]/api/ruleset?api-version=1.0
Accept: application/json
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
Content-Type: application/json; charset=utf-8
```

**Respuesta**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "id": "083a2ef5-7e0e-4754-9d88-9455142dc08b",
        "name": "AppSource Certification"
    },
    {
        "id": "0ad12346-e108-40b8-a956-9a8f95ea18c9",
        "name": "Solution Checker"
    }
]
```

### <a name="see-also"></a>Vea también

[Usar la API web del comprobador de PowerApps](overview.md)<br />
[Recuperar la lista de reglas](retrieve-rules.md)<br />
[Cargar un archivo](upload-file.md)<br />
[Invocar análisis](analyze.md)<br />
[Comprobar estado de análisis](check-status.md)<br />