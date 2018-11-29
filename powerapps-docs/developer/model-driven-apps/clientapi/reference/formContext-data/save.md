---
title: save (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="save-client-api-reference"></a>Guardar (referencia de la API de cliente)



[!INCLUDE[./includes/save-description.md](./includes/save-description.md)]

También puede establecer un objeto para controlar cómo se procesan los registros de cita, cita periódica o actividad de servicio.

## <a name="syntax"></a>Sintaxis

`formContext.data.save(saveOptions).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parámetros

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|saveOptions|Objeto|No|Un objeto para especificar las opciones para guardar el registro. El objeto  tiene los siguientes atributos:<br/><br/>- **saveMode**: (Opcional) Número. Especifique un valor que indique cómo se inició el evento guardar. Para obtener una lista de valores compatibles, consulte el valor de retorno del método [getSaveMode](../save-event-arguments/getsavemode.md). Tenga en cuenta que configurar el parámetro **saveMode** no inicial realmente la acción correspondiente; solo sirve para proporcionar información a los controladores de eventos **OnSave** sober el motivo de la operación guardar.<br/><br/>- **useSchedulingEngine**: (Opcional) Booleano. Indique si van a usarse mensajes **Book** o **Reschedule** en lugar de los mensajes **Create** o **Update**. Esta opción solo está disponible cuando se usa con registros de cita, cita periódica o actividad de servicio.|
|successCallback|Función|No|Una función para llamar a la operación es correcta.|
|errorCallback|Función|No|Una función para llamar cuando la operación tiene error. Se pasará un objeto con las siguientes propiedades:<br/><br/>- **errorCode**: Número. Código de error.<br/><br/>- **message**: Cadena. Mensaje de error localizado.|


### <a name="related-topics"></a>Temas relacionados

[formContext.data.entity.save](../formContext-data-entity/save.md)

[formContext](../../clientapi-form-context.md)

