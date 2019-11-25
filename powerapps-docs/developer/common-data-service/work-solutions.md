---
title: Trabajar con soluciones (Common Data Service) | Microsoft Docs
description: ''
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 33c9da5b-27dd-d82d-1eb1-7b3b69b6032b
author: shmcarth
ms.author: jdaly
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6a99ee0bbc5487575d56b571442db5e6a6d2f329
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749647"
---
# <a name="work-with-solutions"></a>Trabajar con soluciones

Este tema presenta tareas de programación específicas incluidas en [ejemplo: trabajar con soluciones](org-service/samples/work-solutions.md) y [ejemplo: detectar dependencias de la solución](org-service/samples/detect-solution-dependencies.md).  
  
<a name="BKMK_CreatePublisher"></a>

## <a name="create-a-publisher"></a>Crear un editor

 Cada solución necesita un editor, representado por la [Entidad Editora](reference/entities/publisher.md) . Una solución no puede usar el editor de `Microsoft Corporation` pero puede usar el editor `Default` de la organización o un nuevo editor  
  
 Un editor requiere lo siguiente:  
  
- Un prefijo de personalización  
  
- Un nombre único  
  
- Un nombre descriptivo  
  
  El siguiente ejemplo primero define un editor y después se asegura de que el editor exista según el nombre único. Si ya existe, puede que el prefijo de personalización haya cambiado, por lo que este ejemplo busca capturar el prefijo actual de personalización. El `PublisherId` también se captura para poder eliminar el registro del editor. Si no encuentra el editor, se creará un nuevo editor mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Método de <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> 

 ```csharp
//Define a new publisher
Publisher _crmSdkPublisher = new Publisher
{
    UniqueName = "sdksamples",
    FriendlyName = "Microsoft CRM SDK Samples",
    SupportingWebsiteUrl = "https://msdn.microsoft.com/dynamics/crm/default.aspx",
    CustomizationPrefix = "sample",
    EMailAddress = "someone@microsoft.com",
    Description = "This publisher was created with samples from the Microsoft Dynamics CRM SDK"
};
//Does publisher already exist?
QueryExpression querySDKSamplePublisher = new QueryExpression
{
    EntityName = Publisher.EntityLogicalName,
    ColumnSet = new ColumnSet("publisherid", "customizationprefix"),
    Criteria = new FilterExpression()
};

querySDKSamplePublisher.Criteria.AddCondition("uniquename", ConditionOperator.Equal, _crmSdkPublisher.UniqueName);
EntityCollection querySDKSamplePublisherResults = _serviceProxy.RetrieveMultiple(querySDKSamplePublisher);
Publisher SDKSamplePublisherResults = null;
//If it already exists, use it
if (querySDKSamplePublisherResults.Entities.Count > 0)
{
    SDKSamplePublisherResults = (Publisher)querySDKSamplePublisherResults.Entities[0];
    _crmSdkPublisherId = (Guid)SDKSamplePublisherResults.PublisherId;
    _customizationPrefix = SDKSamplePublisherResults.CustomizationPrefix;
}
//If it doesn't exist, create it
if (SDKSamplePublisherResults == null)
{
    _crmSdkPublisherId = _serviceProxy.Create(_crmSdkPublisher);
    Console.WriteLine(String.Format("Created publisher: {0}.", _crmSdkPublisher.FriendlyName));
    _customizationPrefix = _crmSdkPublisher.CustomizationPrefix;
}
``` 
  
<a name="BKMK_RetrieveDefaultPublisher"></a>
   
## <a name="retrieve-the-default-publisher"></a>Recuperar el editor predeterminado.  

Este ejemplo muestra cómo recuperar el editor predeterminado. El editor predeterminado tiene un valor de GUID constante: `d21aab71-79e7-11dd-8874-00188b01e34f`.  

```csharp
// Retrieve the Default Publisher

//The default publisher has a constant GUID value;
Guid DefaultPublisherId = new Guid("{d21aab71-79e7-11dd-8874-00188b01e34f}");

Publisher DefaultPublisher = (Publisher)_serviceProxy.Retrieve(Publisher.EntityLogicalName, DefaultPublisherId, new ColumnSet(new string[] {"friendlyname" }));

EntityReference DefaultPublisherReference = new EntityReference
{
    Id = DefaultPublisher.Id,
    LogicalName = Publisher.EntityLogicalName,
    Name = DefaultPublisher.FriendlyName
};
Console.WriteLine("Retrieved the {0}.", DefaultPublisherReference.Name);
```
  
