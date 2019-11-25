---
title: Insertar, actualizar, eliminar y ordenar las opciones globales del conjunto de opciones (Common Data Service) | Microsoft Docs
description: Ejemplos de código para mostrar cómo insertar, actualizar, eliminar y ordenar opciones en un conjunto de opciones globales
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ac224afc2497d5c7600c95a37f61d5b72c8eb461
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749688"
---
# <a name="insert-update-delete-and-order-global-option-set-options"></a>Insertar, actualizar, elimina, y ordenar las opciones globales del conjunto de opciones

<!-- 

https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/insert-update-delete-order-global-option-set-options 

-->

Estos ejemplos de código muestran cómo insertar, actualizar, eliminar y ordenar opciones en un conjunto de opciones globales.  
  
<a name="BKMK_InsertNewOption"></a>   
## <a name="insert-a-new-option"></a>Insertar una opción nueva  
 Este ejemplo muestra cómo agregar una nueva opción a un conjunto de opciones global mediante <xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest>:  
  
```csharp
// Use InsertOptionValueRequest to insert a new option into a 
// global option set.
InsertOptionValueRequest insertOptionValueRequest =
    new InsertOptionValueRequest
    {
        OptionSetName = _globalOptionSetName,
        Label = new Label("New Picklist Label", _languageCode)
    };

// Execute the request and store the newly inserted option value 
// for cleanup, used in the later part of this sample.
_insertedOptionValue = ((InsertOptionValueResponse)_serviceProxy.Execute(
    insertOptionValueRequest)).NewOptionValue;

//Publish the OptionSet
PublishXmlRequest pxReq2 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
_serviceProxy.Execute(pxReq2);
```


  
<a name="BKMK_UpdateAnOption"></a>   
## <a name="update-an-option"></a>Actualizar una opción  
 Este ejemplo muestra cómo actualizar una opción en un conjunto de opciones global mediante <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionValueRequest>:  
  
```csharp
// In order to change labels on option set values (or delete) option set
// values, you must use UpdateOptionValueRequest 
// (or DeleteOptionValueRequest).
UpdateOptionValueRequest updateOptionValueRequest =
    new UpdateOptionValueRequest
    {
        OptionSetName = _globalOptionSetName,
        // Update the second option value.
        Value = optionList[1].Value.Value,
        Label = new Label("Updated Option 1", _languageCode)
    };

_serviceProxy.Execute(updateOptionValueRequest);

//Publish the OptionSet
PublishXmlRequest pxReq3 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
_serviceProxy.Execute(pxReq3);
```
  
<a name="BKMK_DeleteAnOption"></a>   
## <a name="delete-an-option"></a>Eliminar una opción  
 Este ejemplo muestra cómo eliminar una opción en un conjunto de opciones global mediante <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionValueRequest>:  
  
```csharp
// Use the DeleteOptionValueRequest message 
// to remove the newly inserted label.
DeleteOptionValueRequest deleteOptionValueRequest =
    new DeleteOptionValueRequest
{
    OptionSetName = _globalOptionSetName,
    Value = _insertedOptionValue
};

// Execute the request.
_serviceProxy.Execute(deleteOptionValueRequest);
```  
  
<a name="BKMK_OrderOptions"></a>   
## <a name="order-options"></a>Ordenar opciones  
 Este ejemplo muestra cómo establecer el orden de las opciones en un conjunto de opciones global mediante <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest>:  
  
```csharp
// Change the order of the original option's list.
// Use the OrderBy (OrderByDescending) linq function to sort options in  
// ascending (descending) order according to label text.
// For ascending order use this:
var updateOptionList =
    optionList.OrderBy(x => x.Label.LocalizedLabels[0].Label).ToList();

// For descending order use this:
// var updateOptionList =
//      optionList.OrderByDescending(
//      x => x.Label.LocalizedLabels[0].Label).ToList();

// Create the request.
OrderOptionRequest orderOptionRequest = new OrderOptionRequest
{
    // Set the properties for the request.
    OptionSetName = _globalOptionSetName,
    // Set the changed order using Select linq function 
    // to get only values in an array from the changed option list.
    Values = updateOptionList.Select(x => x.Value.Value).ToArray()
};

// Execute the request
_serviceProxy.Execute(orderOptionRequest);

//Publish the OptionSet
PublishXmlRequest pxReq4 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
_serviceProxy.Execute(pxReq4);
``` 
