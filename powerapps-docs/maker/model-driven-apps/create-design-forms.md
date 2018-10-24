---
title: Creación y diseño de los formularios de una aplicación controlada por modelos | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: 99c795e0-9165-4112-85b1-6b5e1a4aa5ec
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags:
- Links to topic not migrated
ms.openlocfilehash: ed51d04919c6316c827b0286eefaaccdf539c6ef
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39712634"
---
# <a name="create-and-design-model-driven-app-forms"></a>Creación y diseño de los formularios de una aplicación controlada por modelos 

Con PowerApps, los formularios brindan la interfaz de usuario que se usa para interactuar con los datos necesarios para trabajar. Es importante que los formularios que se usan estén diseñados para permitir encontrar o escribir la información que se necesita de manera eficaz. 

En la solución predeterminada o en una solución no administrada, puede crear formularios nuevos o editar formularios existentes para todas las entidades que permiten personalizar los formularios. En una solución no administrada, puede editar las propiedades administradas para una entidad personalizada no administrada que se creó para la solución.
Si está viendo una solución administrada, no puede crear formularios nuevos ni editar formularios existentes para las entidades. Sin embargo, si las propiedades administradas de una entidad en la solución administrada está establecidas para permitir la personalización, puede agregar o editar formularios para esa entidad. 
  

<a name="BKMK_TypesOfForms"></a> 
## <a name="type-of-forms"></a>Tipo de formularios
Hay diferentes tipos de formularios y cada tipo tiene una funcionalidad o un uso específicos. Más información: [Tipo de formularios en PowerApps](types-forms.md).  

  
<a name="BKMK_FormDifferencesByEntity"></a>   
## <a name="updated-versus-classic-entities"></a>Entidades actualizadas frente a entidades clásicas  
PowerApps proporciona muchas opciones para diseñar formularios. Con Interfaz unificada, se actualizó la mayoría de las entidades para adaptarse mejor a la interfaz dinámica. Las entidades actualizadas, al igual que sus propias entidades personalizadas, incluyen compatibilidad con el cliente Dynamics 365 para tabletas, los flujos de proceso de negocio y las reglas de negocio. Cuando use estas entidades, podrá diseñar una vez e implementar en todos los clientes.  
  
Todavía hay un número de entidades, a las que aquí se hace referencia como entidades clásicas, que conservan la apariencia y las funcionalidades de versiones anteriores. Estas entidades se usan con menos frecuencia. Son las siguientes:  
  
||||||  
|-|-|-|-|-|  
|Dirección|Artículo|Comentario de artículo|Operación de eliminación masiva|Conexión|  
|Descuento|Lista de descuentos|Ubicación del documento|Datos adjuntos de correo electrónico|Seguir|  
|Objetivo|Métrica del objetivo|Archivo de origen de importación|Producto de la factura|Producto del pedido|  
|Lista de precios|Elemento de cola|Producto de la cotización|Campo consolidado|Consulta de consolidación|  
|Vista guardada|Servicio|Actividad de servicio|Sitio de SharePoint|Sitio|  
|Territory|Unidad|Unidad de venta|||  
  
### <a name="related-topics"></a>Temas relacionados  
    
[Asignar orden de formulario](assign-form-order.md) <br />
[Controlar el acceso a los formularios](control-access-forms.md) <br />
[Cómo se presentan los formularios de aplicaciones en los distintos dispositivos](main-form-presentations.md) <br />
