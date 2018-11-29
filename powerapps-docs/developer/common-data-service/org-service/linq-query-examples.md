---
title: <Topic Title> (Common Data Service para aplicaciones) | Microsoft Docs
description: <Description>
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
# <a name="linq-query-examples-using-organizationservicecontext-with-common-data-service-for-apps"></a>Ejemplos de la consulta LINQ mediante OrganizationServiceContext con Common Data Service para aplicaciones

Este tema contiene muchos ejemplos de código de consultas LINQ.  
  
<a name="SimpleWhereClause"></a>   
## <a name="simple-where-clause"></a>Cláusula Where sencilla  
 El siguiente ejemplo muestra cómo recuperar una lista de cuentas cuyo campo Name contiene “Contoso”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_where1 = from a in svcContext.AccountSet
        where a.Name.Contains("Contoso")
        select a;
    foreach (var a in query_where1)
    {
        System.Console.WriteLine(a.Name + " " + a.Address1_City);
    }
}
```  
  
 El siguiente ejemplo muestra cómo recuperar una lista de cuentas cuyo campo Name contiene “Contoso” y cuyo campo Address1_City es “Redmond”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_where2 = from a in svcContext.AccountSet
                    where a.Name.Contains("Contoso")
                    where a.Address1_City == "Redmond"
                    select a;

    foreach (var a in query_where2)
    {
        System.Console.WriteLine(a.Name + " " + a.Address1_City);
    }
}
``` 
  
<a name="JoinandSimpleWhereClause"></a>   
## <a name="join-and-simple-where-clause"></a>Combinación y cláusula Where sencilla  
 El siguiente ejemplo muestra cómo recuperar el campo Name de una cuenta y el campo LastName de un contacto cuando el campo Name de la cuenta contiene “Contoso”, el campo LastName del contacto contiene “Smith” y el contacto es el contacto principal de la cuenta.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_where3 = from c in svcContext.ContactSet
                    join a in svcContext.AccountSet
                    on c.ContactId equals a.PrimaryContactId.Id
                    where a.Name.Contains("Contoso")
                    where c.LastName.Contains("Smith")
                    select new
                    {
                     account_name = a.Name,
                     contact_name = c.LastName
                    };

    foreach (var c in query_where3)
    {
        System.Console.WriteLine("acct: " +
        c.account_name +
        "\t\t\t" +
        "contact: " +
        c.contact_name);
    }
}
```  
  
<a name="UsingtheDistinctOperator"></a>   
## <a name="use-the-distinct-operator"></a>Uso del operador Distinct  
 El siguiente ejemplo muestra cómo recuperar una lista de valores distintos con los apellidos de los contactos. Aunque pueda haber duplicados, cada nombre aparecerá una sola vez.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_distinct = (from c in svcContext.ContactSet
                       select c.LastName).Distinct();
    foreach (var c in query_distinct)
    {
        System.Console.WriteLine(c);
    }
}
```
  
<a name="SimpleInnerJoin"></a>   
## <a name="simple-inner-join"></a>Combinación interna sencilla  
El siguiente ejemplo muestra cómo recuperar información de una cuenta y el contacto que figura como el contacto principal de la cuenta.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join1 = from c in svcContext.ContactSet
                   join a in svcContext.AccountSet
                  on c.ContactId equals a.PrimaryContactId.Id
                   select new
                   {
                    c.FullName,
                    c.Address1_City,
                    a.Name,
                    a.Address1_Name
                   };
    foreach (var c in query_join1)
    {
        System.Console.WriteLine("acct: " +
        c.Name +
        "\t\t\t" +
        "contact: " +
        c.FullName);
    }
}
```  
  
<a name="SelfJoin"></a>   
## <a name="self-join"></a>Autocombinación  
 El siguiente ejemplo muestra cómo recuperar información de las cuentas cuando una cuenta es la cuenta primaria de otra cuenta.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join5 = from a in svcContext.AccountSet
                   join a2 in svcContext.AccountSet
                   on a.ParentAccountId.Id equals a2.AccountId

                   select new
                   {
                    account_name = a.Name,
                    account_city = a.Address1_City
                   };
    foreach (var c in query_join5)
    {
        System.Console.WriteLine(c.account_name + "  " + c.account_city);
    }
}
```
  
