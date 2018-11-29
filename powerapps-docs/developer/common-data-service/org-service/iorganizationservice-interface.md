---
title: Interfaz IOrganizationService (Common Data Service para aplicaciones) | Microsoft Docs
description: Obtenga más información sobre los métodos comunes expuestos para realizar operaciones de datos con CDS for Apps.
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
# <a name="iorganizationservice-interface"></a>Interfaz IOrganizationService

La interfaz <xref:Microsoft.Xrm.Sdk.IOrganizationService> proporciona un conjunto de métodos que se usan para realizar las operaciones más frecuentes en las entidades personalizadas y del sistema, y en los metadatos de la organización.

## <a name="client-applications"></a>Aplicaciones de cliente

Esta interfaz se implementa en varias clases que puede usar en su código cuando crea aplicaciones cliente.

|Clase|Descripción|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>|Ésta es la clase de bajo nivel original que usa WCF y el extremo de SOAP |
|<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>|Esta clase de bajo nivel se creó para habilitar la autenticación de OAuth al extremo de SOAP|
|<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>|Esta es la clase que debe usar al crear las aplicaciones cliente .NET. |

> [!NOTE]
> Puede encontrar códigos o ejemplos más antiguos con bajo nivel <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> o clases <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>, pero le recomendamos usar <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> para las nuevas aplicaciones cliente .NET

## <a name="plug-ins"></a>Complementos

Cuando escribe complementos, también hay un objeto devuelto de <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> que implementa la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService> pero no es ninguno de los tipos de las clases anteriores.

## <a name="iorganizationservice-methods"></a>Métodos de IOrganizationService

Cada una de las clases que implementan la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService> puede incluir propiedades adicionales y métodos, pero la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService> tiene solo 8 métodos.


|Método  |Descripción  |
|---------|---------|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*>|Vincule dos entidades mediante una relación entre entidades|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>|Cree un registro de entidad.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>|Elimine un registro de entidad|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*>|Quite el vínculo entre dos entidades mediante una relación entre entidades|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>|Invoque una operación definida como mensaje pasando una instancia de una <xref:Microsoft.Xrm.Sdk.OrganizationRequest> o una clase derivada de ella.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>|Recupere una instancia de un registro de entidad.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>|Recupere una colección de registros de entidad que cumpla con los criterios establecidos en una consulta.|
|<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>|Cambie los valores de atributo de un registro de entidad.|

> [!NOTE]
> El servicio de la organización muestre sólo el método `Execute`. Los otros métodos en la interfaz de <xref:Microsoft.Xrm.Sdk.IOrganizationService> son solo capas alrededor del método `Execute`. Estos otros métodos se proporcionan por comodidad. Puede realizar todas las operaciones con sólo el método `Execute`. Más información: [Usar mensajes con el servicio de la organización](use-messages.md)

## <a name="see-also"></a>Vea también

[Uso de mensajes con el servicio de la organización](use-messages.md)<br />
[Crear una aplicación cliente](create-client-app.md)<br />
[Escribir un complemento](../write-plug-in.md)<br />
[Operaciones de la entidad con el servicio de organización](entity-operations.md)