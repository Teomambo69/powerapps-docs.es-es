---
title: setEntityTypes (referencia API de cliente) en aplicaciones basadas en modelo| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 93154168-1e9f-4849-b4bb-be8804f86f81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setentitytypes-client-api-reference"></a>setEntityTypes (referencia de la API de cliente)



Establece los tipos de entidades permitidas en el control de búsqueda.

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).setEntityTypes([entityLogicalNames]);`

## <a name="parameter"></a>Parámetro

|Nombre|Tipo|Obligatoria|Descripción|
|--|--|--|--|
|entityLogicalNames|Matriz de cadena|Sí|Especifique el nombre lógico de las entidades permitidas en el control de búsquedas.|

### <a name="related-topics"></a>Temas relacionados

[getEntityTypes](getEntityTypes.md)

 


