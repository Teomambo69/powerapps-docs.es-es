---
title: Ejemplos de operaciones básicas de la API web (Common Data Service)| Microsoft Docs
description: Este grupo de ejemplos demuestra cómo realizar operaciones CRUD (crear, recuperar, actualizar y eliminar) mediante la API web. Estos están implementados mediante JavaScript del lado cliente y C#
ms.custom: ''
ms.date: 03/22/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: f006f88c-74cb-4fde-90e5-e1faf2051673
caps.latest.revision: 25
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 073ea8853c8a897e7df40b4560916fc66f709968
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154968"
---
# <a name="web-api-basic-operations-sample"></a>Ejemplo de operaciones básicas de la API web

Este grupo de ejemplos demuestra cómo realizar operaciones básicas CRUD (crear, recuperar, actualizar y eliminar) y asociativas mediante la API web de Common Data Service.  
  
-   [Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)  
  
 En este tema se describe un conjunto común de operaciones implementadas por cada ejemplo en este grupo. En este tema se describen las solicitudes y las respuestas HTTP y el texto generado que cada ejemplo en este grupo realizará sin detalles específicos de idioma. Consulte las descripciones específicas del idioma y los ejemplos individuales para obtener más información acerca de cómo se realizan estas operaciones.  
  
<a name="bkmk_demonstrates"></a>  
 
## <a name="demonstrates"></a>Demostraciones  

Este ejemplo se divide en las siguientes secciones, que contienen operaciones de datos de consulta de la API web de Common Data Service que se describen minuciosamente en los temas conceptuales asociados especificados.  
  
