---
title: Usar acciones de API web (Common Data Service) | Microsoft Docs
descriptions: Actions are reusable operations that can be performed using the Web API. These are used with a POST request to modify data on Common Data Service
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 53eafd67-385a-485b-9022-5127df08ea2f
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-web-api-actions"></a>Usar acciones de la API web

Las acciones y funciones representan operaciones reutilizables que puede realizar mediante la API web. Use una solicitud POST con las acciones que aparecen en <xref:Microsoft.Dynamics.CRM.ActionIndex> para realizar operaciones que tienen efectos secundarios. También puede definir acciones personalizadas y estarán disponibles para uso.

<a name="bkmk_unboundActions"></a>

## <a name="unbound-actions"></a>Acciones sin enlazar

Las acciones se definen en [Documento de metadatos CSDL](web-api-types-operations.md#bkmk_csdl). Por ejemplo, lo siguiente es la definición de la <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" /> representada en el documento de metadatos.

```xml
<Action Name="WinOpportunity">
  <Parameter Name="OpportunityClose" Type="mscrm.opportunityclose" Nullable="false" />
  <Parameter Name="Status" Type="Edm.Int32" Nullable="false" />
</Action>
```

La <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" /> corresponde a <xref:Microsoft.Crm.Sdk.Messages.WinOpportunityRequest> utilizando el servicio de organización. Use esta acción para establecer el estado de una oportunidad como Ganada y crear un <xref href="Microsoft.Dynamics.CRM.opportunityclose?text=opportunityclose EntityType" /> para registrar el evento. Esta acción no incluye un valor de devolución. Si tiene éxito, la operación está completa.

El parámetro `OpportunityClose` requiere una representación de JSON de la entidad opportunityclose para crear en la operación. Esta entidad debe estar relacionada con la oportunidad que se deriva de la propiedad de navegación de un solo valor opportunityid. En el JSON, esto se establece mediante la anotación `@odata.bind`, como se explica en [Asociar entidades en la creación](create-entity-web-api.md#bkmk_associateOnCreate).

El parámetro `Status` debe establecerse en el estado de la oportunidad en el momento en que se cerró. Puede encontrar el valor predeterminado para esto en la propiedad statuscode de <xref href="Microsoft.Dynamics.CRM.opportunity?text=opportunity EntityType" />. La opción **Ganado** tiene un valor de 3. Puede preguntarse por qué es necesario configurar este valor si solo hay una opción de razón para el estado que representa **Ganado**. La razón es que puede definir opciones de estado personalizadas para representar un logro, como **Gran logro** o **Pequeño logro**,por lo que el valor potencialmente podría ser distinto de 3 en esa situación.

El siguiente ejemplo es la solicitud y la respuesta HTTP para llamar a la acción `WinOpportunity` para una oportunidad con un valor opportunityid de `b3828ac8-917a-e511-80d2-00155d2a68d2`.

 **Solicitud**

```http
POST [Organization URI]/api/data/v9.0/WinOpportunity HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "Status": 3,
 "OpportunityClose": {
  "subject": "Won Opportunity",
  "opportunityid@odata.bind": "[Organization URI]/api/data/v9.0/opportunities(b3828ac8-917a-e511-80d2-00155d2a68d2)"
 }
}

```

 **Respuesta**

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
```

<a name="bkmk_boundActions"></a>

## <a name="bound-actions"></a>Acciones enlazadas

En el [Documento de metadatos CSDL](web-api-types-operations.md#bkmk_csdl), cuando un elemento `Action` representa una acción enlazada, tiene un atributo `IsBound` con el valor `true`. El primer elemento `Parameter` definido en la acción representa la entidad a la que está enlazada la operación. Cuando el atributo `Type` del parámetro es una colección, la operación está enlazada a una colección de entidades. Por ejemplo, lo siguiente es la definición de la <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> representada en CSDL:

```xml
 <ComplexType Name="AddToQueueResponse">
 <Property Name="QueueItemId" Type="Edm.Guid" Nullable="false" />
 </ComplexType>
 <Action Name="AddToQueue" IsBound="true">
  <Parameter Name="entity" Type="mscrm.queue" Nullable="false" />
  <Parameter Name="Target" Type="mscrm.crmbaseentity" Nullable="false" />
  <Parameter Name="SourceQueue" Type="mscrm.queue" />
  <Parameter Name="QueueItemProperties" Type="mscrm.queueitem" />
  <ReturnType Type="mscrm.AddToQueueResponse" Nullable="false" />
</Action>
```

Esta acción enlazada es equivalente a la <xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest> usada por el servicio de organización. En API web esta acción está enlazada a <xref href="Microsoft.Dynamics.CRM.queue?text=queue EntityType" />, que representa a la propiedad <xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest>.<xref:Microsoft.Crm.Sdk.Messages.AddToQueueRequest.DestinationQueueId> . Esta acción acepta varios parámetros adicionales y devuelve un <xref href="Microsoft.Dynamics.CRM.AddToQueueResponse?text=AddToQueueResponse ComplexType" /> correspondiente a la <xref:Microsoft.Crm.Sdk.Messages.AddToQueueResponse> devuelta por el servicio de organización. Cuando una acción devuelve un tipo complejo, la definición del tipo complejo aparecerá directamente sobre la acción en el CSDL.

Una acción enlazada debe llamarse mediante un URI para establecer el primer valor de parámetro. No puede establecerlo como un valor de parámetro con nombre.

Cuando invoca una función enlazada, debe incluir el nombre completo de la función incluido el espacio de nombres `Microsoft.Dynamics.CRM`. Si no incluye el nombre completo, obtendrá el siguiente error: Status Code:400 Request message has unresolved parameters.

El siguiente ejemplo muestra el uso de la <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> para agregar una carta a una cola. Dado que el tipo de tipo de parámetro `Target` no es específico (`mscrm.crmbaseentity`), debe declarar explícitamente el tipo de objeto usando el valor de propiedad `@odata.type` del nombre completo de la entidad, incluido el espacio de nombres de `Microsoft.Dynamics.CRM`. En este caso, `Microsoft.Dynamics.CRM.letter`. Más información:[Especificar tipo de parámetro de la entidad](#bkmk_specifyentityparametertype)

 **Solicitud**

```http
POST [Organization URI]/api/data/v9.0/queues(56ae8258-4878-e511-80d4-00155d2a68d1)/Microsoft.Dynamics.CRM.AddToQueue HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "Target": {
  "activityid": "59ae8258-4878-e511-80d4-00155d2a68d1",
  "@odata.type": "Microsoft.Dynamics.CRM.letter"
 }
}
```

 **Respuesta**

```http

HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.AddToQueueResponse",
 "QueueItemId": "5aae8258-4878-e511-80d4-00155d2a68d1"
}
```

<a name="bkmk_customActions"></a>

## <a name="use-a-custom-action"></a>Utilizar una acción personalizada

<!-- TODO: 
If you define custom actions for your organization or solution these will also be included in the [CSDL metadata document](web-api-types-operations.md#bkmk_csdl). For information about creating actions using the customization tools in the application, see the TechNet topic [Actions](/dynamics365/customer-engagement/customize/actions). For information about creating and using your own custom actions, see [Create your own actions](../create-own-actions.md). -->

Independientemente de si las operaciones incluidas en la acción personalizada tienen efectos secundarios, potencialmente pueden modificar datos y, por tanto, se consideran acciones en lugar de funciones. No hay forma de crear una función personalizada.

### <a name="custom-action-example-add-a-note-to-a-contact"></a>Ejemplo de acción personalizada: Agregar una nota a un contacto

 Digamos que desea crear una acción personalizada que agregue una nueva nota a un contacto específico. Puede crear una acción personalizada enlazada a la entidad de contacto con las siguientes propiedades.

|UI Label|valor|
|--------------|-----------|
|**Nombre del proceso**|AddNoteToContact|
|**Nombre único**|new_AddNoteToContact|
|**Entidad**|Contacto|
|**Categoría**|Acción|

 **Argumentos de procesos**

|Nombre|Tipo|Requerido|Dirección|
|----------|----------|--------------|---------------|
|NoteTitle|Cadena|Requerido|Entrada|
|NoteText|Cadena|Requerido|Entrada|
|NoteReference|EntityReference|Requerido|Salida|

 **Pasos**

|Nombre|Tipo de paso|Descripción|
|----------|---------------|-----------------|
|Crear la nota|Crear registro|Title = {NoteTitle(Arguments)}<br /> Note Body = {NoteText(Arguments)}<br /> Regarding = {Contact{Contact}}|
|Devuelve una referencia a la nota|Asignar valor|NoteReference Value = {Note(Create the note (Note))}|

 Tras publicar y activar la acción personalizada, cuando descargue el CSDL encontrará esta nueva acción especificada.

```xml