<a name="DoubleJoin"></a>   
## <a name="double-and-multiple-joins"></a>Combinaciones dobles y múltiples  
 El siguiente ejemplo muestra cómo recuperar información de cuenta, contacto y cliente potencial cuando el contacto es el contacto principal de la cuenta y el cliente potencial era el cliente potencial original de la cuenta.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join4 = from a in svcContext.AccountSet
                   join c in svcContext.ContactSet
                   on a.PrimaryContactId.Id equals c.ContactId
                   join l in svcContext.LeadSet
                   on a.OriginatingLeadId.Id equals l.LeadId
                   select new
                   {
                    contact_name = c.FullName,
                    account_name = a.Name,
                    lead_name = l.FullName
                   };
    foreach (var c in query_join4)
    {
        System.Console.WriteLine(c.contact_name +
        "  " +
        c.account_name +
        "  " +
        c.lead_name);
    }
}
```  
  
 El siguiente ejemplo muestra cómo recuperar información de cuenta y contacto cuando una cuenta es la cuenta primaria de una cuenta y el contacto es el contacto principal de la cuenta.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join6 = from c in svcContext.ContactSet
                   join a in svcContext.AccountSet
                   on c.ContactId equals a.PrimaryContactId.Id
                   join a2 in svcContext.AccountSet
                   on a.ParentAccountId.Id equals a2.AccountId
                   select new
                   {
                    contact_name = c.FullName,
                    account_name = a.Name
                   };
    foreach (var c in query_join6)
    {
        System.Console.WriteLine(c.contact_name + "  " + c.account_name);
    }
}
```
  
<a name="JoinUsingEntityFields"></a>   
## <a name="join-using-entity-fields"></a>Combinación usando campos de entidad  
 El siguiente ejemplo muestra cómo recuperar información sobre cuentas de una lista.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var list_join = (from a in svcContext.AccountSet
                  join c in svcContext.ContactSet
                  on a.PrimaryContactId.Id equals c.ContactId
                  where a.Name == "Contoso Ltd" &&
                  a.Address1_Name == "Contoso Pharmaceuticals"
                  select a).ToList();
    foreach (var c in list_join)
    {
        System.Console.WriteLine("Account " + list_join[0].Name
        + " and it's primary contact "
        + list_join[0].PrimaryContactId.Id);
    }
}
```  
  
<a name="LeftJoin"></a>   
## <a name="late-binding-left-join"></a>Combinación izquierda enlazada en tiempo de ejecución  
 El siguiente ejemplo muestra una combinación izquierda. Una combinación izquierda está diseñada para devolver elementos principales con y sin elementos secundarios desde dos orígenes. Existe una correlación entre los elementos principales y los elementos secundarios, pero es posible que no existan elementos secundarios  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join8 = from a in svcContext.AccountSet
                   join c in svcContext.ContactSet
                   on a.PrimaryContactId.Id equals c.ContactId
                   into gr
                   from c_joined in gr.DefaultIfEmpty()
                   select new
                   {
                    contact_name = c_joined.FullName,
                    account_name = a.Name
                   };
    foreach (var c in query_join8)
    {
        System.Console.WriteLine(c.contact_name + "  " + c.account_name);
    }
}
``` 
  
