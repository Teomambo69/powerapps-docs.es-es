---
title: Uso de OrganizationServiceContext (Common Data Service) | Microsoft Docs
description: La clase OrganizationServiceContext permite controlar los cambios, administrar identidades y relaciones, y proporciona acceso al proveedor de LINQ.
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
ms.openlocfilehash: a9703413b81f7aa95606f215a002957eed5c8d34
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749543"
---
# <a name="use-organizationservicecontext"></a>Usar OrganizationServiceContext

En Common Data Service, puede usar las distintas clases que implementan la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService> para acceder a los servicios web. Como alternativa, puede usar el <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> generado por la herramienta de generación de código para acceder a la funcionalidad adicional. La clase `OrganizationServiceContext` permite controlar los cambios, administrar identidades y relaciones, y proporciona acceso al proveedor de LINQ. Esta clase también contiene un método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> que se usa para enviar los cambios a datos que el contexto está siguiendo. Esta clase se basa en el mismo concepto que el de la clase [DataServiceContext](/dotnet/api/system.data.services.client.dataservicecontext) en los servicios de datos de Windows Communication Foundation (WCF).  
  
Para generar esta clase, proporcione un valor para el parámetro de `/serviceContextName` cuando genere enlaces en tiempo de compilación. La herramienta de generación de código usa este nombre como nombre de la clase generada. Para obtener más información acerca de cómo utilizar la herramienta de generación de código, consulte [Generar clases de entidad con enlace en tiempo de compilación con la herramienta de generación de código (CrmSvcUtil.exe)](generate-early-bound-classes.md). Puede usar el contexto del servicio de la organización cuando desarrolle aplicaciones, complementos y actividades de flujo de trabajo.  
  
<a name="how_to_use"></a>

## <a name="how-to-use-the-organizationservicecontext-class"></a>Cómo usar la clase OrganizationServiceContext  

Para crear una instancia de la clase de contexto, debe pasar al constructor de clases un objeto que implemente la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService>. Una opción es pasar una instancia de la clase <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. Para obtener más información sobre la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService>, vea [Interfaz de IOrganizationService](iorganizationservice-interface.md).
  
El siguiente ejemplo de código muestra cómo crear una nueva instancia de la clase de contexto. En este ejemplo, a la clase de contexto se le dio el nombre `AdventureWorksCycleServiceContext` especificando el nombre mediante el parámetro `/serviceContextName` en la herramienta de generación de código:  
  
```csharp  
//For early bound types to work correctly, they have to be enabled on the proxy.  
_serviceProxy.EnableProxyTypes();  
AdventureWorksCycleServiceContext context = new AdventureWorksCycleServiceContext(svc);  
```  
  
Tras crear el objeto del contexto del servicio de la organización, puede iniciar el seguimiento para crear, editar o eliminar entidades. 
  
El contexto del servicio de la organización debe seguir cualquier entidad o relación que desee enviar a Common Data Service. Por ejemplo, podría recuperar un registro con una consulta LINQ y el contexto realizaría el seguimiento de esa entidad o podría usar el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)> para hacer que el contexto inicie el seguimiento de la entidad. Puede trabajar con datos en una aplicación cliente y crear entidades nuevas, crear entidades relacionadas, y modificar las entidades existentes, pero debe llamar al método de `SaveChanges` en las entidades seguidas para confirmar los cambios en el servidor de Common Data Service.  
  
<a name="track_changes"></a>

## <a name="track-changes"></a>Seguimiento de cambios
 
Para determinar cómo el contexto sigue a una entidad, puede comprobar la propiedad de <xref:Microsoft.Xrm.Sdk.Entity.EntityState> en la instancia de entidad. Debe notificar al contexto del servicio de la organización que siga a una entidad de Common Data Service llamando a varios métodos o utilizando una consulta de LINQ. El contexto de servicio sigue a todas las entidades devueltas por una consulta de LINQ.  
  
