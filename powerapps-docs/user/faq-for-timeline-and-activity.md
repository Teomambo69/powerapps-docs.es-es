---
title: Preguntas frecuentes sobre las actividades y la pared de escala de tiempo | Microsoft Docs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 78b4e997a398bfb806a4e89a70c0ed3e466be381
ms.sourcegitcommit: e3d3a608ef74e1d90ca74ed38de3e5aebc624713
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75333619"
---
# <a name="frequently-asked-questions-about-activities-and-the-timeline-wall"></a>Preguntas frecuentes sobre las actividades y la pared de escala de tiempo  

## <a name="is-a-title-required-when-adding-a-new-note"></a>¿Es necesario un título al agregar una nueva nota?

Núm. Al agregar una nota a una actividad, el campo de título se marca como campo obligatorio, aunque no lo es. Se trata de un problema conocido en el cliente web heredado.

## <a name="for-an-appointment-when-i-choose-the-option-to-save-as-draft-it-doesnt-show-that-the-appointment-has-been-saved-as-a-draft"></a>En una cita, cuando elijo la opción *Guardar como borrador*, no se muestra que la cita se haya guardado como tal.

Cuando se guarda una cita como borrador en el cliente web heredado, el título no muestra **[BORRADOR]** para indicar que la cita se ha guardado como tal.

## <a name="can-i-add-activities-to-read-only-records"></a>¿Puedo agregar actividades a registros de solo lectura?

Sí. Puede agregar actividades a entidades que son de solo lectura, como notas, llamadas telefónicas, tareas, etc. 

## <a name="are-html-tags-supported-in-notes"></a>¿Se admiten etiquetas HTML en **Notas**?

Núm. Al crear una actividad de nota para cualquier registro o entidad, no se admiten etiquetas HTML. Por ejemplo, si agrega `<TAG> </TAG>` a un campo de nota, se mostrará como `<TAG_XXX="XX"> </TAG>`.

## <a name="how-can-i-improve-performance-on-timeline-wall"></a>¿Cómo puedo mejorar el rendimiento en la pared de escala de tiempo?

El rendimiento de la pared de escala de tiempo se puede mejorar mediante la optimización de la cantidad de datos que devuelve un registro de entidad específico. 

1.  Configure los formularios de entidad para mostrar solo las actividades que están en uso.  Esto se puede hacer en el nivel de formulario para mostrar únicamente las actividades útiles.  Por ejemplo, si no usa tareas para los casos, puede configurar la pared de escala de tiempo en el formulario de casos para no mostrar las tareas.
2.  Reduzca el número de registros predeterminados que se muestran en la pared de escala de tiempo.  De forma predeterminada, está establecido para devolver 10; un número más alto puede provocar problemas de rendimiento.  Se recomienda no superar el valor predeterminado. 

## <a name="activity-wall-is-not-supported-in-print-preview"></a>No se admite la pared de actividad en la vista previa de impresión.

Cuando se selecciona la opción **Vista previa de impresión** de Dynamics 365, la **pared de escala de tiempo** no se mostrará en la lista de elementos disponibles. Verá **Notas**, pero no se mostrarán las tareas ni los mensajes de correo electrónico.

## <a name="see-also"></a>Vea también

[Configurar el control de escala de tiempo](../maker/model-driven-apps/set-up-timeline-control.md)

[Preguntas más frecuentes sobre el control de escala de tiempo](../maker/model-driven-apps/faqs-timeline-control.md)

[Agregar una cita, un correo electrónico, una llamada de teléfono, una nota o una actividad de tarea a la escala de tiempo](add-activities.md)

[Sección de escala de tiempo en la aplicación del centro de atención al cliente](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)