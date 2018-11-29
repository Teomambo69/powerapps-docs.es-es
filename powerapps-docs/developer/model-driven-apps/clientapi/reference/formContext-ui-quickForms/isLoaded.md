---
title: isLoaded (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1870151d-6029-4733-ac35-6ee4d43f9553
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isloaded-client-api-reference"></a>isLoaded (referencia de la API de cliente)



[!INCLUDE[./includes/isLoaded-description.md](./includes/isLoaded-description.md)]

## <a name="syntax"></a>Sintaxis

`quickViewControl.isLoaded();`

## <a name="return-value"></a>Valor de retorno

**Tipo**: Booleano.

**Descripción**: true significa que el enlace de datos para un control constituyente está completo; false en caso contrario. 

## <a name="remarks"></a>Comentarios

El enlace de datos para los controles constituyentes en un control de vista rápida puede no completarse durante el evento **OnLoad** del formulario principal porque el formulario de vista de rápida al que está enlazado el control puede no haberse cargado completamente. Como resultado, es posible que no funcione el uso de [getAttribute](../controls/getattribute.md) o cualquiera de los métodos relacionados con datos de un control constituyente. El método **isLoaded** del control de vista rápida ayuda a determinar el estado del enlace de datos para los controles constituyentes en un control de vista rápida.

## <a name="example"></a>Ejemplo

El siguiente código de ejemplo demuestra cómo puede usar el método **isLoaded** para comprobar el estado de enlace y después recuperar el valor del atributo al que está enlazado un control constituyente en un control de vista rápida.

```JavaScript
function getAttributeValue(executionContext) {
    var formContext = executionContext.getFormContext();
    var quickViewControl = formContext.ui.quickForms.get("<QuickViewControlName>");
    if (quickViewControl != undefined) {
        if (quickViewControl.isLoaded()) {
            // Access the value of the attribute bound to the constituent control
            var myValue = quickViewControl.getControl(0).getAttribute().getValue();
            console.log(myValue);
            return;
        }
        else {
            // Wait for some time and check again
            setTimeout(getAttributeValue, 10);
        }
    }
    else {
        console.log("No data to display in the quick view control.");
        return;
    }
}
```

### <a name="related-topics"></a>Temas relacionados

[formContext.ui.quickForms](../formContext-ui-quickForms.md)