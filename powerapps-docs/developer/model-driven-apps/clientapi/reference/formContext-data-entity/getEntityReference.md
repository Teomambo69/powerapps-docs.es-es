---
title: getEntityReference (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1a66f93d-a47c-4316-91f1-dcf5d09f9d19
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentityreference-client-api-reference"></a>getEntityReference (referencia de la API de cliente)



[!INCLUDE[./includes/getEntityReference-description.md](./includes/getEntityReference-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.entity.getEntityReference();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: objeto de búsqueda.

**Descripción**: el objeto devuelto tiene los siguientes tres atributos:

- **entityType**: cadena. El nombre lógico del registro de entidad. Por ejemplo, "cuenta".
- **id**: cadena. El valor de GUID del registro de entidad.
- **name**: cadena (opcional). Nombre del registro de entidad. 