<a name="UsingtheEqualsOperator"></a>   
## <a name="use-the-equals-operator"></a>Uso del operador Equals  
 El siguiente ejemplo muestra cómo recuperar una lista de contactos cuyo campo FirstName contiene “Colin”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_equals1 = from c in svcContext.ContactSet
                     where c.FirstName.Equals("Colin")
                     select new
                     {
                      c.FirstName,
                      c.LastName,
                      c.Address1_City
                     };
    foreach (var c in query_equals1)
    {
        System.Console.WriteLine(c.FirstName +
        " " + c.LastName +
        " " + c.Address1_City);
    }
}
``` 
  
 El siguiente ejemplo muestra cómo recuperar una lista de contactos cuyo campo FamilyStatusCode es 3. Esto corresponde a la opción **Estado civil** de **Divorciado/a**.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_equals2 = from c in svcContext.ContactSet
                     where c.FamilyStatusCode.Equals(3)
                     select new
                     {
                      c.FirstName,
                      c.LastName,
                      c.Address1_City
                     };
    foreach (var c in query_equals2)
    {
        System.Console.WriteLine(c.FirstName +
        " " + c.LastName +
        " " + c.Address1_City);
    }
}
``` 
  
<a name="UsingtheNotEqualsOperator"></a>   
## <a name="use-the-not-equals-operator"></a>Uso del operador no es igual a  
 El siguiente ejemplo muestra cómo recuperar una lista de contactos cuyo campo Address1_City no contiene “Redmond”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_ne1 = from c in svcContext.ContactSet
                 where c.Address1_City != "Redmond"
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };
    foreach (var c in query_ne1)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
```  
  
 El siguiente ejemplo muestra cómo recuperar una lista de contactos cuyo campo FirstName no contiene “Colin”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_ne2 = from c in svcContext.ContactSet
                 where !c.FirstName.Equals("Colin")
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };

    foreach (var c in query_ne2)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
```  
  
<a name="BKMK_UsingMethodBasedLINQQueryWithWhereClause"></a>   
## <a name="use-a-method-based-linq-query-with-a-where-clause"></a>Uso de una consulta LINQ basada en métodos con una cláusula Where  
 El siguiente ejemplo muestra cómo recuperar una lista de contactos cuyo campo LastName es igual a “Smith” o contiene “Smi”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var methodResults = svcContext.ContactSet
    .Where(a => a.LastName == "Smith");
    var methodResults2 = svcContext.ContactSet
    .Where(a => a.LastName.StartsWith("Smi"));
    Console.WriteLine();
    Console.WriteLine("Method query using Lambda expression");
    Console.WriteLine("---------------------------------------");
    foreach (var a in methodResults)
    {
        Console.WriteLine("Name: " + a.FirstName + " " + a.LastName);
    }
    Console.WriteLine("---------------------------------------");
    Console.WriteLine("Method query 2 using Lambda expression");
    Console.WriteLine("---------------------------------------");
    foreach (var a in methodResults2)
    {
        Console.WriteLine("Name: " + a.Attributes["firstname"] +
        " " + a.Attributes["lastname"]);
    }
}
``` 
  
<a name="BKMK_UsingGreaterThanOperator"></a>   
## <a name="use-the-greater-than-operator"></a>Uso del operador mayor que  
 El siguiente ejemplo muestra cómo recuperar una lista de contactos cuyo campo Anniversary contiene una fecha posterior al 5 de febrero de 2010.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_gt1 = from c in svcContext.ContactSet
                 where c.Anniversary > new DateTime(2010, 2, 5)
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };

    foreach (var c in query_gt1)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
``` 
  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo CreditLimit es mayor que 20 000.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_gt2 = from c in svcContext.ContactSet
                 where c.CreditLimit.Value > 20000
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };
    foreach (var c in query_gt2)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