Puede agregar objetos al contexto de servicio llamando a uno de los siguientes métodos en <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.  
  
|Método|Usar|  
|------------|---------|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)>|Agrega una entidad al conjunto de entidades que el contexto del servicio de la organización está siguiendo. El estado de la entidad en el contexto se establece en `Created`. Si se llama al método de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>, este registro se creará o agregará al servidor.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)>|Agrega una entidad al conjunto de entidades que el contexto del servicio de la organización está siguiendo. El estado de la entidad en el contexto se establece en `Unchanged`. Si se llama al método de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>, no se enviará esta entidad al servidor a menos que su estado cambie.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.CreateQuery(System.String)>|Agrega los resultados de una consulta al conjunto de entidades que el contexto del servicio de la organización está siguiendo.|  
  
<a name="track_related"></a>

## <a name="track-related-objects"></a>Seguimiento de objetos relacionados

En Common Data Service, el contexto del servicio de la organización permite crear y actualizar relaciones entre entidades. Las propiedades de navegación generadas por la herramienta CrmSvcUtil.exe y ubicadas en las clases de enlace en tiempo de compilación permiten acceder y cambiar propiedades y relaciones relacionadas con la entidad. El contexto del servicio de la organización debe seguir la entidad relacionada para que la entidad relacionada esté disponible para actualizarse en el servidor.  
  
Use los siguientes métodos en el <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> para trabajar con entidades relacionadas y agregar la entidad al contexto del servicio:  
  
|Método|Usar|  
|------------|---------|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddRelatedObject(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Agrega el destino al contexto. Llama al método de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)> en la entidad de destino y luego llama al método de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)> entre la entidad de origen y la entidad de destino (relacionada).|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AttachLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Agrega la entidad relacionada al contexto para realizar el seguimiento. El estado de la entidad en el contexto se establece en `Unchanged`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Crea una relación entre las entidades de origen y de destino. Agrega el destino al contexto. El estado de la entidad de destino en el contexto se establece en `Created`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.LoadProperty(Microsoft.Xrm.Sdk.Entity,System.String)>|Carga el conjunto de la entidad relacionada para la relación especificada. Da acceso a las entidades relacionadas mediante la propiedad de navegación. Llame al método de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)> en la entidad relacionada tras acceder a la entidad usando una propiedad de navegación en la entidad primaria.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.UpdateObject(Microsoft.Xrm.Sdk.Entity)>|Cambia el estado de la entidad especificada en el `OrganizationServiceContext` a editado.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.DeleteObject(Microsoft.Xrm.Sdk.Entity)>|Cambia el estado de la entidad especificada que se va a eliminar en el `OrganizationServiceContext`.|  
  
<a name="BKMK_LoadRelatedEntities"></a>

### <a name="load-related-entities-using-navigation-properties"></a>Cargar entidades relacionadas mediante propiedades de navegación

Las entidades relacionadas para las entidades que ha recuperado mediante LINQ serán nulas hasta que se use <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.LoadProperty(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship)> para recuperarlas. El siguiente ejemplo de código muestra cómo tener acceso a registros de tarea asociados a un registro de contacto específico.  
  
```csharp  
Contact pam = context.ContactSet.Where(c => c.FirstName == "Pamela").FirstOrDefault();  
if (pam != null)  
{  
// pam.Contact_Tasks is null until you use LoadProperty  
    context.LoadProperty(pam, "Contact_Tasks");  
    Task firstTask = pam.Contact_Tasks.FirstOrDefault();  
}  
```  
### <a name="use-the-addlink-method"></a>Uso del método AddLink  
 Puede usar el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)> para crear asociaciones. Debe llamar al método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> antes de que el servidor se actualice con la información del nuevo vínculo.  
  
 El siguiente ejemplo de código muestra cómo crear una asociación entre un contacto y una cuenta.  
  
```csharp  
Relationship relationship = new Relationship("account_primary_contact");  
context.AddLink(contact, relationship, account);  
context.SaveChanges();  
```  

