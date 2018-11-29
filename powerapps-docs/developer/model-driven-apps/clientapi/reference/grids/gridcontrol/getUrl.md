---
title: getUrl (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f2023d7d-5877-4436-abe6-e81ca68b8ec0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="geturl-client-api-reference"></a>getUrl (referencia de la API de cliente)



[!INCLUDE[./includes/getUrl-description.md](./includes/getUrl-description.md)]

## <a name="grid-types-supported"></a>Tipos de cuadrícula admitidos

Cuadrículas editables y de solo lectura

## <a name="syntax"></a>Sintaxis

`gridContext.getUrl(client);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|cliente|Número|No|Indica el tipo de cliente. Puede especificar uno de los siguientes valores:<br/>0: Explorador<br/>1: Aplicación móvil|

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena

**Descripción**: la dirección URL del control de cuadrícula actual.

## <a name="remarks"></a>Comentarios

Para obtener `gridContext`, consulte [Obtener el contexto de cuadrícula](../../grids.md#bkmk_gridcontext).