``` 
  
<a name="BKMK_UsingGreaterThanOrEqualsAndLessThanOrEqualsOperators"></a>   
## <a name="use-the-greater-than-or-equals-and-less-than-or-equals-operators"></a>Uso de los operadores mayor o igual que y menor o igual que  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo CreditLimit es mayor que 200 y menor que 400.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_gele1 = from c in svcContext.ContactSet
                   where c.CreditLimit.Value >= 200 &&
                   c.CreditLimit.Value <= 400
                   select new
                   {
                    c.FirstName,
                    c.LastName
                   };
 foreach (var c in query_gele1)
 {
  System.Console.WriteLine(c.FirstName + " " + c.LastName);
 }
}
``` 
  
<a name="BKMK_UsingContainsOperator"></a>   
## <a name="use-the-contains-operator"></a>Uso del operador Contains  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo Description contiene “Alpine”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_contains1 = from c in svcContext.ContactSet
                       where c.Description.Contains("Alpine")
                       select new
                       {
                        c.FirstName,
                        c.LastName
                       };
    foreach (var c in query_contains1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```
  
<a name="BKMK_UsingDoesNotContainOperator"></a>   
## <a name="use-the-does-not-contain-operator"></a>Use del operador no contiene  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo Description no contiene “Coho”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_contains2 = from c in svcContext.ContactSet
                       where !c.Description.Contains("Coho")
                       select new
                       {
                        c.FirstName,
                        c.LastName
                       };
    foreach (var c in query_contains2)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  
  
<a name="BKMK_UsingEndsWithOperator"></a>   
## <a name="use-the-startswith-and-endswith-operators"></a>Uso de los operadores StartsWith y EndsWith  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo FirstName comienza por “Bri”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_startswith1 = from c in svcContext.ContactSet
                         where c.FirstName.StartsWith("Bri")
                         select new
                         {
                          c.FirstName,
                          c.LastName
                         };
    foreach (var c in query_startswith1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo LastName termina por “cox”.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_endswith1 = from c in svcContext.ContactSet
                       where c.LastName.EndsWith("cox")
                       select new
                       {
                        c.FirstName,
                        c.LastName
                       };
    foreach (var c in query_endswith1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
<a name="BKMK_UsingAndOrOperators"></a>   
## <a name="use-the-and-and-or-operators"></a>Uso de los operadores And y Or  
 El siguiente ejemplo muestra cómo recuperar los contactos cuyo campo Address1_City contiene "Redmond" o "Bellevue", y cuyo campo CreditLimit es mayor que 200.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_andor1 = from c in svcContext.ContactSet
                    where ((c.Address1_City == "Redmond" ||
                    c.Address1_City == "Bellevue") &&
                    (c.CreditLimit.Value != null &&
                    c.CreditLimit.Value >= 200))
                    select c;

    foreach (var c in query_andor1)
    {
        System.Console.WriteLine(c.LastName + ", " + c.FirstName + " " +
        c.Address1_City + " " + c.CreditLimit.Value);
    }
}
```  

  
<a name="BKMKUsingOrderByOperator"></a>   
## <a name="use-the-orderby-operator"></a>Uso del operador OrderBy  
 El siguiente ejemplo muestra cómo recuperar los contactos ordenados por el contenido del campo CreditLimit en orden descendente.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_orderby1 = from c in svcContext.ContactSet
                      where !c.CreditLimit.Equals(null)
                      orderby c.CreditLimit descending
                      select new
                      {
                       limit = c.CreditLimit,
                       first = c.FirstName,
                       last = c.LastName
                      };
    foreach (var c in query_orderby1)
    {
        System.Console.WriteLine(c.limit.Value + " " +
        c.last + ", " + c.first);
    }
}
```   

  
 El siguiente ejemplo muestra cómo recuperar los contactos ordenados por el contenido del campo LastName en orden descendente y FirstName en orden ascendente.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_orderby2 = from c in svcContext.ContactSet
                      orderby c.LastName descending,
                      c.FirstName ascending
                      select new
                      {
                       first = c.FirstName,
                       last = c.LastName
                      };

    foreach (var c in query_orderby2)
    {
        System.Console.WriteLine(c.last + ", " + c.first);
    }
}
```  

  
<a name="BKMK_UsingFirstAndSingleOperators"></a>   
## <a name="use-the-first-and-single-operators"></a>Uso de los operadores First y Single  
 El siguiente ejemplo muestra cómo recuperar solo el primer registro de contacto devuelto y cómo recuperar un solo registro de contacto que cumpla con el criterio.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    Contact firstcontact = svcContext.ContactSet.First();

    Contact singlecontact = svcContext.ContactSet.Single(c => c.ContactId == _contactId1);
    System.Console.WriteLine(firstcontact.LastName + ", " +
    firstcontact.FirstName + " is the first contact");
    System.Console.WriteLine("==========================");
    System.Console.WriteLine(singlecontact.LastName + ", " +
    singlecontact.FirstName + " is the single contact");
}
```  

  
<a name="BKMK_RetrievingFormattedValues"></a>   
## <a name="retrieving-formatted-values"></a>Recuperación de valores con formato  
 El siguiente ejemplo muestra cómo recuperar la etiqueta para una opción de conjunto de opciones, en este caso el valor del estado del registro actual.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var list_retrieve1 = from c in svcContext.ContactSet
                      where c.ContactId == _contactId1
                      select new { StatusReason = c.FormattedValues["statuscode"] };
    foreach (var c in list_retrieve1)
    {
        System.Console.WriteLine("Status: " + c.StatusReason);
    }
}
```  

  
<a name="BKMK_UsingTheSkipAndTakeOperatorsWithoutPaging"></a>   
## <a name="use-the-skip-and-take-operators-without-paging"></a>Uso de los operadores Skip y Take sin paginación 

 El siguiente ejemplo muestra cómo recuperar solo dos registros después de omitir dos registros cuyo campo LastName no es “Parker” mediante los operadores [Skip](https://msdn.microsoft.com/library/bb358985.aspx) y [Take](https://msdn.microsoft.com/library/bb503062.aspx).  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{

    var query_skip = (from c in svcContext.ContactSet
                   where c.LastName != "Parker"
                   orderby c.FirstName
                   select new
                       {
                        last = c.LastName,
                        first = c.FirstName
                       }).Skip(2).Take(2);
    foreach (var c in query_skip)
    {
        System.Console.WriteLine(c.first + " " + c.last);
    }
}
```  

  
<a name="BKMK_UsingTheFirstOrDefaultAndSingleOrDefaultOperators"></a>   
## <a name="use-the-firstordefault-and-singleordefault-operators"></a>Uso de los operadores FirstOrDefault y SingleOrDefault  
 El operador [FirstOrDefault](https://msdn.microsoft.com/library/system.linq.enumerable.firstordefault.aspx) devuelve el primer elemento de una secuencia, o un valor predeterminado si no se encuentra ningún elemento. El operador [SingleOrDefault](https://msdn.microsoft.com/library/system.linq.enumerable.singleordefault.aspx) devuelve un único elemento específico de una secuencia, o un valor predeterminado no se encuentra dicho elemento. El siguiente ejemplo muestra cómo usar estos operadores.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{

    Contact firstorcontact = svcContext.ContactSet.FirstOrDefault();

    Contact singleorcontact = svcContext.ContactSet
        .SingleOrDefault(c => c.ContactId == _contactId1);


    System.Console.WriteLine(firstorcontact.FullName +
        " is the first contact");
    System.Console.WriteLine("==========================");
    System.Console.WriteLine(singleorcontact.FullName +
        " is the single contact");
}
```  

  
<a name="BKMK_UsingASelfJoinWithConditionOnLinkedEntity"></a>   
## <a name="use-a-self-join-with-a-condition-on-the-linked-entity"></a>Uso de una autocombinación con una condición en la entidad vinculada  
 El siguiente ejemplo muestra cómo recuperar los nombres de dos cuentas cuando una de ellas es la cuenta primaria de la otra.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_joincond = from a1 in svcContext.AccountSet
                      join a2 in svcContext.AccountSet
                      on a1.ParentAccountId.Id equals a2.AccountId
                      where a2.AccountId == _accountId1
                      select new { Account = a1, Parent = a2 };
    foreach (var a in query_joincond)
    {
        System.Console.WriteLine(a.Account.Name + " " + a.Parent.Name);
    }
}
```  

  
<a name="BKMK_UsingTransformationInTheWhereClause"></a>   
## <a name="use-a-transformation-in-the-where-clause"></a>Uso de una transformación en la cláusula Where  
 El siguiente ejemplo muestra cómo recuperar un contacto específico cuyo aniversario es posterior al 1 de enero de 2010.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_wheretrans = from c in svcContext.ContactSet
                        where c.ContactId == _contactId1 &&
                        c.Anniversary > DateTime.Parse("1/1/2010")
                        select new
                        {
                         c.FirstName,
                         c.LastName
                        };
    foreach (var c in query_wheretrans)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
<a name="BKMK_UsingAPagingSort"></a>   
## <a name="use-a-paging-sort"></a>Uso de una ordenación con paginación  
 El siguiente ejemplo muestra una ordenación de varias columnas con una condición adicional.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_pagingsort1 = (from c in svcContext.ContactSet
                          where c.LastName != "Parker"
                          orderby c.LastName ascending,
                          c.FirstName descending
                          select new { c.FirstName, c.LastName })
                          .Skip(2).Take(2);
    foreach (var c in query_pagingsort1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
 El siguiente ejemplo muestra una ordenación con paginación donde la columna que se ordena es distinta de la columna que se recupera.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_pagingsort2 = (from c in svcContext.ContactSet
                          where c.LastName != "Parker"
                          orderby c.FirstName descending
                          select new { c.FirstName }).Skip(2).Take(2);
    foreach (var c in query_pagingsort2)
    {
        System.Console.WriteLine(c.FirstName);
    }
}
```  

  
 El siguiente ejemplo muestra cómo recuperar solo los 10 primeros registros.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_pagingsort3 = (from c in svcContext.ContactSet
                          where c.LastName.StartsWith("W")
                          orderby c.MiddleName ascending,
                          c.FirstName descending
                          select new
                          {
                           c.FirstName,
                           c.MiddleName,
                           c.LastName
                          }).Take(10);
    foreach (var c in query_pagingsort3)
    {
        System.Console.WriteLine(c.FirstName + " " +
            c.MiddleName + " " + c.LastName);
    }
}
```  

  
<a name="BKMK_RetrievingRelatedEntityColumns"></a>   
## <a name="retrieve-related-entity-columns-for-1-to-n-relationships"></a>Recuperación de las columnas de entidad relacionada para las relaciones de 1 a N  
 El siguiente ejemplo muestra cómo recuperar columnas de los registros de cuenta y de contacto relacionados.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
     var query_retrieve1 = from c in svcContext.ContactSet
                       join a in svcContext.AccountSet
                       on c.ContactId equals a.PrimaryContactId.Id
                       where c.ContactId != _contactId1
                       select new { Contact = c, Account = a };
     foreach (var c in query_retrieve1)
    {
          System.Console.WriteLine("Acct: " + c.Account.Name +
           "\t\t" + "Contact: " + c.Contact.FullName);
     }
}
```  
  