<a name="save_changes"></a>

## <a name="save-changes"></a>Guardar cambios

El contexto del servicio de la organización organiza un gráfico de las entidades que está siguiendo. El orden en que el contexto del servicio de la organización procesa cambios en la entidad y los envía al servidor es importante. Las actualizaciones de la entidad primaria se procesan y luego se procesan las entidades relacionadas. Si un valor se establece en la entidad primaria por la entidad relacionada, se usa ese valor al actualizar los datos en el servidor.  
  
Si se produce un error cuando se guarda la información de la entidad, se genera un nuevo tipo de excepción que contiene <xref:Microsoft.Xrm.Sdk.SaveChangesResult> mediante el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> independientemente del valor del parámetro <xref:Microsoft.Xrm.Sdk.Client.SaveChangesOptions> que se pase al método.  
  
<a name="virtual"></a>

## <a name="use-virtual-methods-when-the-context-is-changed"></a>Usar métodos virtuales cuando cambia el contexto

A veces puede ser necesario realizar acciones en función de los cambios en el <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>. Para facilitar esto, se proporcionan métodos virtuales para permitirle interceptar o que se le notifique una operación. Para aprovechar estos métodos, tiene que derivar de <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> o cambiar el contexto generado de servicios de la organización. La siguiente tabla enumera los métodos virtuales.  
  
|Método|Descripción|  
|------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnBeginEntityTracking(Microsoft.Xrm.Sdk.Entity)>|Llamado después de que una entidad se asocie a `OrganizationServiceContext`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnBeginLinkTracking(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Llamado después de que un vínculo se asocie a `OrganizationServiceContext`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnEndEntityTracking(Microsoft.Xrm.Sdk.Entity)>|Llamado después de que una entidad se desasocie de `OrganizationServiceContext`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnEndEntityTracking(Microsoft.Xrm.Sdk.Entity)>|Llamado después de que un vínculo se desasocie de `OrganizationServiceContext`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnExecuting(Microsoft.Xrm.Sdk.OrganizationRequest)>|Llamado inmediatamente antes de que una solicitud se envíe a Common Data Service.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnExecute(Microsoft.Xrm.Sdk.OrganizationRequest,Microsoft.Xrm.Sdk.OrganizationResponse)>|Llamado inmediatamente después de que una solicitud se envíe a Common Data Service, independientemente de si se produjo una excepción o no.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnSavingChanges(Microsoft.Xrm.Sdk.Client.SaveChangesOptions)>|Llamado antes de que ocurra una operación tras una llamada a `SaveChanges`.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnSaveChanges(Microsoft.Xrm.Sdk.SaveChangesResultCollection)>|Llamado cuando todas las operaciones de una llamada a `SaveChanges` se han completado, o si hay un error.|  


<a name="use_context"></a>   

## <a name="data-operations"></a>Operaciones de datos

Puede modificar, crear y eliminar objetos del contexto de servicio de la organización, y Common Data Service hace un seguimiento de los cambios realizados en estos objetos. Cuando se llama al método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> Common Data Service genera y ejecuta comandos que realizan las instrucciones de inserción, actualización o eliminación equivalentes en los datos de Common Data Service.  
  
Al trabajar con clases de entidad de enlace de tiempo de compilación, se utiliza el nombre de entidad y el nombre de esquema del atributo para especificar una entidad o un atributo con el que trabajar. Los nombres de esquema del atributo se definen en <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName> y <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>, o puede usar los nombres de clase y de propiedad mostrados en el archivo generado por el código. El siguiente ejemplo muestra cómo asignar un valor al atributo de correo electrónico de una nueva instancia de contacto.  
  
```csharp  
Contact contact = new Contact();
contact.EMailAddress1 = “sonny@contoso.com”;  
```  
 
  
<a name="create_new"></a>   

## <a name="create-a-new-entity-record"></a>Creación de un nuevo registro

 Si desea insertar datos en Common Data Service mediante el modelo de datos de la entidad, debe crear una instancia de un tipo de entidad y agregar el objeto a un contexto de servicio de la organización. El contexto de servicio de la organización debe realizar un seguimiento del objeto para poder guardarlo en Common Data Service.  
  
 Cuando se crea un nuevo registro de entidad, se agrega el objeto al contexto de servicio de la organización mediante el <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)>. Método.  
  
 El siguiente ejemplo muestra la creación y el guardado de un nuevo registro de contacto usando el modelo de datos de la entidad. También demuestra cómo acceder a un atributo personalizado.  
  
