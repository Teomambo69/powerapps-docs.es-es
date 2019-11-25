---
title: Definir transiciones de razón para el estado con PowerApps | MicrosoftDocs
description: Aprender a definir transiciones de razón para el estado
ms.custom: ''
ms.date: 05/25/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9fb1fc93b5559c47cebeef4fb73ebd095a48f0a5
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705599"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>Definir las transiciones de razón para el estado de la entidad Caso o de entidades personalizadas

Puede especificar las transiciones de razón para el estado de la entidad Incidente (**Caso**) o de entidad personalizada.

> [!NOTE]
> Aunque la entidad de incidente (caso) no se incluye en un entorno predeterminado de Common Data Service, se usa en [Dynamics 365 for Customer Service](https://dynamics.microsoft.com/customer-service/) y se define dentro del [Modelo común de datos](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json)
  
Las transiciones de razón para el estado son un nivel de filtrado adicional y opcional para definir qué valor puede cambiarse para cada razón para el estado. Definir una lista limitada de opciones válidas puede facilitar a los usuarios la selección de la siguiente razón para el estado de un registro cuando tiene un gran número de combinaciones para valores válidos de razón para el estado.  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>¿Cuál es la conexión entre los campos Estado y Razón para el estado?  

Entidades que pueden tener diferentes valores de estado tienen dos campos que capturan estos datos:  
  
|Nombre para mostrar|Descripción|  
|------------------|-----------------|  
|**Estado**|Representa el estado del registro. Normalmente **Activo** o **Inactivo**. No puede agregar nuevas opciones de estado.|  
|**Razón para el estado**|Representa una razón que está vinculada a un estado específico. Cada estado debe tener al menos una razón para el estado posible. Puede agregar opciones adicionales de razón para el estado.|  
  
Los metadatos para el campo definen qué valores de estado son válidos para un estado determinado. Por ejemplo, para la entidad Incidente (**Caso**), el estado predeterminado y las opciones de razón para el estado son:  
  
|Estado|Razón para el estado|  
|------------|-------------------|  
|**Activo**|<li>**En curso**</li><li>**Retenido**</li><li>**Esperando detalles**</li><li>**Investigación**</li>| 
|**Resuelto**|<li>**Problema resuelto**</li><li>**Información proporcionada**</li>|
|**Cancelado**|<li>**Cancelado**</li><li>**Combinado**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>Edite transiciones de razón para el estado
 
Puede modificar las opciones de campo de razón para el estado para que las entidades de entidad de caso y personalizadas definan qué otras opciones de razón para el estado pueden elegir. La única restricción es que cada opción de razón para el estado de un estado activo debe permitir al menos una ruta a un estado inactivo. Si no, podría crear una condición donde no sería posible resolver ni cancelar el caso.  

> [!NOTE]
> Editar las transiciones de razón para el estado requiere el uso del explorador de soluciones. Consulte [Crear y editar campos para Common Data Service usando el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md) para obtener información sobre cómo editar campos.
  
 Cuando edita un campo de razón para el estado, el botón **Editar las transiciones de la razón para el estado** está en el menú. 

![Comando Editar transiciones de razón para el estado](media/status-reason-transitions-command.png)

Al hacer clic en este botón, el cuadro de diálogo **Transiciones de la razón para el estado** proporciona la opción de elegir **Habilitar las transiciones de la razón para el estado**. Cuando esta opción está seleccionada debe definir qué *otros* valores de razón para el estado que se permiten para cada razón para el estado. Para quitar el filtrado aplicado, quite la selección **Habilitar las transiciones de la razón para el estado**. Las transiciones que ha definido se conservarán, pero no se aplicarán.  
  
La captura de pantalla a continuación proporciona un ejemplo que cumple los siguientes requisitos: 
 
- Un caso se puede combinar en cualquier momento. No podrá combinar casos si una transición de razón para el estado no lo permite.  
- Un caso activo se puede cancelar en cualquier momento.  
- Un caso resuelto o cancelado no se puede reactivar.  
- Todos los casos deben pasar a través de las siguientes fases: **En curso** > **En espera** > **Esperando detalles** > **Bajo investigación** antes de que se puedan resolver. Con esta configuración, un caso no se pudo establecer en un estado anterior.  
  > [!NOTE]
  >  Esto no es un buen ejemplo para el trabajo real, pero demuestra cómo las fases de estado se pueden aplicar a través de transiciones de razón para el estado.  
  
 ![Ejemplo de transiciones de razón para el estado de un caso](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>Vea también  

[Crear y editar campos para Common Data Service con el explorador de soluciones de PowerApps](create-edit-field-solution-explorer.md)<br />
[Metadatos de entidad > Estados de entidad](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[Definir transiciones de modelo de estado personalizadas](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

