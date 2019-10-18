---
title: init | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 57a5ce0d4e930184bf42502f1dc16b6a648f1292
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345506"
---
# <a name="init"></a>init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="syntax"></a>Sintaxis

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|contexto|[Context](../context.md)|yes|*Propiedades de entrada* que contienen los parámetros, metadatos de componentes y funciones de interfaz.|
|notifyOutputChanged|`function`|no|El método para notificar al marco de trabajo que tiene nuevas salidas|
|State|`Dictionary`|no|Estado del componente que se guarda desde *setControlState* en la última sesión|
|contenedor|[HTMLDivElement](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|no|Elemento div que se va a representar.|

## <a name="example"></a>Ejemplo

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.init = function (context, notifyOutputChanged, state, container) {
    this._labelElement = document.createElement("label");
    this._labelElement.setAttribute("class", "JS_HelloWorldColor");
    container.appendChild(this._labelElement);
};
```

### <a name="related-topics"></a>Temas relacionados

[Control](../control.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)
