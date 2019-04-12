---
title: Usar LINQ para generar una consulta (Common Data Service) | Microsoft Docs
description: Describe cómo utilizar el proveedor de consulta Consulta integrada del lenguaje .NET (LINQ) en Dynamics 365 para crear una consulta
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
# <a name="use-linq-to-construct-a-query"></a>Usar LINQ para crear una consulta

El proveedor de consulta Consulta integrada del lenguaje .NET (LINQ) en Common Data Service usa sintaxis LINQ estándar. El primer paso en la creación de una consulta de LINQ es identificar los tipos de entidad relevantes y las relaciones entre ellos. A continuación puede especificar el origen de datos y los demás parámetros de consulta.  

 La cláusula `from` se usa para devolver una entidad "raíz" única. El proveedor de consulta solo puede devolver entidades de un único tipo de entidad. Las cláusulas `orderby` y `select` deben hacer referencia a esta entidad raíz. Puede usar cláusulas `join` para agregar entidades a una relación con la entidad "raíz".  

<a name="bkmk_operators"></a>   

## <a name="linq-operators"></a>Operadores LINQ  
 Todas expresiones de consulta LINQ tienen un formato similar. La siguiente tabla muestra las cláusulas más comunes en una expresión de consulta LINQ al usar el proveedor de consulta LINQ de Common Data Service.  

### <a name="from"></a>from  
 Cuando se usa el contexto de servicio generado y el enlace en tiempo de compilación, use el conjunto de entidades `IQueryable`, como `AccountSet`, en el contexto generado.  

 Cuando se use el contexto generado, el método `CreateQuery` del objeto del contexto del servicio de la organización le da acceso a las entidades de Common Data Service.  

 Ejemplo:  

 Mediante el contexto de servicio generado:  

```csharp  
var query1 = from c in context.ContactSet  
select c;  
```  

 Usando el método `CreateQuery`:  

```csharp  
var query1 = from c in context.CreateQuery<Contact>()  
select c;  
```  

### <a name="join"></a>join  
 La cláusula `join` representa una combinación interna. La cláusula se usa para trabajar con dos o varias entidades que se pueden combinar con un valor de atributo común.  

 Ejemplo:  

```csharp  
from c in context.ContactSet  
join a in context.AccountSet on c.ContactId equals a.PrimaryContactId.Id  
```  

### <a name="where"></a>donde  
 La cláusula `where` aplica un filtro a los resultados, ofreciendo a menudo una expresión booleana. El filtro especifica qué elementos se excluirán de la secuencia de origen. Cada cláusula `where` solo puede contener condiciones frente a un tipo de entidad único. Una condición compuesta que abarca varias entidades no es válida. En su lugar, cada entidad debe filtrarse en cláusulas `where` independientes.  

 Ejemplo:  

```csharp  
from a in context.AccountSet  
where (a.Name.StartsWith("Contoso") && a.Address1_StateOrProvince == "WA")  
```  

### <a name="orderby"></a>orderby  
 El operador `orderby` coloca los atributos de consulta devueltos en un orden especificado.  

 Ejemplo:  

```csharp  
var query1 = from c in context.CreateQuery<Contact>()     
    orderby c.FullName ascending     
    select c;  
foreach ( var q in query1)     
{  
    Console.WriteLine(q.FirstName + " " + q.LastName);     
}  
```  

### <a name="select"></a>Seleccionar  
 La cláusula `select` define el formulario de los datos devueltos. La cláusula crea un conjunto de columnas basándose en los resultados de la expresión de consulta. También puede definir una instancia de un nuevo objeto con el que trabajar. El objeto recién creado mediante la cláusula `select` no se crea en el servidor, sino que es una instancia local.  

 Ejemplo:  

```csharp  
select new Contact     
{  
    ContactId = c.ContactId,  
    FirstName = c.FirstName,  
    LastName = c.LastName,  
    Address1_Telephone1 = c.Address1_Telephone1     
};  
```  

<a name="limitations"></a>   

## <a name="linq-limitations"></a>Limitaciones de LINQ  

 El proveedor de la consulta LINQ admite un subconjunto de los operadores LINQ. No se admiten todas las condiciones que se pueden expresar en LINQ. La siguiente tabla muestra algunas de las limitaciones de los operadores LINQ básicos.  


|   Operador LINQ   |                                                                                                                                              Limitaciones                                                                                                                                              |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      `join`       |                                                                                                                Representa una combinación interna o externa. Solo se admiten las uniones externas izquierdas.                                                                                                                |
|      `from`       |                                                                                                                                 Admite una cláusula `from` por consulta.                                                                                                                                 |
|      `where`      | El lado izquierdo de la cláusula debe ser un nombre de atributo y el lado derecho de la cláusula debe ser un valor. No puede establecer el lado izquierdo de una constante. Ambos lados de la cláusula no pueden ser constantes.<br /><br /> Admite las funciones `String` `Contains`, `StartsWith`, `EndsWith` y `Equals`. |
|     `groupBy`     |                               Incompatible. FetchXML admite las opciones de agrupación que no están disponibles con el proveedor de consultas LINQ. Más información: [Uso de agregación FetchXML](/dynamics365/customer-engagement/developer/use-fetchxml-aggregation)                               |
|     `orderBy`     |                                                                                                                  Admite la ordenación por atributos de entidad, como `Contact.FullName`.                                                                                                                  |
|     `select`      |                                                                                                                       Admite inicializadores, constructores y tipos anónimos.                                                                                                                       |
|      `last`       |                                                                                                                                 El operador `last` no es compatible.                                                                                                                                 |
| `skip` y `take` |                                                                                       Admite `skip` y `take` mediante la paginación del lado servidor. El valor `skip` debe ser superior o igual al valor `take`.                                                                                        |
|    `aggregate`    |                             Incompatible. FetchXML admite las opciones de agregación que no están disponibles con el proveedor de consultas LINQ. Más información: [Uso de agregación FetchXML](/dynamics365/customer-engagement/developer/use-fetchxml-aggregation)                              |

<a name="filter"></a>   

## <a name="filter-multiple-entities"></a>Filtrar varias entidades  

 Puede crear consultas integradas del lenguaje .NET (LINQ) complejas en Common Data Service. Se usan varias cláusulas múltiples de `Join` con cláusulas de filtro para crear un resultado que se filtra por atributos de varias entidades.  

 El siguiente ejemplo muestra cómo crear una consulta LINQ que funciona con dos entidades y que filtra el resultado según los valores de cada una de las entidades.  

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
### <a name="see-also"></a>Vea también  
 [Ejemplo: crear una consulta LINQ](/dynamics365/customer-engagement/developer/org-service/sample-create-linq-query.md)   
 [Ejemplo: ejemplos de consulta LINQ](/dynamics365/customer-engagement/developer/org-service/sample-complex-linq-queries.md)   
 [Crear consultas con LINQ (consulta integrada del lenguaje .NET)](/dynamics365/customer-engagement/developer/org-service/build-queries-with-linq-net-language-integrated-query.md)   
 [Usar clase de entidad de enlace en tiempo de ejecución con una consulta LINQ](/dynamics365/customer-engagement/developer/org-service/use-late-bound-entity-class-linq-query.md)   
 [Blog: Controlador LINQPad 4 para API REST/Web de Dynamics CRM está disponible en CodePlex](http://blogs.msdn.com/b/crminthefield/archive/2015/06/11/linqpad-4-driver-for-dynamics-crm-rest-webapi-are-available-on-codeplex.aspx)