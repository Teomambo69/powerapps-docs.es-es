---
title: Tipos de calendario (Common Data Service) | Microsoft Docs
description: ''
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
---
# <a name="types-of-calendars"></a>Tipos de calendarios

La entidad de calendario se ha modificado para ayudar a tipos adicionales de calendarios en Common Data Service.  
  
## <a name="calendar-type"></a>Tipo de calendario  
 El atributo de lista desplegable de `Type` contiene las siguientes opciones:  
  
|Valor|Etiqueta|Descripción|  
|-----------|-----------|-----------------|  
|0|Predeterminado|Todos los calendarios que no son servicio de atención al cliente, programación de vacaciones o calendarios internos.|  
|1|Servicio al cliente|Calendarios de servicio para servicio de atención al cliente|  
|2|Programación de vacaciones|Calendarios de programación de vacaciones para servicio de atención al cliente.|  
|-1|Tipo de calendario interno|Los calendarios internos los usan otros calendarios para crear un gráfico de los intervalos de tiempo disponibles para servicio de atención al cliente o la programación de servicios que se deben realizar.|  
  
### <a name="customer-service-calendars"></a>Calendarios de servicio de atención al cliente  
 Los calendarios de servicio al cliente existen para calcular rendimiento en comparación con los contratos de nivel de servicio (SLAs). Los SLAs con frecuencia se basan en los indicadores clave de rendimiento (KPIs) en función del tiempo, como duración para la primera respuesta o un límite de tiempo antes de elevación de caso. Cuando estos plazos están limitados a los períodos en que las operaciones de servicio de atención al cliente están abiertos, los cálculos para forzar estos contratos deben incluir datos del calendario de servicio al cliente.  
  
 Los calendarios de servicio al cliente definen programaciones semanales habituales. Los eventos que no corresponden a esas programaciones regulares suelen ser vacaciones. Un calendario de servicio al cliente puede estar asociado a una programación de vacaciones para proporcionar una descripción completa de las horas en que los servicio de atención al cliente están disponibles.  
  
### <a name="service-scheduling-calendars"></a>Calendarios de programación de servicios  
 La programación de servicios usa el tipo de calendario predeterminado. Los calendarios de cierre de la empresa se pueden definir y compartir en entidades de servicio y recurso. El motor de programación se asegura de que todas las reglas adecuadas del calendario se tienen en cuenta para una solicitud de la cita.  
  
 Además de periodos de tiempo libre/ocupado, puede definir las restricciones de esfuerzo (requerido/disponible) de la entidad de `CalendarRule`. Estas restricciones se definen como el esfuerzo disponible desde un recurso para realizar, entregar o repetir un servicio específico en un momento determinado. De forma similar, cada servicio define el esfuerzo que se requiere del grupo de recursos necesario para completar una unidad de servicio para la duración especificada. El motor de programación calcula automáticamente los bloques de tiempo apropiados para una cita cuando el esfuerzo total que se necesita para un servicio dado es igual o menor que el esfuerzo disponible total para todos los recursos necesarios.  
  
### <a name="see-also"></a>Vea también  
 [Entidades de calendario](calendar-entities.md)   
 [Entidad Calendar](reference/entities/calendar.md)   
 <xref:Microsoft.Dynamics.CRM.calendarrule>