---
title: Ejemplo de datos de consulta de la API web (Common Data Service)| Microsoft Docs
description: Este grupo de ejemplos demuestra cómo consultar datos utilizando la API web. Estos están implementados mediante JavaScript del lado cliente y C#
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 9457ce4f-0ef6-4085-8346-fe3134ec7106
caps.latest.revision: 18
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a305f1676275c8b6f72d70e4e416a798933b476c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753632"
---
# <a name="web-api-query-data-sample"></a>Ejemplo de datos de consulta de la API web

Este grupo de ejemplos demuestra cómo consultar datos utilizando API web de Common Data Service. Este ejemplo se implementa como proyecto independiente para los siguientes idiomas:

- [Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](samples/query-data-client-side-javascript.md)

- [Ejemplo de datos de consulta (C#)](samples/query-data-csharp.md)

En este tema se describe un conjunto común de operaciones implementadas por cada ejemplo en este grupo. En este tema se describen las solicitudes y las respuestas HTTP y el texto generado que cada ejemplo en este grupo realizará sin detalles específicos de idioma. Consulte las descripciones específicas del idioma y los ejemplos individuales para obtener más información acerca de cómo se realizan estas operaciones.

## <a name="demonstrates"></a>Demostraciones

Este ejemplo se divide en las siguientes secciones principales, que contienen operaciones de datos de consulta de la API web que se describen minuciosamente en los temas conceptuales asociados.

|Sección del tema|Temas asociados|
|-------------------|---------------------------|
|[Seleccionar propiedades específicas](#bkmk_selectproperties)|[Recuperar propiedades específicas](retrieve-entity-using-web-api.md#bkmk_requestProperties)<br /><br /> [Incluir valores con formato](query-data-web-api.md#bkmk_includeFormattedValues)|
|[Uso de funciones de consulta](#bkmk_queryfunctions)|[Filtrar resultados](query-data-web-api.md#bkmk_filter)<br /><br /> [Funciones estándar de consulta](query-data-web-api.md#bkmk_buildInQueryFunctions)<br /><br /> [Crear una consulta con funciones](use-web-api-functions.md#bkmk_composeQueryWithFunctions)<br /><br /> <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>|
|[Uso de operadores](#bkmk_operators)|[Operadores estándar de filtro](query-data-web-api.md#bkmk_buildInFilterOperators)|
|[Establecer prioridad](#bkmk_prededence)|[Operadores estándar de filtro](query-data-web-api.md#bkmk_buildInFilterOperators)|
|[Ordenar resultados](#bkmk_orderresults)|[Ordenar resultados](query-data-web-api.md#bkmk_order)<br /><br /> [Filtrar resultados](query-data-web-api.md#bkmk_filter)|
|[Alias de parámetro](#bkmk_parameteralias)|[Uso de alias de parámetro con opciones de consulta del sistema](query-data-web-api.md#bkmk_useParameterAliases)|
|[Limitar resultados](#bkmk_limitresults)|[Limitar resultados](query-data-web-api.md#bkmk_limitResults)<br /><br /> [Límites en el número de entidades devueltas](query-data-web-api.md#bkmk_limits)|
|[Expandir resultados](#bkmk_expandresults)|[Recuperar entidades relacionadas ampliando las propiedades de navegación](query-data-web-api.md#bkmk_expandRelated)|
<!-- TODO:
|[FetchXML queries](#bkmk_fetchxml)|[FetchXML schema](../org-service/fetchxml-schema.md)<br /><br /> [Page large result sets with FetchXML](../org-service/page-large-result-sets-with-fetchxml.md)<br /><br /> [Use custom FetchXML](retrieve-and-execute-predefined-queries.md#bkmk_useFetchXML)| -->
|[Consultas predefinidas](#bkmk_predefinedqueries)|[Recuperar y ejecutar consultas predefinidas](retrieve-and-execute-predefined-queries.md)<br /><br /> <xref href="Microsoft.Dynamics.CRM.userquery?text=userquery EntityType" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" />|

Las siguientes secciones contienen una breve explicación de las operaciones de la API web de Common Data Service realizadas, junto con mensajes HTTP correspondientes y la salida asociada de la consola.

<a name="bkmk_sampleData"></a>

## <a name="sample-data"></a>Datos de ejemplo

Para asegurarse de que las consultas de este ejemplo funcionan correctamente, se crea un conjunto estándar de registros de ejemplo mediante este ejemplo. Estos registros de ejemplo se eliminarán a menos que el usuario elija no eliminarlos. Estos son los datos que consultará el ejemplo. Puede obtener resultados diferentes en función de los datos existentes en el entorno.  
  
Los datos se agregan mediante *inserción profunda* en una sola solicitud de `POST` y coinciden con la estructura siguiente:  
  
```json  
  
 {  
        "name": "Contoso, Ltd. (sample)",  
        "primarycontactid": {  
            "firstname": "Yvonne", "lastname": "McKay (sample)", "jobtitle": "Coffee Master",  
            "annualincome": 45000, "Contact_Tasks": [  
            { "subject": "Task 1", "description": "Task 1 description" },  
            { "subject": "Task 2", "description": "Task 2 description" },  
            { "subject": "Task 3", "description": "Task 3 description" }  
            ]  
        },   
                            "Account_Tasks": [  
        { "subject": "Task 1", "description": "Task 1 description" },  
        { "subject": "Task 2", "description": "Task 2 description" },  
        { "subject": "Task 3", "description": "Task 3 description" }  
        ],  
        "contact_customer_accounts": [  
            {  
                "firstname": "Susanna", "lastname": "Stubberod (sample)", "jobtitle": "Senior Purchaser",  
                "annualincome": 52000, "Contact_Tasks": [  
            { "subject": "Task 1", "description": "Task 1 description" },  
            { "subject": "Task 2", "description": "Task 2 description" },  
            { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Nancy", "lastname": "Anderson (sample)", "jobtitle": "Activities Manager",  
                "annualincome": 55500, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Maria", "lastname": "Cambell (sample)", "jobtitle": "Accounts Manager",  
                "annualincome": 31000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Nancy", "lastname": "Anderson (sample)", "jobtitle": "Logistics Specialist",  
                "annualincome": 63500, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Scott", "lastname": "Konersmann (sample)", "jobtitle": "Accounts Manager",  
                "annualincome": 38000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Robert", "lastname": "Lyon (sample)", "jobtitle": "Senior Technician",  
                "annualincome": 78000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Paul", "lastname": "Cannon (sample)", "jobtitle": "Ski Instructor",  
                "annualincome": 68500, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Rene", "lastname": "Valdes (sample)", "jobtitle": "Data Analyst III",  
                "annualincome": 86000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Jim", "lastname": "Glynn (sample)", "jobtitle": "Senior International Sales Manager",  
                "annualincome": 81400, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            }  
        ]  
    }  
```  
  
<a name="bkmk_selectproperties"></a>
   
## <a name="selecting-specific-properties"></a>Seleccionar propiedades específicas
  
Genere siempre las consultas mediante la opción de consulta `$select`; si no, el servidor devolverá todas las propiedades de cada entidad, lo que reduce rendimiento. Este ejemplo demuestra cómo generar una consulta básica seleccionando tres propiedades de un <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />. Las propiedades son `fullname`, `jobtitle`, `annualincome`. La sección también muestra las diferencias entre los valores con formato y sin formato que se ve en los resultados de la propiedad `annualincome` de un contacto. Más información:[Solicitar propiedades específicas,](query-data-web-api.md#bkmk_requestProperties), [Incluir valores con formato](query-data-web-api.md#bkmk_includeFormattedValues).  
  
En este ejemplo, solicitamos un contacto específico. En este caso, es el contacto principal de la cuenta, `Yvonne McKay (sample)`.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts(b848fdee-c143-e611-80d5-00155da84802)?$select=fullname,jobtitle,annualincome HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 517  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)/$entity",  
   "@odata.etag":"W/\"619718\"",  
   "fullname":"Yvonne McKay (sample)",  
   "jobtitle":"Coffee Master",  
   "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
   "annualincome":45000.0000,  
   "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
   "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
   "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
}  
```  
  
 **Salida de la consola**  
  
```  
Contact basic info:  
    Fullname: 'Yvonne McKay (sample)'  
    Jobtitle: 'Coffee Master'  
    Annualincome: '45000' (unformatted)  
    Annualincome: $45,000.00 (formatted)  
  
```  
  
<a name="bkmk_queryfunctions"></a>
  
## <a name="using-query-functions"></a>Uso de funciones de consulta
 
Use opciones de filtro para establecer criterios para los resultados deseados. Puede crear filtros sencillos y complejos con una combinación de funciones de consulta, operadores de comparación, y operadores lógicos. Más información:[Filtrar resultados](query-data-web-api.md#bkmk_filter).  
  
Las funciones de consulta son funciones que se pueden usar como criterios de filtro en una consulta. Hay funciones de consulta estándar y funciones de consulta específicas de Common Data Service. Estas funciones aceptan parámetros y devuelven un valor `Boolean`. En este ejemplo se muestra cómo crear una consulta para cada tipo.  
  
### <a name="standard-query-functions"></a>Funciones estándar de consulta

Common Data Service admite un pequeño subconjunto de funciones de consulta integradas de OData, específicamente: `contains`, `endswith`, y `startswith`. Por ejemplo, la función de consulta estándar `contains` permite filtrar las propiedades que coincidan con una cadena. En esta operación, consultamos todos los contactos con `fullname` que contienen la cadena `(sample)`. Más información:[Funciones estándar de consulta](query-data-web-api.md#bkmk_buildInQueryFunctions).  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)') HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts filtered by fullname containing '(sample)':  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
    5) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    6) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    7) Robert Lyon (sample), Senior Technician, $78,000.00  
    8) Paul Cannon (sample), Ski Instructor, $68,500.00  
    9) Rene Valdes (sample), Data Analyst III, $86,000.00  
    10) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
  
```  
  
### <a name="common-data-service-query-functions"></a>Common Data Service Funciones de consulta

Las funciones de consulta de Common Data Service proporcionan un gran número de opciones para generar consultas que son relevantes para Common Data Service. Para obtener una lista completa de estas funciones, vea <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>. Más información: [Crear una consulta con funciones](use-web-api-functions.md#bkmk_composeQueryWithFunctions)  
  
Usará estas funciones de consulta de forma similar a las funciones de consulta estándar. La diferencia principal es que cuando usa funciones de consulta de Common Data Service, debe proporcionar el nombre completo de la función incluidos los nombres de parámetros. Por ejemplo, para obtener una lista de contactos creados en la última hora, puede generar una consulta mediante la <xref href="Microsoft.Dynamics.CRM.LastXHours?text=LastXHours Function" />.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=Microsoft.Dynamics.CRM.LastXHours(PropertyName='createdon',PropertyValue='1') HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts that were created within the last 1hr:  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
    5) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    6) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    7) Robert Lyon (sample), Senior Technician, $78,000.00  
    8) Paul Cannon (sample), Ski Instructor, $68,500.00  
    9) Rene Valdes (sample), Data Analyst III, $86,000.00  
    10) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_operators"></a>
 
## <a name="using-operators"></a>Uso de operadores

Utilice los [operadores de filtro estándar](query-data-web-api.md#bkmk_buildInFilterOperators) (`eq`,`ne`,`gt`,`ge`,`lt`,`le`,`and`,`or`,`not`) para restringir más los resultados. En este ejemplo, solicitamos una lista de todos los contactos con `fullname` que contienen `(sample)` e ingresos anuales mayores que `55000`.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')%20and%20annualincome%20gt%2055000 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 2629  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts filtered by fullname and annualincome (<$55,000):  
    1) Nancy Anderson (sample), Activities Manager, $55,500.00  
    2) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    3) Robert Lyon (sample), Senior Technician, $78,000.00  
    4) Paul Cannon (sample), Ski Instructor, $68,500.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_prededence"></a>
   
## <a name="setting-precedence"></a>Establecer prioridad
 
Use paréntesis para establecer el orden en el cual se evalúan las condiciones.  
  
 En este ejemplo, solicitamos una lista de todos los contactos con `fullname` que contienen `(sample)`, `jobtitle` que contienen `senior` o `specialist` y `annualincome` mayores que `55000`. Para obtener los resultados deseados, se usan paréntesis para agrupar los filtros `jobtitle`. Puesto que todos los operadores tienen la misma prioridad, si omite los paréntesis dará al operador de `or` la misma prioridad que los operadores de `and`.  Los filtros se aplican de izquierda a derecha. El orden en el que estas instrucciones aparecen en el filtro puede afectar a los resultados. Este es el aspecto de la consulta en este ejemplo: `$filter=contains(fullname,'(sample)') and (contains(jobtitle,'senior') or contains(jobtitle,'specialist')) and annualincome gt 55000`.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')%20and%20(contains(jobtitle,'senior')%20or%20contains(jobtitle,'specialist'))%20and%20annualincome%20gt%2055000 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 1393  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts filtered by fullname, annualincome and jobtitle (Senior or Specialist):  
    1) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    2) Robert Lyon (sample), Senior Technician, $78,000.00  
    3) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_orderresults"></a>