<a name="BKMK_CreateASolution"></a>
 
## <a name="create-a-solution"></a>Crear una solución

 El siguiente ejemplo muestra cómo crear una solución no administrada mediante los ejemplos SDK creados en [ Ejemplos creados en el editor ](work-solutions.md#BKMK_CreatePublisher).  
  
 Una solución requiere lo siguiente:  
  
- Un editor  
  
- Un nombre descriptivo  
  
- Un nombre único  
  
- Un número de versión  
  
  La variable `_crmSdkPublisherId` es un valor GUID que representa el valor de `publisherid`.  
  
  Este ejemplo comprueba si la solución ya existe en la organización en función del nombre único. Si la solución no existe, se crea. El valor de `SolutionId` se captura para que la solución se pueda eliminar.  
  
 ```csharp
  // Create a Solution
//Define a solution
Solution solution = new Solution
{
    UniqueName = "samplesolution",
    FriendlyName = "Sample Solution",
    PublisherId = new EntityReference(Publisher.EntityLogicalName, _crmSdkPublisherId),
    Description = "This solution was created by the WorkWithSolutions sample code in the Microsoft Dynamics CRM SDK samples.",
    Version = "1.0"
};

//Check whether it already exists
QueryExpression queryCheckForSampleSolution = new QueryExpression
{
    EntityName = Solution.EntityLogicalName,
    ColumnSet = new ColumnSet(),
    Criteria = new FilterExpression()
};
queryCheckForSampleSolution.Criteria.AddCondition("uniquename", ConditionOperator.Equal, solution.UniqueName);

//Create the solution if it does not already exist.
EntityCollection querySampleSolutionResults = _serviceProxy.RetrieveMultiple(queryCheckForSampleSolution);
Solution SampleSolutionResults = null;
if (querySampleSolutionResults.Entities.Count > 0)
{
    SampleSolutionResults = (Solution)querySampleSolutionResults.Entities[0];
    _solutionsSampleSolutionId = (Guid)SampleSolutionResults.SolutionId;
}
if (SampleSolutionResults == null)
{
    _solutionsSampleSolutionId = _serviceProxy.Create(solution);
}
  ```
  
<a name="BKMK_RetrieveASolution"></a> 
  
## <a name="retrieve-a-solution"></a>Recuperar una solución  

Para recuperar una solución específica puede usar el `UniqueName` de la solución. Cada organización tendrá una solución predeterminada con un valor de GUID constante: `FD140AAF-4DF4-11DD-BD17-0019B9312238`.  
  
Este ejemplo muestra cómo recuperar los datos para una solución con el nombre único "sample solution". Se creará una solución con este nombre en [Crear una solución](work-solutions.md#BKMK_CreateASolution).  
  
 ```csharp
 // Retrieve a solution
String solutionUniqueName = "samplesolution";
QueryExpression querySampleSolution = new QueryExpression
{
    EntityName = Solution.EntityLogicalName,
    ColumnSet = new ColumnSet(new string[] { "publisherid", "installedon", "version", "versionnumber", "friendlyname" }),
    Criteria = new FilterExpression()
};

querySampleSolution.Criteria.AddCondition("uniquename", ConditionOperator.Equal, solutionUniqueName);
Solution SampleSolution = (Solution)_serviceProxy.RetrieveMultiple(querySampleSolution).Entities[0];
 ``` 
  
<a name="BKMK_AddANewSolutionComponent"></a> 
  
## <a name="add-a-new-solution-component"></a>Agregar un nuevo componente de la solución 
 
Este ejemplo muestra cómo crear un componente de la solución que está asociado con una solución específica. Si no asocia el componente de la solución a una solución específica cuando se crea solo se agregará a la solución predeterminada y necesitará agregarlo a una solución manualmente o mediante el código incluido en [Añadir un componente de solución existente](work-solutions.md#BKMK_AddExistingSolutionComponent).  
  
 Este código crea un nuevo conjunto de opciones globales y lo agrega a la solución con un nombre único igual a `_primarySolutionName`.  
  
 ```csharp
 OptionSetMetadata optionSetMetadata = new OptionSetMetadata()
{
    Name = _globalOptionSetName,
    DisplayName = new Label("Example Option Set", _languageCode),
    IsGlobal = true,
    OptionSetType = OptionSetType.Picklist,
    Options =
{
    new OptionMetadata(new Label("Option 1", _languageCode), 1),
    new OptionMetadata(new Label("Option 2", _languageCode), 2)
}
};
CreateOptionSetRequest createOptionSetRequest = new CreateOptionSetRequest
{
    OptionSet = optionSetMetadata                
};

createOptionSetRequest.SolutionUniqueName = _primarySolutionName;
_serviceProxy.Execute(createOptionSetRequest);
 ```  
  
<a name="BKMK_AddExistingSolutionComponent"></a>  
 
## <a name="add-an-existing-solution-component"></a>Agregar un componente de la solución existente  

Este ejemplo muestra cómo agregar un componente de la solución existente a una solución.  
  
El siguiente código usa <xref:Microsoft.Crm.Sdk.Messages.AddSolutionComponentRequest> para agregar la entidad `Account` como componente de la solución a una solución no administrada.  
  
 ```csharp
 // Add an existing Solution Component
//Add the Account entity to the solution
RetrieveEntityRequest retrieveForAddAccountRequest = new RetrieveEntityRequest()
{
    LogicalName = Account.EntityLogicalName
};
RetrieveEntityResponse retrieveForAddAccountResponse = (RetrieveEntityResponse)_serviceProxy.Execute(retrieveForAddAccountRequest);
AddSolutionComponentRequest addReq = new AddSolutionComponentRequest()
{
    ComponentType = (int)componenttype.Entity,
    ComponentId = (Guid)retrieveForAddAccountResponse.EntityMetadata.MetadataId,
    SolutionUniqueName = solution.UniqueName
};
_serviceProxy.Execute(addReq);
``` 
  
<a name="BKMK_RemoveSolutionComponent"></a>  
 
## <a name="remove-a-solution-component"></a>Quitar un componente de la solución  

Este ejemplo muestra cómo quitar un componente de la solución de una solución no administrada. El siguiente código usa <xref:Microsoft.Crm.Sdk.Messages.RemoveSolutionComponentRequest> para quitar un componente de la solución de entidad de una solución no administrada. El `solution.UniqueName` hace referencia a la solución creada en [Crear una solución](work-solutions.md#BKMK_CreateASolution).  
  
 ```csharp
 // Remove a Solution Component
//Remove the Account entity from the solution
RetrieveEntityRequest retrieveForRemoveAccountRequest = new RetrieveEntityRequest()
{
    LogicalName = Account.EntityLogicalName
};
RetrieveEntityResponse retrieveForRemoveAccountResponse = (RetrieveEntityResponse)_serviceProxy.Execute(retrieveForRemoveAccountRequest);

RemoveSolutionComponentRequest removeReq = new RemoveSolutionComponentRequest()
{
    ComponentId = (Guid)retrieveForRemoveAccountResponse.EntityMetadata.MetadataId,
    ComponentType = (int)componenttype.Entity,
    SolutionUniqueName = solution.UniqueName
};
_serviceProxy.Execute(removeReq);
```
  
<a name="BKMK_ExportPackageSolution"></a>
   
## <a name="export-or-package-a-solution"></a>Exportar o empaquetar una solución  

Este ejemplo muestra cómo exportar una solución no administrada o empaquetar una solución administrada. El código usa <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest> para exportar un archivo comprimido que representa una solución no administrada. La opción para crear una solución administrada se configura mediante la propiedad de <xref:Microsoft.Crm.Sdk.Messages.ExportSolutionRequest.Managed>. Este ejemplo guarda un archivo llamado *samplesolution.zip* en la carpeta `c:\temp\`.  
  
```csharp
// Export or package a solution
//Export an a solution

ExportSolutionRequest exportSolutionRequest = new ExportSolutionRequest();
exportSolutionRequest.Managed = false;
exportSolutionRequest.SolutionName = solution.UniqueName;

ExportSolutionResponse exportSolutionResponse = (ExportSolutionResponse)_serviceProxy.Execute(exportSolutionRequest);

byte[] exportXml = exportSolutionResponse.ExportSolutionFile;
string filename = solution.UniqueName + ".zip";
File.WriteAllBytes(outputDir + filename, exportXml);

Console.WriteLine("Solution exported to {0}.", outputDir + filename);
``` 

<a name="BKMK_InstallUpgradeSolution"></a>  
 
## <a name="install-or-upgrade-a-solution"></a>Instalar o actualizar una solución  

Este ejemplo muestra cómo instalar o actualizar una solución con el mensaje de <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest>.  
  
Puede usar la entidad `ImportJob` para capturar datos acerca del éxito de la importación.  
  
El siguiente ejemplo muestra cómo importar una solución sin hacer seguimiento del éxito.  
  
 ```csharp
 // Install or Upgrade a Solution                  

byte[] fileBytes = File.ReadAllBytes(ManagedSolutionLocation);

ImportSolutionRequest impSolReq = new ImportSolutionRequest()
{
    CustomizationFile = fileBytes
};

_serviceProxy.Execute(impSolReq);

Console.WriteLine("Imported Solution from {0}", ManagedSolutionLocation);
 ```  
  
### <a name="tracking-import-success"></a>Seguir el éxito de la importación

 Cuando especifica un <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest.ImportJobId> para `ImportSolutionRequest`, puede usar ese valor para consultar la entidad `ImportJob` sobre el estado de la importación.  
  
 `ImportJobId` también puede usarse para descargar un archivo de registro de importación mediante el mensaje de <xref:Microsoft.Crm.Sdk.Messages.RetrieveFormattedImportJobResultsRequest>.  
  
#### <a name="retrieving-import-job-data"></a>Recuperar datos del trabajo de importación

 El siguiente ejemplo muestra cómo recuperar el registro del trabajo de importación y el contenido del atributo de `ImportJob.Data`.  
  
```csharp
// Monitor import success
byte[] fileBytesWithMonitoring = File.ReadAllBytes(ManagedSolutionLocation);

ImportSolutionRequest impSolReqWithMonitoring = new ImportSolutionRequest()
{
    CustomizationFile = fileBytes,
    ImportJobId = Guid.NewGuid()
};

_serviceProxy.Execute(impSolReqWithMonitoring);
Console.WriteLine("Imported Solution with Monitoring from {0}", ManagedSolutionLocation);

ImportJob job = (ImportJob)_serviceProxy.Retrieve(ImportJob.EntityLogicalName, impSolReqWithMonitoring.ImportJobId, new ColumnSet(new System.String[] { "data", "solutionname" }));


System.Xml.XmlDocument doc = new System.Xml.XmlDocument();
doc.LoadXml(job.Data);

String ImportedSolutionName = doc.SelectSingleNode("//solutionManifest/UniqueName").InnerText;
String SolutionImportResult = doc.SelectSingleNode("//solutionManifest/result/@result").Value;

Console.WriteLine("Report from the ImportJob data");
Console.WriteLine("Solution Unique name: {0}", ImportedSolutionName);
Console.WriteLine("Solution Import Result: {0}", SolutionImportResult);
Console.WriteLine("");

// This code displays the results for Global Option sets installed as part of a solution.

System.Xml.XmlNodeList optionSets = doc.SelectNodes("//optionSets/optionSet");
foreach (System.Xml.XmlNode node in optionSets)
{
    string OptionSetName = node.Attributes["LocalizedName"].Value;
    string result = node.FirstChild.Attributes["result"].Value;

    if (result == "success")
    {
        Console.WriteLine("{0} result: {1}",OptionSetName, result);
    }
    else
    {
        string errorCode = node.FirstChild.Attributes["errorcode"].Value;
        string errorText = node.FirstChild.Attributes["errortext"].Value;

        Console.WriteLine("{0} result: {1} Code: {2} Description: {3}",OptionSetName, result, errorCode, errorText);
    }
}
```   
  
El contenido de la propiedad de `Data` es una cadena que representa un archivo XML. Lo siguiente es un ejemplo capturado mediante el código en este ejemplo. Esta solución administrada contenía un único conjunto de opciones globales llamado `sample_tempsampleglobaloptionsetname`.  
  
```xml  
<importexportxml start="634224017519682730"  
                 stop="634224017609764033"  
                 progress="80"  
                 processed="true">  
 <solutionManifests>  
  <solutionManifest languagecode="1033"  
                    id="samplesolutionforImport"  
                    LocalizedName="Sample Solution for Import"  
                    processed="true">  
   <UniqueName>samplesolutionforImport</UniqueName>  
   <LocalizedNames>  
    <LocalizedName description="Sample Solution for Import"  
                   languagecode="1033" />  
   </LocalizedNames>  
   <Descriptions>  
    <Description description="This solution was created by the WorkWithSolutions sample code in the Microsoft CRM SDK samples."  
                 languagecode="1033" />  
   </Descriptions>  
   <Version>1.0</Version>  
   <Managed>1</Managed>  
   <Publisher>  
    <UniqueName>sdksamples</UniqueName>  
    <LocalizedNames>  
     <LocalizedName description="Microsoft CRM SDK Samples"  
                    languagecode="1033" />  
    </LocalizedNames>  
    <Descriptions>  
     <Description description="This publisher was created with samples from the Microsoft CRM SDK"  
                  languagecode="1033" />  
    </Descriptions>  
    <EMailAddress>someone@microsoft.com</EMailAddress>  
    <SupportingWebsiteUrl>https://msdn.microsoft.com/dynamics/crm/default.aspx</SupportingWebsiteUrl>  
    <Addresses>  
     <Address>  
      <City />  
      <Country />  
      <Line1 />  
      <Line2 />  
      <PostalCode />  
      <StateOrProvince />  
      <Telephone1 />  
     </Address>  
    </Addresses>  
   </Publisher>  
   <results />  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:12.08"  
           datetimeticks="634224269520845122" />  
  </solutionManifest>  
 </solutionManifests>  
 <upgradeSolutionPackageInformation>  
  <upgradeRequired>0</upgradeRequired>  
  <upgradeValid>1</upgradeValid>  
  <fileVersion>5.0.9669.0</fileVersion>  
  <currentVersion>5.0.9669.0</currentVersion>  
  <fileSku>OnPremise</fileSku>  
  <currentSku>OnPremise</currentSku>  
 </upgradeSolutionPackageInformation>  
 <entities />  
 <nodes />  
 <settings />  
 <dashboards />  
 <securityroles />  
 <workflows />  
 <templates />  
 <optionSets>  
  <optionSet id="sample_tempsampleglobaloptionsetname"  
             LocalizedName="Example Option Set"  
             Description=""  
             processed="true">  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:16.10"  
           datetimeticks="634224269561025400" />  
  </optionSet>  
 </optionSets>  
 <ConnectionRoles />  
 <SolutionPluginAssemblies />  
 <SdkMessageProcessingSteps />  
 <ServiceEndpoints />  
 <webResources />  
 <reports />  
 <FieldSecurityProfiles />  
 <languages>  
  <language>  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:12.00"  
           datetimeticks="634224269520092986" />  
  </language>  
 </languages>  
 <entitySubhandlers />  
 <publishes>  
  <publish processed="false" />  
 </publishes>  
 <rootComponents>  
  <rootComponent processed="true">  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:20.83"  
           datetimeticks="634224269608387238" />  
  </rootComponent>  
 </rootComponents>  
 <dependencies>  
  <dependency processed="true">  
   <result result="success"  
           errorcode="0"  
           errortext=""  
           datetime="20:49:20.97"  
           datetimeticks="634224269609715208" />  
  </dependency>  
 </dependencies>  
</importexportxml>  
```  
  
<a name="BKMK_DeleteSolution"></a>

## <a name="delete-a-solution"></a>Eliminar una solución

 Este ejemplo muestra cómo eliminar una solución. El siguiente ejemplo muestra cómo recuperar una solución con el `uniquename` de la solución y después extraer el `solutionid` de los resultados. Use el `solutionid` con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Método <xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>.  
  
```csharp
// Delete a solution

QueryExpression queryImportedSolution = new QueryExpression
{
    EntityName = Solution.EntityLogicalName,
    ColumnSet = new ColumnSet(new string[] { "solutionid", "friendlyname" }),
    Criteria = new FilterExpression()
};


queryImportedSolution.Criteria.AddCondition("uniquename", ConditionOperator.Equal, ImportedSolutionName);

Solution ImportedSolution = (Solution)_serviceProxy.RetrieveMultiple(queryImportedSolution).Entities[0];

_serviceProxy.Delete(Solution.EntityLogicalName, (Guid)ImportedSolution.SolutionId);

Console.WriteLine("Deleted the {0} solution.", ImportedSolution.FriendlyName);
```  
  
<a name="BKMK_DetectSolutionDependencies"></a>

## <a name="detect-solution-dependencies"></a>Detectar dependencias de soluciones

 Este ejemplo muestra cómo crear un informe que muestre las dependencias entre los componentes de la solución.  
  
 Este código:  
  
- Recuperará todos los componentes de una solución.  
  
- Recuperará todas las dependencias para cada componente.  
  
- Para cada dependencia encontrada mostrará un informe describiendo la dependencia.  
  
```csharp
// Grab all Solution Components for a solution.
QueryByAttribute componentQuery = new QueryByAttribute
{
    EntityName = SolutionComponent.EntityLogicalName,
    ColumnSet = new ColumnSet("componenttype", "objectid", "solutioncomponentid", "solutionid"),
    Attributes = { "solutionid" },

    // In your code, this value would probably come from another query.
    Values = { _primarySolutionId }
};

IEnumerable<SolutionComponent> allComponents =
    _serviceProxy.RetrieveMultiple(componentQuery).Entities.Cast<SolutionComponent>();

foreach (SolutionComponent component in allComponents)
{
    // For each solution component, retrieve all dependencies for the component.
    RetrieveDependentComponentsRequest dependentComponentsRequest =
        new RetrieveDependentComponentsRequest
        {
            ComponentType = component.ComponentType.Value,
            ObjectId = component.ObjectId.Value
        };
    RetrieveDependentComponentsResponse dependentComponentsResponse =
        (RetrieveDependentComponentsResponse)_serviceProxy.Execute(dependentComponentsRequest);

    // If there are no dependent components, we can ignore this component.
    if (dependentComponentsResponse.EntityCollection.Entities.Any() == false)
        continue;

    // If there are dependencies upon this solution component, and the solution
    // itself is managed, then you will be unable to delete the solution.
    Console.WriteLine("Found {0} dependencies for Component {1} of type {2}",
        dependentComponentsResponse.EntityCollection.Entities.Count,
        component.ObjectId.Value,
        component.ComponentType.Value
        );
    //A more complete report requires more code
    foreach (Dependency d in dependentComponentsResponse.EntityCollection.Entities)
    {
        DependencyReport(d);
    }
}
``` 
  
  El método `DependencyReport` se encuentra en el siguiente ejemplo de código.  
  
### <a name="dependency-report"></a>Informe de dependencia

 El método de `DependencyReport` proporciona un mensaje más fácil de usar basándose en la información encontrada en la dependencia.  
  
> [!NOTE]
>  En este ejemplo el método se implementa solo parcialmente. Puede enviar mensajes solo para los componentes de la solución de atributo y de conjunto de opciones.  
  
```csharp
/// <summary>
   /// Shows how to get a more friendly message based on information within the dependency
   /// <param name="dependency">A Dependency returned from the RetrieveDependentComponents message</param>
   /// </summary> 
public void DependencyReport(Dependency dependency)
   {
 //These strings represent parameters for the message.
    String dependentComponentName = "";
    String dependentComponentTypeName = "";
    String dependentComponentSolutionName = "";
    String requiredComponentName = "";
    String requiredComponentTypeName = "";
    String requiredComponentSolutionName = "";

 //The ComponentType global Option Set contains options for each possible component.
    RetrieveOptionSetRequest componentTypeRequest = new RetrieveOptionSetRequest
    {
     Name = "componenttype"
    };

    RetrieveOptionSetResponse componentTypeResponse = (RetrieveOptionSetResponse)_serviceProxy.Execute(componentTypeRequest);
    OptionSetMetadata componentTypeOptionSet = (OptionSetMetadata)componentTypeResponse.OptionSetMetadata;
 // Match the Component type with the option value and get the label value of the option.
    foreach (OptionMetadata opt in componentTypeOptionSet.Options)
    {
     if (dependency.DependentComponentType.Value == opt.Value)
     {
      dependentComponentTypeName = opt.Label.UserLocalizedLabel.Label;
     }
     if (dependency.RequiredComponentType.Value == opt.Value)
     {
      requiredComponentTypeName = opt.Label.UserLocalizedLabel.Label;
     }
    }
 //The name or display name of the compoent is retrieved in different ways depending on the component type
    dependentComponentName = getComponentName(dependency.DependentComponentType.Value, (Guid)dependency.DependentComponentObjectId);
    requiredComponentName = getComponentName(dependency.RequiredComponentType.Value, (Guid)dependency.RequiredComponentObjectId);

 // Retrieve the friendly name for the dependent solution.
    Solution dependentSolution = (Solution)_serviceProxy.Retrieve
     (
      Solution.EntityLogicalName,
      (Guid)dependency.DependentComponentBaseSolutionId,
      new ColumnSet("friendlyname")
     );
    dependentComponentSolutionName = dependentSolution.FriendlyName;
    
 // Retrieve the friendly name for the required solution.
    Solution requiredSolution = (Solution)_serviceProxy.Retrieve
      (
       Solution.EntityLogicalName,
       (Guid)dependency.RequiredComponentBaseSolutionId,
       new ColumnSet("friendlyname")
      );
    requiredComponentSolutionName = requiredSolution.FriendlyName;

 //Display the message
     Console.WriteLine("The {0} {1} in the {2} depends on the {3} {4} in the {5} solution.",
     dependentComponentName,
     dependentComponentTypeName,
     dependentComponentSolutionName,
     requiredComponentName,
     requiredComponentTypeName,
     requiredComponentSolutionName);
   }
```
  
### <a name="detect-whether-a-solution-component-may-be-delete"></a>Detectar si un componente de la solución se puede eliminar

 Use el mensaje de <xref:Microsoft.Crm.Sdk.Messages.RetrieveDependenciesForDeleteRequest> para identificar cualquier otro componente de la solución que pueda evitar que un determinado componente de la solución se elimine. El siguiente ejemplo de código busca atributos que utilicen un conjunto de opciones global conocido. Cualquier atributo que utilice el conjunto de opciones global evitará que el conjunto de opciones global se elimine.  
  
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
    (RetrieveOptionSetResponse)_serviceProxy.Execute(
    retrieveOptionSetRequest);
_globalOptionSetId = retrieveOptionSetResponse.OptionSetMetadata.MetadataId;
if (_globalOptionSetId != null)
{ 
 //Use the global OptionSet MetadataId with the appropriate componenttype
 // to call RetrieveDependenciesForDeleteRequest
 RetrieveDependenciesForDeleteRequest retrieveDependenciesForDeleteRequest = new RetrieveDependenciesForDeleteRequest 
{ 
 ComponentType = (int)componenttype.OptionSet,
 ObjectId = (Guid)_globalOptionSetId
};

 RetrieveDependenciesForDeleteResponse retrieveDependenciesForDeleteResponse =
  (RetrieveDependenciesForDeleteResponse)_serviceProxy.Execute(retrieveDependenciesForDeleteRequest);
 Console.WriteLine("");
 foreach (Dependency d in retrieveDependenciesForDeleteResponse.EntityCollection.Entities)
 {

  if (d.DependentComponentType.Value == 2)//Just testing for Attributes
  {
   String attributeLabel = "";
   RetrieveAttributeRequest retrieveAttributeRequest = new RetrieveAttributeRequest
   {
    MetadataId = (Guid)d.DependentComponentObjectId
   };
   RetrieveAttributeResponse retrieveAttributeResponse = (RetrieveAttributeResponse)_serviceProxy.Execute(retrieveAttributeRequest);

   AttributeMetadata attmet = retrieveAttributeResponse.AttributeMetadata;

   attributeLabel = attmet.DisplayName.UserLocalizedLabel.Label;
  
    Console.WriteLine("An {0} named {1} will prevent deleting the {2} global option set.", 
   (componenttype)d.DependentComponentType.Value, 
   attributeLabel, 
   _globalOptionSetName);
  }
 }                 
}
``` 

### <a name="see-also"></a>Vea también

 [Empaquetar y distribuir extensiones con soluciones de Dynamics 365](/dynamics365/customer-engagement/developer/package-distribute-extensions-use-solutions)   
 [Introducción a las soluciones](introduction-solutions.md)   
 [Planear el desarrollo de la solución](/dynamics365/customer-engagement/developer/plan-solution-development)   
 [Seguimiento de las dependencias de los componentes de la solución](dependency-tracking-solution-components.md)   
 [Crear, exportar o importar una solución no administrada](create-export-import-unmanaged-solution.md)   
 [Crear, instalar y actualizar una solución administrada](create-install-update-managed-solution.md)   
 [Desinstalar o eliminar una solución](uninstall-delete-solution.md)   
 [Entidades de solución](/dynamics365/customer-engagement/developer/solution-entities)   
 [Ejemplo: trabajar con soluciones](org-service/samples/work-solutions.md) [Ejemplo: detectar dependencias de la solución](/dynamics365/customer-engagement/developer/sample-detect-solution-dependencies)
