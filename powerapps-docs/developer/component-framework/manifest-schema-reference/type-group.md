---
title: Type Group (elemento) | Microsoft Docs
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
ms.assetid: ec7c1ad4-b834-4755-8a04-2c8940f75674
ms.openlocfilehash: 7b09fad6097bb837c19116d59bb90afbde4d46b2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345989"
---
# <a name="type-group-element"></a>elemento Type-Group

[!INCLUDE [type-group-description](includes/type-group-description.md)]

## <a name="available-for"></a>Disponible para

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="attributes"></a>Atributos

|Nombre|Descripción|Tipo|Requerido|
|--|--|--|--|
|`name`|Nombre del tipo de datos|`string`|Sí|

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|


## <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|Apariciones|
|--|--|--|
|[automáticamente](type.md)|[!INCLUDE [type-description](includes/type-description.md)]|1 o más|


Type-Group tiene una compatibilidad limitada para las aplicaciones de canvas en esta versión preliminar experimental. Los siguientes problemas se producen al intentar importar componentes:

1. Si todos los tipos enumerados en el grupo de tipos son de tipos de JavaScript compatibles, el desarrollador intenta elegir la opción más genérica que se muestra. Los tipos que se consideran compatibles son:
   - Cadenas: SingleLine. Text, Multiple, SingleLine. TextArea, SingleLine. email, SingleLine. Phone, SingleLine. URL, SingleLine. ticker.
   - Números: decimal, punto flotante, entero. ninguno, moneda.
   - Fechas: DateAndTime. DateAndTime, DateAndTime. DateOnly.

2. Si los tipos enumerados en el grupo no se consideran compatibles, el parámetro se tratará como el primer tipo enumerado en el grupo de tipos.

### <a name="example"></a>Ejemplo

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>Temas relacionados

[Referencia del esquema del manifiesto del marco de componentes de PowerApps](index.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)