---
title: Utilizar mensajes con el servicio de la organización (Common Data Service para aplicaciones) | Microsoft Docs
description: Conocer cómo se usan los mensajes para invocar operaciones con el servicio de la organización.
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
# <a name="use-messages-with-the-organization-service"></a>Utilizar mensajes con el servicio de la organización

Todas las operaciones de datos del servicio de la organización se definen como mensajes. Mientras el <xref:Microsoft.Xrm.Sdk.IOrganizationService> proporciona 7 métodos para realizar operaciones de datos (<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*>, y <xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*> ), cada uno de estos métodos es un contenedor cómodo en torno a los mensajes subyacentes que en última instancia se invoca mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>. El servicio de la organización subyacente tiene sólo el método <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> que es un único parámetro: una instancia de la clase <xref:Microsoft.Xrm.Sdk.OrganizationRequest>. El valor devuelto por el método `Execute` es una instancia de la clase <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.

Para mejorar su experiencia al escribir código, todas las operaciones de datos estándar del sistema tienen un par de clases `*Request` y `*Response` definidas en los ensamblados del SDK. Cada una de estas clases heredan de las clases <xref:Microsoft.Xrm.Sdk.OrganizationRequest> y <xref:Microsoft.Xrm.Sdk.OrganizationResponse> correspondientes y proporcionan una experiencia más productiva para usted al escribir código.

Los ejemplos siguientes muestran tres formas distintas de crear un registro de entidad de cuenta definido de esta manera:

```csharp
var account = new Account();
account.Name = "Test account";
```

Usar <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>

```csharp
var id = svc.Create(account);
```

Usar <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> con <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

```csharp
CreateRequest request = new CreateRequest()
{ Target = account };
var id = ((CreateResponse)svc.Execute(request)).id;
```

Usar <xref:Microsoft.Xrm.Sdk.OrganizationRequest> con <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

```csharp
ParameterCollection parameters = new ParameterCollection();
parameters.Add("Target", account);

OrganizationRequest request = new OrganizationRequest() {
RequestName = "Create",
Parameters = parameters
};

OrganizationResponse response = svc.Execute(request);

var id = (Guid)response.Results["id"];
```

Como puede ver, las operaciones de datos comunes se han agilizado usando los métodos los métodos <xref:Microsoft.Xrm.Sdk.IOrganizationService> y los mensajes del sistema se han simplificado por las clases `*Response` y `*Request` en los ensamblados del SDK. La mayor parte del tiempo no necesitará usar las clases <xref:Microsoft.Xrm.Sdk.OrganizationRequest> y <xref:Microsoft.Xrm.Sdk.OrganizationResponse> subyacentes excepto en los siguientes casos.

## <a name="working-with-messages-in-plug-ins"></a>Trabajar con mensajes en complementos

Los datos que se describen una operación en un complemento tendrán la forma de <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> y <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>. Estas propiedades <xref:Microsoft.Xrm.Sdk.ParameterCollection> contienen los valores usados para la <xref:Microsoft.Xrm.Sdk.OrganizationRequest> en las primeras dos fases de la canalización de ejecución de eventos y la clase <xref:Microsoft.Xrm.Sdk.OrganizationResponse> en la fase después de la operación principal.

Conocer la estructura de los mensajes le ayudará a comprender dónde encontrar los datos que desea comprobar o cambiar en el complemento.

Más información: 

- [Escriba complementos para ampliar los procesos de negocio](../plug-ins.md)
- [Marco de trabajo de eventos](../event-framework.md)

## <a name="using-custom-actions"></a>Usar acciones personalizadas

Cuando usa una acción personalizada no hay clases en los ensamblados de SDK para estas operaciones. Puede generar clases para ellos con la herramienta de generación de código `CrmSvcUtil.exe` usando el parámetro `generateActions`, o bien puede crear la instancia de una <xref:Microsoft.Xrm.Sdk.OrganizationRequest> y establecer <xref:Microsoft.Xrm.Sdk.OrganizationRequest.RequestName> y <xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters> para usarla sin las clases generadas. Para trabajar con los resultados, deberá analizar los valores devueltos desde <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.<xref:Microsoft.Xrm.Sdk.OrganizationResponse.Results> .

Más información: 

- [Generar clases para programación en tiempo de compilación con el servicio de la organización](generate-early-bound-classes.md)
- [Acciones personalizadas](../custom-actions.md)

## <a name="passing-optional-parameters-with-a-request"></a>Pasar parámetros opcionales con una solicitud

Puede pasar parámetros opcionales en mensajes mediante la propiedad <xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters> que se expone para todas las clases de mensaje *Request en los ensamblados del SDK. Hay dos parámetros opcionales que puede pasar con mensajes.

|`Parameter`|Descripción|Mensajes|  
|-----------------|-----------------|--------------|  
|`SolutionUniqueName`|Una `String` especifica que el nombre único de la solución a la que se aplica la operación. Más información: [Seguimiento de las dependencias de los componentes de la solución](../dependency-tracking-solution-components.md).|<xref:Microsoft.Crm.Sdk.Messages.AddPrivilegesRoleRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.MakeAvailableToOrganizationTemplateRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>|  
|`SuppressDuplicateDetection`|Un `Boolean` usado para deshabilitar la detección de duplicados en una operación de creación o actualización. Más información: [Usar parámetro SuppressDuplicateDetection para lanzar errores al crear o actualizar registro](detect-duplicate-data.md#use-suppressduplicatedetection-parameter-to-throw-errors-when-you-create-or-update-record).|<xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>|  
  
 El siguiente ejemplo se muestra cómo pasar un parámetro opcional:  
  
```csharp  
Account account = new Account();  
account.Name = "Fabrikam";  
CreateRequest req = new CreateRequest();  
req.Target = account;  
req["SuppressDuplicateDetection"] = true;  
CreateResponse response = (CreateResponse)svc.Execute(req);  
```  

### <a name="see-also"></a>Vea también

[Operaciones de la entidad con el servicio de organización](entity-operations.md)<br />
[Uso de ExecuteAsync](use-executeAsync.md)<br />
[Uso de ExecuteTransaction](use-executetransaction.md)<br />
[Ejecutar varias solicitudes con el servicio de la organización](execute-multiple-requests.md)



