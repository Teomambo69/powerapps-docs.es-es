---
title: Configuración de una entidad para comentarios con PowerApps | Microsoft Docs
description: Obtenga información sobre cómo habilitar los comentarios de una entidad.
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
- powerapps
author: Mattp123
ms.assetid: 5b25cf09-d43b-4165-9eaa-7549f4855e7c
caps.latest.revision: 13
ms.author: matp
manager: kvivek
ms.openlocfilehash: efb1cf167353d5928564b42aeb7a49f43cf272d6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39700974"
---
# <a name="configure-an-entity-for-feedbackratings"></a>Configurar una entidad para comentarios/clasificación

Permita que los clientes o empleados escriban comentarios sobre cualquier registro de entidad, o bien que califiquen registros de entidad en un rango de calificación definido habilitando entidades para comentarios.  

Esta funcionalidad se usa normalmente con un sistema que captura los datos de clientes en un portal o mediante una encuesta. Los datos sobre satisfacción con el servicio o el producto se pueden aplicar con entidades que representan ese tipo de datos.

Los empleados también pueden usar los comentarios para opinar sobre el trabajo colaborativo.

> [!NOTE]
> Necesitará tener el rol de seguridad de Administrador del sistema o de Personalizador del sistema o permisos equivalentes para realizar estos pasos.
  
## <a name="enable-feedback"></a>Habilitar comentarios  
  
Edite la entidad para habilitar **Comentarios**. Más información: [Editar una entidad](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>Agregar una subcuadrícula para comentarios en el formulario de entidad  

De forma predeterminada, los usuarios deben ir a la lista de registros asociados del registro al que desee agregar comentarios. Para facilitar que los usuarios agreguen comentarios, es posible que desee agregar una subcuadrícula de comentarios al formulario de la entidad para la que habilita los comentarios.  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. --> Más información: [Información general sobre las propiedades de subcuadrícula](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>Agregar un campo consolidado al formulario de entidad para mostrar las clasificaciones  

Según cómo quiera calcular la clasificación de la entidad, puede crear un campo consolidado que calcule la clasificación y luego agregarlo al formulario de la entidad para la que va a habilitar los comentarios. Más información: [Definir campos consolidados que agregan valores](define-rollup-fields.md)
  
### <a name="see-also"></a>Vea también  
 [Enviar comentarios o clasificaciones para registros de Dynamics 365](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
