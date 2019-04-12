---
title: Entidades de zona horaria (Common Data Service) | Microsoft Docs
description: 'Las entidades de zona horaria contienen información sobre zonas horarias, como la zona horaria soportada, el código de zona horaria, la zona horaria localizada, y almacena información sobre cómo se calculan los tiempos.'
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
# <a name="time-zone-entities"></a>Entidades de zona horaria

Las entidades de *zona horaria* se pueden usar cuando se escribe un código que funciona en varias zonas horarias. Las siguientes tres entidades de solo lectura en Common Data Service contienen información de zona horaria:  
  
- La *entidad de definición de zona horaria* almacena información básica de cada zona horaria admitida, incluidos el código de zona horaria y el nombre de zona horaria estándar.  
  
- La entidad *nombre localizado de zona horaria* almacena los nombres localizadas de zona horaria.  
  
- La entidad *regla de zona horaria* almacena información sobre cómo se calculan las horas.  
  
  La siguiente tabla muestra los mensajes relacionados con zonas horarias, pero no hace referencia a una entidad específica.  
  
|Mensaje|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.Crm.Sdk.Messages.GetTimeZoneCodeByLocalizedNameRequest>|Recupera todas las definiciones de zona horaria para la configuración regional especificada y devuelve solo el atributo del nombre para mostrar.|  
|<xref:Microsoft.Crm.Sdk.Messages.LocalTimeFromUtcTimeRequest>|Recupera la hora local de la hora UTC especificada.|  
|<xref:Microsoft.Crm.Sdk.Messages.UtcTimeFromLocalTimeRequest>|Recupera la hora UTC para la hora local especificada.|  
  
### <a name="see-also"></a>Vea también  
 [Entidades de administración de empresas](/dynamics365/customer-engagement/developer/business-management-entities)   
 [Ejemplo: Recuperar información de zona horaria](org-service/samples/retrieve-time-zone-information.md)   
 [timezonedefinition EntityType](reference/entities/timezonedefinition.md)   
 [timezonelocalizedname EntityType](reference/entities/timezonelocalizedname.md)   
 [timezonerule EntityType](reference/entities/timezonerule.md)   
 [Ejemplo: Recuperar información de zona horaria](org-service/samples/retrieve-time-zone-information.md)   
 [Entidad de divisa de transacción (divisa)](transaction-currency-currency-entity.md)
