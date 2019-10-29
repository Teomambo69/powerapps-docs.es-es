---
title: Client | Microsoft Docs
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
ms.assetid: 4ce41c82-bf4a-4d34-9344-5311c24d76de
ms.openlocfilehash: 17bcd34226be7b2e0b863849defdce532a0b99a8
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025629"
---
# <a name="client"></a>Client

[!INCLUDE [client-description](includes/client-description.md)]

## <a name="syntax"></a>Sintaxis

`context.client;`

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="properties"></a>Propiedades

### <a name="disablescroll"></a>disableScroll

Deshabilita las capacidades de desplazamiento para los componentes.

**Tipo**: `boolean`

## <a name="methods"></a>Modalidades

|Forma | Descripción |Disponible para|
| ------------- |-------------|------|
|[getClient](client/getclient.md)|[!INCLUDE [getclient-description](client/includes/getclient-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[getFormFactor](client/getformfactor.md)|[!INCLUDE [getformfactor-description](client/includes/getformfactor-description.md)]|Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)|
|[isOffline](client/isoffline.md)|[!INCLUDE [isoffline-description](client/includes/isoffline-description.md)]|Aplicaciones controladas por modelos|

## <a name="example"></a>Ejemplo 

```TypeScript
private createHTMLTableElement(): HTMLTableElement {
    let tableElement: HTMLTableElement = document.createElement("table");
    tableElement.setAttribute("class", "SampleControlHtmlTable_HtmlTable");
    let key: string = "Example Method";
    let value: string = "Result";
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, true));
    key = "getFormFactor()";
    value = String(this._context.client.getFormFactor());
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, false));
    key = "getClient()";
    value = String(this._context.client.getClient());
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, false));
}
```

### <a name="related-topics"></a>Temas relacionados

[Referencia de la API del marco de componentes de PowerApps](../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../overview.md)