---
title: 'Información general sobre crear relaciones entre entidades de 1:N (uno a varios) o N:1 (varios a uno) en PowerApps | MicrosoftDocs'
description: Aprender a crear relaciones entre entidades de uno a varios o varios a uno
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 52c00707-b2bc-4950-abec-89baefd94f6e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-one-to-many-or-many-to-one-entity-relationships-overview"></a>Información general sobre crear relaciones entre entidades de uno a varios o varios a uno

En Common Data Service, las relaciones de 1:N (uno a varios) o N:1 (varios a uno) definen cómo se relacionan dos entidades entre sí. 
  
Antes de crear una relación entre entidades personalizada, evalúe si el uso de una relación entre entidades existente cumple sus requisitos. <br />Más información: [¿Crear nuevos metadatos o usar los metadatos existentes?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Hay dos diseñadores que puede usar para crear y editar relaciones de 1:N (uno a varios) o N:1 (varios a uno):

|Diseñador| Descripción|
|--|--|
|[Portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: [Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) en el portal de PowerApps](create-edit-1n-relationships-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes. <br />Más información: [Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md) |

> [!NOTE]
> También puede crear una nueva relación entre entidades en su entorno mediante lo siguiente:
> - En aplicaciones basadas en modelos, seleccione **Nuevo campo** del editor de formularios y cree un campo *Búsqueda*. <br />Más información: [Agregar un campo a un formulario](../model-driven-apps/add-field-form.md)
> - Crear un nuevo campo de búsqueda para la entidad relacionada. <br />Más información: [Crear y editar campos](create-edit-fields.md)
> - Importe una solución que contenga la definición de la relación entre entidades. <br />Más información: [Importar, actualizar y exportar soluciones](import-update-export-solutions.md)
> - Use Power Query para crear nuevas entidades y rellenarlas con datos. <br />Más información: [Agregar datos a una entidad en Common Data Service mediante Power Query](data-platform-cds-newentity-pq.md).
> - Un programador puede usar [servicios de metadatos](../../developer/common-data-service/metadata-services.md) para escribir un programa para crear y actualizar relaciones entre entidades. <br />Más información: [Personalizar metadatos de relaciones entre entidades](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

La información de este tema le ayudará a elegir el diseñador que puede usar. 

Debe usar el portal PowerApps para crear y editar relaciones entre entidades de 1:N (uno a varios) o N:1 (varios a uno) a menos que necesite satisfacer cualquiera de los siguientes requisitos:

- Configurar asignaciones de campos
- Configurar opciones del panel de navegación para aplicaciones basadas en modelos
- Configurar comportamientos de relaciones
- Definir si la relación está oculta en búsqueda avanzada.
- Crear una relación jerárquica


## <a name="community-tools"></a>Herramientas de la Comunidad

**[Creador de diagramas de relaciones entre entidades](https://www.xrmtoolbox.com/plugins/JourneyIntoCRM.XrmToolbox.ERDPlugin/)** es una herramienta que la comunidad XrmToolbox desarrolló para Common Data Service. Consulte el tema [Herramientas para desarrolladores de Common Data Service](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) para consultar más herramientas desarrolladas por la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Vea también

[Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) en el portal de PowerApps](create-edit-1n-relationships-portal.md)<br />
[Creación y edición de relaciones entre entidades 1:N (uno a varios) o N:1 (varios a uno) con el explorador de soluciones](create-edit-1n-relationships-solution-explorer.md)<br />
[Documentación para desarrolladores: Personalizar metadatos de relaciones entre entidades](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[Documentación para desarrolladores: Elegibilidad de relación entre entidades](/dynamics365/customer-engagement/developer/entity-relationship-eligibility)


