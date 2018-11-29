---
title: getEntityTypes (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c20ba958-821f-4168-a518-e39431603b28
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentitytypes-client-api-reference"></a>getEntityTypes (referencia de la API de cliente)



Obtiene los tipos de entidades permitidas en el control de búsqueda. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Control de búsqueda

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getEntityTypes();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: matriz de cadena

**Descripción**: nombres lógicos de las entidades permitidas en este control.

### <a name="related-topics"></a>Temas relacionados

[setEntityTypes](setEntityTypes.md)
