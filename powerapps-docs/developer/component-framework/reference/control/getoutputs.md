---
title: getOutputs | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: c83c3a09-f04e-4dc6-8ddf-ccd0b4cc080e
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 408633e1fd87c3c9517ec0984251bbbce056cc50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345391"
---
# <a name="getoutputs"></a>getOutputs

[!INCLUDE[./includes/getoutputs-description.md](./includes/getoutputs-description.md)]

## <a name="available-for"></a>Disponible para 

Aplicaciones controladas por modelos y aplicaciones de lienzo (versión preliminar experimental)

## <a name="syntax"></a>Sintaxis

`getOutputs()`

## <a name="remarks"></a>Sección

La salida contendrá un valor para cada propiedad marcada como `input-output` o `bound` en el manifiesto.
Por ejemplo, si el manifiesto tiene una propiedad `value` que es una `input-output` y desea establecerla en la variable local `myvalue` debe devolver:

```javascript
{
    value: myvalue
}
```

## <a name="example"></a>Ejemplo

```javascript
MyControl.prototype.getOutputs = function () {
    var result = {
        value: this._value
    };
    return result;
};
```


### <a name="related-topics"></a>Temas relacionados

[Control](../control.md)<br/>
[Referencia de la API del marco de componentes de PowerApps](../../reference/index.md)<br/>
[Información general sobre el marco de componentes de PowerApps](../../overview.md)