---
title: Elemento propiedad | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
---

# <a name="property-element"></a>elemento propiedad

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Escriba|Requerido|
|--|--|--|--|
|`name`|Nombre de la propiedad.|`string`|Sí|
|`display-name-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen el nombre de la propiedad.|`string`|Sí|
|`of-type`|Deeine el tipo de datos de la propiedad|Consulte [Notas](#remarks)|Opcional|
|`usage`|El atributo de uso identifica si la propiedad está diseñada para representar un atributo de entidad que el componente puede cambiar (enlazada) o valores de sólo lectura (entrada)|`bound`,`input` o `output`|Opcional|
|`required`|Si la propiedad es requerida o no|`boolean`|Opcional|
|`of-type-group`|Nombre del grupo de tipos definido en el manifiesto|`string`|Opcional|
|`description-key`|Se usa en las pantallas de personalización como cadenas localizadas que describen la descripción de la propiedad.|`string`|Opcional|

### <a name="remarks"></a>Comentarios

El valor del atributo `of-type` debe ser uno de los siguientes:

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[manifiesto](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>Ejemplo

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de esquema de manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API de marco de componentes de PowerApps](../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../overview.md)
