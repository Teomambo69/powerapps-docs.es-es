---
title: Comportamiento y formato del campo Fecha y hora en Common Data Service para aplicaciones | MicrosoftDocs
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Comportamiento y formato del campo de fecha y hora

En Common Data Service para aplicaciones, el tipo de datos de fecha y hora se utiliza en muchos campos de entidad estándar. Dependiendo del tipo de fecha que represente el campo, puede elegir distintos comportamientos del campo: **Local de usuario**, **Solo fecha** o **Independiente de zona horaria**.  
  
<a name="Behavior"></a>   

## <a name="date-and-time-field-behavior-and-format"></a>Comportamiento y formato de campos de fecha y hora  

La siguiente tabla contiene información sobre el comportamiento y el formato de los campos de fecha y hora.  
  
|Comportamiento|Formato|Descripción|  
|--------------|------------|-------------------------------|  
|**Local del usuario** |**Solo fecha**<br />- o bien -<br />**Fecha y hora**|Éste es el comportamiento predeterminado de los campos personalizados de fecha y hora.<br /><br />Los valores de campo se muestran en la hora local del usuario actual.<br />En servicios web, estos valores se devuelven utilizando un formato de zona horaria UTC común.<br /><br />Puede cambiar esto una vez si selecciona el comportamiento predeterminado. Más información [Cambiar comportamiento Local del usuario](#change-user-local-behavior)|  
|**Solo fecha**|**Solo fecha**|Sin conversión de zona horaria.<br /><br />La parte de hora del valor siempre es 12:00AM.<br />La parte de fecha del valor se almacena y se recupera como se especifica en la interfaz de usuario y los servicios web.|  
|**Independiente de la zona horaria**|**Solo fecha**<br />- o bien -<br />**Fecha y hora**|Sin conversión de zona horaria.<br /><br />Los valores de fecha y hora se almacenan y se recuperan como se especifica en la interfaz de usuario y los servicios web.|  

## <a name="change-user-local-behavior"></a>Cambiar comportamiento de Local del usuario:

A menos que el editor de una solución administrada lo impida, puede cambiar el comportamiento de los campos de fecha personalizados existentes de **Local del usuario** a **Solo fecha** o **Independiente de la zona horaria**. Se trata de un cambio de una sola vez.

Cambiar el comportamiento del campo afecta a los valores de campo que se agregan o modificaron después de cambiar el comportamiento del campo. Los valores de los campos existentes permanecen en la base de datos con el formato de la zona horaria UTC. Para modificar el comportamiento de los valores de campo existentes de UTC a Solo fecha quizá necesite la ayuda de un desarrollador para hacerlo mediante programación. Más información:  [Convertir el comportamiento de valores existentes de fecha y hora en la base de datos](/dynamics365/customer-engagement/developer/behavior-format-date-time-attribute#convert-behavior-of-existing-date-and-time-values-in-the-database). 

> [!WARNING]
> Antes de modificar el comportamiento de un campo de fecha y hora existente, debe comprobar todas las dependencias del campo, como reglas de negocio, flujos de trabajo, campos calculados o campos consolidados, para asegurarse de que no hay problemas como resultado de modificar el comportamiento. Después de modificar el comportamiento de un campo de fecha y hora, debe abrir cada regla de negocio, flujo de trabajo, campo calculado y campo consolidado dependiente del campo que cambió, revisar la información y guardarla, para asegurarse de que se usarán el comportamiento y el valor más recientes del campo de fecha y hora. 

### <a name="change-behavior-during-a-solution-import"></a>Cambiar comportamiento durante la importación de una solución

Cuando importa una solución que contiene un campo de fecha con el comportamiento **Local del usuario** puede tener la opción de cambiar el comportamiento a **Solo fecha** o **Independiente de la zona horaria**.  

### <a name="prevent-changing-behavior"></a>Evitar cambio de comportamiento

Si va a distribuir un campo de fecha personalizado en una solución administrada, puede impedir que las personas que usan la solución cambien el comportamiento configurando la propiedad administrada **CanChangeDateTimeBehavior** a **False**. Más información: [Propiedades administradas de campos](set-managed-properties-metadata.md#field-managed-properties)
  
## <a name="use-cases"></a>Casos de uso

Tenga en cuenta los siguientes casos de uso para los comportamientos **Solo fecha** e **Independiente de la zona horaria**.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>Escenario de Solo fecha: cumpleaños y aniversarios

El comportamiento Solo fecha es correcto para casos cuando la información sobre la hora del día y de zona horaria no es necesaria, por ejemplo cumpleaños o aniversarios. Con esta selección, todos los usuarios de la aplicación de todo el mundo ven el mismo valor exacto de fecha.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>Escenario de Independiente de la zona horaria: registro en el hotel

Puede usar este comportamiento cuando la información de zona horaria no es necesario, como la hora de registro en un hotel. Con esta selección, todos los usuarios de la aplicación de todo el mundo ven el mismo valor exacto de fecha y hora.  


## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>Operadores de consulta de fecha y hora no admitidos en el comportamiento Solo fecha  

Los siguientes operadores de consulta relacionados con fecha y hora no son válidos para el comportamiento **Solo fecha**. Se genera un error de excepción de operador no válido cuando uno de estos operadores se usa en la consulta.  
  
- Más antiguo de X minutos  
- Más antiguo de X horas  
- Últimas X horas  
- Próximas X horas  

  
### <a name="see-also"></a>Vea también

[Crear y editar campos](create-edit-fields.md)<br />
[Definir campos calculados para automatizar los cálculos manuales](define-calculated-fields.md)<br />
[Propiedades administradas de campos](set-managed-properties-metadata.md#field-managed-properties)<br />
[Propiedades administradas](solutions-overview.md#managed-properties)