<a name="BKMK_UsingValueToRetrieveTheValueOfAnAttribute"></a>   
## <a name="use-value-to-retrieve-the-value-of-an-attribute"></a>Uso de .value para recuperar el valor de un atributo  
 El siguiente ejemplo muestra el uso de .Value para tener acceso al valor de un atributo.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{

     var query_value = from c in svcContext.ContactSet
                   where c.ContactId != _contactId2
                   select new
                   {
                    ContactId = c.ContactId != null ?
                     c.ContactId.Value : Guid.Empty,
                    NumberOfChildren = c.NumberOfChildren != null ?
                     c.NumberOfChildren.Value : default(int),
                    CreditOnHold = c.CreditOnHold != null ?
                     c.CreditOnHold.Value : default(bool),
                    Anniversary = c.Anniversary != null ?
                     c.Anniversary.Value : default(DateTime)
                   };

     foreach (var c in query_value)
     {
      System.Console.WriteLine(c.ContactId + " " + c.NumberOfChildren + 
           " " + c.CreditOnHold + " " + c.Anniversary);
     }
}
```  
  
<a name="BKMK_MultipleProjectionsNewDataTypeCastingToDifferentTypes"></a>   
## <a name="multiple-projections-new-data-type-casting-to-different-types"></a>Proyecciones múltiples y nueva conversión de tipo de datos en tipos distintos  
 El siguiente ejemplo muestra proyecciones múltiples y cómo convertir valores en un tipo distinto.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
     var query_projections = from c in svcContext.ContactSet
                         where c.ContactId == _contactId1
                         && c.NumberOfChildren != null && 
                         c.Anniversary.Value != null
                         select new
                         {
                          Contact = new Contact { 
                           LastName = c.LastName, 
                           NumberOfChildren = c.NumberOfChildren 
                          },
                          NumberOfChildren = (double)c.NumberOfChildren,
                          Anniversary = c.Anniversary.Value.AddYears(1),
                         };
     foreach (var c in query_projections)
     {
          System.Console.WriteLine(c.Contact.LastName + " " + 
               c.NumberOfChildren + " " + c.Anniversary);
     }
}
```  
  
