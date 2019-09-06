---
title: init | MicrosoftDocs
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
author: Nkrb
---
# <a name="init"></a>init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="syntax"></a>Sintaxis

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro|Escriba|Requerido|Descripción|
| ------------- |----|--------|-----------|
|contexto|[Contexto](../context.md)|sí|Las *Propiedades de entrada* que contienen los parámetros, metadatos de componentes y funciones de la interfaz.|
|notifyOutputChanged|`function`|no|El método para notificar el marco que tiene nuevas salidas|
|estado|`Dictionary`|no|El estado del componente que se guarda desde *setControlState* en la última sesión|
|contenedor|[HTMLDivElement](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|no|El elemento div a generar|

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
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)
