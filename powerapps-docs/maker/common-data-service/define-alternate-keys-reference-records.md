---
title: Definir claves alternativas para hacer referencia a registros con Common Data Service | MicrosoftDocs
description: Aprenda a definir claves alternativas que se pueden usar para hacer referencia a registros en Common Data Service
ms.custom: ''
ms.date: 06/04/2019
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
ms.assetid: 29e53691-0b18-4fde-a1d0-7490aa227898
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-alternate-keys-to-reference-records"></a>Definir claves alternativas para hacer referencia a registros

Las *claves alternativas* ofrecen una forma eficaz y precisa de integrar datos con sistemas externos. Es esencial en los casos en que un sistema externo no almacena los Id. de identificador único global (GUID) que identifican de forma única registros en Common Data Service. 

Un sistema de integración de datos usará claves alternativas para identificar de forma exclusiva registros mediante uno o más valores del campo de la entidad que representen una única combinación. Cada clave alternativa tiene un nombre único. 

Por ejemplo, para identificar un registro de cuenta con una clave alternativa, puede usar el número de cuenta o el campo de número de cuenta conjuntamente con otros campos que tienen valores que no deben cambiar.

> [!NOTE]
> Aunque puede definir claves alternativas con PowerApps, solo se pueden usar mediante programación en código. Para obtener más información sobre cómo usar claves alternativas mediante programación, consulte:   
> - [Documentación para desarrolladores: Usar una clave alternativa para crear un registro](/dynamics365/customer-engagement/developer/use-alternate-key-create-record) 
> - [Documentación para desarrolladores: Recuperar un registro con la API web mediante una clave alternativa](/dynamics365/customer-engagement/developer/webapi/retrieve-entity-using-web-api#retrieve-using-an-alternate-key)

Algunas de las ventajas de la característica de claves alternativas:  
  
- Consulta más rápida de los registros.  
- Operaciones de datos en masa más robustas.  
- Programación simplificada con datos importados desde sistemas externos sin identificadores de registro.  
  

## <a name="creating-an-alternate-key"></a>Crear una clave alternativa

Hay dos diseñadores que puede usar para crear claves alternativas:

|Diseñador| Descripción|
|--|--|
|[Portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Proporciona una experiencia fácil y ágil, pero algunas opciones no están disponibles.<br />Más información: [Definir claves alternativas con el portal de PowerApps](define-alternate-keys-portal.md)|
|Explorador de soluciones|No es tan fácil, pero proporciona más flexibilidad para requisitos menos comunes.<br />Más información: [Definir claves alternativas con el explorador de soluciones](define-alternate-keys-solution-explorer.md) |

> [!NOTE]
> También puede crear una clave alternativa en su entorno mediante lo siguiente:
> - Importe una solución que contenga la definición de la clave alternativa.
> - Un desarrollador también puede escribir código para crearlas. Más información: [Documentación para desarrolladores: Definir claves alternativas para una entidad](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)

La información de este tema le ayudará a elegir el diseñador que puede usar. 

Debería usar el [portal de PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) para crear claves alternativas, a menos que necesite satisfacer cualquiera de los siguientes requisitos:

- Crear una clave alternativa en una solución distinta de la solución predeterminada de Common Data Service
- Desea realizar fácilmente un seguimiento del trabajo del sistema que realiza el seguimiento del progreso de creación de los índices de soporte


## <a name="limits-in-creating-alternate-keys"></a>Límites al crear claves alternativas

Hay restricciones a la hora de crear una clave alternativa.

### <a name="fields-that-can-be-used-for-alternate-keys"></a>Campos que se pueden usar para las claves alternativas

Solo estos tipos de campos se pueden usar para crear claves alternativas:
 - Decimal
 - Número entero (entero)
 - Una sola línea de texto (cadena)
 - Fecha y hora
 - Búsqueda
 - Conjunto de opciones

### <a name="number-of-keys"></a>Número de claves

Puede definir hasta cinco claves diferentes para una entidad.
 
### <a name="valid-key-size"></a>Tamaño de clave válido

Cuando se crea una clave, el sistema valida que la plataforma puede admitir la clave, incluido que el tamaño total de la clave no infringe restricciones de índice basadas en SQL como 900 bytes por clave y 16 columnas por clave. Si el tamaño de la clave no cumple las restricciones, un mensaje de error se mostrará.

### <a name="unicode-characters-in-key-value"></a>Caracteres Unicode en valor de clave

Si los datos en un campo que se usa en una clave alternativa contienen uno de los caracteres siguientes `<`,`>`,`*`,`%`,`&`,`:`,`/`,`\\` las acciones de revisión o upsert no funcionarán. 

Si solo necesita unicidad, este método funciona, pero si necesita usar estas claves como parte de la integración de datos, entonces es mejor crear la clave en los campos que no tendrán datos con dichos caracteres.

## <a name="track-the-status-of-the-creation-of-the-alternate-key"></a>Seguir el estado de creación de la clave alternativa

Cuando se crea una clave alternativa, se iniciará un trabajo del sistema para crear índices en las tablas de base de datos para aplicar restricciones exclusivas en los campos que se usan en la clave alternativa. La clave alternativa no surtirá efecto hasta que se creen estos índices. La creación de estos índices puede tardar más tiempo en función de la cantidad de datos del sistema. 

El estado del trabajo del sistema determina el estado de la clave alternativa. La clave alternativa puede tener los siguientes estados:
- **Pendiente**
- **En curso**
- **Active**
- **Con error**

Cuando se completa el trabajo del sistema, el estado de la clave alternativa es **Activo** y está disponible para su uso.

Si se produce un error en el trabajo del sistema, busque el trabajo del sistema para ver los errores. El trabajo del sistema tendrá un nombre que sigue este patrón: `Create index for {0} for entity {1}` donde `0` es el **Nombre para mostrar** de la clave alternativa y `1` es el nombre de la entidad.


> [!NOTE]
> Si desea supervisar el estado del trabajo del sistema debe usar el explorador de soluciones para crear el índice. Incluirá un vínculo al trabajo del sistema para poder supervisarlo. Más información: [(Opcional) Ver el seguimiento del trabajo del sistema de creación de índices](define-alternate-keys-solution-explorer.md#optional-view-the-system-job-tracking-creation-of-indexes)
  
  
### <a name="see-also"></a>Vea también  

[Definir claves alternativas con el portal de PowerApps](define-alternate-keys-portal.md)<br />
[Definir claves alternativas usando el explorador de soluciones](define-alternate-keys-solution-explorer.md)<br />
[Documentación para desarrolladores: Definir claves alternativas para una entidad](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)<br />
[Documentación para desarrolladores: Usar una clave alternativa para crear un registro](/dynamics365/customer-engagement/developer/use-alternate-key-create-record)