|Sección de código|Temas conceptuales asociados|  
|------------------|----------------------------------|  
|[Sección 1: Operaciones básicas crear y actualizar](#bkmk_section1)|[Crear básico](create-entity-web-api.md#bkmk_basicCreate) <br /> [Crear con datos devueltos](create-entity-web-api.md#bkmk_createWithDataReturned) <br /> [Actualización básica](update-delete-entities-using-web-api.md#bkmk_update) <br /> [Actualizar con datos devueltos](update-delete-entities-using-web-api.md#bkmk_updateWithDataReturned)|  
|[Sección 2: Crear con asociación](#bkmk_section2)|[Asociar entidades en la creación](associate-disassociate-entities-using-web-api.md#bkmk_Associateentitiesoncreate)|  
|[Sección 3: Crear entidades relacionadas (inserción en profundidad)](#bkmk_section3)|[Crear entidades relacionadas en una operación](create-entity-web-api.md#bkmk_CreateRelated)|  
|[Sección 4: Asocie y desasocie entidades existentes](#bkmk_section4)|[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)|  
|[Sección 5: Eliminar entidades (limpieza de ejemplo)](#bkmk_section5)|[Eliminación básica](update-delete-entities-using-web-api.md#bkmk_delete)|  
  
> [!NOTE]
>  Para razones de brevedad, se han omitido los encabezados HTTP menos pertinentes. Las direcciones URL de los registros variarán con la dirección de la organización base y el identificador del registro asignado por el servidor de Common Data Service.  
  
<a name="bkmk_section1"></a>
   
## <a name="section-1-basic-create-and-update-operations"></a>Sección 1: Operaciones básicas crear y actualizar 
 
Esta sección crea un solo contacto y después realiza una serie de actualizaciones sobre esa instancia. Tenga en cuenta que el encabezado de respuesta [OData-EntityId](https://docs.oasis-open.org/odata/odata/v4.0/os/part1-protocol/odata-v4.0-os-part1-protocol.html#_Toc372793637) contiene la dirección URL de este registro recién creado (instancia de entidad), que incluye entre paréntesis el identificador único de este registro.  
  
1.  Crear un nuevo contacto, llamado Peter Cambel.  
  
 **Solicitud** 
  
```http
POST https://[Organization URI]/api/data/v9.0/contacts HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "firstname": "Peter",  
  "lastname": "Cambel"  
}  
```  
  
**Respuesta**  
  
```http  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)  
```  
  
**Salida de la consola**  
  
```  
Contact 'Peter Cambel' created.  
```  
  
Las propiedades disponibles para cada tipo se definen en el documento de metadatos y también se documentan para cada tipo en la sección <xref:Microsoft.Dynamics.CRM.EntityTypeIndex>. Para obtener más información general, vea [tipos de API web y operaciones](web-api-types-operations.md).  
  
2.  Actualice el contacto con valores de ingresos anuales ($80,000) y el nombre del puesto (Desarrollador junior).  
  
 **Solicitud** 
  
```http  
PATCH https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "annualincome": 80000,  
  "jobtitle": "Junior Developer"  
}  
```  
  
**Respuesta**  
  
```http  
HTTP/1.1 204 No Content  
```  
  
**Salida de la consola**  
  
```  
Contact 'Peter Cambel' updated with job title and annual income.  
```  
  
3.  Recupere el contacto con su conjunto de propiedades inicializadas de forma explícita.  El `fullname` es una propiedad de sólo lectura que se calcula desde las propiedades `firstname` y `lastname`, que se inicializaron de forma explícita cuando se creó la instancia. En cambio, la propiedad `description` no se inicializó explícitamente, por lo que mantiene su valor predeterminado, una cadena `null`.  
  
     Tenga en cuenta que la respuesta, además de los valores solicitados y los encabezados típicos, también devuelven automáticamente los siguientes tipos de información adicional:  
  
    -   El identificador principal para el tipo de entidad actual, aquí `contactid`.  
  
    -   Un valor *ETag*, denotado por la clave `@odata.etag`, que identifica la versión específica del recurso solicitado. Para obtener más información, consulte [realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md).  
  
    -   El contexto de metadatos, denotado por la clave  `@odata.context`, proporciona una forma de comparar resultados de la consulta para determinar si proceden de la misma consulta.  
  
    -   Un `_transactioncurrencyid_value` que indica la divisa local de la transacción monetaria.  
  
 **Solicitud** 
  
```http  
GET https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)?$select=fullname,annualincome,jobtitle,description HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Respuesta**  
  
```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,annualincome,jobtitle,description)/$entity",  
   "@odata.etag":"W/\"628883\"",  
   "fullname":"Peter Cambel",  
   "annualincome":80000.0000,  
   "jobtitle":"Junior Developer",  
   "description":null,  
   "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03",  
   "contactid":"60f77a42-5f0e-e611-80e0-00155da84c03"  
}  
```  
  
**Salida de la consola**  
  
```http    
Contact 'Peter Cambel' retrieved:  
       Income: 80000  
       Job title: Junior Developer  
       Description: .    
```  
  
> [!IMPORTANT]
>  Debe usar siempre la selección y filtrado en operaciones de recuperación para optimizar el rendimiento. Para obtener más información, consulte [Consulta de datos mediante la API web](query-data-web-api.md).  
  
4.  Actualice la instancia de la entidad de contacto proporcionando nuevos valores a estas mismas propiedades.  
  
**Solicitud** 
  
```http
PATCH https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
   "jobtitle": "Senior Developer",  
   "annualincome": 95000,  
   "description": "Assignment to-be-determined"  
}    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content    
```  
  
**Salida de la consola**  
  
```http    
Contact 'Peter Cambel' updated:  
       Job title: Senior Developer  
       Annual income: 95000  
       Description: Assignment to-be-determined    
```  
  
> [!IMPORTANT]
>  Envíe solo propiedades cambiadas en solicitudes de actualización. Para obtener más información, consulte [Actualización básica](update-delete-entities-using-web-api.md#bkmk_update).  
  
5.  Establezca explícitamente una sola propiedad, el número de teléfono principal. Tenga en cuenta que esto es una solicitud `PUT` y que la clave JSON llamada `value` se utiliza al realizar operaciones en propiedades individuales.  
  
**Solicitud** 
  
```http  
PUT https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)/telephone1 HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "value": "555-0105"  
}  
```  
  
**Respuesta**  
  
```http  
HTTP/1.1 204 No Content  
```  
  
**Salida de la consola**  
  
```  
Contact 'Peter Cambel' phone number updated.  
```  
  
6.  Recupere esa misma propiedad individual, el número de teléfono principal. Una vez más, note el uso de la clave llamada `value`.  
  
**Solicitud** 
  
```http  
GET https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)/telephone1 HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(60f77a42-5f0e-e611-80e0-00155da84c03)/telephone1",  
   "value":"555-0105"  
}    
```  
  
**Salida de la consola**  
  
```  
Contact's telephone# is: 555-0105.  
```  
  
7.  Crea un contacto similar pero también devuelve la información de la instancia en la misma operación. Esta última capacidad está habilitada por el encabezado `Prefer: return=representation`.  
  
**Solicitud** 
  
```http    
POST https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,annualincome,jobtitle,contactid HTTP/1.1  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: return=representation  
{  
  "firstname": "Peter_Alt",  
  "lastname": "Cambel",  
  "jobtitle": "Junior Developer",  
  "annualincome": 80000,  
  "telephone1": "555-0110"  
 }    
 ```  
  
 **Respuesta**  
  
 ```http    
 HTTP/1.1 201 Created  
 Content-Type: application/json; odata.metadata=minimal  
 Preference-Applied: return=representation  
 OData-Version: 4.0  
 {  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts/$entity","@odata.etag":"W/\"758870\"","_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03","annualincome":80000.0000,"contactid":"199250b7-6cbe-e611-80f7-00155da84c08","jobtitle":"Junior Developer","fullname":"Peter_Alt Cambel"  
 }    
 ```  
  
 **Salida de la consola**  
  
 ```    
 Contact 'Peter_Alt Cambel' created:  
        Annual income: 80000  
        Job title: Junior Developer  
 Contact URI: https://[Organization URI]/api/data/v9.0/contacts(199250b7-6cbe-e611-80f7-00155da84c08)  
 ```  
  
8.  Actualiza este contacto similar y también devuelve la información de la instancia en la misma operación. Una vez más, esta capacidad está habilitada por el encabezado `Prefer: return=representation`.
  
 **Solicitud** 
  
 ```http    
 POST https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,annualincome,jobtitle,contactid HTTP/1.1  
 OData-Version: 4.0  
 Content-Type: application/json; charset=utf-8  
 Prefer: return=representation  
 {  
   "firstname": "Peter_Alt",  
   "lastname": "Cambel",  
   "jobtitle": "Junior Developer",  
   "annualincome": 80000,  
   "telephone1": "555-0110"  
 }    
 ```  
  
 **Respuesta**  
  
 ```http    
 HTTP/1.1 201 Created  
 Content-Type: application/json; odata.metadata=minimal  
 Preference-Applied: return=representation  
 OData-Version: 4.0  
 {  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts/$entity","@odata.etag":"W/\"758870\"","_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03","annualincome":80000.0000,"contactid":"199250b7-6cbe-e611-80f7-00155da84c08","jobtitle":"Junior Developer","fullname":"Peter_Alt Cambel"  
 }    
 ```  
  
 **Salida de la consola**  
  
```    
Contact 'Peter_Alt Cambel' updated:  
        Annual income: 95000  
        Job title: Senior Developer   
