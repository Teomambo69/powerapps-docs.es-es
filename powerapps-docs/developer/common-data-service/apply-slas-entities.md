---
title: Aplicar SLA a entidades (Common Data Service) | Microsoft Docs
description: Obtenga información sobre cómo aplicar SLA a entidades personalizadas habilitando entidades para aplicar los SLA. También puede crear KPI de SLA.
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
# <a name="apply-slas-to-entities"></a>Aplicar SLA a entidades

Los contratos de nivel de servicio (SLA) de Common Data Service ayudan a definir el nivel de servicio o de soporte que su organización acuerda proporcionar a un cliente incluidos los elementos para definir métricas o indicadores clave de rendimiento (KPI) para lograr el nivel de servicio. Puede aplicar SLA a entidades personalizadas y las siguientes entidades del sistema:  
  
-   Todas las entidades de actividad (como Correo electrónico, Tarea, y Cita) salvo las citas periódicas (RecurringAppointmentMaster)  
  
-   Cuenta  
  
-   Contacto  
  
-   Factura  
  
-   Incidente (caso)  
  
-   Oportunidad  
  
-   Oferta  
  
-   Cliente potencial  
  
-   SalesOrder (pedido)  
  
<a name="EnableSLAs"></a> 
  
## <a name="enable-entities-for-applying-slas"></a>Habilitar entidades para aplicar SLA  

 Para aplicar SLA a una entidad, debe establecer el atributo <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsSLAEnabled> como true para la entidad. No puede cambiar este valor vez que se ha habilitado. De forma predeterminada, la entidad `Incident` está habilitada para SLA.  
  
 También puede usar la herramienta de personalización para habilitar las entidades para SLAs. Más información: [Habilitar entidades para contratos de nivel de servicio](/dynamics365/customer-engagement/customer-service/enable-entities-service-level-agreements).  
  
 Una vez habilitada una entidad para SLA, los nuevos atributos relacionados con SLA, como `SLAId` y `SLAInvokedId`, se agregarán automáticamente a la entidad.  
  
<a name="CreateSLAKPI"></a>   

## <a name="create-sla-kpis"></a>Crear KPI de SLA  

 Para crear mediante programación KPI de SLA para una entidad, cree un atributo de búsqueda en cualquier entidad habilitada para SLA y después establezca una relación para ese atributo a la entidad `SLAKPIInstance`.  
  
<a name="ApplySLA"></a>
   
## <a name="apply-slas-to-entity-records"></a>Aplicar SLAs a registros de entidad  

 Mediante el cliente web de Common Data Service puede crear SLAs para una entidad habilitada para SLA y establecer un SLA como predeterminado para la entidad para que se aplique automáticamente a los nuevos registros de entidad.  
  
 Sin embargo, si desea aplicar manualmente SLA a registros de entidad basados en cualquier requisito personalizado de negocio, puede actualizar mediante programación el registro de la entidad para establecer el valor del atributo `SLAId` con el registro de SLA activo que desee.  
  
<a name="Limitations"></a>   

## <a name="limitations-to-applying-slas-in-dynamics-365-online"></a>Limitaciones a la aplicación de SLA en Dynamics 365 (online)  

 En Common Data Service, las limitaciones siguientes son aplicables para SLAs por cada instancia de Common Data Service (organización):  
  
-   Puede tener un máximo de 7 entidades que pueden tener SLAs activos. Se mostrará un error al activar un SLA si se supera el límite.  
  
-   Puede tener un máximo de 5 KPI de SLA por cada entidad para SLAs activos. Se mostrará un error al activar un SLA si se supera el límite. Este límite no es aplicable a la entidad `Incident`.  
  
### <a name="see-also"></a>Vea también  
 [Contratos de nivel de servicio mejorados (SLA)](/dynamics365/customer-engagement/admin/enhanced-service-level-agreements)