---
title: addOnLoad (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 01/29/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 24f34ac9-2a15-478e-980c-588a79d84e8d
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonload-client-api-reference"></a>addOnLoad (referencia de la API de cliente)



[!INCLUDE[./includes/addOnLoad-description.md](./includes/addOnLoad-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`gridContext.addOnLoad(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Escriba|Requerido|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se debe ejecutar cuando se carga la subcuadrícula.  La función se agregará al final de la canalización del controlador de eventos. El contexto de ejecución se pasa automáticamente como el primer parámetro a la función. Para obtener más información, consulte [contexto de ejecución](../../../clientapi-execution-context.md).

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).

## <a name="example"></a>Ejemplo

Agregue la función myContactsGridOnloadFunction al evento **OnLoad** de subcuadrícula de Contactos.

```JavaScript
function myFunction(executionContext) {
    var formContext = executionContext.getFormContext(); // get the form context
    var gridContext = formContext.getControl("Contacts");// get the grid context
    var myContactsGridOnloadFunction = function () { console.log("Contacts Subgrid OnLoad event occurred") };
    gridContext.addOnLoad(myContactsGridOnloadFunction);
}
```

### <a name="related-topics"></a>Temas relacionados

[removeOnLoad](removeOnLoad.md)



