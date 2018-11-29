---
title: addOnChange (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
description: Obtenga información sobre el método de addOnchange para atributos para establecer una función a la que se llamará cuando se cambia el valor del atributo.
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonchange-client-api-reference"></a>addOnChange (referencia de la API de cliente)



Establece una función a la que se debe llamar cuando se produce el evento **OnChange**.

## <a name="attribute-types-supported"></a>Tipos de atributos compatibles

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getAttribute(arg).addOnChange(myFunction)`

## <a name="parameters"></a>Parámetros

| Nombre de parámetro| Tipo| Descripción  |
| --------|-----------| -----|
|myFunction| Referencia de funciones| Especifica la función que se ejecutará en el evento **OnChange** para atributos. El [contexto de ejecución](../../clientapi-execution-context.md) se pasa automáticamente como el primer parámetro a esta función.|


### <a name="related-topics"></a>Temas relacionados

[removeOnChange](removeOnChange.md)

[Evento de atributo OnChange](../events/attribute-onchange.md)





