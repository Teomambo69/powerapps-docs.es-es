---
title: Comportamiento y formato del campo Fecha y hora en Common Data Service | MicrosoftDocs
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
ms.assetid: 73d691c7-344e-4c96-8979-c661c290bf81
caps.latest.revision: 47
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67e172bfcb0a9e1b8cc344892f15e74d070d28fe
ms.sourcegitcommit: c6906775005aec98973b1f5c3dbe5924aff6d26e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "3341499"
---
# <a name="behavior-and-format-of-the-date-and-time-field"></a>Comportamiento y formato del campo de fecha y hora

En Common Data Service, el tipo de datos Fecha y hora se usa en muchos campos de entidad estándar. Dependiendo del tipo de fecha que represente el campo, puede elegir distintos comportamientos del campo: **Local de usuario**, **Solo fecha** o **Independiente de zona horaria**.  
  
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

Si va a distribuir un campo de fecha personalizado en una solución administrada, puede impedir que las personas que usan la solución cambien el comportamiento configurando la propiedad administrada **CanChangeDateTimeBehavior** a **False**. Más información: [Establecer propiedades administradas para campos](set-managed-properties-for-field.md)
  
## <a name="use-cases"></a>Casos de uso 

Tenga en cuenta los siguientes casos de uso para los comportamientos **Solo fecha** e **Independiente de la zona horaria**.

### <a name="date-only-scenario-birthdays-and-anniversaries"></a>Escenario de Solo fecha: cumpleaños y aniversarios

El comportamiento Solo fecha es correcto para casos cuando la información sobre la hora del día y de zona horaria no es necesaria, por ejemplo cumpleaños o aniversarios. Con esta selección, todos los usuarios de la aplicación de todo el mundo ven el mismo valor exacto de fecha.  
  
### <a name="time-zone-independent-scenario-hotel-check-in"></a>Escenario de Independiente de la zona horaria: registro en el hotel

Puede usar este comportamiento cuando la información de zona horaria no es necesario, como la hora de registro en un hotel. Con esta selección, todos los usuarios de la aplicación de todo el mundo ven el mismo valor exacto de fecha y hora.  


## <a name="best-practices-for-using-time-zone"></a>Mejores prácticas para usar la zona horaria

### <a name="for-my-datetime-field-i-was-expecting-utclocal-and-i-am-seeing-the-opposite-value"></a>Para mi campo Fecha / Hora esperaba (UTC / Local) y veo el valor opuesto

Esto se debe a la falta de paridad entre la configuración del campo de la entidad y la configuración del formulario de la aplicación. Cuando un campo de entidad se configura para Zona horaria independiente o Usuario local, determina si se respeta o no la compensación de zona horaria cuando los datos se recuperan de la tienda. Sin embargo, el formulario de la aplicación también tiene una configuración de UTC o Local. 
 
Esto le indica al formulario cómo interpretar los datos que recibe de Common Data Service. Si los datos recuperados de la tienda son independientes de la zona horaria, pero el formulario se establece en local, los datos UTC se mostrarán como hora local del usuario en función de la zona horaria del usuario en su perfil. Lo contrario también es cierto, un valor local de usuario de la tienda se mostrará como UTC si el formulario se establece en UTC. Afortunadamente, los valores de zona horaria de fecha del formulario se pueden modificar sin interrumpir los registros existentes.

### <a name="i-picked-date-only-in-my-entity-field-but-my-form-is-showing-a-time-picker-along-with-the-date"></a>Elegí Solo fecha en el campo de mi entidad, pero mi formulario muestra un selector de hora junto con la fecha

