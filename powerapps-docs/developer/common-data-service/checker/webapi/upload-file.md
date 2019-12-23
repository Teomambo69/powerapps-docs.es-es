---
title: Cargar un archivo para análisis | Microsoft Docs
description: Lea cómo formar una solicitud POST mediante la API web del comprobador de Power Apps para cargar un archivo para analizar.
ms.custom: ''
ms.date: 06/04/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 08d7d73b-1377-4d3f-b8ef-5c89b19dd735
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
ms.openlocfilehash: f2e83835e80c2393b9b97077c51338c55dd1c3e4
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861805"
---
# <a name="upload-a-file-for-analysis"></a>Cargar un archivo para analizar

[!INCLUDE [cc-beta-prerelease-disclaimer](../../../../includes/cc-beta-prerelease-disclaimer.md)]

La inicialización de un trabajo de análisis requiere una ruta de acceso a un blob de Azure que es accesible por la dirección URL. Se proporciona la capacidad de cargar un archivo en almacenamiento de Azure Blob en la geografía especificada con el servicio de carga. No es necesario que la API de carga se use para ejecutar análisis. Puede cargar utilizando una solicitud `POST` al siguiente: `[Geographical URI]/api/upload?api-version=1.0`. Se admite cargar un archivo de hasta 30 MB de tamaño. Para cualquier elemento mayor deberá proporcionar su almacenamiento Azure accesible de forma externa y el URI de SAS.

> [!NOTE]
>  Esta API requiere un símbolo de OAuth.

<a name="bkmk_headers"></a>

## <a name="headers"></a>Encabezados

|Nombre|Escriba|Valor esperado|¿Obligatorio?|
|---|---|---|---|
|Autorización|Cadena|El símbolo de portador de OAuth 1 con notificación de identificador de aplicación Azure Active Directory (AAD).|sí|
|x-ms-tenant-id|GUID|El identificador del inquilino para la aplicación.|sí|
|x-ms-correlation-id|GUID|El identificador de la ejecución del análisis. Debe proporcionar el mismo Id. para la ejecución completa (cargar, analizar, estado).|sí|
|Tipo de contenido|objeto|multipart/form-data|sí|
|Disposición de contenido|objeto|Incluya los parámetros de nombre y nombre de archivo, por ejemplo:<br />`form-data; name="solution1.zip"; filename="solution1.zip"`|sí|

<a name="bkmk_responses"></a>

## <a name="expected-responses"></a>Respuestas esperadas

|Código de estado HTTP|Escenario|Resultado|
|---|---|---|
|200|La carga fue un éxito|Sin cuerpo de resultados|
|400|Un archivo no zip se envió, parámetros incorrectos, o un archivo se incluyó con un virus|Sin cuerpo de resultados|
|413|El archivo es demasiado grande|Sin cuerpo de resultados|

<a name="bkmk_upload"></a>

## <a name="example-upload-a-file"></a>Ejemplo: cargar un archivo

Este ejemplo demuestra cómo de puede cargar un archivo que debe ser analizado.

**Solicitud**

```http
POST [Geographical URI]/api/upload
Accept: application/json
x-ms-correlation-id: 9E378E56-6F35-41E9-BF8B-C0CC88E2B832
x-ms-tenant-id: F2E60E49-CB87-4C24-8D4F-908813B22506
Content-Type: multipart/form-data
Content-Disposition: form-data; name=mySolution.zip; filename=mySolution.zip
```

**Respuesta**

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

["https://mystorage.blob.core.windows.net/solution-files/0a4cd700-d1d0-4ef8-8318-e4844cc1636c/mySolution.zip?sv=2017-11-09&sr=b&sig=xyz&se=2019-06-11T19%3A05%3A20Z&sp=rd"]
```

### <a name="see-also"></a>Vea también

[Usar la API web del comprobador de Power Apps](overview.md)<br />
[Recuperar la lista de conjuntos de reglas](retrieve-rulesets.md)<br />
[Recuperar la lista de reglas](retrieve-rules.md)<br />
[Invocar análisis](analyze.md)<br />
[Comprobar estado de análisis](check-status.md)<br />