```  
  
<a name="bkmk_section2"></a>  
 
## <a name="section-2-create-with-association"></a>Sección 2: Crear con asociación 
 
Esta sección crea una nueva instancia de cuenta denominada `Contoso, Ltd.` y la asocia a un contacto existente, `Peter Cambel`, que se creó en [Sección 1](#bkmk_section1).  Esta creación y asociación se realizan en una sola operación POST.  
  
1.  Cree la cuenta Contoso, Ltd. y establezca su atributo de contacto principal al contacto existente Peter Cambel.  La anotación `@odata.bind` indica que se está creando a una asociación, enlazando aquí la propiedad de navegación de un solo valor `primarycontactid` con un contacto existente, Peter Cambel.  
  
**Solicitud** 
  
```http  
POST https://[Organization URI]/api/data/v9.0/accounts HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "name": "Contoso Inc",  
  "telephone1": "555-5555",  
  "primarycontactid@odata.bind": "https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)"  
}    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: https://[Organization URI]/api/data/v9.0/accounts(65f77a42-5f0e-e611-80e0-00155da84c03)    
```  
  
**Salida de la consola**  
  
```  
Account 'Contoso Inc' created.  
```  
  
2.  Recupere el contacto principal de la cuenta Contoso, Ltd., de nuevo usando `$expand`  con la propiedad de navegación de un solo valor  `primarycontactid` para acceder al registro asociado <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />.  
  
**Solicitud** 
  
```http    
GET https://[Organization URI]/api/data/v9.0/accounts(65f77a42-5f0e-e611-80e0-00155da84c03)?$select=name,&$expand=primarycontactid($select=fullname,jobtitle,annualincome) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0   
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
{   
       "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(fullname,jobtitle,annualincome))/$entity",  
       "@odata.etag":"W/\"628886\"",  
       "name":"Contoso Inc",  
       "accountid":"65f77a42-5f0e-e611-80e0-00155da84c03",  
       "primarycontactid":{   
          "@odata.etag":"W/\"628885\"",  
          "fullname":"Peter Cambel",  
          "jobtitle":"Senior Developer",  
          "annualincome":95000.0000,  
          "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03",  
          "contactid":"60f77a42-5f0e-e611-80e0-00155da84c03"  
     }  
}    
```  
  
 **Salida de la consola**  
  
 ```    
 Account 'Contoso Inc' has primary contact 'Peter Cambel':  
     Job title: Senior Developer  
     Income: 95000    
 ```  
  
<a name="bkmk_section3"></a>  
 
## <a name="section-3-create-related-entities-deep-insert"></a>Sección 3: Crear entidades relacionadas (inserción en profundidad)  

En esta sección se muestra cómo crear una instancia de entidad e instancias de entidad relacionada en una sola solicitud POST. Con este método, todas las instancias se crean nuevamente; no hay instancias existentes con las que asociar. Este método tiene dos ventajas. Es más eficiente, reemplazando múltiples operaciones más sencillas de creación y asociación con una operación combinada. Además, es [atómico](https://msdn.microsoft.com/library/aa719484\(v=vs.71\).aspx), pues o bien toda la operación se realiza correctamente y se crean todos los objetos relacionados, o la operación fracasa y no se crea ninguno.  
  
Esta sección crea una cuenta, su contacto principal y un conjunto de tareas para ese contacto en una solicitud.  
  
1.  Cree la cuenta `Fourth Coffee` y su contacto principal `Susie Curtis` y sus tres tareas relacionadas en una operación.  Tenga en cuenta el uso de la propiedad de navegación de un solo valor `primarycontactid` y la propiedad de navegación valorada como colección `Contact_Tasks` para definir estas relaciones, respectivamente.  Las propiedades de navegación de un solo valor toman un valor de objeto, en tanto que las propiedades navegación valoradas como colección toman un valor de matriz.  
  
 **Solicitud** 
  
 ```http    
 POST https://[Organization URI]/api/data/v9.0/accounts HTTP/1.1  
 Content-Type: application/json  
 OData-MaxVersion: 4.0  
 OData-Version: 4.0  
 {  
   "name": "Fourth Coffee",  
   "primarycontactid": {  
   "firstname": "Susie",  
   "lastname": "Curtis",  
   "jobtitle": "Coffee Master",  
   "annualincome": 48000,  
   "Contact_Tasks": [  
   {  
       "subject": "Sign invoice",  
       "description": "Invoice #12321",  
       "scheduledend": "2016-04-19T00:00:00-07:00"  
    },  
    {  
       "subject": "Setup new display",  
       "description": "Theme is - Spring is in the air",  
       "scheduledstart": "2016-04-20T00:00:00-07:00"  
    },  
    {  
       "subject": "Conduct training",  
       "description": "Train team on making our new blended coffee",  
       "scheduledstart": "2016-06-01T00:00:00-07:00"  
     }  
   ]  
  }  
}    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: https://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)    
```  
  
**Salida de la consola**  
  
```  
Account 'Fourth Coffee' created.  
```  
  
2.  Recupere selectivamente la cuenta recién creada de Fourth Coffee y su contacto principal.  Una extensión se realiza en la propiedad de navegación de un solo valor `primarycontactid`.  
  
**Solicitud** 
  
```http    
GET https://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)?$select=name,&$expand=primarycontactid($select=fullname,jobtitle,annualincome) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0   
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(fullname,jobtitle,annualincome))/$entity",  
   "@odata.etag":"W/\"628902\"",  
   "name":"Fourth Coffee",  
   "accountid":"6af77a42-5f0e-e611-80e0-00155da84c03",  
   "primarycontactid":{   
     "@odata.etag":"W/\"628892\"",  
     "fullname":"Susie Curtis",  
     "jobtitle":"Coffee Master",  
     "annualincome":48000.0000,  
     "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03",  
     "contactid":"6bf77a42-5f0e-e611-80e0-00155da84c03"  
  }  
}    
```  
  
**Salida de la consola**  
  
```    
Account 'Fourth Coffee' has primary contact 'Susie Curtis':  
       Job title: Coffee Master  
       Income: 48000    