## <a name="ordering-results"></a>Ordenar resultados

Puede especificar orden ascendente o descendente en los resultados mediante la opción de filtro `$orderby`. En este ejemplo, consultaremos para todos los contactos con `fullname` que contiene `(sample)` y solicitaremos los datos en orden ascendente en función del valor de propiedad `jobtitle` y luego en orden descendente basado en el valor de propiedad `annualincome` usando esta sintaxis: `$orderby=jobtitle asc, annualincome desc`. Más información:[Ordenar resultados](query-data-web-api.md#bkmk_order).  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')%20&$orderby=jobtitle%20asc,%20annualincome%20desc HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts ordered by jobtitle (ascending) and annualincome (descending):  
    1) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    2) Maria Cambell (sample), Accounts Manager, $31,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Yvonne McKay (sample), Coffee Master, $45,000.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    7) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
    8) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    9) Robert Lyon (sample), Senior Technician, $78,000.00  
    10) Paul Cannon (sample), Ski Instructor, $68,500.00  
```  
  
<a name="bkmk_parameteralias"></a>

## <a name="parameter-alias"></a>Alias de parámetro

Use alias de parámetro para reutilizar más fácilmente los parámetros en los filtros. Los alias con parámetros se pueden usar en las opciones `$filter` y `$orderby`. Si al alias no se asigna un valor se da por hecho que es nulo. También puede usar alias de parámetro al llamar funciones. Más información:[Uso de funciones API web](use-web-api-functions.md), [Uso de alias de parámetro con opciones de consulta del sistema](query-data-web-api.md#bkmk_useParameterAliases). Realizando la operación de ordenar resultados, por ejemplo, podemos escribir esa consulta de nuevo con los parámetros y obtendríamos los mismos resultados de salida.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(@p1,'(sample)')%20&$orderby=@p2%20asc,%20@p3%20desc&@p1=fullname&@p2=jobtitle&@p3=annualincome HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts list using parameterized aliases:  
    1) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    2) Maria Cambell (sample), Accounts Manager, $31,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Yvonne McKay (sample), Coffee Master, $45,000.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    7) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
    8) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    9) Robert Lyon (sample), Senior Technician, $78,000.00  
    10) Paul Cannon (sample), Ski Instructor, $68,500.00  
```  
  
