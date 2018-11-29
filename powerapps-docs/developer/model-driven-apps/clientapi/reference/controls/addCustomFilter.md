---
title: addCustomFilter (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e359b-c4d9-48ac-a57b-367c2e6168c5
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addcustomfilter-client-api-reference"></a>addCustomFilter (referencia de la API de cliente)



Agrega filtros a los resultados mostrados en la búsqueda. Cada filtro se combinará con cualquier filtro agregado anteriormente como una condición "Y".

## <a name="control-types-supported"></a>Tipos de control admitidos

Búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).addCustomFilter(filter, entityLogicaName)`

## <a name="parameters"></a>Parámetros

- **filter**: cadena. El elemento de filtro fetchXml a aplicar. Por ejemplo:

    ```xml
    <filter type="and">
      <condition attribute="address1_city" operator="eq" value="Redmond" />
    </filter>
    ```

- **entityLogicalName**: cadena (opcional). Si está establecido, el filtro se aplica solo a ese tipo de entidad. Si no, se aplicará a todos los tipos de entidades devueltas.

## <a name="remarks"></a>Comentarios

Este método solo se puede usar en una función en un controlador de eventos para el [Evento PreSearch de control de búsqueda](../events/presearch.md).

## <a name="example"></a>Ejemplo

El siguiente ejemplo de código es para la búsqueda de **Cuenta** del formulario de oportunidad (parentaccountid). Cuando la función **Sdk.setParentAccountIdFilter** se establece en el controlador de eventos **Onload** del formulario, la función **Sdk.filterCustomAccounts** se agrega al evento **PreSearch** para esa búsqueda. No olvide seleccionar la opción que pasar en el contexto de ejecución al establecer la función en el controlador de eventos **Onload** del formulario. El resultado es que solo se devuelven las cuentas con el valor **Categoría** (accountcategorycode) de **Cliente preferido** (1).

```JavaScript
// A namespace defined for SDK sample code
// You should define a unique namespace for your libraries
var Sdk = window.Sdk || {};

// set 'Sdk.setParentAccountIdFilter' in the Opportunity form onload event handler
Sdk.setParentAccountIdFilter = function (executionContext) {

    // get the form context
    formContext = executionContext.getFormContext();
    formContext.getControl("parentaccountid").addPreSearch(Sdk.filterCustomerAccounts);
}

Sdk.filterCustomerAccounts = function () {

    // Only show accounts with the type 'Preferred Customer'
    var customerAccountFilter = "<filter type='and'><condition attribute='accountcategorycode' operator='eq' value='1'/></filter>";
    formContext.getControl("parentaccountid").addCustomFilter(customerAccountFilter, "account");
}
```
[addPreSearch](addPreSearch.md)

[formContext](../../clientapi-form-context.md)