```  
  
3.  Recupere selectivamente las tareas asociadas con el contacto principal recuperado en la operación anterior.  Una extensión se realiza en la propiedad de navegación valorada como colección `Contact_Tasks`.  
  
**Solicitud** 
  
```http    
GET https://[Organization URI]/api/data/v9.0/contacts(6bf77a42-5f0e-e611-80e0-00155da84c03)?$select=fullname,&$expand=Contact_Tasks($select=subject,description,scheduledstart,scheduledend) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0   
{   
    "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,Contact_Tasks,Contact_Tasks(subject,description,scheduledstart,scheduledend))/$entity",  
    "@odata.etag":"W/\"628892\"",  
    "fullname":"Susie Curtis",  
    "contactid":"6bf77a42-5f0e-e611-80e0-00155da84c03",  
    "Contact_Tasks":[   
      {   
         "@odata.etag":"W/\"628903\"",  
         "subject":"Sign invoice",  
         "description":"Invoice #12321",  
         "scheduledstart":"2016-04-19T00:00:00Z",  
         "scheduledend":"2016-04-19T00:00:00Z",  
         "activityid":"6cf77a42-5f0e-e611-80e0-00155da84c03"  
      },  
      {   
         "@odata.etag":"W/\"628905\"",  
         "subject":"Setup new display",  
         "description":"Theme is - Spring is in the air",  
         "scheduledstart":"2016-04-20T00:00:00Z",  
         "scheduledend":"2016-04-20T00:00:00Z",  
         "activityid":"6df77a42-5f0e-e611-80e0-00155da84c03"  
      },  
          {   
             "@odata.etag":"W/\"628907\"",  
             "subject":"Conduct training",  
             "description":"Train team on making our new blended coffee",  
             "scheduledstart":"2016-06-01T00:00:00Z",  
             "scheduledend":"2016-06-01T00:00:00Z",  
             "activityid":"6ef77a42-5f0e-e611-80e0-00155da84c03"  
          }  
       ]  
    }    