<a name="bkmk_limitresults"></a>

## <a name="limit-results"></a>Limitar resultados

Devolver más datos de los que necesita es malo para el rendimiento. El servidor devolverá un máximo de 5000 entidades por solicitud. Puede restringir el número de resultados devueltos mediante la opción de consulta `$top` o agregando `odata.maxpagesize` en el encabezado de solicitud. La opción de consulta `$top` devuelve únicamente al número superior de entidades del conjunto de resultados y omite el resto. El encabezado de solicitud `odata.maxpagesize` especifica el número de entidades devueltas por página con una propiedad `@odata.nextLink` para obtener resultados de la página siguiente. Para obtener más información acerca de `odata.maxpagesize`, consulte la sección [Paginación](#bkmk_filterPagination) y vea también [Límite para el número de entidades devuelve](query-data-web-api.md#bkmk_limits).  
  
<a name="bkmk_topResults"></a>
 
### <a name="top-results"></a>Resultados superiores

Podemos aplicar la opción de consulta `$top` para limitar la operación de consulta básica a los cinco primeros contactos con `fullname` que contienen `(sample)`. En este caso, la solicitud genera realmente al menos 10 resultados, pero solo las primeras 5 entradas se devuelven en la respuesta.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$top=5 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 2209  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts top 5 results:  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
    5) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
  
