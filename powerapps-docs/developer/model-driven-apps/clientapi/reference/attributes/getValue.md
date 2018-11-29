---
title: getValue (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: acc78a1e-212a-4eef-88c5-8272f9ba3009
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getvalue-client-api-reference"></a>getValue (referencia de la API de cliente)

Recupera el valor de los datos de un atributo.

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).getValue()`

## <a name="return-value"></a>Valor devuelto

**Tipo**: depende del tipo de atributo. 

| Tipo de atributo | Tipo devuelto| 
|----|-----|
| Booleano | [Booleano](https://msdn.microsoft.com/library/t7bkhaz6.aspx) |
| datetime| [Fecha](https://msdn.microsoft.com/library/cd9w2te4.aspx)<br/> Para obtener la versión de la cadena de una fecha utilizando las preferencias de configuración regional del usuario de PowerApps, use los métodos [format](https://msdn.microsoft.com/library/bb384009.aspx) y [localeFormat](https://msdn.microsoft.com/library/bb383816.aspx). Otros métodos formatearán las fechas con la configuración regional del sistema operativo en lugar de las preferencias de configuración regional de PowerApps del usuario. | 
| decimal| [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)| 
| Doble | [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)| 
| entero | [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| búsqueda | [Matriz](https://msdn.microsoft.com/library/k4h76zbx.aspx) <br/>Una matriz de objetos de búsqueda.<br/><br/>NOTA: Algunas búsquedas permiten asociar varios registros en una búsqueda, como el campo Para: de un registro de entidad de correo electrónico. Por consiguiente, todos los valores de los datos de búsqueda usan una matriz de objetos de búsqueda, incluso cuando el atributo de búsqueda no admite que se agregue más de una referencia de registro. <br/><br/>Cada búsqueda tiene las siguientes propiedades:<br/>- *entityType*: cadena. El nombre de la entidad mostrada en la búsqueda.<br/>- *id*: (cadena) la representación de cadena del valor de GUID para el registro mostrado en la búsqueda.<br/>- *name*: (cadena) el texto que representa el registro que se mostrará en la búsqueda.|
| memo  | [Cadena](https://msdn.microsoft.com/library/ecczf11c.aspx)  |
| money| [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| optionset | [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| cadena | [Cadena](https://msdn.microsoft.com/library/ecczf11c.aspx) |


### <a name="related-topic"></a>Tema relacionado
[setValue (referencia de la API de cliente)](setValue.md)
