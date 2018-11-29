---
title: addOption (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9798f168-7b94-411d-9aed-6471042ff11a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addoption-client-api-reference"></a>addOption (referencia de la API de cliente)



Agrega una opción a un control. 

## <a name="control-types-supported"></a>Tipos de control admitidos

OptionSet, MultiSelectOptionSet

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).addOption(option, index);`

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|opción |Objeto |Sí|La opción a agregar. El objeto contiene los siguientes atributos:<br/>**- text**: cadena. La etiqueta de la opción.<br/>**- value**: número. El valor de la opción.|
|index |Número |No|La posición de índice para poner la nueva opción. Si no se proporciona, la opción se agregará al final.|

### <a name="related-topics"></a>Temas relacionados

[clearOptions](clearOptions.md)

[removeOption](removeOption.md)