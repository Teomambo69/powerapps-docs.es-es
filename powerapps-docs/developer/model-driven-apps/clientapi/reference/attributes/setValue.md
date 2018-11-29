---
title: setValue (referencia de la API de cliente)| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1324b465-6012-47d4-bf35-837df82014cb
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setvalue-client-api-reference"></a>setValue (referencia de la API de cliente)

Establece el valor de los datos de un atributo. 

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).setValue(value)`

# <a name="parameters"></a>Parámetros
Depende del tipo de atributo.

<!-- TODO: 

Change type links from msdn to docs, i.e. https://msdn.microsoft.com/library/dwab3ed2.aspx to /scripting/javascript/reference/number-object-javascript 

or MDN https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number
-->

| Tipo de atributo|Tipo de parámetros|
-------|------|
| Booleano| [Booleano](https://msdn.microsoft.com/library/t7bkhaz6.aspx) |
| datetime|[Fecha](https://msdn.microsoft.com/library/cd9w2te4.aspx)|
| decimal| [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| doble| [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx) |
| Entero|[Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| búsqueda  | [Matriz](https://msdn.microsoft.com/library/k4h76zbx.aspx) Una matriz de objetos de búsqueda. <br/><br/>Algunas búsquedas, llamadas búsquedas "partylist", permiten asociar varios registros en una búsqueda, como el campo **Para:** para un registro de entidad de correo electrónico. Por consiguiente, todos los valores de los datos de búsqueda usan una matriz de objetos de búsqueda, incluso cuando el atributo de búsqueda no admite que se agregue más de una referencia de registro.<br/><br/>Cada búsqueda tiene las siguientes propiedades:<br/>- *entityType*: cadena. El nombre de la entidad mostrada en la búsqueda.<br/>- *id*: Cadena: La representación de cadena del valor de GUID para el registro mostrado en la búsqueda. El valor debe coincidir con el siguiente formato: {XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}<br/>- *name*: Cadena: El texto que representa el registro que se mostrará en la búsqueda.|
| memo  | [Cadena](https://msdn.microsoft.com/library/ecczf11c.aspx)  |
| money| [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| optionset | [Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)  |
| cadena | [Cadena](https://msdn.microsoft.com/library/ecczf11c.aspx)|
| memo | [Cadena](https://msdn.microsoft.com/library/ecczf11c.aspx)|
| money|[Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)|
| optionset, multiselectoptionset|[Número](https://msdn.microsoft.com/library/dwab3ed2.aspx)<br/><br/>El método [getOptions](getOptions.md) devuelve valores de opción como cadenas. Debe usar [parseInt](https://msdn.microsoft.com/library/x53yedee.aspx) para convertirlas a números para poder usar esos valores para establecer el valor de un atributo optionset. Las opciones válidas statuscode (razón para el estado) dependen del statecode actual del registro. El campo statecode (Estado) no se puede establecer en scripts de formularios. Para saber qué valores de statecode son válidos, consulte los metadatos para los atributos. <!-- See [Default status and status reason values](../../../customize/default-status-and-status-reason-values.md) for a list of default values for system entities. --> Para las entidades personalizadas use el explorador de los metadatos. Finalmente, considere también cualquier transición de estado personalizada que se haya aplicado al campo. Más información: [Definir transiciones de razón para el estado](/dynamics365/customer-engagement/customize/define-status-reason-transitions).| 
| String| [Cadena](https://msdn.microsoft.com/library/ecczf11c.aspx) <br/><br/> Un campo de cadena con el formato de correo electrónico requiere que la cadena represente una dirección de correo electrónico válida.|


> [!NOTE]
> Actualizar un atributo mediante **setValue** no hace que los controladores de eventos de **OnChange** se ejecuten. Si desea que los controladores de evento **OnChange** se ejecuten debe usar [fireOnChange](../attributes/fireOnChange.md) además de **setValue**. <br/><br/>
Cuando las aplicaciones basadas en modelos de Microsoft para tablets no están conectadas al servidor, **setValue** no funcionará.<br/><br/>No puede establecer el valor atributos compuestos. Más información: [Escribir scripts para atributos compuestos](../composite-attributes.md).

### <a name="related-topic"></a>Tema relacionado
[getValue (Referencia de API de cliente)](getValue.md)
