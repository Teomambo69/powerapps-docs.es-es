---
title: Usar clase de entidad de enlace en tiempo de ejecución con una consulta LINQ (Common Data Service para aplicaciones) | Microsoft Docs
description: Lea cómo puede usar enlaces en tiempo de ejecución con las consulta integradas del lenguaje .NET (LINQ)
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
# <a name="use-late-bound-entity-class-with-a-linq-query"></a>Usar clase de entidad de enlace en tiempo de ejecución con una consulta LINQ

En Common Data Service para aplicaciones puede usar enlaces en tiempo de ejecución con las consulta integradas del lenguaje .NET (LINQ). El enlace en tiempo de ejecución usa el nombre lógico del atributo, y se resuelve en un tiempo de ejecución.  
  
<a name="usinglatebindingjoin"></a>   

## <a name="using-late-binding-in-a-join-clause"></a>Uso del enlace en tiempo de ejecución en una cláusula de combinación  

 Los siguientes ejemplos muestran cómo usar el enlace en tiempo de ejecución en la cláusula de `join` de una consulta de LINQ.  
  
 Recuperar el nombre completo del contacto que representa el contacto principal de una cuenta y el nombre de la cuenta.  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_join2 = from c in orgSvcContext.CreateQuery("contact")
                   join a in orgSvcContext.CreateQuery("account")
                   on c["contactid"] equals a["primarycontactid"]
                   select new
                   {
                    contact_name = c["fullname"],
                    account_name = a["name"]
                   };
 foreach (var c in query_join2)
 {
  System.Console.WriteLine(c.contact_name + "  " + c.account_name);
 }
}
 ```
 Recupere los datos del contacto, de la cuenta y de los clientes potenciales donde el cliente potencial fue el cliente potencial original y el apellidos del contacto no es "Parker"  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_dejoin = from c in orgSvcContext.CreateQuery("contact")
                    join a in orgSvcContext.CreateQuery("account") 
                    on c["contactid"] equals a["primarycontactid"]
                    join l in orgSvcContext.CreateQuery("lead") 
                    on a["originatingleadid"] equals l["leadid"]
                    where (string)c["lastname"] != "Parker"
                    select new { Contact = c, Account = a, Lead = l };
 foreach (var c in query_dejoin)
 {
  System.Console.WriteLine(c.Account.Attributes["name"] + " " + 
   c.Contact.Attributes["fullname"] + " " + c.Lead.Attributes["leadid"]);
 }
}
 ```
<a name="Usinglatebindingleft"></a>   

## <a name="using-late-binding-in-a-left-join"></a>Uso del enlace en tiempo de ejecución en una combinación izquierda  

 En el siguiente ejemplo se muestra cómo recuperar una lista de información de contacto y de la cuenta con una combinación izquierda. Una combinación izquierda está diseñada para devolver elementos principales con y sin elementos secundarios desde dos orígenes. Existe una correlación entre los elementos principales y los elementos secundarios, pero es posible que no existan elementos secundarios  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_join9 = from a in orgSvcContext.CreateQuery("account")
                   join c in orgSvcContext.CreateQuery("contact") 
                   on a["primarycontactid"] equals c["contactid"] into gr
                   from c_joined in gr.DefaultIfEmpty()
                   select new
                   {
                    account_name = a.Attributes["name"]
                   };
 foreach (var c in query_join9)
 {
  System.Console.WriteLine(c.account_name);
 }
}
 ```
<a name="contains"></a>   

## <a name="using-late-binding-and-the-contains-method"></a>Uso del enlace en tiempo de compilación y del método Contains  

 El siguiente ejemplo muestran cómo usar el enlace en tiempo de ejecución con el método de `Contains` de una consulta de LINQ.  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_contains3 = from c in orgSvcContext.CreateQuery("contact")
                       where ((string)c["description"]).Contains("Coho")
                       select new
                       {
                        firstname = c.Attributes["firstname"],
                        lastname = c.Attributes["lastname"]
                       };
 foreach (var c in query_contains3)
 {
  System.Console.WriteLine(c.firstname + " " + c.lastname);
 }
}
 ```
 <a name="notequals"></a>   

## <a name="using-late-binding-and-not-equals-operator"></a>Uso del enlace en tiempo de ejecución y operador Not Equals  

 El siguiente muestra cómo usar el operador Not Equals.  
  
 ```csharp
using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_ne3 = from c in orgSvcContext.CreateQuery("contact")
                 where !c["address1_city"].Equals(null)
                 select new
                 {
                  FirstName = c["firstname"],
                  LastName = c["lastname"],
                  Address1_City = c["address1_city"]
                 };
 foreach (var c in query_ne3)
 {
  System.Console.WriteLine(c.FirstName + " " + 
   c.LastName + " " + c.Address1_City);
 }
}
```

 <a name="getattribute"></a>   

## <a name="using-the-getattributevalue-method"></a>Uso del método de GetAttributeValue  

 En el siguiente ejemplo se muestra cómo recuperar la información de contacto mediante el método de `GetAttributeValue`.  
  
 ```csharp
using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{

 var list_getattrib1 = (from c in orgSvcContext.CreateQuery("contact")
                        where c.GetAttributeValue<Guid?>("contactid") != _contactId1
                        select new { 
                         FirstName = c.GetAttributeValue<string>("firstname"), 
                         LastName = c.GetAttributeValue<string>("lastname") 
                        }).ToList();
 foreach (var c in list_getattrib1)
 {
  System.Console.WriteLine(c.FirstName + " " + c.LastName);
 }
}
```
  
### <a name="see-also"></a>Vea también  
 [Crear consultas con LINQ (.NET Language-Integrated Query)](build-queries-with-linq-net-language-integrated-query.md)   
 [Ordenar resultados mediante atributos de entidad con LINQ](order-results-entity-attributes-linq.md)   
 <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.CreateQuery``1>