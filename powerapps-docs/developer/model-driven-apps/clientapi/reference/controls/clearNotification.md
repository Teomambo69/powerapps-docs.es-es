---
title: clearNotification (referencia API de cliente) en aplicaciones basadas en modelo| Microsoft Docs
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
# <a name="clearnotification-client-api-reference"></a>clearNotification (referencia de la API de cliente)



Eliminar un mensaje que ya se muestra para un control.

## <a name="control-types-supported"></a>Tipos de control admitidos

Todas

## <a name="syntax"></a>Sintaxis

`formContext.getControl(arg).clearNotification(uniqueId);`

## <a name="parameters"></a>Parámetros

|Nombre | Tipo | Obligatoria | Descripción|
|--|--|--|--|
|uniqueId |String |No|El identificador que se usará para borrar un mensaje específico que se estableció usando **setNotification** o **addNotification**. Si no se especifica el parámetro **uniqueId**, se quitará la notificación actual mostrada.| 


## <a name="return-value"></a>Valor devuelto

**Tipo**: booleano 

**Description**: indica si el método se realizó correctamente. 

### <a name="related-topics"></a>Temas relacionados

[addNotification](addNotification.md)

[setNotification](setNotification.md)