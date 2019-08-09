---
title: Comprobar estado de análisis | Microsoft Docs
description: Aprenda a formar solicitud GET mediante la API web del comprobador de PowerApps para comprobar el estado de un trabajo de solicitud de análisis.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 6e2abe2d-2205-4d15-9e0f-5975ccc0484e
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
---

# <a name="check-for-analysis-status"></a>Comprobar estado de análisis

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Se devuelve una dirección URL como parte del encabezado `Location` en respuesta a una solicitud a la API de `analyze`. Debe usarse para consultar mediante `GET` de HTTP para el estado del trabajo de análisis. Cuando finalice el trabajo de análisis el cuerpo de respuesta incluirá la dirección URL o la lista de direcciones URL en la que la salida de resultados se puede descargar. Siga llamando a este URI hasta que un código de estado HTTP de 200 se devuelva. Mientras el trabajo aún se está ejecutando, se devolverá un código de estado HTTP de 202 con el encabezado `Location` que contiene este mismo identificador URI que se devolvió de `analyze`. Una vez que se devuelva una respuesta 200, la propiedad `resultFileUris` incluirá la ubicación o la lista de ubicaciones descargables de la salida, que se incluye en un archivo zip. Un archivo con formato [Static Analysis Results Interchange Format (SARIF)](https://sarifweb.azurewebsites.net) V2 se incluye dentro de esta descarga de zip, que es un archivo con formato `JSON` que contiene los resultados del análisis. El cuerpo de respuesta contendrá un objeto `IssueSummary` que contiene un resumen de recuento de problemas encontrados.

> [!NOTE]
>  Se recomienda esperar entre 15 y 60 segundos entre comprobaciones de estado. El análisis toma normalmente entre 1 y 5 minutos en ejecutarse.<br />
>  Este API requiere un símbolo de OAuth que deben ser un símbolo para la misma aplicación cliente que inició el trabajo de análisis.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Encabezados

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|Autorización|Cadena|El símbolo de portador de OAuth 1 con notificación de identificador de aplicación AAD.|sí|
|x-ms-tenant-id|GUID|El identificador del inquilino para la aplicación.|sí|
|x-ms-correlation-id|GUID|El identificador de la ejecución del análisis. Debe proporcionar el mismo Id. para la ejecución completa (cargar, analizar, estado)|sí|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Respuestas esperadas

|Código de estado HTTP|Escenario|Resultado|
|---|---|---|
|200|Uno o varios resultados se encontraron|Vea el ejemplo siguiente. Un resultado será devuelto.|
|202|Todavía en procesamiento|Vea el ejemplo siguiente. Un resultado será devuelto.|
|403|Prohibida|El solicitante no es lo mismo que originador de la solicitud de análisis.|
|404|No se ha encontrado|No se puede encontrar la solicitud de análisis con referencia proporcionada en la dirección URL.|

### <a name="expected-response-headers"></a>Encabezados de respuesta esperada

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|Location|uri|URI para usar en la consulta del estado actual y para obtener los resultados|sí|

### <a name="expected-response-body"></a>Cuerpo de la respuesta esperada

En la siguiente tabla se esboza la estructura de la respuesta para cada solicitud (respuesta HTTP 200 o 202 solo).

|Propiedad|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|privacyPolicy|Cadena|El URI de la directiva de privacidad.|Sí|
|progreso|int|Un valor que va de 0-100 de porcentaje completado, donde 10 significa que el procesamiento está aproximadamente completado al 10%.|Sí|
|runCorrelationId|GUID|El identificador de solicitud que se incluye en cada solicitud. Se puede usar para correlacionar a la solicitud, si es necesario.|Sí|
|estado|Cadena|`InProgress` se vuelve cuando el trabajo aún se está procesando. `Failed` se vuelve cuando se produjo un problema catastrófico al procesar el trabajo en el servidor. Debe haber más detalles en la propiedad de error. `Finished` se vuelve cuando el trabajo se ha completado correctamente sin problemas. `FinishedWithErrors` se vuelve cuando el trabajo se ha completado correctamente, sin embargo, una o varias reglas no se pudieron completar sin errores. Se trata simplemente una señal para saber que el informe no puede completarse. Microsoft conoce estos problemas en el backend y trabajará para diagnosticar y abordar estos aspectos.|Sí|
|resultFileUris|matriz de cadenas|Una lista de URI que permite la descarga directa de la salida. Debe haber uno por archivo que se incluyó en la llamada de la API de análisis original.|Núm. Sólo se incluye cuando el procesamiento se ha completado.|
|issueSummary|IssueSummary|Propiedades indicadas a continuación|Núm. Sólo se incluye cuando el procesamiento se ha completado.|
|issueSummary.criticalIssueCount|int|Recuento de problemas identificados que tienen una gravedad crítica en el resultado|Sí|
|issueSummary.highIssueCount|int|Recuento de problemas identificados que tienen una gravedad alta en el resultado|Sí|
|issueSummary.mediumIssueCount|int|Recuento de problemas identificados que tienen una gravedad media en el resultado|Sí|
|issueSummary.lowIssueCount|int|Recuento de problemas identificados que tienen una gravedad baja en el resultado|Sí|
|issueSummary.informationalIssueCount|int|Recuento de problemas identificados que tienen una gravedad informativa en el resultado|Sí|

<a name="bkmk_checkStatusDone"></a>

## <a name="example-status-check-when-done"></a>Ejemplo: comprobación de estado al terminar

Este ejemplo genera una llamada de comprobación de estado con el resultado como completado.

**Solicitud**

```http
GET [Geographical URI]/api/status/9E378E56-6F35-41E9-BF8B-C0CC88E2B832&api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506
```

**Respuesta**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
    "privacyPolicy":"https://go.microsoft.com/fwlink/?LinkID=310140",
    "progress":100,
    "resultFileUris":["https://fakeblob.blob.core.windows.net/report-files/mySolution.zip?sv=2017-11-09&sr=b&sig=xyz&se=2019-06-11T20%3A27%3A59Z&sp=rd"],"runCorrelationId":"9E378E56-6F35-41E9-BF8B-C0CC88E2B832","status":"Finished","issueSummary":
    {
        "informationalIssueCount":0,
        "lowIssueCount":0,
        "mediumIssueCount":302,
        "highIssueCount":30,
        "criticalIssueCount":0
    }
}
```


### <a name="see-also"></a>Vea también

[Usar la API web del comprobador de PowerApps](overview.md)<br />
[Recuperar la lista de conjuntos de reglas](retrieve-rulesets.md)<br />
[Recuperar la lista de reglas](retrieve-rules.md)<br />
[Cargar un archivo](upload-file.md)<br />
[Invocar análisis](analyze.md)<br />
