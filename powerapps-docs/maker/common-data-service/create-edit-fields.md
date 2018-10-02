---
title: Cómo crear y editar campos para Common Data Service para aplicaciones | MicrosoftDocs
ms.custom: ''
ms.date: 05/18/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: d88677fa-2caf-47b0-aec6-10a25a7ec9c3
caps.latest.revision: 55
ms.author: matp
manager: brycho
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="how-to-create-and-edit-fields"></a>Cómo crear y editar campos

En Common Data Service para aplicaciones, los campos definen los elementos de datos individuales que se pueden usar para almacenar datos en una entidad. A veces, los desarrolladores denominan *atributos* a los campos. 
  
Antes de crear un campo personalizado, evalúe si el uso de un campo existente cumple sus requisitos. Más información: [¿Crear nuevos metadatos o usar los metadatos existentes?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Hay dos diseñadores que puede usar para crear o editar campos:

|Diseñador| Descripción|
|--|--|
|[Portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: [Crear y editar campos para Common Data Service para aplicaciones mediante el portal de PowerApps](create-edit-field-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes.<br />Más información: [Crear y editar campos para Common Data Service para aplicaciones mediante el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md) |

> [!NOTE]
> También puede crear campos en su entorno mediante lo siguiente:
> - En aplicaciones basadas en modelos, seleccione **Nuevo campo** del editor de formularios.
> - Importe una solución que contenga la definición de los campos.
> - Use Power Query para crear nuevas entidades y rellenarlas con datos.<br />Más información: [Agregar datos a una entidad en Common Data Service mediante Power Query](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Un programador puede usar [servicios de metadatos](/powerapps/developer/common-data-service/use-web-services#metadata-services) para escribir un programa para crear y actualizar campos.

La información de este tema le ayudará a elegir el diseñador que puede usar. 

Debe usar el portal PowerApps para crear y editar campos para Common Data Service para aplicaciones a menos que necesite satisfacer cualquiera de los siguientes requisitos:

- Crear un campo de búsqueda de clientes
- Crear un campo en una solución distinta de la solución predeterminada de CDS
- Definir transiciones de razón para el estado
- Editar varios campos al mismo tiempo
- Habilitar auditoría
- Habilitar perfiles de seguridad de campo
- Seleccionar si el campo aparece en el filtro global en la experiencia interactiva
- Seleccionar si el campo se puede ordenar en paneles de experiencia interactiva
- Establecer un nivel de requisito de campo como Recomendado por la empresa
- Establecer propiedades administradas para un campo

> [!NOTE]
> Puede crear un campo de búsqueda en el portal PowerApps o en el explorador de soluciones creando una relación de uno a varios en la entidad. Pero sólo el explorador de soluciones ofrece la opción de crear esta relación cuando se crea un campo.

## <a name="community-tools"></a>Herramientas de la Comunidad

**[Administrador de atributos](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)** es una herramienta que la comunidad XrmToolbox ha desarrollada para CDS para aplicaciones. Consulte el tema [Herramientas para desarrolladores](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) para obtener información sobre herramientas desarrolladas por la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Vea también  
[Crear y editar campos para Common Data Service para aplicaciones mediante el portal de PowerApps](create-edit-field-portal.md)<br />
[Crear y editar campos para Common Data Service para aplicaciones mediante el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md)<br />
[Tipos de campos y tipos de datos de campos](types-of-fields.md)<br />
[Documentación para desarrolladores: Trabajar con metadatos de atributo](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)
 
