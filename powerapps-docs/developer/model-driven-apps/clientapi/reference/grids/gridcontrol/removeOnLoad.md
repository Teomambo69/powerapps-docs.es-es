---
title: removeOnLoad (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonload-client-api-reference"></a>removeOnLoad (referencia de la API de cliente)



[!INCLUDE[./includes/removeOnLoad-description.md](./includes/removeOnLoad-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas de solo lectura

## <a name="syntax"></a>Sintaxis

`gridContext.removeOnLoad(myFunction);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|myFunction|referencia de funciones|Sí|La función que se quitará del evento **OnLoad**.

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).

### <a name="related-topics"></a>Temas relacionados

[addOnLoad](addOnLoad.md) 


