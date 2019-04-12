---
title: 'Entidades de cliente (cuenta, contacto) (Common Data Service) | Microsoft Docs'
description: 'Las entidades Account y Contact en Dynamics 365 son esenciales para identificar y administrar clientes, vender productos y servicios, y proporcionar un mejor servicio a los clientes. Se usa una entidad de dirección de cliente para almacenar la dirección y la información de envío para un cliente.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="customer-entities-account-contact"></a>Entidades de cliente (cuenta, contacto)

<!-- 
Was Mike Carter

https://docs.microsoft.com/dynamics365/customer-engagement/developer/customer-entities-account-contact

Refactor so that the links to entity reference are in the body, not just in the See allso.
Add some h2 sections so it is skimmable
 -->

Las entidades *cuenta* y *contacto* en Common Data Service son esenciales para identificar y administrar clientes, vender los productos y servicios, y proporcionar un servicio superior a los clientes. Se usa una entidad de *dirección de cliente* para almacenar la dirección y la información de envío para un cliente.  
  
## <a name="account-entity"></a>Entidad de cuenta
 
La entidad de cuenta es una de las entidades de las aplicaciones Common Data Service a la que más se asocian otras entidades. En Common Data Service, una cuenta representa una compañía con la que la unidad de negocio tiene una relación. La información incluida en una cuenta es toda la información de contacto, información de la compañía, categoría, tipo de relación e información de dirección pertinentes. Otra información pertinente incluye los siguientes elementos:  
  
- Una cuenta puede ser un elemento primario de prácticamente cualquier otra entidad. Esto incluye otra cuenta.  
  
- Una cuenta puede ser una entidad independiente.  
  
- Una cuenta puede tener únicamente una cuenta como elemento primario.  
  
- Las cuentas pueden tener varias cuentas y contactos secundarios.  
  
La administración de cuentas es uno de los conceptos importantes de administración de relaciones con el cliente interempresarial (Dynamics 365) porque una organización desea ver todas las actividades que tienen con otra compañía. Todas estas actividades vienen juntas en el nivel de cuenta.  

Más información: [Entidad de cuenta](reference/entities/account.md).
  
## <a name="contact-entity"></a>Entidad de contacto

En Common Data Service, un contacto representa una persona, normalmente un individuo, con el que una unidad de negocio tiene una relación, como un cliente, un proveedor o un compañero. La entidad contacto es una de las entidades a la que se vinculan la mayoría de las otras entidades. Un contacto puede ser una entidad independiente. En esta entidad se incluyen información profesional, personal y familiar, y varias direcciones. Más información: [Entidad Contacto](reference/entities/contact.md).
  
Tanto cuentas como contactos se consideran parte de la administración de clientes y se relacionan unos con otros de las siguientes formas:  
  
- Un contacto puede ser un elemento primario para otra entidad excepto cuentas y contactos.  
  
- Un contacto puede tener únicamente una cuenta como elemento primario.  
  
- Un contacto se puede marcar como persona de contacto principal de una cuenta con el método de <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>.  
  
La entidad de contacto almacena toda la información acerca de una persona, como la dirección de correo electrónico, la dirección postal, los números de teléfono y otra información relacionada, como el cumpleaños o la fecha de aniversario. Según el tipo de clientes que tiene una unidad de negocio, se necesitan solo los contactos, o contactos y cuentas, para ofrecer una vista completa de los clientes.  
  
Las operaciones básicas que puede realizar en un contacto incluyen crear, leer, actualizar y eliminar.  
  
Vincular entidades como actividades y notas a la entidad de contacto permite al usuario ver todas las comunicaciones que el usuario ha tenido con un cliente, las acciones que el usuario ha realizado en nombre del cliente y toda la información que el usuario necesita sobre el cliente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Entidad Account](reference/entities/account.md)  
  
 [Entidad Contact](reference/entities/contact.md)  
  
 [Entidad CustomerAddress](reference/entities/customeraddress.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Modelar los datos profesionales con Dynamics 365](/dynamics365/customer-engagement/developer/model-business-data)  
  
 [Entidades de administración de negocios](/dynamics365/customer-engagement/developer/business-management-entities)
