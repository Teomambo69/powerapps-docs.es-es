---
title: Recuperar un registro de entidad con el servicio de organización (Common Data Service)| Microsoft Docs
description: Describe las opciones disponibles cuando se recupera un registro mediante programación
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 84164ad1914486e011996a66e78ac5f6ff5f3c7d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156072"
---
# <a name="retrieve-an-entity-using-the-organization-service"></a>Recuperación de una entidad usando un servicio de organización

También recuperará normalmente un registro según los resultados de una consulta y los resultados de la consulta deben incluir un identificador único para el registro de entidades.

> [!NOTE]
> En los siguientes ejemplos la variable `accountid` representa al identificador <xref:System.Guid> para el registro de la entidad de cuenta.

Existen algunas opciones para definir los datos devueltos cuando se recupera un registro de entidades. Usará la clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> para definir los valores de atributo que requiere.


> [!IMPORTANT]
> Cuando se recuperan los registros de la entidad debe solicitar solo los valores de atributo que necesita estableciendo los atributos específicos mediante el constructor de la clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>. Aunque el constructor de la clase <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> proporcione una sobrecarga que acepte un parámetro booleano `allColumns`, no debería utilizar este código de producción. Más información: [No recuperar la entidad todas las columnas mediante las API de consulta](/dynamics365/customer-engagement/guidance/data/retrieve-specific-columns-entity-via-query-apis)

Si necesita devolver registros de entidad relacionados puede incluir una consulta en su solicitud de recuperación para definir los registros relacionados que se van a volver.


## <a name="basic-retrieve"></a>Recuperación básica

Puede recuperar registros individuales mediante el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> o estableciendo la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.Target> de la clase <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> en un registro de referencia y utilizar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .

Este ejemplo muestra cómo se usa el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> .

```csharp
Entity entity = svc.Retrieve("account", accountid, new ColumnSet("name"));
Console.WriteLine("account name: {0}", entity["name"]);
```

Este ejemplo muestra cómo se usan las clases <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> y <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> .

```csharp
RetrieveRequest request = new RetrieveRequest()
{
  ColumnSet = new ColumnSet("name"),
  Target = new EntityReference("account", accountid)
};
var response = (RetrieveResponse)svc.Execute(request);
Entity entity = response.Entity;
Console.WriteLine("account name: {0}", entity["name"]);
```

> [!NOTE]
> La mayor parte del tiempo debe usar el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> .
>
> Use el <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> con el método <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> para las circunstancias especiales según se describen a continuación. 
> Más información: 
> - [Recuperación con los registros relacionados](#retrieve-with-related-records)
> - [Recuperación con una clave alternativa](#retrieve-with-an-alternate-key)


## <a name="retrieve-with-related-records"></a>Recuperación con los registros relacionados

Cuando se recupera un registro individual también puede incluir una consulta para incluir registros relacionados configurando la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.RelatedEntitiesQuery> de <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>.

Puede definir una consulta utilizando cualquiera de las clases derivadas de <xref:Microsoft.Xrm.Sdk.Query.QueryBase> y asociarla con una relación de entidad específica. Agregue un conjunto de pares de consultas y de relaciones a la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.RelatedEntitiesQuery> mediante un <xref:Microsoft.Xrm.Sdk.RelationshipQueryCollection>.

El siguiente ejemplo incluye los registros `task` y `contact` relacionados con el registro de entidad `account` que se está recuperando.

```csharp

var relationshipQueryCollection = new RelationshipQueryCollection();

var relatedTasks = new QueryExpression("task");
relatedTasks.ColumnSet = new ColumnSet("subject", "description");
var taskRelationship = new Relationship("Account_Tasks");
relationshipQueryCollection.Add(taskRelationship, relatedTasks);


var relatedContacts = new QueryExpression("contact");
relatedContacts.ColumnSet = new ColumnSet("fullname", "emailaddress1");
var contactRelationship = new Relationship("account_primary_contact");
relationshipQueryCollection.Add(contactRelationship, relatedContacts);

var request = new RetrieveRequest()
{
  ColumnSet = new ColumnSet(true),
  RelatedEntitiesQuery = relationshipQueryCollection,
  Target = new EntityReference("account", accountid)
};

RetrieveResponse response = (RetrieveResponse)svc.Execute(request);

Entity retrievedAccount = response.Entity;

Console.WriteLine("Account Name: {0}",retrievedAccount["name"]);

var tasks = retrievedAccount.RelatedEntities[new Relationship("Account_Tasks")];

Console.WriteLine("Tasks:");
tasks.Entities.ToList().ForEach(x => {
  Console.WriteLine(" Task Subject: {0}",x["subject"]);
});

Entity primaryContact = retrievedAccount
  .RelatedEntities[new Relationship("account_primary_contact")]
  .Entities.FirstOrDefault();

Console.WriteLine("Primary Contact Fullname: {0}",primaryContact["fullname"]);
```
Los resultados del ejemplo pueden tener el siguiente aspecto:

```
Account Name: City Power & Light (sample)
Tasks:
 Task Subject: Task 1
 Task Subject: Task 2
Primary Contact Fullname: Scott Konersmann (sample)
```

Más información: [Consulta de datos duplicados con el servicio de la organización](entity-operations-query-data.md)


## <a name="retrieve-with-an-alternate-key"></a>Recuperación con una clave alternativa

Si ha configurado una entidad para usar una clave alternativa, puede usar esta clave alternativa para definir un <xref:Microsoft.Xrm.Sdk.EntityReference> y para pasar este valor como la propiedad <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.Target> .

Por ejemplo, si define el atributo `account` `accountnumber` para que sea una clave alternativa, puede recuperar una cuenta si utiliza el valor de ese atributo.


```csharp
RetrieveRequest request = new RetrieveRequest()
{
ColumnSet = new ColumnSet("name"),
Target = new EntityReference("account", "accountnumber", "0001")
};
var response = (RetrieveResponse)svc.Execute(request);
Entity entity = response.Entity;

Console.WriteLine(entity["name"]);
```

Si la clave alternativa es un conjunto de varios atributos, definirá una <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection>. El siguiente ejemplo es para una entidad cuenta que tiene una clave alternativa que incluye los atributos `accountnumber` y `sic`.

```csharp
var keyCollection = new KeyAttributeCollection();
keyCollection.Add("accountnumber", "0001");
keyCollection.Add("sic", "7372");

RetrieveRequest request = new RetrieveRequest()
{
ColumnSet = new ColumnSet("name"),
Target = new EntityReference("account", keyCollection)
};
var response = (RetrieveResponse)svc.Execute(request);
Entity entity = response.Entity;

Console.WriteLine(entity["name"]);
```
> [!NOTE]
> Las claves alternativas se usan normalmente solo para los escenarios de integración de datos


## <a name="access-formatted-values"></a>Valores de acceso con formato

El método para obtener acceso a valores con formato en una operación de recuperación es el mismo que usará al obtener acceso a los mismos en los resultados de una consulta. Más información: [Obtener acceso a valores con formato](entity-operations-query-data.md#access-formatted-values).

<!-- TODO Move the information about accessing formatted values here, where the topic is shorter rather than the query topic which is longer -->

### <a name="see-also"></a>Vea también

[Crear entidades con el servicio de la organización](entity-operations-create.md)<br />
[Actualizar y eliminar entidades con el servicio de la organización](entity-operations-update-delete.md)<br />
[Asociar y desasociar entidades con el servicio de la organización](entity-operations-associate-disassociate.md)<br />
