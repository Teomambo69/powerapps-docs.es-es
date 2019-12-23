---
title: Entidades restringidas que requieren licencias de Dynamics 365 | Microsoft Docs
description: Una lista de entidades restringidas en Common Data Service que requieren licencias de Dynamics 365.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: reference
ms.date: 05/01/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5672922d04ae8ea4342139ef9179c7a871fd5ea6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861223"
---
# <a name="restricted-entities-requiring-dynamics-365-licenses"></a>Entidades con restricciones que requieren licencias de Dynamics 365

> [!IMPORTANT]
> Este tema está obsoleto y se actualizará pronto para reflejar los últimos cambios en licencias aplicables a partir del 1 de octubre de 2019. Para obtener la información más reciente sobre los requisitos de licencia para entidades, consulte [Manual de licencias de Power Apps](https://go.microsoft.com/fwlink/?linkid=2085130).

Los creadores de aplicaciones pueden usar la mayoría de entidades disponibles en Common Data Service para crear aplicaciones y flujos para los usuarios que solo tengan una licencia de Plan 1 de Power Apps. Sin embargo, algunas entidades contienen lógica de negocios compleja que requiere a los usuarios de la aplicación tener una licencia de Plan 2 de Power Apps o de Plan 2 de Power Automate (para obtener más información, consulte [Requisitos de licencia de entidad](data-platform-entity-licenses.md)). Un conjunto incluso inferior a entidades vinculadas a productos de Dynamics 365 requiere a los usuarios de aplicaciones de lienzo y controladas por modelos que tengan una licencia del producto de Dynamics 365 correspondiente si tienen que crear, actualizar o eliminar registros dentro de las entidades. Estas se conocen como entidades *restringidas*.

Las entidades pueden estar restringidas a una licencia de Dynamics 365 por las siguientes razones:

* La entidad se usa para almacenar y mantener los datos de configuración específicos de productos que no se suelen usar fuera de la aplicación.
* La entidad viene acompañada por una lógica avanzada que crea y mantiene los datos de una forma específica cuando se usan dentro de un producto de Dynamics 365.

Si una aplicación o un flujo lee únicamente información de una entidad, no se necesita una licencia de Dynamics 365, tan solo la licencia apropiada de Power Apps o Power Automate. 

## <a name="restricted-entities-for-create-update-and-delete-operations"></a>Entidades restringidas para operaciones de creación, actualización y eliminación
En la tabla siguiente se muestran las entidades restringidas y los requisitos de licencia de Dynamics 365 asociados para los usuarios de aplicaciones de Power Apps y Power Automate que crean, actualizan o eliminan los datos almacenados dentro de las entidades. 

|Entidad  |Nombre lógico  |Licencia necesaria  |
|---------|---------|---------|
Real |msdyn_actual |Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Proceso de negocio de acuerdo |msdyn_bpf_baa0a411a239410cb8bded8b5fdd88e3 |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Diario de reserva | msdyn_bookingjournal|Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Metadatos de la configuración de reserva | msdyn_bookingsetupmetadata|Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Marca de tiempo de reserva | msdyn_bookingtimestamp|Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Caso | incident | Dynamics 365 for Customer Service, Enterprise edition <br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Proceso de negocio de caso a orden de trabajo |msdyn_bpf_989e9b1857e24af18787d5143b67523b |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Configuración |msdyn_configuration |Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Derecho | derecho | Dynamics 365 for Customer Service, Enterprise edition <br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Línea de estimación|msdyn_estimateline|Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Estimación|msdyn_estimate |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Hecho|msdyn_fact |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Configuración de Field Service |msdyn_fieldservicesetting |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Trabajo del sistema de Field Service |msdyn_fieldservicesystemjob |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Objetivo | goal | Dynamics 365 for Sales Professional, <br>**o** Dynamics 365 for Sales, Enterprise edition, <br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Diario de inventario |msdyn_inventoryjournal |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Proceso de factura |msdyn_bpf_d8f9dc7f099f44db9d641dd81fbd470d |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Recorrido | recorrido | Dynamics 365 for Marketing <br> **o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Artículo de conocimientos | Artículo de conocimientos | Dynamics 365 for Customer Service, Enterprise edition <br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Unidad organizativa |msdyn_organizationalunit |Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Inventario de productos |msdyn_productinventory |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Parámetro de proyecto|msdyn_projectparameter |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Fases del proyecto| msdyn_bpf_665e73aa18c247d886bfc50499c73b82|Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Dependencia de tareas de proyecto|msdyn_projecttaskdependency |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Tarea de proyecto|msdyn_projecttask |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Miembro del equipo del proyecto|msdyn_projecteam |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Proceso de negocio de pedido de compra | msdyn_bpf_2c5fe86acc8b414b8322ae571000c799|Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Detalle de asignación de recursos (obsoleto)|msdyn_resourceassignmentdetail |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Asignación de recursos|msdyn_resourceassignment |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Restricción de recursos (obsoleto) |msdyn_workorderresourcerestriction | Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Conjunto de reglas de enrutamiento | routingrule | Dynamics 365 for Customer Service, Enterprise edition <br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Configuración del tablero de programación |msdyn_scheduleboardsetting |Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Parámetro de programación |msdyn_schedulingparameter |Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
SLA| sla | Dynamics 365 for Customer Service, Enterprise edition <br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Configuración del programador de usuarios del sistema |msdyn_systemuserschedulersetting|Dynamics 365 for Field Service <br> **o** Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Conexión de transacciones|msdyn_transactionconnection |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Origen de la transacción|msdyn_transactionorigin |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Tipo de transacción|msdyn_transactiontype |Dynamics 365 for Project Service Automation<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Número único|msdyn_uniquenumber |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Proceso de negocio de orden de trabajo |msdyn_bpf_d3d97bac8c294105840e99e37a9d1c39 |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365
Cola de generación de detalles de orden de trabajo (obsoleta)|msdyn_workorderdetailsgenerationqueue |Dynamics 365 for Field Service<br>**o** plan de Dynamics 365 Customer Engagement <br> **o** plan de Dynamics 365

## <a name="licensing"></a>Licencias
Para obtener más información acerca de las licencias de Power Apps y Dynamics 365, consulte la página [Información general de las licencias](../../administrator/pricing-billing-skus.md).

