---
title: Cómo crear y editar campos para Common Data Service| MicrosoftDocs
ms.custom: ''
ms.date: 02/08/2019
ms.reviewer: ''
ms.service: powerapps
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
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="how-to-create-and-edit-fields"></a>Cómo crear y editar campos

En Common Data Service, los campos definen los elementos de datos individuales que se pueden usar para almacenar datos en una entidad. A veces, los desarrolladores denominan *atributos* a los campos. 
  
Antes de crear un campo personalizado, evalúe si el uso de un campo existente cumple sus requisitos. Más información: [¿Crear nuevos metadatos o usar los metadatos existentes?](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Hay dos diseñadores que puede usar para crear o editar campos:

|Diseñador| Descripción|
|--|--|
|[Portal PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: [Crear y editar campos para Common Data Service mediante el portal de PowerApps](create-edit-field-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes.<br />Más información: [Crear y editar campos para Common Data Service con el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md) |

> [!NOTE]
> También puede crear campos en su entorno mediante lo siguiente:
> - En aplicaciones basadas en modelos, seleccione **Nuevo campo** del editor de formularios.
> - Importe una solución que contenga la definición de los campos.
> - Use Power Query para crear nuevas entidades y rellenarlas con datos.<br />Más información: [Agregar datos a una entidad en Common Data Service mediante Power Query.](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq).
> - Un programador puede usar [servicios de metadatos](/powerapps/developer/common-data-service/use-web-services#metadata-services) para escribir un programa para crear y actualizar campos.

La información de este tema le ayudará a elegir el diseñador que puede usar. 

Debería usar el portal de PowerApps para Crear y editar campos para Common Data Service, a menos que necesite satisfacer cualquiera de los siguientes requisitos:

- Crear un campo de búsqueda de clientes. 
   - Más información: [Diferentes tipos de búsquedas](types-of-fields.md#different-types-of-lookups)
- Crear un campo en una solución distinta de la solución predeterminada de Common Data Service. 
   - Para obtener más información: [Información general de las soluciones](solutions-overview.md)
- Definir transiciones de razón para el estado. 
   - Más información: [Definir las transiciones de razón para el caso o las entidades personalizadas](define-status-reason-transitions.md)
- Editar varios campos al mismo tiempo.
- Habilitar la auditoría. 
   - Más información: [Información general sobre auditorías](../../developer/common-data-service/auditing-overview.md)
- Habilitar perfiles de seguridad de campo. 
   - Más información: [Entidades de seguridad de campo](../../developer/common-data-service/field-security-entities.md)
- Seleccionar si el campo aparece en el filtro global en la experiencia interactiva. 
   - Más información: [Configurar paneles de experiencia interactiva de aplicaciones basadas en modelos](../model-driven-apps/configure-interactive-experience-dashboards.md)
- Seleccionar si el campo se puede ordenar en paneles de experiencia interactiva. 
   - Más información: [Configurar paneles de experiencia interactiva de aplicaciones basadas en modelos](../model-driven-apps/configure-interactive-experience-dashboards.md)
- Establecer un nivel de requisito de campo como Recomendado por la empresa. 
   - Más información: [Crear reglas de negocio y recomendaciones para aplicar lógica en un formulario de aplicaciones basadas en modelos](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
- Establecer propiedades administradas para un campo. 
   - Más información: [Establecer propiedades administradas para campos](set-managed-properties-for-field.md)

> [!NOTE]
> Puede crear un campo de búsqueda en el portal de PowerApps o en el explorador de soluciones creando una relación de uno a varios en la entidad. Pero sólo el explorador de soluciones ofrece la opción de crear esta relación cuando se crea un campo.

## <a name="community-tools"></a>Herramientas de la Comunidad

**[Administrador de atributos](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)** es una herramienta que la comunidad XrmToolbox ha desarrollada para Common Data Service. Consulte el tema [Herramientas para desarrolladores](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) para obtener información sobre herramientas desarrolladas por la comunidad.

> [!NOTE]
> Las herramientas de la comunidad no son un producto de Microsoft y no se incluyen en el soporte técnico. Si tiene alguna duda relacionada con la herramienta, póngase en contacto con el Editor. Más información: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Vea también  
[Crear y editar campos para Common Data Service utilizando el portal PowerApps](create-edit-field-portal.md)<br />
[Crear y editar campos para Common Data Service con el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md)<br />
[Tipos de campos y tipos de datos de campos](types-of-fields.md)<br />
[Documentación para desarrolladores: Trabajar con metadatos de atributo](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)
 
