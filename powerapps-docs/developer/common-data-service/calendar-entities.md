---
title: Entidades de calendario (Common Data Service) | Microsoft Docs
description: Lea cómo almacenar datos para los calendarios de servicio de atención al cliente y para las programaciones de vacaciones usando entidades de calendario.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 629421059fc822d9e4adc24d81f3750cec76c5fc
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2749585"
---
# <a name="calendar-entities"></a>Entidades de calendario

La entidad de calendario almacena datos para los calendarios de servicio de atención al cliente y para las programaciones de vacaciones además de para negocios. Cada calendario se establece para una zona horaria específica.  
  
 Un calendario describe la disponibilidad de un servicio o un recurso. Los calendarios están relacionados con los registros `calendarrule`, que incluyen detalles acerca de la duración, la hora de inicio y de finalización, y los patrones periódicos de los eventos incluidos en el calendario.  
  
 Existen dos tipos de reglas de calendario en Common Data Service:  
  
- **Raíz**: una regla de calendario que contiene un calendario interno o que tiene reglas (hoja) anidadas. Puede especificar un calendario interno para una regla de calendario raíz mediante el atributo `CalendarRule.InnerCalendarId`. El valor de atributo de `CalendarRule.InnerCalendarId` de una regla raíz es el mismo que el valor de atributo de `CalendarRule.CalendarId` de sus reglas hoja.  
  
- **Hoja**: una regla de calendario que no contiene un calendario interno y, por consiguiente, es el final de la "rama".  
  
 Las reglas de calendario se ordenan, o clasifican, para describir su prioridad, y las reglas se pueden solapar. La expansión de reglas anidadas define el intervalo de tiempo, o el alcance, de una regla. Puede usar el atributo `CalendarRule.ExtentCode` para definir cómo se administra la superposición de la expansión de reglas, por ejemplo, si se muestran el intervalo de tiempo y el alcance de una regla o solo se incluye uno de ellos. Estas características proporcionan a los patrones de periodicidad, por ejemplo, diferentes programaciones de turnos para los meses de invierno y de verano en un solo calendario de servicios.  
  
 Un calendario puede ser un árbol complejo de reglas y calendarios anidadas que representan una abstracción de alto nivel de la programación del trabajo. La entidad de calendario admite el mensaje <xref:Microsoft.Crm.Sdk.Messages.ExpandCalendarRequest> para convertirse en una vista básica, que es una matriz de bloques horarios que determinan la disponibilidad sobre intervalos específicos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Tipos de calendarios](types-calendars.md)  
  
 [Entidad Calendar](/reference/entities/calendar.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Entidades de cita](/dynamics365/customer-engagement/developer/appointment-entities)  
  
 [Entidades de cita periódica](/dynamics365/customer-engagement/developer/recurring-appointment-entities)  
  
 [Entidades de recursos](/dynamics365/customer-engagement/developer/resource-entities)  
  
 [Entidad Service](/dynamics365/customer-engagement/developer/service-entity)  
  
 [Código de ejemplo para las entidades de programación y cita](/dynamics365/customer-engagement/developer/sample-code-schedule-appointment-entities)