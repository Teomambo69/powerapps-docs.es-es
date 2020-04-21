---
title: Información general sobre crear relaciones entre entidades de varios a varios en Common Data Service | MicrosoftDocs
description: Aprender a crear relaciones entre entidades de varios a varios
ms.custom: ''
ms.date: 04/07/2020
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
ms.assetid: 248cecfd-c9e8-430b-b4b0-860669866084
caps.latest.revision: 33
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5f5c0f78f94ae2ec452bcbf6f5d677723d5ede52
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238302"
---
# <a name="create-many-to-many-entity-relationships-overview"></a>Crear información general de relación varios a varios entre entidades

Las relaciones entre entidades de uno a varios (1:N) establecen una jerarquía entre registros. Con relaciones de varios a varios (N:N) no existe una jerarquía explícita. No existen campos de búsqueda ni comportamientos para configurar. Los registros creados utilizando relaciones de varios a varios pueden considerarse iguales y la relación es recíproca.  

Un ejemplo de relación varios a varios se define entre dos entidades estándar incluidas con la aplicación Dynamics 365 Sales. La entidad Oportunidad también tiene una relación de N:N con la entidad Competidor. Esto permite agregar múltiples competidores a la oportunidad y múltiples oportunidades asociadas con el mismo competidor. 
  
Con relaciones de varios a varios una entidad de relaciones (o intersección) almacena los datos que asocia las entidades. Esta entidad tiene una relación entre entidades de uno a varios con las dos entidades relacionadas y almacena solo los valores necesarios para definir relación. No puede agregar campos personalizados a una entidad de relación y nunca es visible en la interfaz de usuario. 
  
Crear una relación de varios a varios requiere elegir las dos entidades que desea que participen en la relación. Para aplicaciones basadas en modelos usted puede decidir cómo desea que las listas respectivas estén disponibles en la navegación para cada entidad. Estas son las mismas opciones usadas para la entidad principal en las relaciones de entidad de 1:N. Más información: [Elemento del panel de navegación para una entidad principal](create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
No todas las entidades se pueden usar con relaciones de varios a varios. Si la entidad no está disponible para elegir en el diseñador, no puede crear una nueva relación de varios a varios con esta entidad. Más información: [Documentación para desarrolladores: Elegibilidad de relación entre entidades](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)

Hay dos diseñadores que puede usar para crear y editar relaciones de 1:N (uno a varios) o N:1 (varios a uno):

|Diseñador| Descripción|
|--|--|
|[Portal Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunos valores especiales no están disponibles.<br />Más información: [Crear relaciones varios a varios entre entidades en Common Data Service con el portal de Power Apps](create-edit-nn-relationships-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes.<br />Más información: [Crear relaciones entre entidades N:N (varios a varios) en Common Data Service mediante el explorador de soluciones](create-edit-nn-relationships-solution-explorer.md) |

> [!NOTE]
> También puede crear una nueva relación entre entidades de varios a varios (N:N) en su entorno mediante lo siguiente:
> - Importe una solución que contenga la definición de la relación. Más información: [Importar, actualizar y exportar soluciones](import-update-export-solutions.md)
> - Un programador puede usar [servicios de metadatos](../../developer/common-data-service/metadata-services.md) para escribir un programa para crear y actualizar relaciones entre entidades. Más información: [Documentación para desarrolladores: Personalizar metadatos de relaciones entre entidades](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

La información de este tema le ayudará a elegir el diseñador que puede usar. 

Debe usar el portal Power Apps para crear y editar relaciones entre entidades de varios a varios (N:N) a menos que necesite satisfacer cualquiera de los siguientes requisitos:

- Configurar opciones del panel de navegación para aplicaciones basadas en modelos
- Ocultar la relación de la Búsqueda avanzada en aplicaciones basadas en modelos.

## <a name="see-also"></a>Vea también

[Crear y editar relaciones entre entidades](create-edit-entity-relationships.md)<br />
[Crear relaciones varios a varios entre entidades en Common Data Service con el portal de Power Apps](create-edit-nn-relationships-portal.md)<br />
[Crear relaciones entre entidades N:N (varios a varios) en Common Data Service mediante el explorador de soluciones](create-edit-nn-relationships-solution-explorer.md)<br />
[Documentación para desarrolladores: Personalizar metadatos de relaciones entre entidades](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[Documentación para desarrolladores: Elegibilidad de relación entre entidades](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)