```  
  
<a name="bkmk_resultCount"></a>

### <a name="result-count"></a>Número de resultados

Puede obtener únicamente el recuento de registros de una propiedad valorada como colección o un recuento de entidades que coinciden en un filtro. Realizar un recuento nos indica el número de entidades posibles en el resultado. Sin embargo, el servidor de Common Data Service devolverá 5000 como recuento máximo aunque el resultado puede tener más. En este ejemplo, construimos un filtro con `jobtitle` que contiene `Senior` o `Manager` y también solicitamos un `$count` del resultado. La respuesta contiene el recuento en la propiedad `@odata.count` así como los resultados de la consulta. Más información:[Recuperar un recuento de entidades](query-data-web-api.md#bkmk_retrieveCount).  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(jobtitle,'senior')%20or%20contains(jobtitle,%20'manager')&$count=true HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 2654  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "@odata.count":6,  
   "value":[  
      {  
         "@odata.etag":"W/\"620258\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"bf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620260\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620262\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c748fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620266\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"cf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620268\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"d348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620274\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"df48fdee-c143-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
6 contacts have either 'Manager' or 'Senior' designation in their jobtitle.  
Manager or Senior:  
    1) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
    3) Maria Cambell (sample), Accounts Manager, $31,000.00  
    4) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    5) Robert Lyon (sample), Senior Technician, $78,000.00  
    6) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
  
```  
  
<a name="bkmk_filterPagination"></a>

### <a name="pagination"></a>Paginación

