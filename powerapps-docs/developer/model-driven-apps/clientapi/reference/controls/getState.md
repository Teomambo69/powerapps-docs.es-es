---
title: getState (referencia API de cliente) en aplicaciones basadas en modelos | Microsoft Docs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 199d1344-351a-44ee-8c43-f6b00b85a793
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getstate-client-api-reference"></a>getState (referencia de la API de cliente)



Devuelve el estado del control de temporizador.

Este método sólo se admite para la [Interfaz unificada](/dynamics365/get-started/whats-new/customer-engagement/new-in-july-2017-update#unified-interface-framework-for-new-apps).. 

## <a name="control-types-supported"></a>Tipos de control admitidos

Temporizador

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).getState();`

## <a name="return-value"></a>Valor devuelto

**Tipo**: Número

**Descripción**: devuelve uno de los siguientes valores:

|Value | Est. |
|--|--|
|1 | Sin establecer|
|2 | En curso|
|3 | Advertencia|
|4 | Infringido|
|5 | Correcto|
|6 | Expirada|
|7 | Cancelada|
|8 | En pausa|

### <a name="related-topics"></a>Temas relacionados

[Controles](../controls.md)