```  
  
**Salida de la consola**  
  
```    
Contact 'Susie Curtis' has the following assigned tasks:  
Subject: Sign invoice,  
        Description: Invoice #12321  
        Start: 4/19/2016  
        End: 4/19/2016  
  
Subject: Setup new display,  
        Description: Theme is - Spring is in the air  
        Start: 4/20/2016  
        End: 4/20/2016  
  
Subject: Conduct training  
        Description: Train team on making our new blended coffee,  
        Start: 6/1/2016  
        End: 6/1/2016    
```  
  
<a name="bkmk_section4"></a>
   
## <a name="section-4-associate-and-disassociate-existing-entities"></a>Sección 4: Asocie y desasocie entidades existentes  

En esta sección se muestra cómo asociar y desasociar instancias de entidad existentes. La formación de una asociación requiere el uso de un URI de referencia y un objeto de relación, que a continuación se envían en una solicitud POST. Para desasociar se requiere el envío de una solicitud de ELIMINACIÓN al URI de referencia para esa asociación.  Primero se forma una asociación de uno a varios entre un contacto y una cuenta.  A continuación se forma una asociación de varios a varios entre un competidor y una o varias oportunidades.  
  
1.  Agregue a Peter Cambel como contacto a la cuenta de Fourth Coffee utilizando la propiedad de navegación valorada como colección `contact_customer_accounts`. Tenga en cuenta el uso de la clave especial `@odata.id` para especificar el registro asociado.  
  
**Solicitud** 
  
```http    
POST https://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)/contact_customer_accounts/$ref HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "@odata.id": "https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)"  
}    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content    
```  
  
**Salida de la consola**  
  
```  
Contact 'Peter Cambel' associated to account 'Fourth Coffee'.  
```  
  
2.  Confirme la operación anterior recuperando la colección de contactos para la cuenta Fourth Coffee. La respuesta contiene la matriz con un solo elemento, el contacto recientemente asignado Peter Cambel.  
  
**Solicitud** 
  
```http    
GET https://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)/contact_customer_accounts?$select=fullname,jobtitle HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
**Respuesta**  
  
