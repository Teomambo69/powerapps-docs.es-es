---
title: getShowTime (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 43341b96-ca2c-4c7e-b6d5-fe7a5fd3c8b2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getshowtime-client-api-reference"></a>getShowTime (referencia de la API de cliente)



Obtenga si un control de fecha muestra la parte de hora de la fecha. 

## <a name="control-types-supported"></a>Tipos de control admitidos

control estándar para atributos **datetime**.

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getShowTime();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: booleano

**Descripción**: true si muestra la parte horaria de la fecha; false en caso contrario.

### <a name="related-topics"></a>Temas relacionados

[setShowTime](setShowTime.md)

