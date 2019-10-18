---
title: updateView | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 899d6eb3-62b4-4c1f-947c-aed1f8643caa
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d7ac81ef617aa4e9e3564ade01bc469b0d7f5bc8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345345"
---
# <a name="updateview"></a>updateView

[!INCLUDE[./includes/updateview-description.md](./includes/updateview-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="syntax"></a>Sintaxis

`updateView(context)`

## <a name="parameters"></a>Parámetros

| Nombre del parámetro|Tipo|Requerido|Descripción|
| ------------- |----|--------|-----------|
|contexto|`context`|yes|Contiene los valores establecidos por el personalizador asignado al nombre definido en el manifiesto, así como en las funciones de utilidad.|

## <a name="example"></a>Ejemplo

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.updateView = function (context) {
    this._labelElement.innerText = "Hello World! (JS)";
};
```

## <a name="remarks"></a>Sección

Establecer el valor del componente de campo en el valor sin formato del campo configurado


### <a name="related-topics"></a>Temas relacionados

[Control](../control.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)