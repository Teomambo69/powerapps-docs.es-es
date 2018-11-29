---
title: formContext.data (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
description: Aprenda a trabajar con procesos en aplicaciones basadas en modelos mediante la API de cliente.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextdata-client-api-reference"></a>formContext.data (referencia de la API de cliente)



Proporciona propiedades y métodos para trabajar con los datos en un formulario.

![Modelo de objeto de datos formContext](../../media/ClientAPI-formContext-data-Model.png)

## <a name="properties"></a>Propiedades

|Nombre|Descripción|
|--|--|
|atributos|Recopilación de datos sin entidad en el formulario. Los elementos de esta recopilación son del mismo tipo que la recopilación de atributos, pero no son atributos de la entidad de formulario. <br/>Más información: [Recopilaciones](collections.md).|
|entidad|Proporciona métodos para recuperar información específica del registro que se muestra en la página, el método save y una recopilación de todos los atributos incluidos en el formulario. Los datos del atributo están limitados a los atributos representados por campos en el formulario. <br/>Más información: [formContext.data.entity](formContext-data-entity.md)|
|proceso|Proporciona objetos y métodos para interactuar con los datos del flujo de proceso de negocio en un formulario.<br/>Más información: [formContext.data.process](formContext-data-process.md)|


## <a name="methods"></a>Métodos 

|Nombre|Descripción|
|--|--|
|[addOnLoad](formContext-data/addOnload.md)|[!INCLUDE[formContext-data/includes/addOnLoad-description.md](formContext-data/includes/addOnLoad-description.md)]|
|[getIsDirty](formContext-data/getIsDirty.md)|[!INCLUDE[formContext-data/includes/getIsDirty-description.md](formContext-data/includes/getIsDirty-description.md)]|
|[isValid](formContext-data/isValid.md)|[!INCLUDE[formContext-data/includes/isValid-description.md](formContext-data/includes/isValid-description.md)]|
|[actualizar](formContext-data/refresh.md)|[!INCLUDE[formContext-data/includes/refresh-description.md](formContext-data/includes/refresh-description.md)]|
|[removeOnLoad](formContext-data/removeOnLoad.md)|[!INCLUDE[formContext-data/includes/removeOnLoad-description.md](formContext-data/includes/removeOnLoad-description.md)]|
|[save](formContext-data/save.md)|[!INCLUDE[formContext-data/includes/save-description.md](formContext-data/includes/save-description.md)]|


### <a name="related-topics"></a>Temas relacionados

[formContext.data.entity](formContext-data-entity.md)

[formContext.data.process](formContext-data-process.md)




