---
title: Entidad ActivityPointer (actividad) (Common Data Service para aplicaciones) | Microsoft Docs
description: 'La entidad de puntero de actividad (actividad) representa cualquier actividad o tarea que se realiza, o que será realizada por un usuario. Una actividad es cualquier acción para la que se puede crear una entrada en un calendario.'
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
# <a name="activitypointer-activity-entity"></a>Entidad ActivityPointer (actividad)

La entidad de puntero de actividad (actividad) representa cualquier actividad o tarea que se realiza, o que será realizada por un usuario. Una actividad es cualquier acción para la que se puede crear una entrada en un calendario.  
  
 Cada vez que cree un registro de actividad en Common Data Service para aplicaciones, se crea un registro correspondiente de puntero de actividad. Esto indica que el registro de la actividad y el registro correspondiente del puntero de actividad tienen el mismo valor del atributo de `ActivityId`. Por ejemplo, si crea un registro de `Email` , los valores de atributo de `Email.ActivityId` y el correspondiente `ActivityPointer.ActivityId` serán iguales.  
  
 El atributo de `ActivityPointer.ActivityTypeCode` define el tipo de actividad. Los valores posibles para este atributo se definen en el conjunto de opciones globales de `activitypointer_activitytypecode`.  
  
<a name="bkmk_sortdate"></a>   

## <a name="control-how-activities-are-sorted-by-date"></a>Controlar cómo las actividades se ordenan por fecha  
  
 Cuando muestra una lista de entidades de actividad y las ordena por fecha, puede usar solo los atributos de fecha comunes definidos en la entidad de activitypointer. Sin embargo, algunas veces pueden convenir diferentes comportamientos de ordenación según el tipo de actividad. Por ejemplo, con la entidad de correo electrónico quizá le convenga ordenar por el valor del atributo senton en lugar del valor del atributo modifiedon.  
  
 Use el atributo sortdate para controlar cómo las actividades se ordenan por fecha. De forma predeterminada, el valor de atributo sortdate es nulo. Debe incluir lógica de negocios para rellenar el valor de fecha que se establecerá para este atributo y luego usar el atributo sortdate dentro de la consulta definida para la vista. Puede establecer el valor de atributo sortdate mediante un flujo de trabajo o un complemento. Para obtener resultados coherentes debe configurar este valor para cada tipo de actividad y los datos de actividad existentes en el sistema.  
  
### <a name="see-also"></a>Vea también  
 [Entidades de actividad](activity-entities.md)   
 [Entidad ActivityPointer](reference/entities/activitypointer.md)