<a name="BKMK_UsingTheGetAttributeValueMethod"></a>   
## <a name="use-the-getattributevalue-method"></a>Uso del método GetAttributeValue  
 El siguiente ejemplo muestra cómo usar el método <xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)>.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_getattrib = from c in svcContext.ContactSet
                       where c.GetAttributeValue<Guid>("contactid") != _contactId1
                       select new
                       {
                        ContactId = c.GetAttributeValue<Guid?>("contactid"),
                        NumberOfChildren = c.GetAttributeValue<int?>("numberofchildren"),
                        CreditOnHold = c.GetAttributeValue<bool?>("creditonhold"),
                        Anniversary = c.GetAttributeValue<DateTime?>("anniversary"),
                       };

    foreach (var c in query_getattrib)
    {
        System.Console.WriteLine(c.ContactId + " " + c.NumberOfChildren + 
            " " + c.CreditOnHold + " " + c.Anniversary);
    }
}
```  
  
<a name="mathoperators"></a>   
## <a name="use-math-methods"></a>Uso de los métodos matemáticos  
 El siguiente ejemplo muestra cómo usar distintos métodos de la clase [Math](https://msdn.microsoft.com/library/system.math.aspx).  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_math = from c in svcContext.ContactSet
                  where c.ContactId != _contactId2
                  && c.Address1_Latitude != null && 
                  c.Address1_Longitude != null
                  select new
                  {
                   Round = Math.Round(c.Address1_Latitude.Value),
                   Floor = Math.Floor(c.Address1_Latitude.Value),
                   Ceiling = Math.Ceiling(c.Address1_Latitude.Value),
                   Abs = Math.Abs(c.Address1_Latitude.Value),
                  };
    foreach (var c in query_math)
    {
        System.Console.WriteLine(c.Round + " " + c.Floor + 
            " " + c.Ceiling + " " + c.Abs);
    }
}
```  
  
