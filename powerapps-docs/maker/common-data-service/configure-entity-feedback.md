---
title: Configurar una entidad para comentarios con PowerApps | MicrosoftDocs
description: Obtenga información sobre cómo habilitar comentarios para una entidad
ms.custom: ''
ms.date: 05/18/2018
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
ms.assetid: 5b25cf09-d43b-4165-9eaa-7549f4855e7c
caps.latest.revision: 13
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-an-entity-for-feedbackratings"></a>Configurar una entidad para comentarios/clasificación

Permita que los clientes o empleados escriban comentarios sobre cualquier registro de entidad, o califiquen registros de entidad en un rango de calificación definido habilitando entidades para comentarios.  

Esta capacidad es de uso general con un sistema que captura datos de clientes a través de un portal, o encuesta. Los datos sobre satisfacción con el servicio o el producto se pueden aplicar con entidades que representan ese tipo de datos.

La comentarios también se puede usar por empleados para proporcionar comentarios acerca de un esfuerzo colaborativo.

> [!NOTE]
> Necesitará tener el rol de seguridad de Administrador del sistema o de Personalizador del sistema o permisos equivalentes para realizar estos pasos.
  
## <a name="enable-feedback"></a>Habilitar comentarios  
  
Edite la entidad para habilitar **Comentarios**. Más información: [Editar una entidad](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>Agregar una subcuadrícula para comentarios en el formulario de entidad  

De forma predeterminada, los usuarios deben ir a la lista de registros asociados del registro al que desee agregar comentarios. Para facilitar que los usuarios agreguen comentarios, es posible que desee agregar una subcuadrícula de comentarios al formulario de la entidad para la que habilita comentarios.  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. -->
Más información:  [Información general sobre las propiedades de subcuadrícula](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>Agregar un campo consolidado al formulario de entidad para mostrar las clasificaciones  

Según cómo quiera calcular la clasificación de la entidad, puede crear un campo consolidado que calcule la clasificación y luego agregarlo al formulario de la entidad que está habilitando para comentarios. Más información: [Definir campos consolidados que agregan valores](define-rollup-fields.md)
  
### <a name="see-also"></a>Vea también  
 [Enviar comentarios o clasificaciones para registros de Dynamics 365](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
