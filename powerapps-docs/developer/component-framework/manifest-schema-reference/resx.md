---
title: Elemento Resx | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38acfda3-4adc-4aa2-bb8b-f29ba572a6e5
---

# <a name="resx-element"></a>elemento resx

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [resx-description](includes/resx-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`path`|La ruta de acceso relativa con respecto a manifiesta dónde se encuentran los archivos resx|`string`|Sí|
|`version`|La versión actual del archivo resx|`string`|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[recursos](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Ejemplo

```xml
<resources>
      <code path="TS_LocalizationAPI.js" order="1" />
        <css path="css/TS_LocalizationAPI.css" order="1" />
      <resx path="strings/TSLocalizationAPI.1033.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.1035.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.3082.resx" version="1.0.0" />
    </resources>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)
