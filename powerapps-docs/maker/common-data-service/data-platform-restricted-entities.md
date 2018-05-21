---
title: Entidades restringidas que requieren licencias de Dynamics 365 | Microsoft Docs
description: Una lista de entidades restringidas en Common Data Service (CDS) for Apps que requieren licencias de Dynamics 365.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 05/01/2018
ms.author: clwesene
ms.openlocfilehash: 79b6e386154b15ae6c625afbebbed18a8a86c420
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2018
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Entidades restringidas que requieren licencias de Dynamics 365
Los creadores de aplicaciones pueden usar la mayoría de las entidades disponibles en Common Data Service (CDS) for Apps para crear aplicaciones y los flujos para los usuarios que solo tienen una licencia del Plan 1 de PowerApps. Pero algunas entidades contienen lógica de negocios compleja que requiere que los usuarios de la aplicación tengan una licencia del Plan 2 de PowerApps o Plan 2 de Flow (para obtener más información, vea [Entity license requirements](data-platform-entity-licenses.md) [Requisitos de licencia de entidades]). Un conjunto incluso más pequeño de entidades asociado a los productos de Dynamics 365 requiere que los usuarios de aplicaciones de lienzo y controladas por modelos tengan una licencia para el producto de Dynamics 365 correspondiente si tienen que crear, actualizar o eliminar registros dentro de las entidades. Estas se conocen como entidades *restringidas*.

Las entidades pueden estar restringidas a una licencia de Dynamics 365 por las razones siguientes:

* La entidad se usa para almacenar y mantener datos de configuración específicos de cada producto que normalmente no se usan fuera de la aplicación.
* La entidad está acompañada por lógica avanzada que crea y mantiene los datos de una manera específica cuando se usa dentro de un producto de Dynamics 365.

Si una aplicación o flujo solo lee la información de una entidad, no se requiere una licencia de Dynamics 365 y todo lo que se necesita es una licencia correspondiente de PowerApps o Microsoft Flow. 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>Entidades restringidas para crear, actualizar y eliminar operaciones
En la tabla siguiente se enumeran las entidades restringidas y los requisitos de licencia de Dynamics 365 asociados para los usuarios de aplicaciones de PowerApps y Microsoft Flow que crean, actualizan o eliminan los datos almacenados en las entidades. 

|Entidad  |Nombre lógico  |Licencia necesaria  |
|---------|---------|---------|
Real |msdyn_actual |Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Proceso de negocio de acuerdo |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Diario de reservas | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Metadatos de la configuración de reservas | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Marca de tiempo de reserva | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Proceso empresarial de caso de orden de trabajo |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Configuración |msdyn_configuration |Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Derecho | entitlement | Dynamics 365 for Customer Service, edición Enterprise <br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Línea de estimación|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Estimación|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Hechos|msdyn_fact |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Configuración de servicio de campo |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Trabajo del sistema de servicio de campo |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Objetivo | goal | Dynamics 365 for Sales Professional, <br>**o bien** Dynamics 365 for Sales, edición Enterprise, <br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Incidente | incident | Dynamics 365 for Customer Service, edición Enterprise <br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Diario de inventario |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Proceso de factura |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Recorrido | journey | Dynamics 365 for Marketing <br> **o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Artículo de conocimientos | knowledgearticle | Dynamics 365 for Customer Service, edición Enterprise <br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Unidad organizativa |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Inventario de productos |msdyn_productinventory |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Parámetro de proyecto|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Fases del proyecto| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Dependencia de la tarea de proyecto|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Tarea del proyecto|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Miembro del equipo de proyecto|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Proceso empresarial de pedido de compra | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Detalles de asignación de recursos (en desuso)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Asignación de recursos|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Restricción de recursos (en desuso) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Conjunto de reglas de enrutamiento | routingrule | Dynamics 365 for Customer Service, edición Enterprise <br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Configuración de tablero de programación |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Parámetro de programación |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Contrato de nivel de servicio| sla | Dynamics 365 for Customer Service, edición Enterprise <br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Configuración del programador de usuario del sistema |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **o bien** Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Conexión de transacción|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Origen de la transacción|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Tipo de transacción|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Número único|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Proceso empresarial de orden de trabajo |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365
Cola de generación de detalles de orden de trabajo (en desuso)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**o bien** plan de Dynamics 365 Customer Engagement <br> **o bien** plan de Dynamics 365

## <a name="licensing"></a>Licencias
Para obtener más información sobre las licencias de PowerApps y Dynamics 365, vea la página [Introducción a las licencias](../../administrator/pricing-billing-skus.md).

