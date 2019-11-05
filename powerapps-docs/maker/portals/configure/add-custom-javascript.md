---
title: Usar JavaScript personalizado para un portal | MicrosoftDocs
description: Instrucciones para agregar JavaScript personalizado a un formulario en un portal
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 42e31fc2ecb18d4f26327f8ccbeabe034d7a1700
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553656"
---
# <a name="add-custom-javascript"></a>Agregar JavaScript personalizado

El registro de paso de formulario web contiene un campo denominado **JavaScript personalizado** que se puede usar para almacenar código JavaScript que le permita extender o modificar la función o presentación visual del formulario.

El bloque personalizado de JavaScript se agregará a la parte inferior de la página justo antes del elemento de etiqueta de cierre del formulario.

## <a name="form-fields"></a>Campos de formulario

El ID. de entrada HTML de un campo de entidad se establece en el nombre lógico del atributo. Esto facilita la selección de un campo, la configuración de valores u otra manipulación del lado cliente con [jQuery](https://jquery.com/).  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>Validación adicional de campos del lado cliente
En ocasiones, es posible que tenga que personalizar la validación de los campos del formulario. En el ejemplo siguiente se muestra cómo agregar un validador personalizado. Este ejemplo obliga al usuario a especificar un correo electrónico solo si el otro campo del método de contacto preferido está establecido en email.

> [!NOTE]
> La validación de campos del lado cliente no se admite en una subcuadrícula.

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>Validación general

Al hacer clic en el **siguiente**/botón **Enviar** , se ejecuta una función denominada **webFormClientValidate** . Puede extender este método para agregar lógica de validación personalizada.

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>Vea también

[Configuración de un portal](configure-portal.md)  
[Definir formularios de entidad](entity-forms.md)  
[Pasos de Web Form para portales](web-form-steps.md)  
[Tipo de paso cargar formulario/pestaña carga](load-form-step.md)  
[Tipo de paso de redirección](add-redirect-step.md)  
[Tipo de paso condicional](add-conditional-step.md)