```csharp  
OrganizationServiceContext orgContext =new OrganizationServiceContext(svc);  
Contact contact = new Contact()     
 {  
   FirstName = "Charles",  
   LastName = "Brown",  
   Address1_Line1 = "123 Main St.",  
   Address1_City = "Des Moines",  
   Address1_StateOrProvince = "IA",  
   Address1_PostalCode = "21254",  
   new_twittername = "Chuck",  
   Telephone1 = "123-234-5678"  
 };   
orgContext.AddObject(contact);
orgContext.SaveChanges();  
```  

Existen varios puntos a tener en cuenta en el código de ejemplo anterior. Primero, después de que se cree una instancia de un nuevo contacto, pasa ese objeto de contacto al método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)> de manera que el contexto puede seguir realizando un seguimiento del objeto. El segundo punto es que el nuevo objeto se guarda en el servidor mediante el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> .  
  
Después de agregar un objeto al contexto y antes de que se llame al método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>, el contexto genera un identificador para el nuevo objeto. Una excepción que contiene el valor `SaveChangesResults` se genera desde el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> si falla alguna actualización en los datos de Common Data Service.  
  
<a name="update"></a>   

## <a name="update-an-entity-record"></a>Actualizar un registro de entidad  

Common Data Service hace un seguimiento de los cambios en los objetos asociados al contexto de servicio de la organización. Para modificar un registro de entidad existente, primero debe agregar el objeto al contexto. Para agregar un objeto al contexto, primero debe recuperar el registro de entidad de Common Data Service y después agregar el objeto al contexto mediante el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)>. Una vez el contexto esté realizando el seguimiento del objeto, puede actualizar el registro estableciendo los atributos de la entidad.  
  
El siguiente ejemplo muestra cómo actualizar un atributo de cuenta con clases de enlaces en tiempo de compilación.  
  
```csharp  
Account.EMailAddress1 = “Contoso-WebMaster@contoso.com”;  
```  
  
 El siguiente ejemplo muestra cómo eliminar un valor de atributo.  
  
```csharp  
Account.EMailAddress1 = null;  
```  
  
 Existen dos métodos parciales denominados `OnPropertyChanging` y `OnPropertyChanged` para cada entidad. A estos métodos se les llama en el establecedor de propiedad. Puede ampliar estos métodos mediante clases parciales para insertar lógica de negocios personalizada.  
  
<a name="delete"></a>   

## <a name="delete-an-entity-record"></a>Elimine un registro de entidad   

Para eliminar un registro de entidad, el contexto de servicio de la organización debe realizar un seguimiento del objeto. Una vez el objeto esté en el contexto, puede usar el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.DeleteObject(Microsoft.Xrm.Sdk.Entity)> para marcar el objeto en el contexto para su eliminación. Tenga en cuenta que el registro de entidad de Common Data Service no se eliminará hasta que se llame al método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> .  
  
### <a name="see-also"></a>Vea también

[Ejemplos de la consulta LINQ mediante OrganizationServiceContext con Common Data Service](linq-query-examples.md)<br />
[Generar clases para programación en tiempo de compilación con el servicio de la organización](generate-early-bound-classes.md)<br />
<xref:Microsoft.Xrm.Sdk.IOrganizationService><br />
<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>