```http    
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0   
    {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle)","value":[  
        {  
          "@odata.etag":"W/\"632481\"","fullname":"Peter Cambel","jobtitle":"Senior Developer","contactid":"00b6e0e2-b010-e611-80e1-00155da84c03"  
        }  
      ]  
    }    
```  
  
**Salida de la consola**  
  
```    
    Contact list for account 'Fourth Coffee':  
    Name: Peter Cambel, Job title: Senior Developer    
```  
  
3.  Quite la asociación que se creó recientemente entre la cuenta Fourth Coffee y el contacto Peter Cambel.  
  
 **Solicitud** 
  
```http    
DELETE https://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)/contact_customer_accounts/$ref?$id=https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content    
```  
  
 **Salida de la consola**  
  
```  
Contact 'Peter Cambel' dissociated from account 'Fourth Coffee'.  
```  
  
4.  Crear un competidor llamado `Adventure Works`.  
  
**Solicitud** 
  
```http    
POST https://[Organization URI]/api/data/v9.0/competitors HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "name": "Adventure Works",  
      "strengths": "Strong promoter of private tours for multi-day outdoor adventures"  
    }    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: https://[Organization URI]/api/data/v9.0/accounts(77f77a42-5f0e-e611-80e0-00155da84c03)    
```  
  
**Salida de la consola**  
  
```  
Competitor 'Adventure Works' created.  
```  
  
5.  Cree una oportunidad llamada `River rafting adventure`.  
  
**Solicitud** 
  
```http    
POST https://[Organization URI]/api/data/v9.0/opportunities HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "name": "River rafting adventure",  
  "description": "Sales team on a river-rafting offsite and team building"  
}    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: https://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03)    
```  
  
**Salida de la consola**  
  
```  
Opportunity 'River rafting adventure' created.  
```  
  
6.  Asocie esta nueva oportunidad a este nuevo competidor. Tenga en cuenta que en esta asociación de varios a varios se usa la misma sintaxis general que se usó en una asociación anterior de uno a varios.  
  
