---
title: Recuperar la lista de reglas | Microsoft Docs
description: Aprenda a formar una solicitud GET mediante la API web del comprobador de Power Apps para recuperar la lista de reglas disponibles.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: a8dc3019-c49e-48e4-a646-8a3a3fecd3a6
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
ms.openlocfilehash: 54db18819f22b01195fa1462395fc2be17f5ec74
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861825"
---
# <a name="retrieve-the-list-of-rules"></a>Recuperar la lista de reglas

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Las reglas se agrupan mediante un conjunto de reglas. Una regla puede no estar en ningún conjunto de reglas o en varios. Use una solicitud `GET` para obtener una lista de todas las reglas disponibles, de reglas en un conjunto de reglas o de conjuntos de reglas llamando a la API `[Geographical URI]/api/rule`. Hay algunas variaciones para llamar a esta API, sin embargo, el uso más común es recuperar la lista de reglas para un conjunto de reglas específico.

> [!NOTE]
>  Esta API no requiere un símbolo OAuth, pero puede aceptar uno si se proporciona.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Encabezados

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|Accept-Language|Cadena|El código de idioma (por ejemplo, en-US). El predeterminado es en-US.|no

<a name="bkmk_params"></a>

## <a name="parameters"></a>Parámetros

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|ruleset|Cadena|El nombre o el identificador del conjunto de reglas o una lista de Id. del conjunto de reglas, o nombres separados por coma o punto y coma (por ejemplo, “Comprobador de soluciones”).|no|
|includeMessageFormats|bool|Cuando se establezca como `true`, la lista de variaciones posibles del mensaje se incluyen en los resultados de las solicitudes de idiomas, si procede. Esto resulta útil para traducciones a varios idiomas. Si no necesario, no proporcione este parámetro o establezca `false` como valor, ya que este parámetro incrementará el tamaño de la respuesta y puede aumentar el tiempo de procesamiento.|no|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Respuestas esperadas

|Código de estado HTTP|Escenario|Resultado|
|---|---|---|
|200|Uno o varios resultados se encontraron|Vea el ejemplo siguiente. Se pueden devolver uno o varios resultados.|
|204|No se encontraron resultados|No hay resultados en el cuerpo de respuesta.|

### <a name="expected-response-body"></a>Cuerpo de la respuesta esperada

En la siguiente tabla se esboza la estructura de la respuesta para cada solicitud (respuesta HTTP 200 solo).

|Propiedad|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|código|Cadena|El identificador de la regla, algunas veces denominado identificador de la regla.|Sí|
|summary|Cadena|Un resumen de la regla.|Sí|
|description|Cadena|Descripción más detallada de la regla.|Sí|
|guidanceUrl|URI|La dirección URL en la que encontrar instrucciones publicadas. Puede haber algunos casos donde no haya ningún artículo de instrucciones de ayuda dedicado.|Sí|
|include|Booleano|Señala al servicio que la regla se incluirá en el análisis. Será `true` para esta API.|No|
|messageTemplates|array|Este valor de propiedad se incluye únicamente cuando `includeMessageFormats` es `true`.|No|
|messageTemplates.ruleId|Cadena| Devuelve el mismo valor de identificador que la propiedad `code`.|Sí|
|messageTemplates.messageTemplateId|Cadena| Identificador usado en el informe Static Analysis Results Interchange Format (SARIF) para indicar una variación de mensaje de problema para la regla.|Sí|
|messageTemplates.messageTemplate|Cadena|El texto de la variación de mensaje para el escenario de problema sobre el que informa la regla. Ésta es una cadena de formato que puede contener tokens en los que los argumentos sumnistrados en el informe SARIF se pueden usar para generar un mensaje detallado.|Sí|

<a name="bkmk_retrieveForRuleset"></a>

## <a name="example-retrieve-rules-for-a-ruleset-in-another-language"></a>Ejemplo: recuperar reglas para un conjunto de reglas en otro idioma

Este ejemplo devuelve los datos para todas las reglas del conjunto de reglas *Comprobador de soluciones* en idioma francés. Si el idioma deseado es inglés, quite solo el encabezado Accept-Language.

**Solicitud**

```http
GET [Geographical URI]/api/rule?ruleset=083A2EF5-7E0E-4754-9D88-9455142DC08B&api-version=1.0
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
Accept: application/json
Content-Type: application/json; charset=utf-8
Accept-Language: fr
```

