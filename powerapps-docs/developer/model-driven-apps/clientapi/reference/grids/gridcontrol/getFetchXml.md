---
title: getFetchXml (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getfetchxml-client-api-reference"></a>getFetchXml (referencia de la API de cliente)



[!INCLUDE[./includes/getFetchXml-description.md](./includes/getFetchXml-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`var result = gridContext.getfetchXml();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: la consulta FetchXML.

## <a name="remarks"></a>Comentarios

Para obtener el `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext). 

## <a name="example"></a>Ejemplo

El ejemplo siguiente, muestra el XML de búsqueda recuperado de la subcuadrícula Contactos en la consola:

```JavaScript
function myFunction(executionContext) {
    var formContext = executionContext.getFormContext(); // get the form context
    var gridContext = formContext.getControl("Contacts"); // get the grid context
    var retrieveFetchXML = function () {
        var result = gridContext.getFetchXml();
        console.log(result)
    };
    gridContext.addOnLoad(retrieveFetchXML);    
}
```