Para recuperar un subconjunto secuencial de resultados para una consulta que devuelva un gran número de entidades, use `odata.maxpagesize` en lugar de `$top`. Más información:[Especifique el número de entidades para devolver a una página](query-data-web-api.md#bkmk_specifyNumber).  
  
En este ejemplo, pedimos `$count` y establecemos `odata.maxpagesize` como `4`. Este filtro coincide con 10 contactos, pero solo estamos recuperando 4 a la vez. También usamos el recuento y el tamaño máximo de página para averiguar el número de páginas totales que hay. El resultado de la primera página se devuelve en esta solicitud.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=4, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=4  
Content-Length: 2294  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "@odata.count":10,  
   "value":[  
      {  
         "@odata.etag":"W/\"620138\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b848fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620258\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"bf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620260\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620262\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c748fdee-c143-e611-80d5-00155da84802"  
      }  
   ],  
   "@odata.nextLink":"https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253ccontactid%2520last%253d%2522%257bC748FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520first%253d%2522%257bB848FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts total: 10  Contacts per page: 4.  
Page 1 of 3:  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
  
```  
  
 Para recuperar la página 2, use una solicitud `GET` con el valor de la propiedad `@odata.nextLink`.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253ccontactid%2520last%253d%2522%257bC748FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520first%253d%2522%257bB848FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=4, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=4  
Content-Length: 2294  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "@odata.count":10,  
   "value":[  
      {  
         "@odata.etag":"W/\"620264\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"cb48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620266\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"cf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620268\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"d348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620270\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"d748fdee-c143-e611-80d5-00155da84802"  
      }  
   ],  
   "@odata.nextLink":"https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true&$skiptoken=%3Ccookie%20pagenumber=%223%22%20pagingcookie=%22%253ccookie%2520page%253d%25222%2522%253e%253ccontactid%2520last%253d%2522%257bD748FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520first%253d%2522%257bCB48FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"  
}  
```  
  
 **Salida de la consola**  
  
```  
Page 2 of 3:  
    1) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    2) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    3) Robert Lyon (sample), Senior Technician, $78,000.00  
    4) Paul Cannon (sample), Ski Instructor, $68,500.00  
```  
  
<a name="bkmk_expandresults"></a>

## <a name="expanding-results"></a>Expandir resultados

Para recuperar la información de entidades asociadas, use la opción de consulta `$expand` en propiedades de navegación. Más información:[Recuperar entidades relacionadas ampliando las propiedades de navegación](query-data-web-api.md#bkmk_expandRelated).  
  
### <a name="expand-on-single-valued-navigation-property"></a>Expandir la propiedad de navegación de un solo valor

Una propiedad de navegación de un solo valor representa relaciones de varios a uno. En nuestros datos de ejemplo, la cuenta tiene una relación con un contacto mediante el atributo `primarycontactid`. En esta relación, la cuenta solo puede tener un contacto principal.  Con el <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />, podemos crear una consulta para obtener información sobre la cuenta y información ampliada sobre su contacto principal.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts(b2546951-c543-e611-80d5-00155da84802)?$select=name&$expand=primarycontactid($select=fullname,jobtitle,annualincome) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 700  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(fullname,jobtitle,annualincome))/$entity",  
   "@odata.etag":"W/\"620641\"",  
   "name":"Contoso, Ltd. (sample)",  
   "accountid":"b2546951-c543-e611-80d5-00155da84802",  
   "primarycontactid":{  
      "@odata.etag":"W/\"620534\"",  
      "fullname":"Yvonne McKay (sample)",  
      "jobtitle":"Coffee Master",  
      "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
      "annualincome":45000.0000,  
      "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
      "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
      "contactid":"b3546951-c543-e611-80d5-00155da84802"  
   }  
}  
```  
  
 **Salida de la consola**  
  
```  
Account 'Contoso, Ltd. (sample)' has the following primary contact person:  
    Fullname: 'Yvonne McKay (sample)'   
    Jobtitle: 'Coffee Master'   
    Annualincome: '45000'  
```  
  
### <a name="expand-on-partner-property"></a>Expandir la propiedad de asociados

Cada propiedad de navegación tiene una propiedad de “asociado" correspondiente. Una vez que crea una asociación, podemos recuperar la información a través de esta asociación. Qué atributo usemos depende de la entidad base con la que se realiza la consulta. Por ejemplo, en la operación anterior, creamos una consulta para el <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> y deseábamos obtener información adicional sobre su contacto principal. Lo hicimos mediante el atributo `primarycontactid`. Si consultamos el <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />, en la sección [Propiedades de navegación de valor único](/dynamics365/customer-engagement/web-api/account?view=dynamics-ce-odata-9#Single-valued_navigation_properties), podemos ver que la propiedad de asociados que corresponde a `primarycontactid` es la propiedad de navegación valorada como colección `account_primary_contact`  que se encuentra en el <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />.  
  
Escribiendo una consulta para un contacto, puede expandir en el atributo `account_primary_contact` para obtener información de las cuentas donde ese contacto es el contacto principal. En los datos de ejemplo, `Yvonne McKay (sample)` es la persona de contacto principal únicamente para una cuenta. Sin embargo, puede asignarse potencialmente a otras cuentas como contacto principal. Puesto que la propiedad `account_primary_contact` tiene una relación de varios a uno el resultado se devuelve como una matriz de entidades de cuenta.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts(b3546951-c543-e611-80d5-00155da84802)?$select=fullname,jobtitle,annualincome&$expand=account_primary_contact($select=name) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 737  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome,account_primary_contact,account_primary_contact(name))/$entity",  
   "@odata.etag":"W/\"620534\"",  
   "fullname":"Yvonne McKay (sample)",  
   "jobtitle":"Coffee Master",  
   "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
   "annualincome":45000.0000,  
   "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
   "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
   "contactid":"b3546951-c543-e611-80d5-00155da84802",  
   "account_primary_contact":[  
      {  
         "@odata.etag":"W/\"620919\"",  
         "name":"Contoso, Ltd. (sample)",  
         "accountid":"b2546951-c543-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contact 'Yvonne McKay (sample)' is the primary contact for the following accounts:  
    1) Contoso, Ltd. (sample)  
```  
  
