---
title: setShowTime (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 77999c82-3d6a-4db9-af9c-7322491768d9
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setshowtime-client-api-reference"></a>setShowTime (referencia de la API de cliente)



Especifique si un control de fecha debe mostrar la parte de hora de la fecha. 

## <a name="control-types-supported"></a>Tipos de control admitidos

control estándar para atributos **datetime**.

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).setShowTime(bool);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|bool|Boolean|Sí|Especifique true para mostrar la parte horaria de la fecha; false en caso contrario.|

## <a name="remarks"></a>Comentarios

Este método mostrará u ocultará el componente de hora de un control de fecha cuyo atributo usa el formato **DateAndTime**. Este método no tendrán efecto cuando se use el formato de **DateOnly**.

### <a name="related-topics"></a>Temas relacionados

[getShowTime](getShowTime.md)