<a name="BKMK_UsingMultipleSelectAndWhereClauses"></a>   
## <a name="use-multiple-select-and-where-clauses"></a>Uso de varias cláusulas Select y Where  
 El siguiente ejemplo muestra varias cláusulas Select y Where que usan una sintaxis de consulta basada en métodos.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_multiselect = svcContext.IncidentSet
                        .Where(i => i.IncidentId != _incidentId1)
                        .Select(i => i.incident_customer_accounts)
                        .Where(a => a.AccountId != _accountId2)
                        .Select(a => a.account_primary_contact)
                        .OrderBy(c => c.FirstName)
                        .Select(c => c.ContactId);
    foreach (var c in query_multiselect)
    {
        System.Console.WriteLine(c.GetValueOrDefault());
    }
}
```  
  
<a name="BKMK_UsingSelectMany"></a>   
## <a name="use-selectmany"></a>Uso de SelectMany  
 El siguiente ejemplo muestra cómo usar el [método SelectMany](https://msdn.microsoft.com/library/system.linq.enumerable.selectmany.aspx).  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_selectmany = svcContext.ContactSet
                        .Where(c => c.ContactId != _contactId2)
                        .SelectMany(c => c.account_primary_contact)
                        .OrderBy(a => a.Name);
    foreach (var c in query_selectmany)
    {
        System.Console.WriteLine(c.AccountId + " " + c.Name);    
    }
}
```
  