### <a name="expand-on-collection-valued-navigation-property"></a>Expandir la propiedad de navegación valorada como colección

Las propiedades de navegación valoradas como colección admiten relaciones de uno a varios o de varios a varios. Por ejemplo, en nuestros datos de ejemplo, la cuenta tiene una relación con muchos contactos mediante el atributo `contact_customer_accounts`.  
  
Con el <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />, podemos crear una consulta para obtener información sobre la cuenta y expanda información sobre sus contactos. En este caso, el `Contoso, Ltd. (sample)` se asocia a otros nueve contactos mediante la propiedad de navegación valorada como colección `contact_customer_accounts`.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts(86546951-c543-e611-80d5-00155da84802)?$select=name&$expand=contact_customer_accounts($select=fullname,jobtitle,annualincome) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4073  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,contact_customer_accounts,contact_customer_accounts(fullname,jobtitle,annualincome))/$entity",  
   "@odata.etag":"W/\"620921\"",  
   "name":"Contoso, Ltd. (sample)",  
   "accountid":"86546951-c543-e611-80d5-00155da84802",  
   "contact_customer_accounts":[  
      {  
         "@odata.etag":"W/\"620847\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"8e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620849\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"92546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620851\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"96546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620853\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9a546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620855\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620857\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a2546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620859\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a6546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620861\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"aa546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620863\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"ae546951-c543-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Account 'Contoso, Ltd. (sample)' has the following contact customers:  
    1) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
    3) Maria Cambell (sample), Accounts Manager, $31,000.00  
    4) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    5) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    6) Robert Lyon (sample), Senior Technician, $78,000.00  
    7) Paul Cannon (sample), Ski Instructor, $68,500.00  
    8) Rene Valdes (sample), Data Analyst III, $86,000.00  
    9) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
### <a name="expand-on-multiple-navigation-properties"></a>Expandir varias propiedades de navegación

Puede expandir tantas propiedades de navegación como la consulta requiera. Sin embargo, la opción `$expand` solo puede ir a un nivel de profundidad.  
  
Este ejemplo expande las propiedades de propiedad `primarycontactid`, `contact_customer_accounts` y `Account_Tasks` del <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />.  Esta consulta devuelve una respuesta que contiene información sobre la cuenta y dos colecciones: una colección de contactos y una colección de tareas. El código de ejemplo procesará estas colecciones de forma independiente.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts(86546951-c543-e611-80d5-00155da84802)?$select=name&$expand=primarycontactid($select=fullname,jobtitle,annualincome),contact_customer_accounts($select=fullname,jobtitle,annualincome),Account_Tasks($select=subject,description) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 5093  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,contact_customer_accounts,Account_Tasks,primarycontactid(fullname,jobtitle,annualincome),contact_customer_accounts(fullname,jobtitle,annualincome),Account_Tasks(subject,description))/$entity",  
   "@odata.etag":"W/\"620921\"",  
   "name":"Contoso, Ltd. (sample)",  
   "accountid":"86546951-c543-e611-80d5-00155da84802",  
   "primarycontactid":{  
      "@odata.etag":"W/\"620726\"",  
      "fullname":"Yvonne McKay (sample)",  
      "jobtitle":"Coffee Master",  
      "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
      "annualincome":45000.0000,  
      "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
      "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
      "contactid":"87546951-c543-e611-80d5-00155da84802"  
   },  
   "contact_customer_accounts":[  
      {  
         "@odata.etag":"W/\"620847\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"8e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620849\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"92546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620851\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"96546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620853\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9a546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620855\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620857\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a2546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620859\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a6546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620861\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"aa546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620863\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"ae546951-c543-e611-80d5-00155da84802"  
      }  
   ],  
   "Account_Tasks":[  
      {  
         "@odata.etag":"W/\"620840\"",  
         "subject":"Task 1",  
         "description":"Task 1 description",  
         "activityid":"8b546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620842\"",  
         "subject":"Task 2",  
         "description":"Task 2 description",  
         "activityid":"8c546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620844\"",  
         "subject":"Task 3",  
         "description":"Task 3 description",  
         "activityid":"8d546951-c543-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
-- Expanding multiple property types in one request --   
Account 'Contoso, Ltd. (sample)' has the following primary contact person:  
    Fullname: 'Yvonne McKay (sample)'   
    Jobtitle: 'Coffee Master'   
    Annualincome: '45000'  
Account 'Contoso, Ltd. (sample)' has the following related contacts:  
    1) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
    3) Maria Cambell (sample), Accounts Manager, $31,000.00  
    4) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    5) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    6) Robert Lyon (sample), Senior Technician, $78,000.00  
    7) Paul Cannon (sample), Ski Instructor, $68,500.00  
    8) Rene Valdes (sample), Data Analyst III, $86,000.00  
    9) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
Account 'Contoso, Ltd. (sample)' has the following tasks:  
    1) Task 1, Task 1 description  
    2) Task 2, Task 2 description  
    3) Task 3, Task 3 description  
