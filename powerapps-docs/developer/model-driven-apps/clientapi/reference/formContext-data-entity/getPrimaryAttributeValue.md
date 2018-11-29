---
title: getPrimaryAttributeValue (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getprimaryattributevalue-client-api-reference"></a>getPrimaryAttributeValue (referencia de la API de cliente)



[!INCLUDE[./includes/getPrimaryAttributeValue-description.md](./includes/getPrimaryAttributeValue-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.entity.getPrimaryAttributeValue();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena.

**Descripción**: el nombre para mostrar de la entidad.

## <a name="remarks"></a>Comentarios

Cada entidad tiene un atributo de cadena que está designado como <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.PrimaryNameAttribute>. El valor para este atributo se usa cuando se muestran los vínculos al registro.



