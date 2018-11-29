---
title: getAttribute (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5ba037da-59f3-4e10-80f8-4e46d5410f81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getattribute-client-api-reference"></a>getAttribute (referencia de la API de cliente)



Devuelve el atributo con el que está enlazado el control.

Los controles que no están enlazados a un atributo (subcuadrícula, recurso web, e IFRAME) no tienen este método. Se generará un error si intenta usar este método en uno de estos controles. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Estándar, de búsqueda, conjunto de opciones

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getAttribute();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Objeto

**Descripción**: un atributo

## <a name="remarks"></a>Comentarios

Los controles constituyentes en un [control de vista rápida](../formContext-ui-quickForms.md) se incluyen en la colección de controles y estos controles tienen el método **getAttribute**. Sin embargo, el atributo no es parte de la colección de atributos de la entidad. Aunque puede recuperar el valor de ese atributo mediante [getValue](../attributes/getValue.md) e incluso cambiar el valor mediante [setValue](../attributes/setValue.md), los cambios realizados no se guardarán con la entidad.
 
El código siguiente muestra el uso del valor del atributo **mobilephone** de contacto cuando se muestra en un formulario de entidad de cuenta utilizando un control de vista rápida llamado **contactQuickForm**. Este código oculta el control cuando el valor del atributo es **null**.

```JavaScript
var quickViewMobilePhoneControl = formContext.getControl("contactQuickForm_contactQuickForm_contact_mobilephone");
if (quickViewMobilePhoneControl.getAttribute().getValue() == null) {
    quickViewMobilePhoneControl.setVisible(false);
}
```


[Control de vista rápida](../formContext-ui-quickForms.md)

[Atributos](../attributes.md)