**Solicitud** 
  
```http    
POST https://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03)/opportunitycompetitors_association/$ref HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
{  
  "@odata.id": "https://[Organization URI]/api/data/v9.0/competitors(77f77a42-5f0e-e611-80e0-00155da84c03)"  
}    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content    
```  
  
**Salida de la consola**  
  
```  
Opportunity 'River rafting adventure' associated with competitor 'Adventure Works'.  
```  
  
7.  Recupere selectivamente todas las oportunidades asociadas al competidor Adventure Works.  Una matriz se devuelve que contiene una sola oportunidad.  
  
 **Solicitud** 
  
```http    
GET https://[Organization URI]/api/data/v9.0/competitors(77f77a42-5f0e-e611-80e0-00155da84c03)?$select=name,&$expand=opportunitycompetitors_association($select=name,description) HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
 **Respuesta**  
  
```http    
HTTP/1.1 200 OK  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#competitors(name,opportunitycompetitors_association,opportunitycompetitors_association(name,description))/$entity",  
   "@odata.etag":"W/\"628913\"",  
   "name":"Adventure Works",  
   "competitorid":"77f77a42-5f0e-e611-80e0-00155da84c03",  
   "opportunitycompetitors_association":[   
      {   
        "@odata.etag":"W/\"628917\"",  
        "name":"River rafting adventure",  
        "description":"Sales team on a river-rafting offsite and team building",  
        "opportunityid":"7cf77a42-5f0e-e611-80e0-00155da84c03"  
      }  
   ]  
}    
```  
  
 **Salida de la consola**  
  
```    
Competitor 'Adventure Works' has the following opportunities:  
       Name: River rafting adventure,  
       Description: Sales team on a river-rafting offsite and team building    
```  
  
8.  Anule la asociación de la oportunidad del competidor.  Observe de nuevo, que tiene la misma sintaxis general usada para quitar una asociación de uno a varios.  
  
**Solicitud** 
  
```http    
DELETE https://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03)/opportunitycompetitors_association/$ref?$id=https://[Token-CRM-Org-Name]/Contoso/api/data/v8.1/competitors(77f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content    
```  
  
**Salida de la consola**  
  
```  
Opportunity 'River rafting adventure' disassociated from competitor 'Adventure Works'.  
```  
  
<a name="bkmk_section5"></a> 
  
## <a name="section-5-delete-entities-sample-cleanup"></a>Sección 5: Eliminar entidades (limpieza de ejemplo) 
 
<!-- TODO:
This section demonstrates how to delete entity instances. The corresponding message is a straightforward DELETE request that uses the URI of the entity instance to be deleted.  If the target entity has a parent-child relationship with other entities, then deleting the parent will, by default, automatically cascade delete child instances. For example, in this sample, tasks have contact as their parent. For more information, see [Entity relationship behavior](../entity-relationship-behavior.md).   -->
  
1.  Cada elemento de la recopilación de direcciones URL de la entidad se elimina.  El primero es un registro de contacto para Peter Cambel.  
  
**Solicitud** 
  
```http
DELETE https://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0    
```  
  
**Respuesta**  
  
```http    
HTTP/1.1 204 No Content    
```  
  
2.  Las iteraciones siguientes a través de la colección eliminan los registros restantes.  
  
**Solicitud** 
  
```http    
DELETE https://[Organization URI]/api/data/v9.0/accounts(65f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
. . .  
  
DELETE https://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
. . .  
  
DELETE https://[Organization URI]/api/data/v9.0/contacts(6bf77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
. . .  
  
DELETE https://[Organization URI]/api/data/v9.0/competitors(77f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
. . .  
  
DELETE https://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
. . .    
```  
  
### <a name="see-also"></a>Vea también  

[Usar la API web de Common Data Service](overview.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Ejemplo de operaciones básicas de la API web (C#)](samples/basic-operations-csharp.md)<br />