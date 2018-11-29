---
title: refreshRibbon (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: dbd43d7b-c9b0-4ca5-943d-dd813d3bb049
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="refreshribbon-client-api-reference"></a>refreshRibbon (referencia de la API de cliente)



[!INCLUDE[./includes/refreshRibbon-description.md](./includes/refreshRibbon-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.ui.refreshRibbon(refreshAll);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|refreshAll|Boolean|No|Indica si se han actualizado todas las barras de comando de la cinta de opciones en la página actual. Si especifica **false**, solo se ha actualizado la barra de comandos de la cinta de opciones de nivel de página. Si no especifica este parámetro, se pasa **false** de forma predeterminada.|

## <a name="remarks"></a>Comentarios

 Esta funcionalidad se suele usar cuando una cinta de opciones <EnableRule> (RibbonDiffXml) depende de un valor en el formulario. Después de que el código cambie un valor usado por una regla, use este método para forzar a la cinta de opciones a reevaluar los datos del formulario para poder aplicar la regla.

### <a name="related-topics"></a>Temas relacionados

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)