```  
  
<a name="bkmk_fetchxml"></a>

## <a name="fetchxml-queries"></a>consultas FetchXML

<!-- TODO:
Besides query filter operations, the Web API also supports FetchXML queries. FetchXml provides an alternative way to define queries and additional options to perform aggregations. More information:[Build queries with FetchXML](../org-service/build-queries-fetchxml.md)   -->
  
<!-- TODO: To use fetch xml you must compose a string representing the query. Make sure the query string conforms to the [FetchXML schema](../org-service/fetchxml-schema.md). Before you include the string in the URL you must URL encode the string.   -->
  
 Todas las opciones de consulta que definiríamos normalmente como `$select`, `$filter` y `$orderby` ahora se definen en el XML. En esta operación, consultamos todos los contactos cuyo `fullname` coincida con `(sample)`, y ordenamos los resultados en orden descendente por `fullname`. Este es el XML para esta consulta.  
  
```xml  
<fetch mapping="logical" output-format="xml-platform" version="1.0" distinct="false">  
  <entity name="contact">  
    <attribute name="fullname" />  
    <attribute name="jobtitle" />  
    <attribute name="annualincome" />  
    <order descending="true"  
           attribute="fullname" />  
    <filter type="and">  
      <condition value="%(sample)%"  
                 attribute="fullname"  
                 operator="like" />  
    </filter>  
  </entity>  
</fetch>  
```  
  
 **Solicitud HTTP**  
  
 La cadena de consulta de la solicitud se envía al servidor en formato codificado. El encabezado codificado tiene este aspecto.  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?fetchXml=%253Cfetch%2520mapping%253D%2522logical%2522%2520output-format%253D%2522xml-platform%2522%2520version%253D%25221.0%2522%2520distinct%253D%2522false%2522%253E%2520%2520%2520%253Centity%2520name%253D%2522contact%2522%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522jobtitle%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522annualincome%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Corder%2520descending%253D%2522true%2522%2520attribute%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cfilter%2520type%253D%2522and%2522%253E%2520%2520%2520%2520%2520%2520%2520%253Ccondition%2520value%253D%2522%2525(sample)%2525%2522%2520attribute%253D%2522fullname%2522%2520operator%253D%2522like%2522%2520%252F%253E%2520%2520%2520%2520%2520%253C%252Ffilter%253E%2520%2520%2520%253C%252Fentity%253E%2520%253C%252Ffetch%253E%2520 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 4345  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome,_transactioncurrencyid_value,transactioncurrencyid,contactid)",  
   "value":[  
      {  
         "@odata.etag":"W/\"621502\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9255b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621627\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9955b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621635\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a955b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621637\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"ad55b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621641\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b555b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621639\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b155b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621629\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9d55b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621633\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a555b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621631\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a155b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621643\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b955b257-c843-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts Fetched by fullname containing '(sample)':  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    4) Robert Lyon (sample), Senior Technician, $78,000.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Paul Cannon (sample), Ski Instructor, $68,500.00  
    7) Nancy Anderson (sample), Activities Manager, $55,500.00  
    8) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    9) Maria Cambell (sample), Accounts Manager, $31,000.00  
    10) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
### <a name="fetchxml-pagination"></a>Paginación FetchXML

La forma en que FetchXML administra la paginación es diferente de cómo lo hace el filtro de consulta. En FetchXML, puede especificar un atributo `count` que indique cuántos resultados se devolverán por página. En la misma solicitud, use el atributo `page` para especificar el número de página que desee. Esta operación hará una solicitud de la página 3 del ejemplo FetchXML anterior. En función de nuestros datos de ejemplo, deberíamos tener diez contactos en nuestro resultado. Descomponiendo cada página a solo cuatro entidades por página, deberíamos tener tres páginas. La página 3 debe contener solo dos entidades. Si a continuación pedimos la página 4, el sistema devolverá cero resultados.  
  
```xml  
<fetch mapping="logical"  
       output-format="xml-platform"  
       version="1.0"  
       distinct="false"  
       page="3"  
       count="4">  
  <entity name="contact">  
    <attribute name="fullname" />  
    <attribute name="jobtitle" />  
    <attribute name="annualincome" />  
    <order descending="true"  
           attribute="fullname" />  
    <filter type="and">  
      <condition value="%(sample)%"  
                 attribute="fullname"  
                 operator="like" />  
    </filter>  
  </entity>  
