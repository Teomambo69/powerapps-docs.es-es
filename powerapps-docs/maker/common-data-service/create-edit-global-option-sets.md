---
title: Creación y edición de conjuntos de opciones globales (listas desplegables) para Common Data Service | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: f06b8941-8dca-4601-b965-341cfb6fc3b2
caps.latest.revision: 11
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-edit-global-option-sets-overview"></a>Información general para crear y editar conjuntos de opciones globales 

Un conjunto de opciones (lista desplegable) es un tipo de campo que se puede incluir en una entidad. Define un conjunto de opciones. Cuando un conjunto de opciones se muestra en un formulario usa un control de lista desplegable. Cuando se muestra en **Búsqueda avanzada**, se usa un control de *lista desplegable*. A veces, los desarrolladores llaman a los conjuntos de opciones listas desplegables.  
  
Puede definir un conjunto de opciones para usar un conjunto de opciones definido en sí mismo (localmente) o puede usar un conjunto de opciones definido en otra parte (globalmente) que se pueda usar en otros campos del conjunto de opciones. 

Los conjuntos de opciones globales son útiles cuando existe un conjunto estándar de categorías que se pueden aplicar a más de un campo. Mantener dos conjuntos de opciones independientes con los mismos valores es difícil y si no se sincronizan pueden aparecer errores, especialmente si está asignando campos de la entidad con una relación de entidad de uno a varios. Más información: [Asignación de campos de entidad](map-entity-fields.md)

> [!NOTE]
> Si define cada conjunto de opciones como conjunto de opciones global, la lista de conjuntos de opciones globales crecerá y puede resultar difícil de administrar. Si sabe que el conjunto de opciones solo se usará en un lugar, use un conjunto de opciones local.

Hay dos diseñadores que puede usar para crear o editar conjuntos de opciones globales:

|Diseñador| Descripción|
|--|--|
|[Portal PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: [Crear un conjunto de opciones](custom-picklists.md) |
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes. <br />Más información: [Creación y edición de conjuntos de opciones globales para Common Data Service utilizando el explorador de soluciones](create-edit-global-option-sets-solution-explorer.md) |

> [!NOTE]
> También puede crear conjuntos de opciones globales en su entorno mediante lo siguiente:
> - Importe una solución que contenga la definición de los conjuntos de opciones globales.
> - Un desarrollador puede escribir un programa para crearlas. <br />Más información: [Documentación de desarrollador: Personalizar conjuntos de opciones globales](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets).

La información de este tema le ayudará a elegir el diseñador que puede usar. 

Debe usar el [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) para trabajar con conjuntos de opciones globales a menos que necesite satisfacer cualquiera de los siguientes requisitos:

- Asignar colores a opciones
- Cambiar el orden de las opciones
- Creación de un conjunto de opciones global en una solución distinta de la solución predeterminada de Common Data Service
- Establecer propiedades administradas
- Establezca propiedades usadas para entidades virtuales
- Ver dependencias

## <a name="see-also"></a>Vea también

[Crear un conjunto de opciones](custom-picklists.md)<br />
[Creación y edición de conjuntos de opciones globales para Common Data Service utilizando el explorador de soluciones](create-edit-global-option-sets-solution-explorer.md)<br />
[Documentación para desarrolladores: Personalizar conjuntos de opciones globales](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
  

 
