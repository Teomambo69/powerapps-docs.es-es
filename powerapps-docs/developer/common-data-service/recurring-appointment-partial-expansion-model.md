---
title: Modelo de expansión parcial de citas periódicas (Common Data Service) | Microsoft Docs
description: El modelo de expansión parcial es un trabajo asincrónico que se ejecuta a intervalos predefinidos y se define en el nivel de organización y se usa para crear instancias de citas recurrentes.
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
ms.openlocfilehash: 1f8db578a771cca7985a3a52110257ee35692a16
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749810"
---
# <a name="recurring-appointment-partial-expansion-model"></a>Modelo de expansión parcial de citas periódicas

Common Data Service implementa un modelo de expansión parcial para crear repeticiones de citas periódicas en la base de datos. La información de periodicidad, que se especifica al crear un registro `RecurringAppointmentMaster`, se usa para crear o sincronizar repeticiones individuales por fases. De esta forma se controla la creación de un gran número de registros de cita en Common Data Service debida a la creación o sincronización de citas periódicas que tienen un intervalo de periodicidad grande o infinito (que no tienen fecha de finalización).  

 El modelo de expansión parcial es un trabajo asincrónico en Common Data Service que se ejecuta a intervalos predefinidos y se define en el nivel de organización mediante el atributo de `Organization.RecurrenceExpansionJobBatchInterval`. Además, el modelo de expansión de repeticiones depende de un parámetro en el nivel de organización, por ejemplo, “N”, donde “N” representa el número máximo de repeticiones que se pueden crear forma sincrónica. Puede especificar un valor apropiado para esta variable mediante el atributo `Organization.RecurrenceExpansionSynchCreateMax`. Estas propiedades se describen en detalle la sección [Parámetros para el trabajo de expansión parcial](#Parameter) más adelante.  

<a name="Scenario1"></a>   
## <a name="when-the-recurring-appointment-instances-are-less-than-or-equal-to-n"></a>Cuando las repeticiones de una cita periódica son “N” o menos  
 Si el número de repeticiones que se van a generar debido a la información de periodicidad es igual o menor que “N”, se crea dicho número de repeticiones forma sincrónica a partir de la fecha de inicio efectiva de la cita. Cada repetición se almacena como un registro de cita en Common Data Service.  

<a name="Scenario2"></a>   

## <a name="when-the-recurring-appointment-instances-are-more-than-n"></a>Cuando las repeticiones de una cita periódica son más de “N”  
 Para cada cita periódica creada en Common Data Service, se crea un trabajo de expansión asincrónico. Las repeticiones de la cita periódica se expanden en las siguientes fases:  

1. **Expansión sincrónica**: las primeras “N” repeticiones de la cita periódica se crean de forma sincrónica desde la fecha de inicio efectiva. Cada repetición se almacena como un registro de cita con el atributo `Appointment.InstanceTypeCode` establecido en “2” (repetición periódica). La expansión del resto de las repeticiones se pasa a un trabajo asincrónico. La fecha de inicio efectiva es la fecha a partir de la cual se debe expandir la serie de citas periódicas.  

2. **Expansión asincrónica**: los trabajos asincrónicos controlan el resto del trabajo de expansión y expanden periódicamente las repeticiones según la información de periodicidad. La expansión asincrónica se produce solo hasta la siguiente ventana de expansión (`Organization.FutureExpansionWindow`). Después de ella, se crea un nuevo trabajo asincrónico que controla la expansión hasta la siguiente ventana de expansión futura. El servicio asincrónico expande periódicamente las repeticiones y las almacena como registros de cita en el sistema.  

<a name="Parameter"></a>   
## <a name="parameters-for-the-partial-expansion-job"></a>Parámetros del trabajo de expansión parcial  
 Debe establecer los valores adecuados para estos atributos en el nivel de la organización en el registro `Organization` para que el modelo de expansión funcione según los requisitos establecidos. Para ello, debe tener el rol Administrador del sistema o los privilegios adecuados. La siguiente tabla proporciona información sobre estas propiedades.  


|                    Atributo                     |                                                                                                                                                                                                                    Descripción                                                                                                                                                                                                                    |
|--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Organization.RecurrenceExpansionSynchCreateMax  |                                                                                             Este es el número máximo de repeticiones de citas que se crea en el momento de la creación o sincronización de una cita periódica. Debe especificar un valor entero correspondiente al número de repeticiones. Este valor corresponde a “N”.                                                                                              |
|         Organization.PastExpansionWindow         |    Este es el máximo período de tiempo válido en el pasado hasta el que las citas periódicas se pueden expandir o sincronizar con Dynamics 365 for Outlook. Debe especificar un valor entero correspondiente al número de meses.<br /><br /> El valor de este atributo determina la fecha límite de las repeticiones pasadas para expandir o sincronizar las repeticiones de la cita periódica.    |
|        Organization.FutureExpansionWindow        | Este es el máximo período de tiempo válido en el futuro hasta el que las citas periódicas se pueden expandir o sincronizar con Dynamics 365 for Outlook. Debe especificar un valor entero correspondiente al número de meses.<br /><br /> El valor de este atributo determina la fecha límite de las repeticiones futuras para expandir o sincronizar las repeticiones de la cita periódica. |
| Organization.RecurrenceExpansionJobBatchInterval |                                                                                                                                                                               Esta es la frecuencia en segundos después de la cual se desencadena el trabajo de expansión parcial.                                                                                                                                                                                |
|   Organization.RecurrenceExpansionJobBatchSize   |                                                                                                                                                                                  Este es el número de repeticiones expandidas cada vez que se ejecuta el trabajo asincrónico.                                                                                                                                                                                   |

### <a name="see-also"></a>Vea también  
 [Entidades de cita periódica](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [Crear una instancia, excepción o serie de cita periódica](create-recurring-appointment-series-instance-exception.md)   
 [Eliminar o finalizar una instancia o serie de cita periódica](/dynamics365/customer-engagement/developer/delete-or-end-a-recurring-appointment-series-or-instance)   
 [Actualizar una cita periódica](update-recurring-appointment.md)
