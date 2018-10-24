---
title: Comportamiento y formato del campo Fecha y hora en Common Data Service para aplicaciones | Microsoft Docs
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
ms.assetid: 73d691c7-344e-4c96-8979-c661c290bf81
caps.latest.revision: 47
ms.author: matp
manager: kvivek
ms.openlocfilehash: 2f62f2433fe959e3713df544628db186b801731e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39711482"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Comportamiento y formato del campo Fecha y hora

En Common Data Service para aplicaciones, el tipo de datos de Fecha y hora se usa en muchos campos de entidad estándar. Dependiendo del tipo de fecha que el campo represente, podrá elegir diferentes comportamientos de campo: **Local del usuario**, **Fecha solo** o **Independiente de la zona horaria**.  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>Formato y comportamiento del campo Fecha y hora  

En la tabla siguiente se incluye información sobre el formato y comportamiento del campo Fecha y hora.  
  
|Comportamiento|Formato|Descripción|  
|--------------|------------|-------------------------------|  
|**Local del usuario** |**Fecha solo**<br />- o -<br />**Fecha y hora**|Este es el comportamiento predeterminado de los campos Fecha y hora personalizados.<br /><br />Los valores de campo se muestran en la hora local del usuario actual.<br />En los servicios web, estos valores se devuelven mediante un formato de zona horaria UTC común.<br /><br />Puede cambiar esto una vez si selecciona el comportamiento predeterminado. Más información [Cambiar comportamiento Local del usuario](#change-user-local-behavior)|  
|**Fecha solo**|**Fecha solo**|Ninguna conversión de zona horaria.<br /><br />La parte de la hora del valor siempre es 12:00 a.m.<br />La parte de la fecha del valor se almacena y recupera tal como se indica en la interfaz de usuario y los servicios web.|  
|**Independiente de la zona horaria**|**Fecha solo**<br />- o -<br />**Fecha y hora**|Ninguna conversión de zona horaria.<br /><br />Los valores Fecha y hora se almacenan y recuperan tal como se indica en la interfaz de usuario y los servicios web.|  

## <a name="change-user-local-behavior"></a>Cambiar comportamiento Local del usuario:

A menos que el publicador de una solución administrada lo evite, puede cambiar el comportamiento de un campo Fecha personalizado existente de **Local del usuario** a **Fecha solo** o **Independiente de la zona horaria**. Esto es un cambio único.

Cambiar el comportamiento de campo afecta a los valores de campo que se agregan o modifican una vez cambiado el comportamiento de campo. Los valores de campo existentes permanecen en la base de datos en el formato de zona horaria UTC. Para cambiar el comportamiento de los valores de campo existentes de UTC a Fecha solo, puede que necesite la ayuda de un desarrollador para hacerlo mediante programación. Más información:  [Convertir comportamiento de los valores Fecha y hora existentes en la base de datos](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database). 

> [!WARNING]
> Antes de cambiar el comportamiento de un campo Fecha y hora existente, debe revisar todas las dependencias del campo, como reglas de negocio, flujos de trabajo, campos calculados o campos consolidados, a fin de garantizar que no haya problemas como resultado del cambio del comportamiento. Tras cambiar el comportamiento de un campo Fecha y hora, debe abrir cada regla de negocio, flujo de trabajo, campo calculado y campo consolidado dependiente del campo que ha cambiado, revisar la información y guardarla, a fin de garantizar el uso del comportamiento y el valor más recientes del campo Fecha y hora. 

### <a name="change-behavior-during-a-solution-import"></a>Cambiar comportamiento durante la importación de una solución

Al importar una solución que incluye un campo Fecha mediante el comportamiento **Local del usuario**, puede que tenga la opción de cambiar el comportamiento a **Fecha solo** o **Independiente de la zona horaria**.  

### <a name="prevent-changing-behavior"></a>Evitar cambiar el comportamiento

Si distribuye un campo Fecha personalizado en una solución administrada, puede evitar que se use su solución resultante del cambio del comportamiento estableciendo la propiedad administrada **CanChangeDateTimeBehavior** en **False**. Más información: [Propiedades administradas de campo](set-managed-properties-metadata.md#field-managed-properties)
  
## <a name="use-cases"></a>Casos de uso

Tenga en cuenta los siguientes casos de uso para los comportamientos **Fecha solo** e **Independiente de la zona horaria**.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>Escenario Fecha solo: cumpleaños y aniversarios

El comportamiento Fecha solo es bueno para casos en los cuales no es necesaria la información sobre la hora del día y la zona horaria, como cumpleaños o aniversarios. Con esta selección, todos los usuarios de aplicaciones de todo el mundo ven el mismo valor de fecha exacto.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>Escenario Independiente de la zona horaria: inserción en el repositorio de un hotel

Podrá usar este comportamiento cuando la información de la zona horaria no sea necesaria, como la hora de inserción en el repositorio de un hotel. Con esta selección, todos los usuarios de aplicaciones de todo el mundo ven el mismo valor Fecha y hora.  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>Operadores de consulta Fecha y hora no compatibles con el comportamiento Fecha solo  

Los siguientes operadores de consulta relacionados con Fecha y hora no son válidos para el comportamiento **Fecha solo**. Se inicia un error de excepción de operador no válido cuando se usa en la consulta uno de estos operadores.  
  
- Antigüedad superior a X minutos  
- Antigüedad superior a X horas  
- Últimas X horas  
- Próximas X horas  

  
### <a name="see-also"></a>Vea también

[Crear y editar campos](create-edit-fields.md)<br />
[Definir campos calculados para automatizar cálculos manuales](define-calculated-fields.md)<br />
[Propiedades administradas de campo](set-managed-properties-metadata.md#field-managed-properties)<br />
[Propiedades administradas](solutions-overview.md#managed-properties)

