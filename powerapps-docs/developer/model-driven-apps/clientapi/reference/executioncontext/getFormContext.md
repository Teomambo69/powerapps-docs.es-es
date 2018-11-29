---
title: getFormContext (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
description: Obtenga más información sobre el método getFormContext que devuelve una referencia al formulario o a un elemento del formulario dependiendo de dónde se haya llamado el método.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getformcontext-client-api-reference"></a>getFormContext (referencia de la API de cliente)



Devuelve una referencia al formulario o a un elemento del formulario dependiendo de dónde se haya llamado al método.

## <a name="syntax"></a>Sintaxis

`ExecutionContextObj.getFormContext()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: Devuelve una referencia al formulario o a un elemento del formulario, como una cuadrícula editable, dependiendo de dónde se haya llamado al método. Este método le permite crear controladores de eventos comunes que pueden trabajar en un formulario o en un elemento del formulario en función de dónde se llame.

## <a name="example"></a>Ejemplo

El código de ejemplo siguiente demuestra cómo puede crear un método que establece una notificación en un campo de formulario o en una celda de cuadrícula editable en función de dónde registró el script (evento [Campo OnChange](../events/attribute-onchange.md) o evento de cuadrícula editable [OnChange](../events/grid-onchange.md)):

```JavaScript
function commonEventHandler(executionContext) {
    var formContext = executionContext.getFormContext();    
    var telephoneAttr = formContext.data.entity.attributes.getByName('telephone1');
    var isNumberWithCountryCode = telephoneAttr.getValue().substring(0,1) === '+';

    // telephoneField will be a form control if invoked from a form OnChange event;
    // telephoneField will be a editable grid GridCell object if invoked from editable grid OnChange event.
    var telephoneField = telephoneAttr.controls.getByIndex(0);

    if (!isNumberWithCountryCode) {
        telephoneField.setNotification('Please include the country code beginning with ‘+’.', 'countryCodeNotification');
    }
    else {
        telephoneField.clearNotification('countryCodeNotification');
    }
}
```


### <a name="related-topics"></a>Temas relacionados
[Contexto de ejecución](../execution-context.md)

[Contexto de formulario](../../clientapi-form-context.md)