<a name="BKMK_UsingStringOperations"></a>   
## <a name="use-string-operations"></a>Uso de operaciones de cadena  
 El siguiente ejemplo muestra cómo usar distintos métodos de cadena.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_string = from c in svcContext.ContactSet
                    where c.ContactId == _contactId2
                    select new
                    {
                     IndexOf = c.FirstName.IndexOf("contact"),
                     Insert = c.FirstName.Insert(1, "Insert"),
                     Remove = c.FirstName.Remove(1, 1),
                     Substring = c.FirstName.Substring(1, 1),
                     ToUpper = c.FirstName.ToUpper(),
                     ToLower = c.FirstName.ToLower(),
                     TrimStart = c.FirstName.TrimStart(),
                     TrimEnd = c.FirstName.TrimEnd(),
                    };

    foreach (var c in query_string)
    {
        System.Console.WriteLine(c.IndexOf + "\n" + c.Insert + "\n" + 
            c.Remove + "\n" + c.Substring + "\n"
            + c.ToUpper + "\n" + c.ToLower + 
            "\n" + c.TrimStart + " " + c.TrimEnd);
    }
}
```
  
<a name="BKMK_UsingTwoWhereClauses"></a>   
## <a name="use-two-where-clauses"></a>Uso de dos cláusulas Where  
 El siguiente ejemplo muestra cómo usar dos cláusulas Where.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_twowhere = from a in svcContext.AccountSet
                      join c in svcContext.ContactSet 
                      on a.PrimaryContactId.Id equals c.ContactId
                      where c.LastName == "Smith" && c.CreditOnHold != null
                      where a.Name == "Contoso Ltd"
                      orderby a.Name
                      select a;
    foreach (var c in query_twowhere)
    {
         System.Console.WriteLine(c.AccountId + " " + c.Name);
    }
}
``` 
  
<a name="BKMK_UseLoadProperty"></a>   
## <a name="use-loadproperty-to-retrieve-related-records"></a>Uso de LoadProperty para recuperar registros relacionados  
 El siguiente ejemplo muestra cómo usar [Relaciones]<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.LoadProperty(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship)> para tener acceso a registros relacionados.  
  
```csharp
Contact benAndrews = svcContext.ContactSet.Where(c => c.FullName == "Ben Andrews").FirstOrDefault();
if (benAndrews != null)
{
     //benAndrews.Contact_Tasks is null until LoadProperty is used.
     svcContext.LoadProperty(benAndrews, "Contact_Tasks");
     Task benAndrewsFirstTask = benAndrews.Contact_Tasks.FirstOrDefault();
     if (benAndrewsFirstTask != null)
     {
          Console.WriteLine("Ben Andrews first task with Subject: '{0}' retrieved.", benAndrewsFirstTask.Subject);
     }
}
```
  
