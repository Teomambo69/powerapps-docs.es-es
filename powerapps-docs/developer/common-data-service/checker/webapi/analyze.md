---
title: Invocar análisis | Microsoft Docs
description: Aprenda a formar solicitud POST mediante la API web del comprobador de PowerApps para iniciar el trabajo de solicitud de análisis.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a2c771f4-7eb6-4445-af2d-f775619ac3e8
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

# <a name="invoke-analysis"></a>Invocar análisis

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

Para iniciar un trabajo de análisis se envía una solicitud `POST` a la ruta `analyze`. El análisis puede ser un proceso largo que normalmente dura más de un minuto. La API primero realiza cierta validación básica, inicia la solicitud en el backend enviando un trabajo, y después responde con un código de estado de 202 y un encabezado `Location` o con los detalles de error apropiados. El valor del encabezado `Location` es una dirección URL que puede usarse para comprobar el estado de la solicitud y obtener las direcciones URL de los resultados. Hay distintas opciones a través de la acción `POST` para adaptar el trabajo en función de sus criterios, como la lista de reglas o conjuntos de reglas, archivos para excluir del análisis, etc. Puede iniciar el análisis con la siguiente `[Geographical URL]/api/analyze?api-version=1.0`.


> [!NOTE]
>  Se recomienda esperar entre 15 y 60 segundos entre comprobaciones de estado. El análisis toma normalmente entre 1 y 5 minutos en ejecutarse.<br /> Esta API requiere un símbolo de OAuth.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Encabezados

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|Autorización|Cadena|El símbolo de portador de OAuth 1 con notificación de identificador de aplicación Azure Active Directory (AAD).|sí|
|x-ms-tenant-id|GUID|El identificador del inquilino para la aplicación.|sí|
|x-ms-correlation-id|GUID|El identificador de la ejecución del análisis. Debe proporcionar el mismo Id. para la ejecución completa (cargar, analizar, estado).|sí|
|Aceptar|objeto|`application/json, application/x-ms-sarif-v2`|sí|
|Accept-Language|Cadena|El código o los códigos de idioma (por ejemplo, en-US). El predeterminado es en-US. Si se proporcionan varios idiomas, el primero será el principal. No obstante, se incluirán todas las traducciones (si se admite el idioma).|no

<a name="bkmk_body"></a>

## <a name="body"></a>Cuerpo

### <a name="commonly-used-options"></a>Opciones de uso general:

|Propiedad|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|sasUriList|matriz de cadenas|Una lista de URI que proporciona el acceso de servicio para descargar una única solución, un archivo zip que contiene varios archivos de solución o un paquete.|Sí|
|ruleSets|matriz de personalizado|0 o más|No|
|ruleSets.id|guid|El identificador del conjunto de reglas, que se encuentra consultando la API del conjunto de reglas.|No, pero normalmente es lo que desearía usar. Debe usar esto o ruleCodes.|
|ruleCodes.code|Cadena|El identificador de la regla deseada, que se encuentra consultando las API del conjunto de reglas y de la regla.|No, debe usar esto o ruleSets.|
|fileExclusions|matriz de cadenas|Una lista de nombres de archivo o de patrones de nombre para excluir. Hay compatibilidad para el uso de “*” como comodín al principio y/o al final de un nombre de archivo (p. ej., \*jquery.dll y \*jquery\*).|No|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Respuestas esperadas

|Código de estado HTTP|Escenario|Resultado|
|---|---|---|
|202|La solicitud de análisis se aceptó y el URI de comprobación de estado se devolvió en el encabezado `Location`|Sin cuerpo de resultados
|400|Un archivo no zip se envió, parámetros incorrectos, o un archivo se incluyó con un virus|Sin cuerpo de resultados|
|409|Se envió una solicitud con un valor de encabezado `x-ms-correlation-id` duplicado|Sin cuerpo de resultados|

### <a name="expected-response-headers"></a>Encabezados de respuesta esperada

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|Location|URI|URL para usar en la consulta del estado actual y para obtener los resultados|sí|

<a name="bkmk_analyzeExample"></a>

## <a name="example-initiate-an-analysis"></a>Ejemplo: iniciar un análisis

Este es un ejemplo de iniciar un trabajo de análisis con el conjunto de reglas _AppSource Certification_, un solo archivo, y excluyendo los archivos que contengan el texto _jquery_ y _json_ en el nombre.

**Solicitud**

```http
POST [Geographical URI]/api/analyze?api-version=1.0
Accept: application/json
Content-Type: application/json; charset=utf-8
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506

{
    "ruleSets": [{
        "id": "0ad12346-e108-40b8-a956-9a8f95ea18c9"
    }],
    "sasUriList": ["https://testenvfakelocation.blob.core.windows.net/mySolution.zip"],
    "fileExclusions": ["*jquery*", "*json*"]
}
```

**Respuesta**

```http
HTTP/1.1 202 Accepted
Content-Type: application/json; charset=utf-8
Location: [Geographical URI]/api/status/9E378E56-6F35-41E9-BF8B-C0CC88E2B832&api-version=1.0
```

### <a name="see-also"></a>Vea también

[Usar la API web del comprobador de PowerApps](overview.md)<br />
[Recuperar la lista de conjuntos de reglas](retrieve-rulesets.md)<br />
[Recuperar la lista de reglas](retrieve-rules.md)<br />
[Cargar un archivo](upload-file.md)<br />
[Comprobar estado de análisis](check-status.md)<br />