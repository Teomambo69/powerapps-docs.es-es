---
title: refreshParentGrid (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="refreshparentgrid-client-api-reference"></a>refreshParentGrid (referencia de la API de cliente)



[!INCLUDE[./includes/refreshParentGrid-description.md](./includes/refreshParentGrid-description.md)] 

## <a name="syntax"></a>Sintaxis

`Xrm.Utility.refreshParentGrid(lookupOptions)`

## <a name="parameters"></a>Parámetros

**lookupOptions**: un objeto con las propiedades siguientes para especificar el registro:

|Nombre de la propiedad |Tipo |Obligatoria  |Descripción |
|---|---|---|---|
|entityType|String|Sí |Tipo de entidad del registro.|
|id.|String|Sí |Identificador del registro.|
|nombre|String|No |Nombre del registro.|

### <a name="related-topics"></a>Temas relacionados

[Xrm.Utility](../xrm-utility.md)



