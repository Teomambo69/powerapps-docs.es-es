---
title: setSubmitMode (Referencia de API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d0728377-4365-4571-97af-9b99b2a39b65
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setsubmitmode-client-api-reference"></a>setSubmitMode (Referencia de API de cliente)| MicrosoftDocs



Establece si los datos del atributo se enviarán al guardar el registro. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).setSubmitMode(mode)`

## <a name="parameters"></a>Parámetros

**Tipo**: Cadena. 

**Descripción**: establezca uno de los siguientes valores de modo:
- **always**: Los datos se envían siempre al guardar.
- **never**: Los datos no se envían nunca al guardar. Cuando se utiliza esto, no se pueden modificar los campos del formulario para este atributo.
- **dirty**: Comportamiento predeterminado. Los datos se envían al guardar cuando han cambiado.
 
## <a name="remarks"></a>Comentarios
Utilice este método para controlar cuándo se envían los datos de un atributo al crear o guardar un registro. Por ejemplo, puede tener un campo en el formulario que está pensado solo para controlar la lógica en el formulario. No está interesado en capturar los datos que contiene. Es posible configurarlo para no guardar los datos. También puede tener un complemento que dependa de que se incluya el valor Always. Es posible que desee establecer el atributo de modo que siempre se incluya. 

Los atributos que no se actualizan tras guardar inicialmente el registro, como **createdby**, se configuran de forma que no se envíen al guardar. Para forzar un valor de atributo para que se envíe, haya cambiado o no, use este método con el parámetro *mode* establecido como “always”.

### <a name="related-topic"></a>Tema relacionado
[getSubmitMode (Referencia de API de cliente)](getSubmitMode.md)

