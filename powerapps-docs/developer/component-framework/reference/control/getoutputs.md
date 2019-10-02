---
title: getOutputs | MicrosoftDocs
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: c83c3a09-f04e-4dc6-8ddf-ccd0b4cc080e
ms.author: nabuthuk
---
# <a name="getoutputs"></a>getOutputs

[!INCLUDE[./includes/getoutputs-description.md](./includes/getoutputs-description.md)]

## <a name="syntax"></a>Sintaxis

`getOutputs()`

## <a name="remarks"></a>Comentarios

La salida contendrá un valor para cada propiedad marcada como `input-output` o `bound` en el manifiesto.
Por ejemplo, si el manifiesto tiene una propiedad `value` que es una `input-output` y desea establecerla en la variable local `myvalue` deberá devolver:

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
[Referencia de la API de marco de componentes de PowerApps](../../reference/index.md)<br/>
[Descripción general de marco de componentes de PowerApps](../../overview.md)