</fetch>  
```  
  
 **Solicitud HTTP**  
  
 La cadena de consulta de la solicitud se envía al servidor en formato codificado. El encabezado codificado tiene este aspecto.  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?fetchXml=%253Cfetch%2520mapping%253D%2522logical%2522%2520output-format%253D%2522xml-platform%2522%2520version%253D%25221.0%2522%2520distinct%253D%2522false%2522%2520page%253D%25223%2522%2520count%253D%25224%2522%253E%2520%2520%2520%253Centity%2520name%253D%2522contact%2522%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522jobtitle%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522annualincome%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Corder%2520descending%253D%2522true%2522%2520attribute%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cfilter%2520type%253D%2522and%2522%253E%2520%2520%2520%2520%2520%2520%2520%253Ccondition%2520value%253D%2522%2525(sample)%2525%2522%2520attribute%253D%2522fullname%2522%2520operator%253D%2522like%2522%2520%252F%253E%2520%2520%2520%2520%2520%253C%252Ffilter%253E%2520%2520%2520%253C%252Fentity%253E%2520%253C%252Ffetch%253E%2520 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 1037  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome,_transactioncurrencyid_value,transactioncurrencyid,contactid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621631\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a155b257-c843-e611-80d5-00155da84802"  
      },  
      {   
         "@odata.etag":"W/\"621643\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b955b257-c843-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
Contacts Fetched by fullname containing '(sample)' - Page 3:  
    1) Maria Cambell (sample), Accounts Manager, $31,000.00  
    2) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_predefinedqueries"></a>
 
## <a name="predefined-queries"></a>Consultas predefinidas

Puede usar la API web para ejecutar consultas predefinidas. Más información:[Recuperar y ejecutar consultas predefinidas](retrieve-and-execute-predefined-queries.md).  
  
### <a name="saved-query"></a>Consulta guardada

En esta operación, haremos una solicitud para el GUID `savedqueryid` de la consulta guardada con el nombre **Cuentas activas**. A continuación utilizando el GUID y el parámetro `savedQuery`, consultaremos para una lista de cuentas activas.  
  
 Obtener el GUID de la consulta guardada.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/savedqueries?$select=name,savedqueryid&$filter=name%20eq%20'Active%20Accounts' HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
Referer: https://localhost:1469/WebAPIQuery.html  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 251  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#savedqueries(name,savedqueryid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"443067\"",  
         "name":"Active Accounts",  
         "savedqueryid":"00000000-0000-0000-00aa-000010001002"  
      }  
   ]  
}  
```  
  
 Obtener el contenido de la consulta guardada con el parámetro `savedQuery`  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts?savedQuery=00000000-0000-0000-00aa-000010001002 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
REQ_ID: 2bc532c4-d445-44cd-adae-1909a616d6bc  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 446  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,_primarycontactid_value,primarycontactid,accountid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621613\"",  
         "name":"Contoso, Ltd. (sample)",  
         "_primarycontactid_value@OData.Community.Display.V1.FormattedValue":"Yvonne McKay (sample)",  
         "_primarycontactid_value":"9255b257-c843-e611-80d5-00155da84802",  
         "accountid":"9155b257-c843-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
-- Saved Query --   
Saved Query (Active Accounts):  
    1) Contoso, Ltd. (sample)  
```  
  
### <a name="user-query"></a>Consulta de usuario

Este ejemplo crea una consulta de usuario, la ejecuta y luego la elimina del sistema. Esta consulta de usuario pide contactos cuyo `fullname` contiene `(sample)`, `jobtitle` contiene `manager`, y `annualincome` mayor que `55000`. Nuestros datos de ejemplo tiene dos contactos que coinciden con esta consulta.  
  
 Obtener el GUID de la consulta de usuario.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/userqueries?$select=name,userqueryid,&$filter=name%20eq%20'My%20User%20Query' HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Referer: https://localhost:1469/WebAPIQuery.html  
  
```  
  
 **Respuesta HTTP**  
  
```  
Pragma: no-cache  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 246  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#userqueries(name,userqueryid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621698\"",  
         "name":"My User Query",  
         "userqueryid":"7ec390ab-c943-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 Obtener el contenido de la consulta de usuario que pasa el valor GUID con el parámetro `userQuery`.  
  
 **Solicitud HTTP**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?userQuery=7ec390ab-c943-e611-80d5-00155da84802 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
  
```  
  
 **Respuesta HTTP**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 1040  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,contactid,jobtitle,annualincome,_transactioncurrencyid_value,transactioncurrencyid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621643\"",  
         "fullname":"Jim Glynn (sample)",  
         "contactid":"b955b257-c843-e611-80d5-00155da84802",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802"  
      },  
      {   
         "@odata.etag":"W/\"621629\"",  
         "fullname":"Nancy Anderson (sample)",  
         "contactid":"9d55b257-c843-e611-80d5-00155da84802",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802"  
      }  
   ]  
}  
```  
  
 **Salida de la consola**  
  
```  
-- User Query --   
Saved User Query:  
    1) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
```  
  
### <a name="see-also"></a>Vea también

[Usar la API web de Common Data Service](overview.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Recuperar y ejecutar consultas predefinidas](retrieve-and-execute-predefined-queries.md)<br />
[Ejemplo de datos de consulta API (C#)](samples/query-data-csharp.md)<br />
[Ejemplo de datos de consulta de la API web (JavaScript del lado del cliente)](samples/query-data-client-side-javascript.md)