<Action Name="new_AddNoteToContact" IsBound="true">
  <Parameter Name="entity" Type="mscrm.contact" Nullable="false" />
  <Parameter Name="NoteTitle" Type="Edm.String" Nullable="false" Unicode="false" />
  <Parameter Name="NoteText" Type="Edm.String" Nullable="false" Unicode="false" />
  <ReturnType Type="mscrm.annotation" Nullable="false" />
</Action>

```

La solicitud y respuesta HTTP siguientes muestran cómo llamar a la acción personalizada y la respuesta que devuelve si es correcta.  

 **Solicitud**

```http
POST [Organization URI]/api/data/v9.0/contacts(94d8c461-a27a-e511-80d2-00155d2a68d2)/Microsoft.Dynamics.CRM.new_AddNoteToContact HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0

{
 "NoteTitle": "New Note Title",
 "NoteText": "This is the text of the note"
}
```


 **Respuesta**

```http

HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#annotations/$entity",
 "annotationid": "9ad8c461-a27a-e511-80d2-00155d2a68d2"
}
```

<a name="bkmk_specifyentityparametertype"></a>

## <a name="specify-entity-parameter-type"></a>Especificar tipo de parámetro de la entidad

Cuando una acción requiere una entidad como parámetro y el tipo de entidad es ambiguo, debe usar la propiedad `@odata.type` para especificar el tipo de entidad. El valor de esta propiedad es el nombre completo de la entidad, que sigue este patrón: `Microsoft.Dynamics.CRM.`+*\<nombre lógico de la entidad>*.

Como se muestra en la sección [Acciones enlazadas](#bkmk_boundActions) arriba, el parámetro `Target` con la <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> es una actividad. Pero dado que todas las actividades se heredan del <xref href="Microsoft.Dynamics.CRM.activitypointer?text=activitypointer EntityType" />, debe incluir la propiedad siguiente en la entidad JSON para especificar que el tipo de entidad es una carta: `"@odata.type": "Microsoft.Dynamics.CRM.letter"`.

Otros dos ejemplos son <xref href="Microsoft.Dynamics.CRM.AddMembersTeam?text=AddMembersTeam Action" /> y <xref href="Microsoft.Dynamics.CRM.RemoveMembersTeam?text=RemoveMembersTeam Action" /> porque el parámetro `Members` es una colección de <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /> que hereda su clave principal `ownerid` del <xref href="Microsoft.Dynamics.CRM.principal?text=principal EntityType" />. Si pasa el JSON siguiente para representar un solo systemuser en la colección, está claro que la entidad es un systemuser y no un <xref href="Microsoft.Dynamics.CRM.team?text=team EntityType" />, que también se hereda del entitytype principal.

```json
{
 "Members": [{
  "@odata.type": "Microsoft.Dynamics.CRM.systemuser",
  "ownerid": "5dbf5efc-4507-e611-80de-5065f38a7b01"
 }]
}
```

Si no especifica el tipo de entidad en esta situación, puede obtener el siguiente error: `"EdmEntityObject passed should have the key property value set."`.

### <a name="see-also"></a>Vea también

[Ejemplo de funciones y acciones de la API web (C#)](samples/functions-actions-csharp.md)<br />
[Ejemplo de funciones y acciones de la API web (JavaScript del lado del cliente)](samples/functions-actions-client-side-javascript.md)<br />
[Realizar operaciones mediante la API web](perform-operations-web-api.md)<br />
[Componer solicitudes HTTP y administrar errores](compose-http-requests-handle-errors.md)<br />
[Consultar datos utilizando la API web](query-data-web-api.md)<br />
[Cree una entidad usando API web](create-entity-web-api.md)<br />
[Recuperar una entidad usando API web](retrieve-entity-using-web-api.md)<br />
[Actualizar y eliminar entidades mediante la API web](update-delete-entities-using-web-api.md)<br />
[Asociar y anular la asociación de entidades mediante la API web](associate-disassociate-entities-using-web-api.md)<br />
[Usar funciones de la API web](use-web-api-functions.md)<br />
[Ejecute las operaciones por lotes mediante API web](execute-batch-operations-using-web-api.md)<br />
[Suplantar a otro usuario utilizando la API web](impersonate-another-user-web-api.md)<br />
[Realizar operaciones condicionales mediante la API web](perform-conditional-operations-using-web-api.md)<br />