Esto sucedería si elige un comportamiento de zona horaria independiente o local de usuario para su campo de solo fecha. Common Data Service almacenará una hora de 00:00:00 de forma predeterminada, pero si agrega el campo a un formulario, asumirá que también necesita establecer la hora. Si deja los selectores de hora en el formulario, los usuarios pueden ingresar una hora y se guardará como algo diferente de 00:00:00. Cómo puede solucionar esto
* Edite el formulario y elimine el selector de tiempo y las fórmulas asociadas. Esto guardará la hora como 00:00:00 y permitirá los cálculos de fecha basados en la zona horaria.
* Si su campo está configurado actualmente como usuario local, y no necesita la fecha para calcular la zona horaria, puede cambiarla solo a la fecha. Este es un cambio permanente y no se puede deshacer. Este cambio no se puede realizar en los campos de comportamiento independientes de la zona horaria. Siempre tenga cuidado al cambiar los comportamientos ya que otras aplicaciones, complementos o flujos de trabajo pueden depender de los datos.

### <a name="i-have-a-date-only-field-but-it-is-showing-the-wrong-date-for-some-users"></a>Tengo un campo de solo fecha, pero muestra la fecha incorrecta para algunos usuarios
Si esto sucede, verifique el comportamiento configurado para el campo de solo fecha. Si el campo está configurado como zona horaria independiente o local del usuario, la marca de tiempo incluida hará que la fecha aparezca de manera diferente para los diferentes usuarios. La configuración de visualización del formulario de UTC o Local determinará si la fecha que se muestra se calcula utilizando la configuración de zona horaria del usuario o si se muestra como el valor UTC. Cambiar los valores del formulario a UTC en lugar del usuario local evitará los cálculos de desplazamiento de zona horaria y mostrará la fecha UTC para el registro guardado. Alternativamente, si necesita que esta sea una fecha estática que no cambia y el campo es actualmente usuario local, puede cambiar el comportamiento del campo a Solo fecha. Sin embargo, tenga cuidado ya que esto no se puede deshacer.

### <a name="my-scriptplug-in-is-supposed-to-intercept-the-date-submitted-using-the-universal-client-before-the-user-local-conversion-occurs-but-instead-it-is-being-treated-as-user-local-data"></a>Mi (script / plug-in) debe interceptar la fecha de envío utilizando Universal Client antes de que ocurra la conversión local del usuario, pero en su lugar se trata como datos locales del usuario 

El cliente web y el cliente universal tienen comportamientos ligeramente diferentes cuando se trata de cuando los datos se traducen entre UTC y Local de usuario. En el cliente web, las fechas se introducen en el cliente, se pasan a la API según lo provisto y se convierten más tarde a la hora local del usuario. Esto permitió que los scripts / complementos recuperaran los datos y tomaran medidas antes de que los datos se pasaran a los servicios de la plataforma y se tradujeran a la hora local del usuario. En el cliente universal, la traducción de una fecha en valores locales del usuario ocurre antes de que los datos se pasen a la API, debido a esto, los datos proporcionados no serán una fecha UTC sino una fecha local del usuario basada en el usuario que recuperó o publicado. Para resolver esto, un usuario puede:

* Cambiar el formulario a una zona horaria independiente que retendrá el valor UTC. Esto solo funciona si el usuario no necesita que se muestre el formulario en la hora local del usuario.
* Modificar su secuencia de comandos para detectar el desplazamiento de zona horaria utilizado, vuelva a calcular a UTC dentro de la secuencia de comandos y luego tome medidas.

## <a name="date-and-time-query-operators-not-supported-for-date-only-behavior"></a>Operadores de consulta de fecha y hora no admitidos en el comportamiento Solo fecha  

Los siguientes operadores de consulta relacionados con fecha y hora no son válidos para el comportamiento **Solo fecha**. Se genera un error de excepción de operador no válido cuando uno de estos operadores se usa en la consulta.  
  
- Más antiguo de X minutos  
- Más antiguo de X horas  
- Últimas X horas  
- Próximas X horas  

  
### <a name="see-also"></a>Vea también

[Crear y editar campos](create-edit-fields.md)<br />
[Definir campos calculados para automatizar los cálculos manuales](define-calculated-fields.md)<br />
[Propiedades administradas de campos](set-managed-properties-metadata.md#view-and-edit-field-managed-properties)<br />
[Propiedades administradas](/power-platform/alm/managed-properties-alm)  
[Blog: Trabajar con zonas horarias en Common Data Service](https://powerapps.microsoft.com/en-us/blog/working-with-time-zones-in-the-common-data-service/)


