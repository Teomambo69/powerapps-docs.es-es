---
title: setDisabled (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 86383cb1-c4c8-4e82-9f60-1dc4588b519d
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setdisabled-client-api-reference"></a>setDisabled (referencia de la API de cliente)



Establece si el control está deshabilitado.

## <a name="control-types-supported"></a>Tipos de control admitidos

Todos excepto tipo de control **kbsearch**

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).setDisabled(bool);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|bool|Boolean|Sí|Especifique **true** o **false** para habilitar o inhabilitar el control.|

### <a name="related-topics"></a>Temas relacionados

[getDisabled](getDisabled.md)



