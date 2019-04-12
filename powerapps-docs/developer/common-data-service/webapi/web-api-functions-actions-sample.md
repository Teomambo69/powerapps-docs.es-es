---
title: Ejemplo de funciones y acciones de API web (Common Data Service) | Microsoft Docs
description: 'Este grupo de ejemplos demuestra cómo realizar funciones y acciones enlazadas y sin enlazar, incluidas las acciones personalizadas, mediante la API web de Common Data Service. Estos están implementados mediante JavaScript del lado cliente y C#'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 953c3137-6171-4e6e-b249-6a96221c6e96
caps.latest.revision: 16
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-functions-and-actions-sample"></a>Ejemplo de funciones y acciones de la API web

Este grupo de ejemplos demuestra cómo realizar funciones y acciones enlazadas y sin enlazar, incluidas las acciones personalizadas, mediante la API web de Common Data Service. Este ejemplo se implementa como proyecto independiente para los siguientes idiomas:  
  
-   [Ejemplo de funciones y acciones de la API web (C#)](samples/functions-actions-csharp.md)  
  
En este tema se explican la estructura y el contenido del ejemplo en un nivel superior de lenguaje neutro. Revise los temas de ejemplo vinculados anteriores para detalles de implementación específicos del idioma sobre cómo realizar las operaciones descritas en este tema.  
  
<a name="bkmk_demonstrates"></a>  
 
## <a name="demonstrates"></a>Demostraciones  

Este ejemplo se divide en las siguientes secciones principales, que contienen operaciones de funciones y acciones de la API web que se describen minuciosamente en los temas conceptuales asociados.  
  
|Sección del tema|Temas asociados|  
|-------------------|---------------------------|  
|[Datos de ejemplo](#bkmk_sampleData)||  
|[Uso de la función sin enlazar sin parámetros](#bkmk_unboundFunctionNoParams)|[Funciones sin enlazar](use-web-api-functions.md#bkmk_unboundFunctions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" />|  
|[Uso de la función sin enlazar con parámetros](#bkmk_unboundFunctionWithParams)|[Funciones sin enlazar](use-web-api-functions.md#bkmk_unboundFunctions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedName?text=GetTimeZoneCodeByLocalizedName Function" />|  
|[Uso de la función enlazada sin parámetros](#bkmk_boundFunctionWithParams)|[Funciones enlazadas](use-web-api-functions.md#bkmk_boundFunctions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" />|  
|[Uso de la acción sin enlazar con parámetros](#bkmk_unboundActionWithParams)|[Acciones sin enlazar](use-web-api-actions.md#bkmk_unboundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.opportunity?text=opportunity EntityType" />|  
|[Uso de la acción enlazada con parámetros](#bkmk_boundActionWithParams)|[Acciones enlazadas](use-web-api-actions.md#bkmk_boundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.letter?text=letter EntityType" />|  
|[Uso de acción personalizada enlazada con parámetros](#bkmk_boundCustomActionWithParams)|[Utilizar una acción personalizada](use-web-api-actions.md#bkmk_customActions)<br /><br /> [Acciones enlazadas](use-web-api-actions.md#bkmk_boundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />|  
|[Uso de la acción personalizada sin enlazar con parámetros](#bkmk_unboundCustomActionWithParams)|[Utilizar una acción personalizada](use-web-api-actions.md#bkmk_customActions)<br /><br /> [Acciones sin enlazar](use-web-api-actions.md#bkmk_unboundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />|  
|[Administrar excepciones de la acción personalizada](#bkmk_boundCustomActionErrorHandling)|[Utilizar una acción personalizada](use-web-api-actions.md#bkmk_customActions)<br /><br /> [Acciones sin enlazar](use-web-api-actions.md#bkmk_unboundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />|  
  
Las siguientes secciones contienen una breve explicación de las operaciones de la API web de Common Data Service realizadas, junto con mensajes HTTP correspondientes y la salida asociada de la consola.  
  
<a name="bkmk_sampleData"></a>
   
## <a name="sample-data"></a>Datos de ejemplo  

Para garantizar que las operaciones de este ejemplo funcionan correctamente, primero creamos datos de ejemplo en el servidor de Common Data Service. Estos datos de ejemplo se eliminarán del servidor a menos que el usuario elija no eliminarlos. Los datos de este ejemplo se crean individualmente de la siguiente forma.  
  
- Cree una cuenta (por ejemplo: `Fourth Coffee`) y asóciela con un incidente que tiene tres tareas de 30 minutos (90 minutos en total). Tras crear las tareas, se marcan como completadas. La operación calculará el tiempo total que se tardó en completar estas tres tareas.  
  
    ```json  
    {  
      title: "Sample Case",  
      "customerid_account@odata.bind": accountUri,  
      Incident_Tasks: [  
       {  
        subject: "Task 1",  
        actualdurationminutes: 30  
       },  
       {  
        subject: "Task 2",  
        actualdurationminutes: 30  
       },  
       {  
        subject: "Task 3",  
        actualdurationminutes: 30  
       }  
      ]  
     };  
    ```  
  
- Cree una cuenta y asóciela con una oportunidad. Esta oportunidad se marcará como ganada en la operación de ejemplo.  
  
    ```json  
    {  
     name: "Sample Account for WebAPIFunctionsAndActions sample",  
     opportunity_customer_accounts: [{  
      name: "Opportunity to win"  
     }]  
    };  
    ```  
  
- Cree una actividad de carta. La letra se agregará a la cola del usuario actual en la operación de ejemplo.  
  
    ```json  
    {  
      description: "Example letter"  
    }  
    ```  
  
- Cree un contacto para usar con una acción personalizada `sample_AddNoteToContact` en la operación de ejemplo.  
  
    ```json  
    {  
      firstname: "Jon",  
      lastname: "Fogg"  
    }  
    ```  
  
<a name="bkmk_sampleOperations"></a>
   
## <a name="sample-operations"></a>Operaciones de ejemplo  

Las operaciones de ejemplo de este tema se organizan de las siguientes formas.  
  
- Trabajar con funciones: Estas operaciones muestran funciones enlazadas y sin enlazar que aceptan parámetros o no.  
- Trabajar con acciones: Estas operaciones muestran acciones enlazadas y sin enlazar que aceptan parámetros o no.  
- Acciones personalizadas: Estas operaciones muestran acciones enlazadas y sin enlazar y cómo administrar excepciones de errores personalizados.  
  
<a name="bkmk_workingWithFunctions"></a> 
  
## <a name="working-with-functions"></a>Trabajar con funciones  

[Funciones](web-api-types-operations.md#bkmk_functions) son operaciones que no tienen efectos secundarios. Una función se puede vincular a una instancia de entidad o una colección de entidades. Las funciones de consulta nunca están enlazadas. Para obtener más información, consulte [Utilizar funciones de la API web](use-web-api-functions.md). En esta sección se muestran ejemplos de cómo se usan funciones enlazadas y sin enlazar y de cómo se pasan parámetros.  
  
<a name="bkmk_unboundFunctionNoParams"></a>  
 
### <a name="using-unbound-function-with-no-parameters"></a>Uso de la función sin enlazar sin parámetros 
 
Use una función sin enlazar para recuperar el nombre completo del usuario actual haciendo uso de la <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" />. Esta operación demuestra cómo llamar a una función sin enlazar que no acepta parámetros. Esta operación devuelve el nombre completo del usuario actual.  
  
Obtener la solicitud y respuesta para la <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" />.  
  
 **Solicitud**  
  
```http  
GET http://[Organization URI]/api/data/v9.0/WhoAmI HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8   
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 273  
  
{  
   "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.WhoAmIResponse",  
   "BusinessUnitId":"0d6cc84a-d3f6-e511-80d0-00155da84802",  
   "UserId":"b08dc84a-d3f6-e511-80d0-00155da84802",  
   "OrganizationId":"0f47eae2-a906-4ae4-9215-f09875979f6a"  
}  
```  
  
<a name="bkmk_unboundFunctionWithParams"></a>
   
### <a name="using-unbound-function-with-parameters"></a>Uso de la función sin enlazar con parámetros  

Use una función sin enlazar para recuperar el código de la zona horaria. Esta operación demuestra cómo llamar a una función sin enlazar que acepta parámetros. Esta operación devuelve el código de la zona de hora actual de la zona horaria especificada. Más información:[Paso de parámetros a una función](use-web-api-functions.md#bkmk_passParametersToFunctions)  
  
 **Solicitud**  
  
```http  
GET http://[Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName=@p1,LocaleId=@p2)?@p1='Pacific%20Standard%20Time'&@p2=1033 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8 
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 154  
  
{  
   "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedNameResponse",  
   "TimeZoneCode":4  
}  
```  
  
 **Salida de la consola**  
  
```  
Unbound function: GetTimeZoneCodeByLocalizedName  
    Function returned time zone Pacific Standard Time, with code '4'.  
```  
  
<a name="bkmk_boundFunctionWithParams"></a>
   
### <a name="using-bound-function-with-no-parameters"></a>Uso de la función enlazada sin parámetros  

Use una función enlazada para recuperar el tiempo total que tardaron en completarse todas las tareas de un incidente. Esta operación demuestra cómo llamar a una función enlazada que no acepta parámetros. Esta operación devuelve los minutos totales que el incidente tardó en cerrar todas sus tareas. Esta función también usa los datos de incidentes que creamos para este programa de ejemplo. Más información:[Funciones enlazadas](use-web-api-functions.md#bkmk_boundFunctions).  
  
 **Solicitud**  
  
```http  
GET http://[Organization URI]/api/data/v9.0/incidents(3d920da5-fb4a-e611-80d5-00155da84802)/Microsoft.Dynamics.CRM.CalculateTotalTimeIncident() HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 148  
  
{  
   "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse",  
   "TotalTime":90  
}  
```  
  
 **Salida de la consola**  
  
```  
Bound function: CalculateTotalTimeIncident  
    Function returned 90 minutes - total duration of tasks associated with the incident.  
```  
  
<a name="bkmk_workingWithActions"></a> 
  
## <a name="working-with-actions"></a>Trabajar con acciones  

[Acciones](web-api-types-operations.md#bkmk_actions) son operaciones que permiten efectos secundarios. Una acción es enlazada o sin enlazar. Para obtener más información, consulte [Utilizar acciones de la API web](use-web-api-actions.md). En esta sección se muestran ejemplos de cómo se usan acciones enlazadas y sin enlazar y de cómo se pasan parámetros. También se muestra cómo se usan las acciones personalizadas y cómo administrar excepciones de estas acciones personalizadas.  
  
<a name="bkmk_unboundActionWithParams"></a>
   
### <a name="using-unbound-action-with-parameters"></a>Uso de la acción sin enlazar con parámetros 
 
Use una acción sin enlazar que tome un conjunto de parámetros. Esta operación cierra una oportunidad y la marca como ganada llamando a la <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" />. El <xref href="Microsoft.Dynamics.CRM.opportunity?text=opportunity EntityType" /> fue creado como datos de ejemplo anteriormente en el programa. Más información:[Acciones sin enlazar](use-web-api-actions.md#bkmk_unboundActions).  
  
 **Solicitud**  
  
```http  
POST http://[Organization URI]/api/data/v9.0/WinOpportunity HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
  
{  
   "Status":3,  
   "OpportunityClose":{  
      "subject":"Won Opportunity",  
      "opportunityid@odata.bind":"http://[Organization URI]/api/data/v9.0/opportunities(47920da5-fb4a-e611-80d5-00155da84802)"  
   }  
}  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 204 No Content  
OData-Version: 4.0   
```  
  
 **Salida de la consola**  
  
```  
Unbound Action: WinOpportunity  
    Opportunity won.  
```  
  
<a name="bkmk_boundActionWithParams"></a>
   
### <a name="using-bound-action-with-parameters"></a>Uso de la acción enlazada con parámetros
  
Use una acción enlazada que tome parámetros. Esta operación agrega una carta a la cola del usuario actual. Para lograrlo, usamos la <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> y el <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /> para obtener una referencia a la cola del usuario actual.  También es necesario hacer referencia al <xref href="Microsoft.Dynamics.CRM.letter?text=letter EntityType" />. Esta carta fue creada como datos de ejemplo anteriormente en el programa. A continuación se llama a la <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> enlazada para agregar la carta a la cola del usuario actual. Más información:[Acciones enlazadas](use-web-api-actions.md#bkmk_boundActions).  
  
 **Solicitud**  
  
```http  
POST http://[Organization URI]/api/data/v9.0/queues(1f7bcc50-d3f6-e511-80d0-00155da84802)/Microsoft.Dynamics.CRM.AddToQueue HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 110  
  
{  
   "Target":{  
      "activityid":"4c920da5-fb4a-e611-80d5-00155da84802",  
      "@odata.type":"Microsoft.Dynamics.CRM.letter"  
   }  
}  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 170  
  
{  
   "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.AddToQueueResponse",  
   "QueueItemId":"67bdfabd-fc4a-e611-80d5-00155da84802"  
}  
```  
  
 **Salida de la consola**  
  
```  
Bound Action: AddToQueue  
    QueueItemId returned from AddToQueue Action: 67bdfabd-fc4a-e611-80d5-00155da84802  
```  
  
<a name="bkmk_customActions"></a> 
  
## <a name="working-with-custom-actions"></a>Trabajar con acciones personalizadas  

Si define las acciones personalizadas para la solución, puede llamarlas mediante la API web de Common Data Service. Independientemente de si las operaciones incluidas en la acción personalizada tienen efectos secundarios, potencialmente pueden modificar datos y, por tanto, se consideran acciones en lugar de funciones. No hay forma de crear una función personalizada. Más información:[Usar una acción personalizada](use-web-api-actions.md#bkmk_customActions).  
  
Este ejemplo se suministra con dos acciones personalizadas. Ambas requieren parámetros pero una está enlazada y la otra sin enlazar.  
  
- `sample_AddNoteToContact`: Una acción personalizada enlazada que toma dos parámetros. Una es una `NoteTitle` y la otra es una `NoteText`. Esta acción personalizada agrega una nota a un <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />. A continuación se proporciona una captura de pantalla de la página **Información** para esta acción personalizada.  
  
 <!-- TODO:
 ![Custom Action &#45; AddNoteToContact information](../media/custom-action-add-note-contact.PNG "Custom Action - AddNoteToContact information")   -->
  
- `sample_CreateCustomer`: Una acción personalizada no enlazada que requiere diferentes parámetros según el tipo de cliente que se esté creando. Por ejemplo, cuando el `AccountType` es ”cuenta” requiere sólo el parámetro `AccountName`. Cuando la `AccountType` es “contacto”, son necesarios parámetros `ContactFirstName` y `ContactLastName`. A continuación se proporciona una captura de pantalla de la página **Información** para esta acción personalizada.  
<!-- TODO:  
 ![Custom Action &#45; CreateCustomer information](../media/custom-action-create-customer.PNG "Custom Action - CreateCustomer information")  
   -->
<a name="bkmk_boundCustomActionWithParams"></a>
   
### <a name="using-bound-custom-action-with-parameters"></a>Uso de la acción personalizada enlazada con parámetros 
 
Este ejemplo llama a la acción personalizada `sample_AddNoteToContact` que está enlazada a la entidad de contacto con los parámetros requeridos. Esta acción personalizada agrega una nota a un contacto existente. Esta acción devuelve una entidad con una propiedad `annotationid`. Para mostrar que la nota se agregó, se usa la `annotationid` para pedir información acerca de la nota.  
  
La solicitud y respuesta de la acción.  
  
 **Solicitud**  
  
```http  
POST http://[Organization URI]/api/data/v9.0/contacts(4d920da5-fb4a-e611-80d5-00155da84802)/Microsoft.Dynamics.CRM.sample_AddNoteToContact HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 80  
  
{  
   "NoteTitle":"The Title of the Note",  
   "NoteText":"The text content of the note."  
}  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 149  
  
{  
   "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#annotations/$entity",  
   "annotationid":"ba146d0b-fd4a-e611-80d5-00155da84802"  
}  
```  
  
 La solicitud y respuesta de la anotación.  
  
 **Solicitud**  
  
```http  
GET http://[Organization URI]/api/data/v9.0/annotations(ba146d0b-fd4a-e611-80d5-00155da84802)?$select=subject,notetext&$expand=objectid_contact($select=fullname) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 200 OK  
OData-Version: 4.0  
Content-Length: 450  
  
{  
   "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#annotations(subject,notetext,objectid_contact,objectid_contact(fullname))/$entity",  
   "@odata.etag":"W/\"622978\"",  
   "subject":"The Title of the Note",  
   "notetext":"The text content of the note.",  
   "annotationid":"ba146d0b-fd4a-e611-80d5-00155da84802",  
   "objectid_contact":{  
      "@odata.etag":"W/\"622968\"",  
      "fullname":"Jon Fogg",  
      "contactid":"4d920da5-fb4a-e611-80d5-00155da84802"  
   }  
}  
```  
  
 **Salida de la consola**  
  
```http  
Custom action: sample_AddNoteToContact  
    A note with the title 'The Title of the Note' and the content 'The text content of the note.' was created and associated with the contact Jon Fogg.  
```  
  
<a name="bkmk_unboundCustomActionWithParams"></a> 
  
### <a name="using-unbound-custom-action-with-parameters"></a>Uso de la acción personalizada sin enlazar con parámetros  

Esta operación llama a la acción personalizada `sample_CreateCustomer` para crear un cliente de ”cuenta”. Los parámetros obligatorios se pasan para un `CustomerType` de `account`.  
  
 **Solicitud**  
  
```http  
POST http://[Organization URI]/api/data/v9.0/sample_CreateCustomer HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 103  
  
{  
   "CustomerType":"account",  
   "AccountName":"Account Customer Created in WebAPIFunctionsAndActions sample"  
}  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
<a name="bkmk_boundCustomActionErrorHandling"></a> 
  
### <a name="handling-custom-action-exceptions"></a>Administrar excepciones de la acción personalizada  

Este ejemplo muestra que las acciones personalizadas pueden devolver mensajes de error personalizados. También controla excepciones personalizadas del mismo modo que controla excepciones estándar. Para enviar el mensaje de error personalizado desde la acción personalizada `sample_CreateCustomer`, este ejemplo crea un cliente de ”contacto”. Sin embargo, pasamos de forma intencionada los parámetros incorrectos para este parámetro `CustomerType`. Esta operación a continuación recoge la excepción y muestra el mensaje de error, y luego continúa con el programa de ejemplo.  
  
 **Solicitud**  
  
```http  
POST http://[Organization URI]/api/data/v9.0/sample_CreateCustomer HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 103  
  
{  
   "CustomerType":"contact",  
   "AccountName":"Account Customer Created in WebAPIFunctionsAndActions sample"  
}  
```  
  
 **Respuesta**  
  
```http  
HTTP/1.1 500 Internal Server Error  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 2760  
  
{  
   "error":{  
      "code":"",  
      "message":"ContactFirstName and ContactLastName are required when CustomerType is contact.",  
      "innererror":{  
         "message":"ContactFirstName and ContactLastName are required when CustomerType is contact.",  
         ...[truncated]  
      }  
   }  
}  
```  
  
 **Salida de la consola**  
  
```  
Expected custom error: ContactFirstName and ContactLastName are required when CustomerType is contact.  
```  
  
### <a name="see-also"></a>Vea también  

[Utilizar API Web de Common Data Service](overview.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Usar acciones de la API web](use-web-api-actions.md)<br />
[Ejemplo de funciones y acciones de la API web (C#)](samples/functions-actions-csharp.md)<br />

