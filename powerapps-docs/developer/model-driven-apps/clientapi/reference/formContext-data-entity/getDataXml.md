---
title: getDataXml (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
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
# <a name="getdataxml-client-api-reference"></a>getDataXml (referencia de la API de cliente)



[!INCLUDE[./includes/getDataXml-description.md](./includes/getDataXml-description.md)]

## <a name="syntax"></a>Sintaxis

`formContext.data.entity.getDataXml();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Cadena.

**Descripción**: en este ejemplo, se actualizaron los siguientes tres campos de un registro de cuenta: nombre, número de cuenta y teléfono 2.

```"<account><name>Contoso</name><accountnumber>55555</accountnumber><telephone2>425 555-1234</telephone2></account>"```

## <a name="remarks"></a>Comentarios

Este método no funciona con Microsoft Dynamics 365 para tabletas.



