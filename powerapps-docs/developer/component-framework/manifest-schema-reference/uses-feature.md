---
title: uses-feature | Microsoft Docs
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
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
---

# <a name="uses-feature-element"></a>elemento uses-feature

Indica qué característica desea que utilicen sus componentes.

## <a name="parent-element"></a>Elemento principal

|Elemento|Descripción|
|--|--|
|feature-usage|El elemento feature-usage actúa como contenedor de los elementos uses-feature, que a su vez permiten a los desarrolladores declarar qué características quieren que utilice su componente. Si no hay elementos uses-feature definidos, el elemento feature-usage no es obligatorio.|

## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|--|--|
|nombre|Nombre de la característica que se declara en el componente|
|obligatorio|Indica si el componente requiere esa característica o no|


### <a name="example"></a>Ejemplo 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

La tabla de debajo muestra la relación de estos valores con lo que ocurre en el código en tiempo de ejecución si la función de característica estará disponible para llamar en función de la configuración de uses-feature definida en el manifiesto.

|Manifiesto|Si lo admite el host|Si no lo admite el host|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null`, no se necesita comprobación.|Advertencia en tiempo de diseño. La carga del componente producirá un error en tiempo de ejecución.|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null`, el componente puede comprobar esto de manera adaptativa en tiempo de ejecución. |
|(ninguno)|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)