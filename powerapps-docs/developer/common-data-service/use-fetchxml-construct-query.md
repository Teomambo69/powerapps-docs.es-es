---
title: Usar FetchXML para consultar datos (Common Data Service para aplicaciones) | Microsoft Docs
description: FetchXML es un lenguaje de consulta propietario que se usa en Common Data Service (CDS) para aplicaciones. Se basa en un esquema que describe las funciones del idioma.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-fetchxml-to-construct-a-query"></a>Usar FetchXML para crear una consulta

FetchXML es un lenguaje de consulta propietario que se usa en Common Data Service (CDS) para aplicaciones. Se basa en un esquema que describe las funciones del idioma. El idioma FetchXML admite funciones de consulta similares a las expresiones de consulta. Además, se usa como formulario serializado de consulta, usado para guardar una consulta como una vista guardada propiedad del usuario en la [entidad UserQuery](reference/entities/savedquery.md) y como una vista guardada propiedad de la organización en la [Entidad SavedQuery](reference/entities/userquery.md).  
  
Una consulta FetchXML se puede ejecutar mediante la **API de la web** o el **servicio de la organización**.

## <a name="create-the-fetchxml-query-string"></a>Crear la cadena de consulta FetchXML
  
Para ejecutar una consulta FetchXML, primero debe crear la cadena de consulta XML. Después de crear la cadena de consulta, use<xref:Microsoft.Xrm.Sdk.IOrganizationService> <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> método para ejecutar la cadena de consulta. Los privilegios del usuario que inició la sesión afectan el conjunto de registros devueltos. Solo se devolverán los registros a los que tiene acceso de lectura el usuario que inició sesión  
  
 La cadena de consulta de FetchXML debe adaptarlas a la definición del esquema para el lenguaje FetchXML. Para obtener más información, consulte [Esquema Fetch XML](fetchxml-schema.md).  
  
 Puede guardar una consulta al crear un registro de `SavedQuery`. Defina `visible` en el nodo de `link-entity` en `false` para ocultar la entidad vinculada en la interfaz de usuario **Búsqueda avanzada**. Aún así participará en la ejecución de la consulta y devolverá los resultados apropiados.  
  
> [!WARNING]
>  No se recuperan todos los atributos en una consulta debido al efecto negativo en el rendimiento. Este valor es "true" si la consulta se usa como parámetro de una solicitud de actualización. En una actualización, si están incluidos todos los atributos, se definen todos los valores de campo, incluso si no se cambian. Con frecuencia, esto activa las actualizaciones en cascada para los registros secundarios.  
  

### <a name="example-fetchxml-query-strings"></a>Cadenas de consulta FetchXML de ejemplo

En el siguiente ejemplo, la instrucción **FetchXML** recupera todas las cuentas:  
  
```xml  
  
<fetch mapping='logical'>   
   <entity name='account'>  
      <attribute name='accountid'/>   
      <attribute name='name'/>   
</entity>  
</fetch>  
  
```  
  
 En el siguiente ejemplo, la instrucción **FetchXML** recupera todas las cuentas donde el apellido del usuario que es propietario no es igual a Cannon:  
  
```xml  
  
<fetch mapping='logical'>  
   <entity name='account'>   
      <attribute name='accountid'/>   
      <attribute name='name'/>   
      <link-entity name='systemuser' to='owninguser'>   
         <filter type='and'>   
            <condition attribute='lastname' operator='ne' value='Cannon' />   
          </filter>   
      </link-entity>   
   </entity>   
</fetch>  
  
```  
  
 En el siguiente ejemplo, la instrucción **FetchXML** utiliza Count para definir el número máximo de registros de devolución de la consulta. En este caso las primeras 3 cuentas se devuelven desde la consulta,  
  
```xml  
<fetch mapping='logical' count='3'>  
  <entity name='account'>  
   <attribute name='name' alias='name'/>  
  </entity></fetch>  
```  
  
Este ejemplo muestra una combinación interna entre EntityMap y AttributeMap donde EntityMapID coincide.  
  
```xml  
<fetch version='1.0' mapping='logical' distinct='false'>  
   <entity name='entitymap'>  
      <attribute name='sourceentityname'/>  
      <attribute name='targetentityname'/>  
      <link-entity name='attributemap' alias='attributemap' to='entitymapid' from='entitymapid' link-type='inner'>  
         <attribute name='sourceattributename'/>  
         <attribute name='targetattributename'/>  
      </link-entity>  
   </entity>  
 </fetch>  
```  
  
## <a name="execute-the-fetchxml-query"></a>Ejecutar la consulta FetchXML

Puede ejecutar una consulta FetchXML mediante la **API web** o el **servicio de la organización**.

### <a name="using-web-api"></a>Uso de la API web
Puede pasar una cadena FetchXml con código URL al entityset correspondiente mediante el parámetro de cadena de la consulta `fetchXml`. Más información: [Usar FetchXML personalizado](webapi/retrieve-and-execute-predefined-queries.md#use-custom-fetchxml).

### <a name="using-organization-service"></a>Uso del servicio de organización

Use el <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> método pasando un <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> donde la <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query> propiedad contiene la consulta FetchXml.

El siguiente código muestra cómo ejecutar una consulta **FetchXML** con el servicio de la organización:  
  
```csharp  
  
// Retrieve all accounts owned by the user with read access rights to the accounts and   
// where the last name of the user is not Cannon.   
string fetch2 = @"  
   <fetch mapping='logical'>  
     <entity name='account'>   
        <attribute name='accountid'/>   
        <attribute name='name'/>   
        <link-entity name='systemuser' to='owninguser'>   
           <filter type='and'>   
              <condition attribute='lastname' operator='ne' value='Cannon' />   
           </filter>   
        </link-entity>   
     </entity>   
   </fetch> ";   
  
EntityCollection result = _serviceProxy.RetrieveMultiple(new FetchExpression(fetch2));
foreach (var c in result.Entities)
{
   System.Console.WriteLine(c.Attributes["name"]);
}  
```  
> [!NOTE]
> Puede convertir una consulta de FetchXML en una expresión de consulta con el mensaje de <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>. 

  
## <a name="fetchxml-query-results"></a>Resultados de la consulta FetchXML  
 Cuando se ejecuta una consulta de FetchXML usando el método <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.RetrieveMultiple(Microsoft.Xrm.Sdk.Query.QueryBase)> se autentica el usuario. método de autenticación del usuario. Método, el valor devuelto es un <xref:Microsoft.Xrm.Sdk.EntityCollection> que contiene los resultados de la consulta. A continuación puede iterar a través de la colección de entidades. El ejemplo anterior usa el bucle de `foreach` para iterar a través de la recopilación de resultados de la consulta de FetchXML.  
  
