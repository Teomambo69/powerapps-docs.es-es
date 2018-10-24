---
title: Definición de transiciones de razón para el estado con PowerApps | Microsoft Docs
description: Aprenda cómo definir las transiciones de razón para el estado
ms.custom: ''
ms.date: 05/25/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: dbc4f436-0b23-42f9-8079-b0de482aaebe
caps.latest.revision: 11
ms.author: matp
manager: kvivek
ms.openlocfilehash: e21069a86d2ef21e8209fea6ea4a4b05e604cda4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39702822"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>Definición de transiciones de razón para el estado para entidades de caso o personalizadas

Puede especificar las transiciones de la razón para el estado para la entidad Incidente (**Caso**) o una entidad personalizada.

> [!NOTE]
> Aunque la entidad Incidente (Caso) no está incluida en un entorno predeterminado de Common Data Service para aplicaciones, la utiliza [Dynamics 365 for Customer Service](https://dynamics.microsoft.com/customer-service/) y se define en [Common Data Service](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json).
  
Las transiciones de razón para el estado son un nivel adicional opcional de filtrado para definir el valor de la razón para el estado que se puede modificar para cada razón. La definición de una lista limitada de opciones válidas puede facilitar a las personas la selección de la razón para el estado siguiente correcto para un registro cuando se tiene un gran número de combinaciones para valores de razón para el estado válidos.  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>¿Qué es la conexión entre los campos Estado y Razón para el estado?  

Las entidades que pueden tener valores de estado diferentes tienen dos campos que capturan estos datos:  
  
|Nombre para mostrar|Descripción|  
|------------------|-----------------|  
|**Status**|Representa el estado del registro. Normalmente es **Activo** o **Inactivo**. No se pueden agregar nuevas opciones de estado.|  
|**Razón para el estado**|Representa una razón que está vinculada a un estado concreto. Cada estado debe tener al menos una razón para el estado posible. Puede agregar opciones de razón para el estado adicionales.|  
  
Los metadatos para el campo definen qué valores de estado son válidos para un estado determinado. Por ejemplo, para la entidad Incidente (**Caso**), las opciones de estado y de razón para el estado predeterminadas son las siguientes:  
  
|Estado|Razón para el estado|  
|------------|-------------------|  
|**Activo**|<li>**En curso**</li><li>**En espera**</li><li>**Esperando detalles**</li><li>**Investigación**</li>| 
|**Resuelto**|<li>**Problema resuelto**</li><li>**Información proporcionada**</li>|
|**Cancelado**|<li>**Cancelado**</li><li>**Combinado**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>Edición de las transiciones de la razón para el estado
 
Puede modificar las opciones del campo de razón para el estado para que la entidad Caso y las entidades personalizadas definan qué otras opciones de razón de estado pueden elegir las personas. La única restricción es que cada opción de la razón para el estado para un estado activo debe permitir al menos una ruta de acceso a un estado inactivo. De lo contrario, podría crear una condición en la que no sería posible resolver o cancelar el caso.  

> [!NOTE]
> La modificación de las transiciones de la razón para el estado requiere el uso del explorador de soluciones. Consulte [Create and edit fields for Common Data Service for Apps using PowerApps solution explorer](create-edit-field-solution-explorer.md) (Creación y modificación de campos para Common Data Service para aplicaciones mediante el explorador de soluciones de PowerApps) para más información sobre cómo editar los campos.
  
 Cuando edite un campo de razón para el estado, el botón **Editar las transiciones de la razón para el estado** se muestra en el menú. 

![Edición del comando de transiciones de la razón para el estado](media/status-reason-transitions-command.png)

Al hacer clic en este botón, el cuadro de diálogo **Transiciones de la razón para el estado** ofrece la opción de elegir **Habilitar las transiciones de la razón para el estado**. Cuando se selecciona esta opción debe definir qué *otros* valores de la razón para el estado se permiten para cada razón. Para quitar el filtro aplicado, quite la selección **Habilitar las transiciones de la razón para el estado**. Las transiciones que ha definido se mantienen pero no se aplican.  
  
La siguiente captura de pantalla proporciona un ejemplo que cumple con los siguientes requisitos: 
 
- Un caso puede combinarse en cualquier momento. No podrá combinar casos si una transición de la razón para el estado no lo permite.  
- Un caso activo se puede cancelar en cualquier momento.  
- No se puede reactivar un caso resuelto o cancelado.  
- Todos los casos deben pasar por las siguientes fases: **En curso** > **En espera** > **Esperando detalles** > **Investigación** antes de que puedan resolverse. Con esta configuración, no se puede establecer el caso a un estado anterior.  
  > [!NOTE]
  >  Este no es un buen ejemplo para el trabajo real, pero demuestra cómo se pueden aplicar las fases del estado mediante transiciones de la razón para el estado.  
  
 ![Ejemplo de transiciones de la razón para el estado para el caso](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>Vea también  

[Create and edit fields for Common Data Service for Apps using PowerApps solution explorer](create-edit-field-solution-explorer.md) (Creación y modificación de campos para Common Data Service para aplicaciones mediante el explorador de soluciones de PowerApps)<br />
[Metadatos de entidad > Estados de entidad](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[Definir transiciones de modelo de estado personalizadas](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