**Respuesta**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "description": "Ne pas implémenter d’activités de workflow Microsoft Dynamics CRM 4.0",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm4-wf&client=PAChecker",
        "include": true,
        "code": "il-avoid-crm4-wf",
        "summary": "Ne pas implémenter d’activités de workflow Microsoft Dynamics CRM 4.0",
        "howToFix": {
            "summary": ""
        }
    },
    {
        "description": "Utiliser InvalidPluginExecutionException dans des plug-ins et activités de workflow",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-standard-exception&client=PAChecker",
        "include": true,
        "code": "il-use-standard-exception",
        "summary": "Utiliser InvalidPluginExecutionException dans des plug-ins et activités de workflow",
        "howToFix": {
            "summary": ""
        }
    },
...
]
```

<a name="bkmk_retrieveAll"></a>

## <a name="example-retrieve-all"></a>Ejemplo: recuperar todo

Este ejemplo devuelve los datos de todas las reglas disponibles.

**Solicitud**

```http
GET [Geographical URI]/api/rule?api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
```

**Respuesta**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "description": "Retrieve specific columns for an entity via query APIs",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-specify-column&client=PAChecker",
        "include": true,
        "code": "il-specify-column",
        "summary": "Retrieve specific columns for an entity via query APIs",
        "howToFix": {
            "summary": ""
        }
    },
    {
        "description": "Do not duplicate plug-in step registration",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=meta-remove-dup-reg&client=PAChecker",
        "include": true,
        "code": "meta-remove-dup-reg",
        "summary": "Do not duplicate plug-in step registration",
        "howToFix": {
            "summary": ""
        }
    },
...
]
```

<a name="bkmk_retrieveForRuleset"></a>

## <a name="example-retrieve-for-a-ruleset-with-message-formats"></a>Ejemplo: recuperación para un conjunto de reglas con formatos de mensaje

Este ejemplo devuelve los datos para todas las reglas del conjunto de reglas *Comprobador de soluciones* en idioma francés. Si el idioma deseado es inglés, quite solo el encabezado Accept-Language.

**Solicitud**

```http
GET [Geographical URI]/api/rule?ruleset=083A2EF5-7E0E-4754-9D88-9455142DC08B&includeMessageFormats=true&api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
```

**Respuesta**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "description": "Do not implement Microsoft Dynamics CRM 4.0 workflow activities",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-avoid-crm4-wf&client=PAChecker",
        "include": true,
        "code": "il-avoid-crm4-wf",
        "summary": "Do not implement Microsoft Dynamics CRM 4.0 workflow activities",
        "howToFix": {
            "summary": ""
        },
        "messageTemplates": [
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message1",
                "messageTemplate": "Update the {0} class to derive from System.Workflow.Activities.CodeActivity, refactor Execute method implementation, and remove Microsoft.Crm.Workflow.CrmWorkflowActivityAttribute from type"
            },
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message2",
                "messageTemplate": "Change the {0} property's type from {1} to {2} Argument &lt;T&gt; type"
            },
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message3",
                "messageTemplate": "Replace the Microsoft.Crm.Workflow.Crm{0}Attribute with Microsoft.Xrm.Sdk.Workflow.{0}Attribute"
            },
            {
                "ruleId": "il-avoid-crm4-wf",
                "messageTemplateId": "message4",
                "messageTemplate": "Remove the {0} System.Workflow.ComponentModel.DependencyProperty type field"
            }
        ]
    },
    {
        "description": "Use InvalidPluginExecutionException in plug-ins and workflow activities",
        "guidanceUrl": "https://go.microsoft.com/fwlink/?LinkID=398563&error=il-use-standard-exception&client=PAChecker",
        "include": true,
        "code": "il-use-standard-exception",
        "summary": "Use InvalidPluginExecutionException in plug-ins and workflow activities",
        "howToFix": {
            "summary": ""
        },
        "messageTemplates": [
            {
                "ruleId": "il-use-standard-exception",
                "messageTemplateId": "message1",
                "messageTemplate": "An unguarded throw of type {0} was detected. Refactor this code to either throw an exception of type InvalidPluginExecutionException or guard against thrown exceptions of other types."
            },
            {
                "ruleId": "il-use-standard-exception",
                "messageTemplateId": "message2",
                "messageTemplate": "An unguarded rethrow of type {0} was detected. Refactor this code to either throw an exception of type InvalidPluginExecutionException or guard against thrown exceptions of other types."
            }
        ]
    },
...
]
```

### <a name="see-also"></a>Vea también

[Usar la API web del comprobador de Power Apps](overview.md)<br />
[Recuperar la lista de conjuntos de reglas](retrieve-rulesets.md)<br />
[Cargar un archivo](upload-file.md)<br />
[Invocar análisis](analyze.md)<br />
[Comprobar estado de análisis](check-status.md)<br />