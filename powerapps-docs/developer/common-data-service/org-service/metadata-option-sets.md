---
title: Conjunto de opciones personalizados (Common Data Service para aplicaciones) | Microsoft Docs
description: Describe cómo trabajar con los conjuntos de opciones globales y locales en código.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="customize-option-sets"></a>Conjunto de opciones personalizadas

Normalmente, usa conjuntos de opciones *globales* para definir campos de manera que los campos diferentes puedan compartir el mismo conjunto de opciones, que se mantiene en una ubicación. A diferencia de conjuntos de opciones *locales* que se definen solo para un atributo específico, puede volver a usar conjuntos de opciones globales. También los verá usados en los parámetros de solicitudes de manera similar a una enumeración.  
  
Cuando define un conjunto de opciones glogal mediante <xref:Microsoft.Xrm.Sdk.Messages.CreateOptionSetRequest>, se recomienda dejar que el sistema asigne un valor. Realice esta acción al pasar un valor **null** al crear la nueva instancia de `OptionMetadata`. Al definir una opción, contendrá un determinada prefijo de valor de opción específico del contexto del editor establecido para la solución en la que se crea el conjunto de opciones. Este prefijo ayuda a reducir la oportunidad de crear conjuntos de opciones duplicados para una solución administrada, y en cualquier conjunto de opciones que están definidos en organizaciones donde está instalada la solución administrada. Para obtener más información, consulte [Combinar opciones del conjunto de opciones](../understand-managed-solutions-merged.md#merge-option-set-options).  
 
## <a name="messages-request-classes"></a>Clases de solicitud de mensajes  

Use las siguientes clases de solicitud de mensajes para trabajar con conjuntos de opciones globales

- <xref:Microsoft.Xrm.Sdk.Messages.CreateOptionSetRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionSetRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>  
- <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionSetRequest> 

Use las siguientes clases de solicitud de mensajes tanto con conjuntos de opciones globales como locales.

- <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.InsertStatusValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionValueRequest>
- <xref:Microsoft.Xrm.Sdk.Messages.UpdateStateValueRequest>  

<a name="BKMK_RetrieveAGlobalOptionSet"></a>

## <a name="retrieve-a-global-option-set"></a>Recuperar un conjunto de opciones globales  

 El siguiente ejemplo muestra cómo recuperar un conjunto de opciones globales por nombre mediante el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.RetrieveOptionSetRequest>:  
  

```csharp
// Use the RetrieveOptionSetRequest message to retrieve  
// a global option set by it's name.
RetrieveOptionSetRequest retrieveOptionSetRequest =
    new RetrieveOptionSetRequest
    {
        Name = _globalOptionSetName
    };

// Execute the request.
RetrieveOptionSetResponse retrieveOptionSetResponse =
    (RetrieveOptionSetResponse)svc.Execute(
    retrieveOptionSetRequest);

Console.WriteLine("Retrieved {0}.",
    retrieveOptionSetRequest.Name);

// Access the retrieved OptionSetMetadata.
OptionSetMetadata retrievedOptionSetMetadata =
    (OptionSetMetadata)retrieveOptionSetResponse.OptionSetMetadata;

// Get the current options list for the retrieved attribute.
OptionMetadata[] optionList =
    retrievedOptionSetMetadata.Options.ToArray();
```

  
<a name="BKMK_CreateGlobalOptionSet"></a>  
 
## <a name="create-a-global-option-set"></a>Creación de un conjunto de opciones global
  
Use el mensaje de <xref:Microsoft.Xrm.Sdk.Messages.CreateOptionSetRequest> para crear un nuevo conjunto de opciones global. Definir la propiedad de <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadataBase.IsGlobal> en `true` para indicar que el conjunto de opciones es global. El siguiente ejemplo de código crea un conjunto de opciones global denominado "Conjunto de opciones de ejemplo":  
  
```csharp
// Define the request object and pass to the service.
CreateOptionSetRequest createOptionSetRequest = new CreateOptionSetRequest
{
    // Create a global option set (OptionSetMetadata).
    OptionSet = new OptionSetMetadata
    {
        Name = _globalOptionSetName,
        DisplayName = new Label("Example Option Set", _languageCode),
        IsGlobal = true,
        OptionSetType = OptionSetType.Picklist,
        Options = 
    {
        new OptionMetadata(new Label("Open", _languageCode), null),
        new OptionMetadata(new Label("Suspended", _languageCode), null),
        new OptionMetadata(new Label("Cancelled", _languageCode), null),
        new OptionMetadata(new Label("Closed", _languageCode), null)
    }
    }
};

// Execute the request.
CreateOptionSetResponse optionsResp =
    (CreateOptionSetResponse)svc.Execute(createOptionSetRequest);
```

  
<a name="BKMK_CreatePicklistWithGlobalOptionSet"></a>  
 
## <a name="create-a-picklist-that-uses-a-global-option-set"></a>Crear una lista desplegable que usa un conjunto de opciones global  

 El siguiente ejemplo muestra cómo crear un atributo de lista desplegable que usa un conjunto de opciones global con <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>:  
  

```csharp
// Create a Picklist linked to the option set.
// Specify which entity will own the picklist, and create it.
CreateAttributeRequest createRequest = new CreateAttributeRequest
{
    EntityName = Contact.EntityLogicalName,
    Attribute = new PicklistAttributeMetadata
    {
        SchemaName = "sample_examplepicklist",
        LogicalName = "sample_examplepicklist",
        DisplayName = new Label("Example Picklist", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),

        // In order to relate the picklist to the global option set, be sure
        // to specify the two attributes below appropriately.
        // Failing to do so will lead to errors.
        OptionSet = new OptionSetMetadata
        {
            IsGlobal = true,
            Name = _globalOptionSetName
        }
    }
};

svc.Execute(createRequest);
```

  
<a name="BKMK_UpdateGlobalOptionSet"></a>

## <a name="update-a-global-option-set"></a>Actualizar un conjunto de opciones global 

El siguiente ejemplo muestra cómo actualizar la etiqueta para un conjunto de opciones global por nombre mediante <xref:Microsoft.Xrm.Sdk.Messages.UpdateOptionSetRequest>:  
  

```csharp
// Use UpdateOptionSetRequest to update the basic information of an option
// set. Updating option set values requires different messages (see below).
UpdateOptionSetRequest updateOptionSetRequest = new UpdateOptionSetRequest
{
    OptionSet = new OptionSetMetadata
    {
        DisplayName = new Label("Updated Option Set", _languageCode),
        Name = _globalOptionSetName,
        IsGlobal = true
    }
};

svc.Execute(updateOptionSetRequest);

//Publish the OptionSet
PublishXmlRequest pxReq1 = new PublishXmlRequest { ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) };
svc.Execute(pxReq1);
```

  
<a name="BKMK_OrderingOptions"></a> 
  
## <a name="ordering-options"></a>Opciones de ordenación  

El siguiente ejemplo muestra cómo se pueden ordenar las opciones en un conjunto de opciones global por nombre mediante <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest>:  
  

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
svc.Execute(orderOptionRequest);

//Publish the OptionSet
PublishXmlRequest pxReq4 = new PublishXmlRequest { 
ParameterXml = String.Format("<importexportxml><optionsets><optionset>{0}</optionset></optionsets></importexportxml>", _globalOptionSetName) 
};
svc.Execute(pxReq4);
```

  
<a name="BKMK_RetrieveAllGlobalOptionSets"></a>  
 
## <a name="retrieve-all-global-option-sets"></a>Recuperar todos los conjuntos de opciones globales  

El siguiente ejemplo muestra cómo recuperar todos los conjuntos de opciones globales mediante <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllOptionSetsRequest>:  
  

```csharp
// Use RetrieveAllOptionSetsRequest to retrieve all global option sets.
// Create the request.
RetrieveAllOptionSetsRequest retrieveAllOptionSetsRequest =
    new RetrieveAllOptionSetsRequest();

// Execute the request
RetrieveAllOptionSetsResponse retrieveAllOptionSetsResponse =
    (RetrieveAllOptionSetsResponse)svc.Execute(
    retrieveAllOptionSetsRequest);

// Now you can use RetrieveAllOptionSetsResponse.OptionSetMetadata property to 
// work with all retrieved option sets.
if (retrieveAllOptionSetsResponse.OptionSetMetadata.Count() > 0)
{
    Console.WriteLine("All the global option sets retrieved as below:");
    int count = 1;
    foreach (OptionSetMetadataBase optionSetMetadata in
        retrieveAllOptionSetsResponse.OptionSetMetadata)
    {
        Console.WriteLine("{0} {1}", count++,
            (optionSetMetadata.DisplayName.LocalizedLabels.Count >0)? optionSetMetadata.DisplayName.LocalizedLabels[0].Label : String.Empty);
    }
}
```

  
<a name="BKMK_DeleteAGlobalOptionSet"></a>

## <a name="delete-a-global-option-set"></a>Eliminar un conjunto de opciones global

 El siguiente ejemplo muestra cómo comprobar si otro componente de la solución está usando un conjunto de opciones globales mediante el mensaje `RetrieveDependentComponents` (<xref href="Microsoft.Dynamics.CRM.RetrieveDependentComponents?text=RetrieveDependentComponents Function" /> o <xref:Microsoft.Crm.Sdk.Messages.RetrieveDependentComponentsRequest>) y cómo eliminarlo mediante el mensaje `DeleteOptionSet` (para el servicio de la organización, consulte <xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionSetRequest>):  
  

```csharp
// Create the request to see which components have a dependency on the
// global option set.
RetrieveDependentComponentsRequest dependencyRequest =
    new RetrieveDependentComponentsRequest
    {
        ObjectId = _optionSetId,
        ComponentType = (int)componenttype.OptionSet
    };

RetrieveDependentComponentsResponse dependencyResponse =
    (RetrieveDependentComponentsResponse)svc.Execute(
    dependencyRequest);

// Here you would check the dependencyResponse.EntityCollection property
// and act as appropriate. However, we know there is exactly one 
// dependency so this example deals with it directly and deletes 
// the previously created attribute.
DeleteAttributeRequest deleteAttributeRequest =
    new DeleteAttributeRequest
{
    EntityLogicalName = Contact.EntityLogicalName,
    LogicalName = "sample_examplepicklist"
};

svc.Execute(deleteAttributeRequest);

Console.WriteLine("Referring attribute deleted.");
  
// Finally, delete the global option set. Attempting this before deleting
// the picklist above will result in an exception being thrown.
DeleteOptionSetRequest deleteRequest = new DeleteOptionSetRequest
{
    Name = _globalOptionSetName
};

svc.Execute(deleteRequest);
```

  
### <a name="see-also"></a>Vea también

[Crear y actualizar conjuntos de opciones mediante la API web](../webapi/create-update-optionsets.md)